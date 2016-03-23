# Your first App

***Problem:*** How do I create an app?

## Environment Setup

First, [setup your environment](../setup_1.md), then [setup nvm](../setup_2_nvm.md).

* Install these following node packages
```
$ npm install -g gulp cordova ionic@alpha
```

## Creating and launching the app

* Go to your projects directory
```
$ cd ~/[my]/[projects]/[dir]
```

* Create your application
```
$ ionic start myFirstApp --v2
$ cd myFirstApp
```

* Add the Android and iOS platforms
```
$ ionic platform add android
$ ionic platform add ios
```

## Running the App

### In the browser
```
$ ionic serve
```
### On Android
```
$ ionic run android
```
### On iOS
```
$ ionic run ios
```

### On a iOS simulator
* If it is not installed you need to install
```
$ npm install ios-sim --save-dev
```
* You can then run:
```
$ ionic emulate ios
```
