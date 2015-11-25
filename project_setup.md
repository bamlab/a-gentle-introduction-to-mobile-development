# Your first App

## Environment Setup

* Install the latest version of XCode

* Install Java and JDK

* Install brew 
```
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

* Install the android sdk 
```
$ brew install android-sdk
$ android sdk
```
* Install the following sdk tools:
    * Android SDK Tools
    * Android SDK Platform-tools
    * The latest Android SDK Build-tools
    * Every SDK Platform from API 18 to most recent
    * The Intel x86 atom 64 System Image from the most recent API
    * The Google APIs Intel x86 Atom 64 System Image from the most recent API
    * Android Support Library
    * Android Support Repository
    * Google Play Services
    * Google Repository


* Install node
```
$ brew install nvm
$ nvm install stable
$ nvm use stable
```

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