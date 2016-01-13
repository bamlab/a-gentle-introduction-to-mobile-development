# Running on device

So, you just ran your project in the browser. Awesome!

Running your project in the browser is practical for development and you can do so most of the time. However, developing for device has its own quirks so it is best to test your app in a real device. Doing so, will allow you not only to perceive how your users will see the app, but it will also allow you to test native functionalities of the phone such as the camera, GPS, etc.

If you did not setup your environment (install Ionic, ADK, etc.), do so as explained in [Your first App](ionic_1.md). Once you have so you can run your app on your device.

## Debugging on device

The code that you are running in your device is divided into two separate types, web and native. Web code it the javascript, html and css that you wrote, and it runs inside a web view. The native code are all the cordova plugins that you added to your project.

### Debugging web code on Android

https://developers.google.com/web/tools/chrome-devtools/debug/remote-debugging/remote-debugging#remote-debugging-on-android-with-chrome-devtools

### Debugging web code on iOS

https://developers.google.com/web/tools/chrome-devtools/debug/remote-debugging/remote-debugging#remote-debugging-on-ios-with-safari-web-inspector

## Developing plugins

http://docs.phonegap.com/en/2.0.0/guide_plugin-development_index.md.html

### Debugging native android code

https://blog.nraboy.com/2014/12/debugging-android-source-code-adb/

### Debugging native ios code

Use xcode.
