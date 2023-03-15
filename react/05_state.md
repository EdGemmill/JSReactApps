# State

## Objectives

At the end of this section you should be able to:
 * Explain what is "state" in a React component
 * Explain how React re-renders a component when its state changes
 * Use the `useState()` hook to add state to a component
 * Test-drive a component with state

## On state

So far our components are "static" — once they are rendered with some props, they won't update (unless we reload the entire application).

By adding state to a component, it can then "change" dynamically the way it looks (or the way it's been rendered), depending on how its state changes.

A trivial example is a component to show a counter — it starts by displaying an initial value of 0, but then can change to display increasing values.

## Creating state

We use the function `useState` in a component when we want to define a state value. This function takes one argument, which is the initial state value.

This function also returns two things:
 * The state value itself.
 * A function to update the state value. 

We therefore always call it using the same pattern:

```jsx
const [value, setValue] = useState(initialValue)
```

```jsx
const Counter = () => {
    const [count, setCount] = useState(0)

    return (<div>{count}</div>)
}
```

We can use the React DevTools "Components" tab to inspect the current state of our component.

## Changing state

When a component is mounted on the tree with some props, this component will keep the same props values. State is different — it can change. In the example above, the `Counter` component will be mounted on the page, and the state value `count` can change.

To change the state value, we **must** call the function returned by `useState()`. This is often done in reaction to a user interaction with the component, by using the `onClick` attribute, for example:

```jsx
const Counter = () => {
    const [count, setCount] = useState(0)

    const incrementCounter = () => {
        setCount(count + 1);
    }

    return (<div>
        <h1>{count}</h1>
        <button onClick={incrementCounter}>Increment the counter</button>
    </div>)
}
```

When the user clicks the button, `setCount` is called with the new state value. React re-renders the component, "remembering" the new `count` value, and returning the HTML including this new value.

## Re-rendering

When the state is updated, React will "know" it needs to re-render the component again, to make the page look like it should.

In the example of the Counter, when we update the value from 0 to 1 using `setCount()`, React then "knows" it needs to re-render (call) the component, as the value of `count` has changed.

## Exercise

Implement the `Counter` component in your project. Use the React DevTools to inspect the state of this component changing as you manually increment the counter on the web page.

## Testing a component with state

@TODO

Testing a component with state follows the same principles. The only difference is that we will usually simulate a user action — for example, clicking on a button. This user action changes the state of the component, and we test that the component has changed.

```js
// file: src/Counter.test.js

import React from 'react'
import {render, screen} from '@testing-library/react'
import userEvent from '@testing-library/user-event'
import '@testing-library/jest-dom'
import Counter from './Counter'

test('renders with initial value of 0 ', () => {
    // Setup
    render(<Counter />)

    // Assert
    expect(screen.getByRole("heading")).toHaveTextContent('0')
});

test('renders with a new value of 2 ', async () => {
    // Setup
    render(<Counter />)

    // Act - click the button twice
    await userEvent.click(screen.getByText('Increment'))
    await userEvent.click(screen.getByText('Increment'))

    // Assert
    expect(screen.getByRole("heading")).toHaveTextContent('2')
});
```

@TODO why did we have to use `async` and `await`?

## Exercise

Test-drive the component `Counter` with a new button to **decrement** the counter.

## Challenge

@TODO Test-drive a component with state.


------

## Advanced - Breaking it down 

```jsx
const Counter = () => {
    const [count, setCount] = useState(0)

    // count is 0

    const incrementCounter = () => {
        setCount(count + 1);
    }

    return (<div>
        <h1>{count}</h1>
        <button onClick={incrementCounter}>Increment the counter</button>
    </div>)
}
```

After `setCount(0 + 1)` is called, `state` takes the new value 1:

```jsx
const Counter = () => {
    const [count, setCount] = useState(0)

    // count is now 1

    const incrementCounter = () => {
        setCount(count + 1);
    }

    return (<div>
        <h1>{count}</h1>
        <button onClick={incrementCounter}>Increment the counter</button>
    </div>)
}
```



[Next Challenge](06_forms.md)

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F05_state.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F05_state.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F05_state.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F05_state.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F05_state.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
