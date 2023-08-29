# Sending HTTP requests

## Objectives

At the end of this section you should be able to:

- Explain how a JavaScript program run in a browser can act as an HTTP client to
  send requests to remote servers.
- Use `fetch()` to send an HTTP request to a remote server and prints the
  received response in the browser console.

## Prerequisites

This section relies on knowledge of a few topics you have covered before, that
you may want to refresh yourself on before you continue, or look back to if
there is something here you don't understand. These are:

- The HTTP request/response cycle
- Promises, and `.then`

## On fetching data

You should always have in mind that the HTML code and JavaScript code are both
interpreted and run by the web browser, on the user's computer or mobile phone.

Once the HTML and JavaScript code have been sent in the HTTP response, the
interaction with the web server stops.

There are two ways for the web browser to get new data from the web server:

- by sending a new request to get a new web page, for example when the user
  clicks on a link, or submits a form. You've done this before when writing web
  applications using Flask or Sinatra.
- by sending HTTP requests _without_ reloading the page. The HTML document stays
  loaded in the browser, but a chunk of data can be fetched "in the background".
  This can be done using JavaScript.

## Fetch

JavaScript's built-in function for fetching data is `fetch`. Because `fetch`
takes time to complete, it returns a Promise object, that we can attach
callbacks to:

```javascript
// jsonplaceholder is a website that returns placeholder JSON responses.
const URL = "https://jsonplaceholder.typicode.com/todos/1";

fetch(URL)
  .then((response) => response.json()) // Get JSON data out of Response object
  .then((todo) => {
    // Use the returned data in some way
    console.log(todo);
  });
```

## Exercise

In the same project directory, update the code of `index.js` so it sends an HTTP
request to this url:

```
https://official-joke-api.appspot.com/random_joke
```

Print out the JSON response in the console and inspect the result. You should
see something like the following in the console.

```js
{
  type: "general",
  setup: "Don't trust JavaScript programmers.",
  punchline: "All they do is Promise but they never callback.",
  id: 386
}
```

## Challenge

Combine your code in the exercise above with the DOM manipulation from last
section to create a page that displays a random joke each time you visit it.


[Next Challenge](04_event_listeners.md)

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=javascript_bites%2F03_sending_http_requests.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=javascript_bites%2F03_sending_http_requests.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=javascript_bites%2F03_sending_http_requests.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=javascript_bites%2F03_sending_http_requests.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=javascript_bites%2F03_sending_http_requests.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
