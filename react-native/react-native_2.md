# About React and React Native components

React Native requires you to have an index.[os].js for each platform. But any other component can be written once for both OSes.

Components are written *the React way*:

  * A component is a Javascript class (as introduced in ES6, but you can also write your code in a more traditional ES5 style).
  * Each component is passed `props`, containing information useful for the component coming from its parent. For example, a text component will be passed the text to display and the styling of the text.
  * Each component has a `state`. For example, a high level component displaying a page of your app can have in its state the current tab being displayed or the data coming from the API.
  * It has a `render` method returning the components to display.

`render` is a *pure* function, meaning that it always return the same result for a given component `state`. It's very important to respect this as it makes your component easier to reason with (i.e: render won't do any complicated computation, it just takes the state of the component and render it).

Moreover, this assumption is used by React to render the app. The core mechanism used by React for rendering is called `virtual DOM`: React keeps in memory a representation of your components and update the native UI components according to the changes made.

Finally, to ease the writing of `render` methods, React uses a specific syntax called `JSX`: you can write the components and nest them using a syntax very similar to HTML:

```js
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
