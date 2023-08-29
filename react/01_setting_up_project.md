# Setting up a React project

<!-- OMITTED -->

## Objectives

At the end of this section you should be able to:
 * Setup a new React project and use it in your web browser

## Prerequisites
This section relies on knowledge of a few topics you have covered before, that you may want to refresh yourself on before you continue, or look back to if there is something here you don't understand. These are:
 * Using NPM to install dependencies

## Using the starter codebase

The process to setup a new React app can be a bit long if you're doing this for
the first time.

If you don't want to follow the entire step-by-step project, you
can use this starter codebase (@TODO) and start using it right away.

Otherwise, follow the steps below.

## Step-by-step process

You should have the following directory structure at the end of this process:

```
public/
    index.html
src/
    App.js
.babelrc
index.js
package-lock.json
package.json
webpack.config.js
```

### 1. Create the project

```bash
# Initialise the project directory
mkdir my-react-app
cd my-react-app
npm init -y

# Install packages
npm install --save-dev @babel/core babel-loader @babel/cli @babel/preset-env @babel/preset-react
npm install --save-dev webpack webpack-cli webpack-dev-server
npm install --save-dev html-webpack-plugin

npm install --save-dev @testing-library/react
npm install --save-dev @testing-library/jest-dom
npm install --save-dev @testing-library/user-event
npm install --save-dev jest-environment-jsdom
npm install react react-dom 
```

### 2. Create the HTML and JS files

In this step you will create three files:
* The HTML document (`index.html`)
* The main JS file (`index.js`)
* The "root" React component (`src/App.js`)

```html
<!-- file: index.html -->

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>React App</title>
</head>
<body>
    <div id="root"></div>
</body>
</html>
```

```js
// file: src/App.js

import React from "react";

const App = () =>{
    return (
        <h1>
            Hello world! I am using React
        </h1>
    )
}

export default App
```

```js
// file: index.js

import React from 'react'
import  { createRoot }  from 'react-dom/client';
import App from './src/App.js'

const container = document.getElementById('root');
const root = createRoot(container);
root.render(<App/>);
```

### 3. Create configuration files

In this step you will create three more files:
 * `.babelrc`
 * `webpack.config.js`
 * `jest.config.js`

```json
{
    "presets": ["@babel/preset-env","@babel/preset-react"]
}
```

```js
const HtmlWebpackPlugin = require('html-webpack-plugin');
const path = require('path');

module.exports = {
  entry: './index.js',
  mode: 'development',
  output: {
    path: path.resolve(__dirname, './dist'),
    filename: 'bundle.js',
  },
  target: 'web',
  devServer: {
    port: '5000',
    static: {
      directory: path.join(__dirname, 'public')
},
    open: true,
    hot: true,
    liveReload: true,
  },
  resolve: {
    extensions: ['.js', '.jsx', '.json'],
  },
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/, 
        exclude: /node_modules/, 
        use: 'babel-loader', 
      },
    ],
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: path.join(__dirname, 'public', 'index.html')
    })
  ]
};
```

```js
module.exports = {
    testEnvironment: 'jsdom'
}
```

### 4. Run the webpack development server

Run the following command:

```bash
./node_modules/.bin/webpack-dev-server .
```

It should open a new browser tab at `http://localhost:5000` with your application running.

### Why so many files?

In the end, what is read and interpreted by the browser to display and run the final web application is only:
 * the HTML document
 * the JavaScript code bundled by `webpack` (you can have a look at the generated file `http://localhost:5000/bundle.js` if you're curious)

So why do we need so many files in our project?

The answer is that, for the React library to function, we need a few different libraries and software tools. For example, the JSX syntax (which allows mixing of HTML and JavaScript code in the same file) cannot be read natively by web browsers, so we need a tool to translate or "transpile" the source JSX code to JavaScript code that is readable by the browser.

This is one of the jobs of the `babel` and `webpack` libraries, for example. The different configuration files are needed for these tools to behave correctly to produce the final web application (the "build").

Most modern JavaScript projects will implement some kind of tool chain including similar tools, if not more. You do not need to know in details how every tool in your tool chain work to build your application (in fact, most engineers using them don't!).

[Next Challenge](02_components.md)

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F01_setting_up_project.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F01_setting_up_project.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F01_setting_up_project.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F01_setting_up_project.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F01_setting_up_project.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
