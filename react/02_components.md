# Components

## Objectives

At the end of this section you should be able to:
 * Explain that a React component is a reusable piece of user interface
 * Implement a React component by writing a function returning a tree of HTML
   tags, and add it to your React app
 * Implement a React component rendering another component (parent-child)

## What is component?

When building a webpage in HTML, we think of it as made of HTML tags:

```html
<body>
    <h1>Welcome to your feed</h1>
    <div id="feed">
        <div class="post">
            <p>A first post</p>
            <p class="posted-at">Posted last week</p>
        </div>
        <div class="post">
            <p>Another post</p>
            <p class="posted-at">Posted last month</p>
        </div>
    </div>
</body>
```

The previous HTML document can also be represented with the following "tree",
which is what we call the DOM tree, or document tree:

```
body
    h1
    div#feed
        div.post
            p
            p.posted-at
        div.post
            p
            p.posted-at
```

When building with React, we think of the page as made of components. Components
are reusable pieces of user interface, and they can be made of many HTML tags.
Here's an example of the same webpage, when "translated" to components:

```jsx
<App>
    <Title title="Welcome to your feed" /> 
    <Feed>
        <Post title="A first post">
        <Post title="Another post">
    </Feed>
</App>
```

We can also build the following **component tree** from the previous React
structure of components:

```
App
    Title
        Feed
            Post
            Post
```

(The root component is often called `App` by convention).

In this example, the component `Post` is a self-contained piece of user
interface, containing only the HTML needed to display a single post.

Note that while HTML tags are always lowercase, by convention React components
are **always** capitalised.

## Writing a component

When written in JavaScript, a component is a JavaScript function which returns
the HTML structure for this component. A component is usually declared in its
own file.

```jsx
// file: src/Post.js

// We always need to import React when declaring a component
import React from "react";

const Post = () => {

    return (
        <div className="post">
            <p>A first post</p>
            <p className="posted-at">Posted last week</p>
        </div>
    )
}

export default Post
```

It can be then imported and added to the root component (`App`):

```js
// file: src/App.js

import React from "react";
import Post from "./Post";

const App = () =>{
    return (
        <Post />
    )
}
```

The reason we can mix HTML and JavaScript in the same files is because React
uses a special version of JavaScript, called **JSX**, in which it is perfectly
valid to write HTML tags (following a few rules, which you'll learn about
later).

## Rendering

When React goes through the component tree, it "calls" each component (which,
remember, is a JavaScript function), gets the returned HTML tree, and insert it
into the DOM of the webpage, to display it to the user.

We can break the process down in the following steps:

```jsx
// 1 - Component
<Post />
```

```jsx
// 2 - Component is called (the function is called)

Post() // returns <div class="post">(...)</div>
```

```jsx
// 3 - The returned HTML is inserted in the webpage
<div class="post">
    <p>A first post</p>
    <p class="posted-at">Posted last week</p>
</div>
```

We say that React **renders** the component on the page.

Note: in this module, we will sometimes mention component names using their name
only (such as `Feed`) or using tag-like syntax, with chevrons (`<Feed />`). They
will refer to the same thing — the component.

## Using the React Developer Tools

[You should install the React Developer Tools for your web
browser](https://beta.reactjs.org/learn/react-developer-tools), as they'll be
really helpful into getting visibility in your React components and debugging
them.

After installing it, you should see two new tabs in your browser Developer tools, "Components" and "Profiler". You'll use mainly the first one for now.



## Exercise

In a new React project, write a component `Profile` in a file `Profile.js` which
returns the following HTML tree:

```html
<div id="profile">
    <h1 id="name">Quackie Makers</h1>

    <p id="job">Makers' favourite rubber duck</p>
    <p id="birthdate">2013</p>
</div>
```

Insert this component in your `App` component tree (in `App.js`), and view the
app in a web browser.

## Exercise

Use the React Developer tools to inspect the component in the app component tree.

[Next Challenge](03_props.md)

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F02_components.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F02_components.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F02_components.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F02_components.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F02_components.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
