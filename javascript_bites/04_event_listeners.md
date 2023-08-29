# Event Listeners

## Objectives

At the end of this section you should be able to:
 * Explain how we can use JavaScript code to respond to user interactions on the web page
 * Use JavaScript event listeners to run code when the user interacts with the page (e.g clicking on a button)

 ## Prerequisites
This section relies on knowledge of a few topics you have covered before, that you may want to refresh yourself on before you continue, or look back to if there is something here you don't understand. These are:
 * CSS Selectors
 * Anonymous functions
 * Passing functions as arguments

## On Event listeners

In JavaScript, we can attach what is called an event listener to a DOM element. The "listener" is a function that will be called whenever the event "happens".

For example, we can attach a function to be executed whenever the user clicks on the button having the HTML ID `#my-button` (if you're not sure of what an HTML ID is, or how to use it, [read this first](../pills/manipulating_dom_with_javascript.md#get-one-element-by-its-html-id)):

```js
// 1. Getting the DOM element
const buttonEl = document.querySelector('#my-button');

// 2. Attaching the event listener
buttonEl.addEventListener('click', () => {
  // this will execute when the user clicks on the button
  console.log('clicked!');
});
```

If we don't need to use the variable referencing the DOM element again, we can use this more concise syntax:
```js
document.querySelector('#my-button').addEventListener('click', () => {
  console.log('clicked!');
});
```

Note that if the user clicks **before** the event listener has been "attached" (i.e before `addEventListener` has been called), the event will not be handled at all.

```js
// This function will attach the event listener when called 
const attachListener = () => {
  document.querySelector('#my-button').addEventListener('click', () => {
    console.log('clicked!');
  });
}

// If the user clicks on the button now, nothing will happen (yet)

// ...

// Later, we call the function defined previously
attachListener();

// The click is now handled

```

## What other events can I use?

There are [an enormous number of events](https://developer.mozilla.org/en-US/docs/Web/Events#event_listing)
available for us to listen for, everything from mouse clicks, key strokes,
and scrolling, to rotating your device, printing the page or even plugging
in a gamepad! 🎮 But in this guidance, we'll stick to clicks.

## Exercise

In the current project directory:
1. Create an HTML button
2. Attach an event listener to the button so when it is clicked, the TODO data is loaded

## Challenge

The following sequence diagram contains the different components involved in the application written so far. 

Complete the diagram with the missing arrows to indicate the interactions between the components. Make sure that:
 * you label the arrows
 * the arrows are in the correct order (time flows from the top of the diagram to the bottom)

When done, [submit your completed diagram to your coach for feedback](https://airtable.com/shrnql7AaT1eYNJbI?prefill_Item=react_as01).

## Bonus Challenge
Take your joke code from the previous section, and adapt it so that the punchline to the joke is only shown after the user clicks a button.

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=javascript_bites%2F04_event_listeners.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=javascript_bites%2F04_event_listeners.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=javascript_bites%2F04_event_listeners.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=javascript_bites%2F04_event_listeners.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=javascript_bites%2F04_event_listeners.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
