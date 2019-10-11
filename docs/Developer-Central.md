[](Main-hub-for-all-technical-developer-and-coding-information.)

This page serves as a central nexus for information on using Evennia as well as developing the library itself.

### General Evennia development information

- [Introduction to coding with Evennia](Coding-Introduction)
- [Evennia Licensing FAQ](Licensing.md)
- [Contributing to Evennia](Contributing.md)
- [Code Style Guide](https://github.com/evennia/evennia/blob/master/CODING_STYLE.md) (Important!)
- [Policy for 'MUX-like' default commands](Using-MUX-As-a-Standard)
- [Setting up a Git environment for coding](Version-Control)
- [Getting started with Travis and Github for continuous integration testing](Using-Travis)
- [Planning your own Evennia game](Game-Planning)
- [First steps coding Evennia](First-Steps-Coding)
- [Translating Evennia](Internationalization#translating-evennia)
- [Evennia Quirks](Quirks.md) to keep in mind.
- [Directions for configuring PyCharm with Evennia on Windows](Setting-up-PyCharm)

### Evennia API

- [Directory Overview](Directory-Overview)
- [evennia - the flat API](Evennia-API)
  - [Running and Testing Python code](Execute-Python-Code)

#### Core components and protocols

- [Server and Portal](Portal-and-Server)  
  - [Sessions](Sessions.md)
  - [Configuration and module plugins](Server-Conf)
- [The message path](Messagepath.md)
  - [OOB](OOB.md) - Out-of-band communication
  - [Inputfuncs](Inputfuncs.md)
  - [Adding new protocols (client APIs) and services](Custom-Protocols)
- [Adding new database models](New-Models)
- [Running and writing unit tests](Unit-Testing)
- [Running profiling](Profiling.md) 
- [Debugging your code](Debugging.md)

#### In-game Commands

- [Command System overview](Command-System)
- [Commands](Commands.md) 
- [Command Sets](Command-Sets)
- [Command Auto-help](Help-System#command-auto-help-system)

#### Typeclasses and related concepts

- [General about Typeclasses](Typeclasses.md)
- [Objects](Objects.md)
  - [Characters](Objects#characters)
  - [Rooms](Objects#rooms)
  - [Exits](Objects#exits)
- [Accounts](Accounts.md)
- [Communications](Communications.md)
  - [Channels](Communications#channels)
- [Scripts](Scripts.md)
  - [Global Scripts](Scripts#Global-Scripts)
  - [TickerHandler](TickerHandler.md)
  - [utils.delay](https://github.com/evennia/evennia/wiki/Coding-Utils#utilsdelay)
  - [MonitorHandler](MonitorHandler.md)
- [Attributes](Attributes.md)
- [Nicks](Nicks.md)
- [Tags](Tags.md)
  - [Tags for Aliases and Permissions](Tags#using-aliases-and-permissions)

#### Other systems

- [Locks](Locks.md)
   - [Permissions](Locks#permissions)
- [Help System](Help-System)
- [Signals](Signals.md)
- [Web](Web-features)
   - [Web tutorials](Web-tutorial)
- [General coding utilities](Coding-Utils)
   - [Utils in evennia.utils.utils](evennia.utils.utils)
- [Game time](Coding-Utils#game-time)
- [Game Menus](EvMenu.md) (EvMenu)
- [Text paging/scrolling](EvMore) (EvMore)
- [Text Line Editor](EvEditor.md) (EvEditor)
- [Text Tables](https://github.com/evennia/evennia/wiki/evennia.utils.evtable) (EvTable)
- [Text Form generation](https://github.com/evennia/evennia/wiki/evennia.utils.evform) (EvForm)
- [Spawner and Prototypes](https://github.com/evennia/evennia/wiki/Spawner-and-Prototypes)
- [Inlinefuncs](TextTags#inline-functions)
- [Asynchronous execution](Async-Process)

### Developer brainstorms and whitepages

- [API refactoring](API-refactoring), discussing what parts of the Evennia API needs a refactoring/cleanup/simplification
- [Docs refactoring](Docs-refactoring), discussing how to reorganize and structure this wiki/docs better going forward
- [Webclient brainstorm](Webclient-brainstorm), some ideas for a future webclient gui
- [Roadmap](Roadmap.md), a tentative list of future major features
- [Change log](https://github.com/evennia/evennia/blob/master/CHANGELOG.md) of big Evennia updates over time


[group]: https://groups.google.com/forum/#!forum/evennia
[online-form]: https://docs.google.com/spreadsheet/viewform?hl=en_US&formkey=dGN0VlJXMWpCT3VHaHpscDEzY1RoZGc6MQ#gid=0 
[issues]: https://github.com/evennia/evennia/issues
