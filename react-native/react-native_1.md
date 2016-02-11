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

## About React components

React Native requires you to have an index.[os].js for each platform. But any other component can be written once for both OSes.

Components are written *the React way*:

  * A component is a Javascript class (as introduced in ES6, but you can also write your code in a more traditional ES5 style).
  * Each component is passed `props`, containing information useful for the component coming from its parent. For example, a text component will be passed the text to display and the styling of the text.
  * Each component has a `state`. For example, a high level component displaying a page of your app can have in its state the current tab being displayed or the data coming from the API.
  * It has a `render` method returning the components to display.

`render` is a *pure* function, meaning that it always return the same result for a given component `state`. It's very important to respect this as it makes your component easier to reason with (i.e: render won't do any complicated computation, it just takes the state of the component and render it).

Moreover, this assumption is used by React to render the app. The core mechanism used by React for rendering is called `virtual DOM`: React keeps in memory a representation of your components and update the native UI components according to the changes made.

Finally, to ease the writing of `render` methods, React uses a specific syntax called `JSX`: you can write the components and nest them using a syntax very similar to HTML:

```
class MyComponent extends React.Component {
    render() {
        return <View>
            <Text>First text</Text>
            <Text>Second text</Text>
        </View>
    }
}
```

Note that JSX is converted to traditional Javascript function calls by the build toolchain. There is no magic here, you're just using functions and Javascript like usual, except that it's more adapted to writing UI.

In the next chapter, we'll start writing components to write an app! Note that the app itself is represented by a root component that you can find in index.[os].js.
