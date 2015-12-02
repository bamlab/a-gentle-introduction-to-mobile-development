# Continuous Integration

Once you have tests in your projects, you may want to automatically run them at any time a change is pushed by a developer. Continuous Integration goal is to run these automated tests and even launch an automated build of your project.

## Setting up CircleCI

CircleCI is a Continuous Integration service that is available for free. The way it works is quite simple and similar to most CI services: each time a commit is pushed to a branch in your git repository, CircleCI provisions a new, blank, machine. Your project is then cloned on it, installed and tests are run.

### Open an account on CircleCI.

Go to https://circleci.com/ noob.

### Add your project

**[TODO insert image]**

### Enjoy the builds

CircleCI will try to infere most settings that you need. For projects using *Node.js* and *npm*, it will launch `npm install` and then `run test`.

Anytime you push a new commit/branch to your git repository, CircleCI will launch a new build. By default, you're notified by mail if something went wrong.

### Override the settings with `circle.yml`

Most of the time, the settings infered by CircleCI aren't adapted to your project. You may want to run a particular script before installing dependencies or install fixtures if you're testing a backend.  

These settings can be added and changed in a configuration file called `circle.yml`, stored at the root of your repository.

#### Example 1: using a different Node version

If your project is using a particular version of Node, you can ask CircleCI to use it:

```yaml
machine:
  node:
    version: 4.1.0
```

#### Example 2: TODO


