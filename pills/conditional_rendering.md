# Notes

- Example at the beginning
- "Hiding components"
- Recognise the problem first

# Conditional Rendering

Reactive components aren't very useful if they display the same information all
of the time. Some times we want to control what information is shown when, and
conditional rendering allows for this.

But first, we need to understand how the boolean operators work in JavaScript.

## The Weird World of Boolean Operators in JS

Take a look at the code below. What value do you think `result` will be?

```javascript
const result = true && false;
```

The answer is `false`. The `&&` represents the AND operation, where both sides
need to be true for the result to be true. With that in mind, what will `result`
equal here?

So far so good. But what if one of the values in the operation isn't a boolean?

```javascript
const result = true && undefined;
```

What do you expect `result` will equal here? Try it in your browser console.

Is that result what you expected? Take a moment to consider what might be going
on here.

What about if we use another primitive type in the expression?

```javascript
const result = 5 && 6;
```

What do you expect this to equal? Give it a try. Does this fit with your
explanation from before? If not, can you think of a new idea for what is
happening?

How about these other examples? Before each one, think about what you've seen so
far, and make a prediction as to what the result will be.

```javascript
const result1 = "Hello" && "World";
const result2 = null && 42;
const result3 = 1 && 2;
const result4 = 2 && 1;
const result5 = 5 && 0;
const result6 = 0 && 5;
const result6 = 0 && "Zero";
```

## So What is Going On?!

There are two JavaScript features at play here, "short-circuiting", and
"truthiness". Together, they explain the results we've seen above. Let's tackle
short-circuiting first.

### Short Circuiting

In JavaScript, a logical operation (such as `&&` or `||`) is evaluated left to
right. The evaluation will only go for as long as it has to. In the examples
below, the expression will only run as far as `false &&`. There's no point
continuing, because `false` AND any other value will always be false, so the
result is determined.

<!-- prettier-ignore-start -->
```javascript
const result1 = false && true;                         // false
const result2 = false && 5;                            // false
const result3 = false && "myString";                   // false
const result4 = false && true && true && true && true; // false
//    <-   will run   -> <--       won't run       -->
```
<!-- prettier-ignore-end -->

But this means that if the condition is _not_ determined, it _will_ continue.
For `&&`, the condition is only determined when _both_ sides of the `&&` have
been evaluated. The resulting value is the last value evaluated.

<!-- prettier-ignore-start -->
```javascript
const result1 = true && true;     // true
const result2 = true && 5;        // 5
const result3 = true && "string"; // "string"
const result4 = true && false;    // false
//    <--      will run      -->
```
<!-- prettier-ignore-end -->

But you knew that last one already!

With that in mind, what do you think will be printed to the console if you were
to run this code:

```javascript
const result = true && false;
result && console.log("Hello World");
```

Bear this in mind, it will be very useful when we get back to React!

### Truthy and Falsey Values

So short circuiting explains some of the results we've seen above, so let's move
on to how JavaScript treats other values...

In JavaScript, _all values_ are either "truthy" or "falsey". A truthy value will
be interpreted as `true` in boolean expressions, and falsey values will be
interpreted as `false`.

The falsey values are: `0`, `''`, `undefined`, `null`, `NaN` and `false`.
**Everything else is truthy.**

Keeping short-circuiting and truthiness in mind, predict the outcome of these
expressions, and check your understanding:

```javascript
const result1 = "Hello" && "World";
const result2 = "Hello" && "" && "World";
const result3 = 15 && undefined;
const result4 = null && "myString";
const result5 = false && true && 42;
const result6 = 5 && 0;
const result7 = 0 && 5;
const result8 = 0 && "Zero";
```

### Using this in React

This can be incredibly useful when writing pages in React. We can use this
short-circuiting behaviour to render elements and components _conditionally_, i.e.
only when some condition is met.

For example, say we have a React component which is going to represent the home
page of our app. If the user is logged in, a `name` prop will be passed to the
`HomePage` component. If the user is not logged in, this prop will be
`undefined`.

We can use the `&&` operator to change the contents of the page, depending on
whether the user is logged in. Remember, this is a JavaScript operation, not
JSX, so it needs to be wrapped in curly brackets `{}`.

```jsx
const HomePage = (props) => {
  return (
    <>
      <h1>Home Page</h1>
      {props.name && <h2>Welcome back {props.name}!</h2>}
    </>
  );
};
```

This is an incredibly common pattern in React, and it's definitely worth getting
used to.


<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=pills%2Fconditional_rendering.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=pills%2Fconditional_rendering.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=pills%2Fconditional_rendering.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=pills%2Fconditional_rendering.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=pills%2Fconditional_rendering.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
