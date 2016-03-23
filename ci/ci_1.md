# Continuous Integration

***Problem:*** How do I automatically make sure my tests work after modifying the code?

Once you have your tests setup in your projects, you may want to automatically run them at any time a change is pushed by a developer. Continuous Integration's goal is to run these automated tests and even launch an automated build of your project.

## Setting up CircleCI

CircleCI is a Continuous Integration service that is available for free. The way it works is quite simple and similar to most CI services: each time a commit is pushed to a branch in your git repository, CircleCI provisions a new, blank, machine. Your project is then cloned on it, installed and tests are run.

### Open an account on CircleCI.

Go to https://circleci.com/ noob.

### Add your project

**[TODO insert image]**

### Enjoy the builds

CircleCI will try to infer most of the settings that you need. For projects using *Node.js* and *npm*, it will launch `npm install` and then run `npm test`.

Anytime you push a new commit/branch to your git repository, CircleCI will launch a new build. By default, you will be notified by mail if something went wrong.

## Customize the settings with `circle.yml`

Most of the time, the settings inferred by CircleCI aren't adapted to your project. You may want to run a particular script before installing dependencies or install fixtures if you're testing a backend.  

These settings can be added and changed in a configuration file called `circle.yml`, stored at the root of your repository.

### Example 1: using a different Node version

If your project is using a particular version of Node, you can ask CircleCI to use it:

```yaml
machine:
  node:
    version: 4.1.0
```

### Example 2: Customize how your tests are run and reported

You can also change entire section of the build, and replace the way tests are run.

```yaml
test:
  override:
    - MOCHA_FILE=$CIRCLE_TEST_REPORTS/unit.xml npm run test:unit -- --reporter mocha-junit-reporter
```

In this example, we're replacing the test run command by a new one that reports the result in a file.
CircleCi exposes a few *environment variables* (like `$CIRCLE_TEST_REPORTS` here): the full list is in the [CircleCI documentation](https://circleci.com/docs).


## Others services

CircleCI is only one of the many providers to offer Continuous Integration as a service. We chose it because it was easy to set up and free to try. You can also try [Travis-CI](https://travis-ci.org/) which is free for open source projects.

In any case, be sure to read the docs if you're missing something.
