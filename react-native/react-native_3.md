# Making your app with React Native components

As explained in the first part, *React Native* exposes the native components of the platform (iOS or Android). Even if some components can be platform specific, most components are available for both OSes.

## Some React Native basic components

We're first going to have a quick overview of React Native most useful components.

### View

A view is the basic building block. It could be compared to a HTML `div`.

### Text

You already saw it in the last chapter: it's the primitive block used to display text in your app.

```js
<Text>Hello mobile app world</Text>
```

Styling is applied to most components using the `style` attribute:

```js
<Text style={{fontSize: 14, color: 'blue'}}>Hello mobile app world</Text>
```

### TouchableHighlight

Touchable highlight is one of the basic building block to react to user input: simply put it around a component and add a callback:

```js
<TouchableHighlight onPress={() => { console.log("Hello!"); }}>
    <Text>Tap me!</Text>
</TouchableHighlight>
```

## Create your first component

Let's write one of the most basic component: a counter! This is a classic example often used in React tutorials.

First, we create the component and add it to the app. Create a new file called `counter.jsx`:

```js
//Import React Native components
import {
    Text,
    View,
    TouchableHighlight
}, React from 'react-native'

class Counter extends React.Component {
    render() {
        return <View>
            <Text>0</Text>
        </View>
    }
}

//Expose the component we just made, so that we can import it in other files
export default Counter;
```

We then add the component to index.ios.js and index.android.js. First, import it at the top of the file:

```js
import Counter from './counter.js'
```

Then, add the component after the last `<Text>`:

```js
    //...
    </Text>
    <Counter />
</View>
//...
```

That's it! Reload the app in your simulator (Cmd+R for the iOS simulator).

## Add touches and update the component state

The component will contain the value of the counter in its state. Let's add it:

```js
class Counter extends React.Component {
    constructor() {
        this.state = {
            counter: 0,
        };
    }

    render() {
        return <View>
            <Text>{ this.state.counter }</Text>
        </View>
    }
}
```

We now need to mutate the state when the text is touched. We're going to use the TouchableHighlight component:


```js
class Counter extends React.Component {
    constructor() {
        this.state = {
            counter: 0,
        };
    }

    increment() {
        this.setState({
            counter: this.state.counter + 1,
        })
    }

    render() {
        return <View>
            <TouchableHighlight onPress={() => this.increment()}>
                <Text>{ this.state.counter }</Text>
            </TouchableHighlight>
        </View>
    }
}
```

And it's done. You now have a standalone counter component that update when it's touched.

## Dumb and Stateful components

We took the counter as an example of a simple component, but in a more complex app containing one or more counters, you probably want to do something more with the counter: displaying a message according to the state of the counter, activating or deactivating a button...

In this case, the counter we made would be transformed into a "dumb" component, that will only display the number passed as a prop, and will call a callback when it's touched.

The responsibility for updating the state of the counter would be transferred to the parent, which is in this case a "stateful" component. You should strive to have as few stateful component as possible: make most of your components dumbs and used for presentation only, and keep the logic in a few component, that will at the top of the tree.
