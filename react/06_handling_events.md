# Handling Events

## Objectives

At the end of this section you should be able to:

- Explain how we can write "Event Handlers" to listen to interactivity.
<!-- OMITTED -->

## Prerequisites

This section relies on knowledge of a few topics you have covered before, that
you may want to refresh yourself on before you continue, or look back to if
there is something here you don't understand. These are:

- Event Listeners

# Events

Previously, we discussed how in vanilla JavaScript, we can use the built-in
`document.addEventListener` function to react to events that occur in the
browser, such as clicks.

Similarly, React emits an event whenever an element is interacted with. We can
listen for these events through an _event handler_. To do this, we define a
function within the component, and pass it as a value to the `onClick` attribute
on an element:

```javascript
// in ClickListener.js

const ClickListener = () => {
  // Defining handleClick inside the ClickListener component.
  const handleClick = () => {
    console.log("Clicked!");
  };

  return (
    <>
      <button onClick={handleClick}>Click Me!</button>
    </>
  );
};
```

Render this component inside your App.jsx and make sure it works. If everything
works correctly, you should see the word "Clicked!" appear in the console every
time the button is pressed.

This is a good start, but React also provides us with a lot of information about
each event which is triggered. We can see this by changing our `handleClick`
function to take an argument:

```javascript
const handleClick = (event) => {
  console.log(event);
};
```

Update your component and take a look in the browser console again. What do you
see?

You should be able to see a lot of information about the event that was just
triggered, such as the element that was clicked (the `target`), and where on the
screen the click occurred (`screenX` and `screenY`). See if you can identify
some of the other properties in the object, and research any which sound
interesting.

# Exercise

Use an `input` element and the `onChange` prop to create a component that will
log to the console everything that is typed into it.

# Exercise

Using what you learned about state in the previous section, along with the
`onClick` prop, create a new component `<Die />` to represent rolling a die. It
should have a button, and when pressed, a new random integer between 1 and 6
should be generated, stored in state, and presented on the page. Each time the
button is pressed, a new roll should be presented.


[Next Challenge](07_sharing_state.md)

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F06_handling_events.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F06_handling_events.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F06_handling_events.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F06_handling_events.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F06_handling_events.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
