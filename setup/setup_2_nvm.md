# Setup NodeJS with NVM

NVM (Node Version Manager) is a great tool that enables the user to switch between differents versions of Node.js

## Installation

```shell
$ curl https://raw.githubusercontent.com/creationix/nvm/v0.23.2/install.sh | bash
```
Then you can restart your terminal and check that `nvm` is installed:

```shell
$ nvm --version
0.23.2
```

## Switching between versions of Node.js

To switch to the latest version of Node.js, you can now run:
```shell
$ nvm use stable
```
To switch to a specify version, say `4.2.4`, run:
```shell
$ nvm install 4.2.4
```

NVM will install the new version in `~/.npm`, and the system will use it as the default Node.js environment.

For instance:

```shell
$ nvm install 4.2.4
$ echo $PATH
/Users/almouro/.nvm/versions/node/v4.2.1/bin:...
```

##### Pro Tip
To automatically have a version of Node.js ready when you open your terminal, you can add a line like below to your `.zshrc` or `.bashrc`:
```bash
nvm alias default 4.2.1
```

Checkout [the NVM docs](https://github.com/creationix/nvm/blob/master/README.markdown) for more information!

## AVN

[AVN](https://github.com/wbyoung/avn) is a tool that handles switching between Node.js versions for you.

Install it:
```shell
npm install -g avn avn-nvm avn-n
avn setup
```

Now when you `cd` into a directory with a `.node-version` file, `avn` will
automatically detect the change and use your installed version manager to
switch to that version of node.

What goes in your `.node-version` file? A
[semver](http://semver.org/) version number corresponding to the version of Node.js that
your project uses, for instance:

```bash
# .node-version
4.2.4
```
