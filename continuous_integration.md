# Continuous Integration

Once you have tests in your projects, you may want to automatically run them at any time a change is pushed by a developer. Continuous Integration goal is to run these automated tests, and even launch an automated build of your project.

## Using CircleCI

CircleCI is a Continuous Integration service that is available for free. The way it works is quite simple and similar to most CI services: each time a commit is pushed to a branch in your git repository, CircleCI provisions a new, blank, machine. Your project is then cloned on it, installed and tests are run.

### Open an account on CircleCI.

Go to https://circleci.com/.
TODO

### Add your project

TODO

### Enjoy

CircleCI will try to infere most settings that you need. For projects using npm, it will launch `npm install` and then `run test`.

### Override the settings

TODO