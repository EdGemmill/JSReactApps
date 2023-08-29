# Running JavaScript in the browser

## Objectives

At the end of this section you should be able to:

- Explain how JavaScript code can be run in the browser being loaded from an
  HTML document.
- Run a small snippet of JavaScript code from a webpage.
- Use the browser developer tools to get visibility into your JS code.

## Prerequisites

This section relies on knowledge of a few topics you have covered before, that
you may want to refresh yourself on before you continue, or look back to if
there is something here you don't understand. These are:

- The HTTP request/response cycle
- HTML Tags

## JavaScript and the browser

You already have experience of running JavaScript using the `node` runtime.

JavaScript initially became popular because it is the language of the browser.
JavaScript code can be loaded from an HTML page, and executed within the context
of the browser.

We can use JS to dynamically manipulate the web page and allow the user to
interact with it in ways classic HTML and CSS do not allow.

## Viewing the HTML page

Before going ahead, note that there are two ways of viewing an HTML page inside
a web browser:

1.  By directly opening it as file (e.g by clicking on it in your file
    explorer).
2.  Through a web server — when browsing a web application deployed online, the
    browser sends an HTTP request to the server, and the HTML page is contained
    in the received HTTP response.

We will use the second way throughout this section. We can use `npm` to run an
ad-hoc webserver which will serve a folder for us:

```
npx http-server . -c-1
```

You can now access your HTML page at http://127.0.0.1:8080/ by default, this
will display an `index.html` file, if one exists.

> **Note:** The `-c-1` flag disables caching, meaning that when we visit our
> server we will _always_ be getting the most recent version of our HTML and JS
> files, and _not_ an older version saved by the browser.

## Loading JavaScript

To load a JS file from an HTML page, we need to use the `<script>` HTML tag:

```html
<script type="text/javascript" src="index.js"></script>
```

```js
// file: index.js

console.log("Hello from JavaScript");
```

Create the new file `index.js` in the same directory and add the `<script>` tag
to the HTML document.

Reload the page. To display the messages output by `console.log`, you will need
to open the Developer Console (`Cmd+Option+J` on Mac).

**Keep in mind that console.log does not write onto the page — it is used only
for you to debug using the developer console, not to display information to the
users of the application**

## Exercise

1. In a new directory, create an HTML file `index.html` and a JavaScript file
   `index.js`.

2. Use `http-server` to serve this directory.

3. Load the JavaScript file from the HTML page so that it prints a message to
   the developer console.

4. Instead of printing to the developer console, use JavaScript's `alert`
   function to display a message to the user.

\*\* EDU

## Learners experience

Learners will:

- See a demonstration (written and/or video) on how to create an HTML page which
  loads a JS file
- See a demonstration (written and/or video) on how to use `console.log` and the
  browser dev console to get visibility into a program.
- Work on an exercise to create an HTML file and load a JS file from it (this
  file would log something in the console). They'll have to use the browser
  console to see the console output.

\*\*


[Next Challenge](02_manipulating_the_dom.md)

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=javascript_bites%2F01_running_js_in_browser.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=javascript_bites%2F01_running_js_in_browser.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=javascript_bites%2F01_running_js_in_browser.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=javascript_bites%2F01_running_js_in_browser.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=javascript_bites%2F01_running_js_in_browser.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
