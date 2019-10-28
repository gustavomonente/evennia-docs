# evennia-docs
Documentation for the Evennia MUD creation system.

## Building the documentation

You require Python (ideally Python3.7) and the [Mkdocs](https://www.mkdocs.org/) static site generator.

  1. clone this repo, then `cd` to it. It's a good idea to activate a virtualenv.
  2. `pip install -r requirements.txt`
  3. `mkdocs build` - this generates a new local `site/` directory.
  4. `mkdocs serve` - You should now be able to go to `http://localhost:8000` to see the docs in your browser.

Deployment, for those with commit rights:

  1. Pull the latest `master` branch, activate environment.
  2. run `mkdocs gh-deploy` to build and deploy to the online static stite on github. 
  
The site will be available at `https://evennia.github.io/evennia-docs`.
