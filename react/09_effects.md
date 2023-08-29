# Effects

## Objectives

At the end of this section you should be able to:

- Explain why we need to use `useEffect` in our components
- Use the `useEffect` hook to sends an HTTP request in a React component
- Implement a React component loading data from a remote server

## Prerequisites

This section relies on knowledge of a few topics you have covered before, that
you may want to refresh yourself on before you continue, or look back to if
there is something here you don't understand. These are:

- HTTP Requests in JavaScript (fetch)
- Component Rendering

## Render Loops

Whenever we **render** a component, we run its function. As a rule of thumb, we
**re-render** a component _every time_ its _props_ or _state_ change.

This is good for updating the contents or appearance of a component, but it
poses a challenge if we want to do HTTP requests to a server. Consider this
component:

<!-- OMITTED -->

(If you'd like to try running this code, you can use the `<Todo />` component
from earlier in the module. Remember to pass the `TodoList` a `tag` prop!)

```jsx
const TodoList = (props) => {
  const [todos, setTodos] = useState([]);

  const URL = `http://todoServer.com/tagged/${props.tag}`;
  fetch(URL)
    .then((res) => res.json())
    .then((data) => setTodos(data));

  return (
    <>
      <h2>Todos List:</h2>
      <div className="todo-list">
        {todos.map((todoData) => (
          <Todo data={todoData} />
        ))}
      </div>
    </>
  );
};
```

There's a few parts to this component, so let's break it down.

1. We set up some _state_ to hold the list of todos. We initialise this with an
   empty array.
2. We build a URL based off of the component's `props`. This allows us to fetch
   only the todos with a specific tag.
3. We _fetch_ the list of todos from our server, parse the JSON response, and
   use `setState` to update the state.
4. We iterate over the `todos` array, producing a `<Todo />` for each element,
   passing the `todoData` as a prop.

Looks good so far? Remember that the `TodoPage` function will run _every time_
the state changes. Which means that every time we fetch the data and set the
todos, we run the function again... meaning we fetch the data again, and set the
todos again.... meaning we fetch the data again and....

An infinite loop! Not ideal. In react, we call this a _render loop_.

## Effects we can control

To avoid this, we need a way to run the fetch _only once_, the first time the
component is rendered. To do this, we can use a built-in react function called
`useEffect`.

> **Note:** `useEffect` and `useState` are known as _hooks_. You don't need to
> worry too much about the details now, but by convention, react hooks always
> start with the word "use".

The `useEffect` function takes two arguments:

1. The function (effect) we want to run.
2. A _dependency array_, which controls _when_ the component will run the
   effect. If the dependency array contains different values between one
   component render and the next, the effect will run.

   This means that if we want the effect to only ever run once, we can provide
   an empty dependency array.

It looks like this:

```javascript
useEffect(() => {
  // Effect code goes here
}, []);
```

We can rewrite our `TodoList` component to only fetch once:

```jsx
const TodoList = (props) => {
  const [todos, setTodos] = useState([]);

  useEffect(() => {
    const URL = `http://todoServer.com/tagged/${props.tag}`;
    fetch(URL)
      .then((res) => res.json())
      .then((data) => setTodos(data));
  }, []);

  return (
    <>
      <h2>Todos List:</h2>
      <div className="todo-list">
        {todos.map((todoData) => (
          <Todo data={todoData} />
        ))}
      </div>
    </>
  );
};
```

Now, our `fetch` will only run once, the first time this component is loaded.
Once the data comes back, it will update the state, and display the todos on the
page.

<!-- OMITTED -->

## Exercise

Write a component called `Joke` that will do a fetch request to the Joke API
below, and display it on the page.

URL: https://official-joke-api.appspot.com/random_joke

You can use `curl` or the browser to see the format of the response.

## Changing the Dependency Array

Our `TodoList` component above is ok, but what happens if the props change, and
we pass in a different tag? Ideally, this would mean we want the `TodoList` to
fetch a new list, based off the new tag, and display those instead.

But we've written the component to only ever run once, when the component loads!

To fix this, we need to use the second `useEffect` parameter, the _dependency
array_.

Remember that the effect runs if the contents of the dependency array changes
between one render and the next. So if we want the effect to run if the tag
changes, we can include it in the dependency array:

```jsx
useEffect(() => {
  const URL = `http://todoServer.com/tagged/${props.tag}`;
  fetch(URL)
    .then((res) => res.json())
    .then((data) => setTodos(data));
}, [props.tag]);
```

Now any time the tag changes, we re-run the effect, and fetch the new list!

Perfect!

## Challenge

We have built a very basic backend API which will send a list of events.

You can find the repo for this API here:
https://github.com/makersacademy/react-gig-backend/tree/main

The API is hosted on render here:
`https://makers-gig-backend.onrender.com/events`

1. Update your gig application to fetch the list of events from this backend the
   first time the application is loaded, instead of hard coding them.
2. While the events are loading, your application should somehow communicate to
   the user that the data is loading, either through a spinner, or the word
   "Loading" etc. It is up to you how to display it.


<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F09_effects.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F09_effects.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F09_effects.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F09_effects.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F09_effects.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
