# Setting up a React project

## Objectives

At the end of this section you should be able to:

- Setup a new React project and use it in your web browser

## Prerequisites

This section relies on knowledge of a few topics you have covered before, that
you may want to refresh yourself on before you continue, or look back to if
there is something here you don't understand. These are:

- Using NPM to install dependencies

## Using the starter codebase

If you don't want to follow the step-by-step project, you can use
[this starter codebase](https://github.com/makersacademy/react-template) and
start using it right away.

## Vite

This starter project uses [Vite](https://vitejs.dev/) to provide a scaffold for the
project. Vite provides us with a number of useful features out the box:

#### A Dev Server

For any file to be accessible over the internet (HTML, JS, CSS etc.) it needs to
be _served_ on a _server_. Vite provides us with a web server so that our
browser can access the React application we write.

#### A Bundler

React applications are written in a syntax called JSX, which can't be read
directly in the browser. We need to convert it to "Vanilla" JS first. Vite
provides us with a bundler that will do this conversion for us.

#### HMR (Hot Module Reloading)
This is a very useful feature of Vite, which partially reloads the server every time we make a change. It means we don't have to start the server manually each time, and it is even clever enough to keep React state intact as we go!

## Step-by-step Instructions
First we create a new Vite project:

```sh
$ npm create vite@latest
```

Follow the instructions in your terminal. We want to create a React project with JavaScript.

Once you've done that, `cd` into the newly-created project directory.

Next add some libraries for testing:
```$ npm install vitest @testing-library/react @testing-library/jest-dom jsdom```

Next we want to [configure Vitest](https://vitest.dev/config/) by adding some information into the `vite.config.js` file:

```js
  test: {
    globals: true, // Allow us to use expect, describe etc. without importing in every file
    environment: "jsdom", // We are testing a DOM environment, not Node
    setupFiles: "./tests/setup.js",
  },
```

Lastly, we want to add the `test` command to our `package.json` so that we can run our tests with `npm run test`:

```
"scripts": {
  "test": "vitest"
  // ...other scripts
}
```

Done! You now have a working React project!

[Next Challenge](02_components.md)

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F01_setting_up_project.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F01_setting_up_project.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F01_setting_up_project.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F01_setting_up_project.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F01_setting_up_project.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
