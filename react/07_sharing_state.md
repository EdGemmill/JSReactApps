# Sharing State

## Objectives

At the end of this section you should be able to:

- Explain why it's useful to share state
- Allow two components to speak to each other by "lifting" their state into a
  parent component.

## Prerequisites

This section relies on knowledge of a few topics you have covered before, that
you may want to refresh yourself on before you continue, or look back to if
there is something here you don't understand. These are:

- Passing functions as arguments

## Sharing State for Refactoring

As our react applications get larger, we often want to refactor into smaller
components, to make our code simpler, cleaner, and easier to reuse. This counter
component isn't very large, but let's refactor it anyway.

```jsx
const Counter = () => {
  const [count, setCount] = useState(0);

  const incrementCounter = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={incrementCounter}>Increment the counter</button>
    </div>
  );
};
```

We're going to separate the count display and the button into two separate react
components, which we can use together to produce the Counter component. It
shouldn't be too complex, but we might have some trouble along the way.

```jsx
const CountDisplay = () => {
  return <h1>{count}</h1>;
};

const CountButton = () => {
  const incrementCounter = () => {
    setCount(count + 1);
  };

  return <button onClick={incrementCounter}>Increment the counter</button>;
};

const Counter = () => {
  const [count, setCount] = useState(0);

  return (
    <div>
      <CountDisplay />
      <CountButton />
    </div>
  );
};
```

We're getting there, but there's a problem. Our `CountDisplay` component needs
access to the count, and the `CountButton` component needs to be able to update
it. Luckily we have a way to pass data and functionality between components:
Props!!

Let's give the `CountDisplay` the current count as a prop, and pass the
`CountButton` the ability to increment.

```jsx
const CountDisplay = (props) => {
  return <h1>{props.count}</h1>;
};

const CountButton = (props) => {
  const incrementCounter = () => {
    props.setCount(count + 1);
  };

  return <button onClick={incrementCounter}>Increment the counter</button>;
};

const Counter = () => {
  const [count, setCount] = useState(0);

  return (
    <div>
      <CountDisplay count={count} />
      <CountButton setCount={setCount} />
    </div>
  );
};
```

And there we have it! We are now sharing state between two components. We can
use this method to keep our components small and easy to handle.


[Next Challenge](08_forms.md)

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F07_sharing_state.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F07_sharing_state.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F07_sharing_state.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F07_sharing_state.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F07_sharing_state.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
