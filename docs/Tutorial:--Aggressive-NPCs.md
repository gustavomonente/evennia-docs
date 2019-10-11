[](A-tutorial-on-making-NPC's-do-things-(like-attack)-when-a-character-enters.)

This tutorial shows the implementation of an NPC object that responds to characters entering their location. In this example the NPC has the option to respond aggressively or not, but any actions could be triggered this way.

One could imagine using a [Script](Scripts.md) that is constantly checking for newcomers. This would be highly inefficient (most of the time its check would fail). Instead we handle this on-demand by using a couple of existing object hooks to inform the NPC that a Character has entered.

It is assumed that you already know how to create custom room and character typeclasses, please see the [Basic Game tutorial](https://github.com/evennia/evennia/wiki/Tutorial%20for%20basic%20MUSH%20like%20game) if you haven't already done this.

What we will need is the following: 

- An NPC typeclass that can react when someone enters
- A custom [Room](Objects.md) typeclass that can tell the NPC that someone entered
- We will also tweak our default `Character` typeclass a little. 

To begin with, we need to create an NPC typeclass.

```python
# mygame/typeclasses/npc.py

from characters import Character 

class Npc(Character):
    """
    A NPC typeclass which extends the character class.
    """
    def at_char_entered(self, character):
        """
         A simple is_aggressive check. 
         Can be expanded upon later.
        """       
        if self.db.is_aggressive:
            self.execute_cmd("say Graaah, die %s!" % character)
        else:
            self.execute_cmd("say Greetings, %s!" % character)
```

We will define our custom `Character` typeclass below. As for the new `at_char_entered` method we've just defined, we'll ensure that it will be called by the room where the NPC is located, when a player enters that room.  You'll notice that right now, the NPC merely speaks.  You can expand this part as you like and trigger all sorts of effects here (like combat code, fleeing, bartering or quest-giving) as your game design dictates.

Now your room typeclass needs to have the following added:

```python
# mygame/typeclasses/rooms.py

from evennia import utils
from characters import Character
from npc import Npc

    # ... inside your Room typeclass ...
    def at_object_receive(self, obj, source_location):
        if utils.inherits_from(obj, 'Npc'): # An NPC has entered
            pass
        else:
            if utils.inherits_from(obj, 'Character'): 
                # A PC has entered, NPC is caught above.
                # Cause the character to look around
                obj.execute_cmd('look')
                for item in self.contents:
                    if utils.inherits_from(item, 'Npc'): 
                        # An NPC is in the room
                        item.at_char_entered(obj)
```

Take particular note of the inherits at the top of this section, you'll need to ensure that they correctly point to your default `Character` class as well as the newly created `Npc` class.

> Note:  [at_object_receive](https://github.com/evennia/evennia/wiki/evennia.objects.objects#defaultroomat_object_receive) is a default hook of the `DefaultObject` typeclass (and its children). Here we are overriding this hook in our customized room typeclass to suit our needs. 

This room checks the typeclass of objects entering it (using `utils.inherits_from` and responds to `Characters`, ignoring other NPCs or objects.  When triggered the room will look through its contents and inform any `Npc`s inside by calling their `at_char_entered` method.

You'll also see that we have added a 'look' into this code, this is because by default the `at_object_receive` is carried out *before* the characters' `at_after_move` which, we will now overload.  This meant that a character entering would see the NPC perform its actions before the 'look' command. So we deactivate the look in our default `Character` class: 

```python
# mygame/typeclasses/characters.py

    # inside the character class
    def at_after_move(self, source_location):
        """
        Default is to look around after a move 
        Note:  This has been moved to room.at_object_receive
        """
        #self.execute_cmd('look')
        pass
```

Now that's done, let's create an NPC and make it aggressive.

```
@reload
@create/drop Orc:npc.Npc
```

(you could also give the path as `typeclasses.npc.Npc`, but Evennia will look into the `typeclasses` folder automatically so this is a little shorter). 

When you enter the aggressive NPC's location, it will default to using its peaceful action (say your name is Anna):

```
Orc says, "Greetings, Anna!"
```

Now we turn on the aggressive mode (we do it manually but it could also be triggered by some sort of AI code). 

```
@set orc/is_aggressive = True
```

Now it will perform its aggressive action whenever a character enters.

```
Orc says, "Graaah, die, Anna!"
```
