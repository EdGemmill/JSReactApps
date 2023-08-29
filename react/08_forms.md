# Forms

/\*\* EDU @TODO This feels like a lot for one section. I think possibly it would
be better to split it into multiple. For example, maybe we could have an earlier
section on handling events in React, such as an `onClick` button. Hard to think
of anything interesting that could happen with a single button that isn't a
counter. Maybe a ping/pong server? Or hitting another random API, similar to the
Joke API used in the `sending_http_requests` section.

RPS GAME!

Additionally, this section could use being made more interactive. Maybe have
each step as a challenge, with the answer hidden inside a \<details> block \*\*/

## Objectives

At the end of this section you should be able to:

- Explain how state is used in a React form
- Implement a React form component
- Test-drive a React form component

## Forms in HTML

For this section, follow along in a React project as you go.

As you've seen before, we can create a form in HTML with `form`, `input` and
`label` tags:

```html
<form method="POST">
  <label>
    Enter your username:
    <input type="username" name="username" />
  </label>
  <label for="password-field">
    Enter your password:
    <input type="password" name="password" />
  </label>
  <input type="submit" />
</form>
```

When we create a form like this, we are letting the browser handle most of the
operation, specifically:

- Keeping track of what's been typed into the input elements
- Updating the input element when the user types
- Submitting the form with a HTTP request, when the user hits submit.

But quite often in React, we want more control over the form ourselves. We want
to take some of this functionality from the browser, and use JavaScript to
achieve it instead. For this, we use _controlled components_.

## Forms in React

As mentioned above, there are three main operations we want to handle in
JavaScript rather than directly by the browser when creating a React Form.
Luckily, we've learned how to do these already:

**Keeping track of what's been typed into the input elements**

- We can use _state_ for this, with the `useState` hook.

**Updating the input element when the user types**

- We can use _Event Handlers_ to react to events on the page, such as typing.

**Submitting the form**

- We can use `fetch` to create our HTTP requests.

## Example

First, we want to create a react component that is going to represent our form:

```jsx
const Form = () => {
  return <form></form>;
};
```

So far this is very simple, and essentially just renders a form element on the
page. Let's add an input.

```jsx
const Form = () => {
  return (
    <form>
      <label>
        Enter your username:
        <input type="username" name="username" />
      </label>
    </form>
  );
};
```

Great! But we want to store the input ourselves, rather than just let the
browser handle it. Let's use `useState` to do this.

```jsx
const Form = () => {
  const [username, setUsername] = useState(""); // Initial state is an empty string ''

  return (
    <form>
      <label>
        Enter your username:
        <input type="username" name="username" />
      </label>
    </form>
  );
};
```

Now we can connect the two, making sure that the value of the input is coming
from our `username` variable.

```jsx
const Form = () => {
  const [username, setUsername] = useState("");

  return (
    <form>
      <label>
        Enter your username:
        <input type="username" name="username" value={username} />
      </label>
    </form>
  );
};
```

Give this a go! If we render this on our page, and try typing in the box, what
do you see?

That's not quite the behaviour we want though, we want to be updating the input
as we go. To do this, we need to use event listeners. We want to define an
_event handler_ function which will run every time the input changes. We're
going to use the `onChange` attribute for this.

```jsx
const Form = () => {
  const [username, setUsername] = useState("");

  const handleChange = () => {
    console.log("Input changed!");
  };

  return (
    <form>
      <label>
        Enter your username:
        <input
          type="username"
          name="username"
          value={username}
          onChange={handleChange}
        />
      </label>
    </form>
  );
};
```

Now every time we write into that input, our handler will run. You can see this
by opening up the console when this component is rendered. What happens when you
type?

This is a good step, but what we want to know is the new _value_ of the element,
after the user types. For this, recall that we can get the element that
triggered the event through the `target` property:

```jsx
const Form = () => {
  const [username, setUsername] = useState("");

  const handleChange = (event) => {
    console.log(event.target);
  };

  return (
    <form>
      <label>
        Enter your username:
        <input
          type="username"
          name="username"
          value={username}
          onChange={handleChange}
        />
      </label>
    </form>
  );
};
```

What happens now? What is being logged to the console when we type into the
input? Give it a go.

The specific information we are wanting to know about is the new _value_ of the
input element. This can be accessed through the `value` property on the
`HTMLElement`:

```jsx
const Form = () => {
  const [username, setUsername] = useState("");

  const handleChange = (event) => {
    const inputEl = event.target;
    console.log(inputEl.value);
  };

  return (
    <form>
      <label>
        Enter your username:
        <input
          type="username"
          name="username"
          value={username}
          onChange={handleChange}
        />
      </label>
    </form>
  );
};
```

Give this a go! What do you see in the console now?

We're getting close! We're now picking up on the change events through
JavaScript. The next step is to update the input's value when the change handler
is run. We can do this with the `setUsername` function!

```jsx
const Form = () => {
  const [username, setUsername] = useState("");

  const handleChange = (event) => {
    const inputEl = event.target;
    setUsername(inputEl.value);
  };

  return (
    <form>
      <label>
        Enter your username:
        <input
          type="username"
          name="username"
          value={username}
          onChange={handleChange}
        />
      </label>
    </form>
  );
};
```

And voila! Our form is now a controlled component! We have wrestled control of
the input from the browser, and are handling it ourselves. But the browser still
has control over submitting the form. We need to be able to submit the form from
JavaScript instead! And for this we need to use `fetch`.

Fetch takes two arguments: A url, and an object, containing more information
about the request. A POST request using fetch can be written like this:

```js
const payload = { someKey: "someValue" };

fetch("http://someurl.com/endpoint", {
  method: "POST",
  body: JSON.stringify(payload),
});
```

> **Note:** We can't send JS objects in a HTTP request directly, so we first
> need to convert it into a string. We do this with `JSON.stringify`.

What we want to do is create a `handleSubmit` function which we can attach to
the form, that will execute when the submit button is pressed. This will be very
similar to the `handleChange` function above, but will use the `onSubmit`
attribute on the form instead.

```jsx
const Form = () => {
  const [username, setUsername] = useState("");

  const handleChange = (event) => {
    const inputEl = event.target;
    setUsername(inputEl.value);
  };

  const handleSubmit = () => {
    fetch("http://url.com/endpoint", {
      method: "POST",
      body: JSON.stringify({ username: username }),
    });
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Enter your username:
        <input
          type="username"
          name="username"
          value={username}
          onChange={handleChange}
        />
      </label>
      <label>
        Submit
        <input type="submit" name="submit" />
      </label>
    </form>
  );
};
```

If we run this, and submit a username, we encounter a problem! Take a look in
the network tab of the developer console to see if you can work out what's going
on. You will need to make sure the "preserve log" option is checked.

You should see two requests happening, one is a POST request, to our endpoint.
The other, is a GET request, with a query parameter at the end. Something like
`?username=myusername`. What's happening here is that our `form` element is
submitting as normal, _as well as_ triggering the handler we've passed to
`onSubmit`.

To get around this, we'll need to prevent the default behaviour from occurring.
Luckily for us, the Event object has a function exactly for this!
`.preventDefault()` We can adapt our submit function to do this:

```js
const handleSubmit = (event) => {
  event.preventDefault();

  fetch("http://url.com/endpoint", {
    method: "POST",
    body: JSON.stringify({ username: username }),
  });
};
```

Once this is done, we have a working, JS controlled form in React! Pat yourself
on the back.

## Summary

Phew! We've covered a lot here! Specifically:

- How to control the contents of an input, by specifying the `value` attribute.
- How to attach functions (event handlers) to elements, using attributes such as
  `onChange` and `onSubmit`
- How to do a POST request to a server.
- How to prevent default browser behaviour, using `event.preventDefault()`

## Exercise

Add a password field to the form we just made. It should work similarly to the
username field.

1. You may need to rename some of your variables to make sure the component is
   easy to read.

2. You shouldn't be able to see the password as it's being entered. Research how
   to hide it.

## Exercise

Add a phone number field to the form above. Edit the handler function so that
only numbers are allowed in the input, and letters are removed.

## Bonus:

Use [conditional rendering](../pills/conditional_rendering.md) to display an
error message if the password that the user enters is less than 8 characters.


[Next Challenge](09_effects.md)

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F08_forms.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F08_forms.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F08_forms.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F08_forms.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F08_forms.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
