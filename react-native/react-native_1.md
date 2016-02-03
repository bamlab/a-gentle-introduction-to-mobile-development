# Your first React Native app

*React Native* is a framework developed by Facebook enabling to create applications for iOS and Android based on *React* and Javascript.

Compared to the approach of Cordova, in which the application is running inside a full-fledged browser, React Native uses the native components of the platform for your app. For both platform, your Javascript app is executed by *JavaScript Core*. React Native expose the components of the platform as well as APIs (which are usually close to the one existing in browser).

This approach allow to have applications with a *native look'n'feel* while keeping a fast development pace without having to rewrite the app for two OSes. *Performance* is also very good because the UI is entirely handled by the OS and Javascript is run is its own thread.

## Starting a new React Native project

The React Native *Getting Started* is well written and should be sufficient to let you be up and running: https://facebook.github.io/react-native/docs/getting-started.html#content

A few comments on the way React Native works:

  * Once `react-native init` is done, you can launch the XCode/Android projects as explained in the page. These XCode/Android projects are *part of* your app source (contrary to Cordova where the projects for iOS/Android can be regenerated at any time). Be sure to include them in your git repository.

  * As we're developing "native" apps, the testing is always directly done in emulators (or even on real device). You can quickly reload any time you make changes so it's not a problem.

  * React native is bundled with a packager. You don't need to install *webpack* or a task runner like *gulp* or *grunt*.

  * *Babel* is used to let you use ES2016. It's a good habit to write your app using the latest JavaScript standard.

## Launch your app

If you've followed the React Native getting started, you have a working project. You can launch it as specified in this page:

 * Open `ios/[YourProjectName].xcodeproj` and hit run in Xcode.
 * For Android `react-native run-android`.

To start developing, you can edit a few lines in `index.ios.js` or `index.android.js` and reload on your simulator (Cmd+R on an iPhone simulator). On devices, shake the device to open the *development menu*.

## Create your first component

React Native requires you to have an index.[os].js for each platform. But any other component can be written once.

Components are written *the React way*.
