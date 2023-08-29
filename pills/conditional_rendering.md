@TODO Conditional Rendering

# Conditional Rendering

Reactive components aren't very useful if they display the same information all
of the time. Some times we want to control what information is shown when, and
conditional rendering allows for this.

But first, we need to understand how the boolean operators work in JavaScript.

## Truthy and Falsey Values

In JavaScript, all values are either "truthy" or "falsey". A truthy value can be
used in place of a `true` in boolean expressions, and vice versa for falsey
values.

The falsey values are: `0`, `''`, `undefined`, `null`, `NaN` and `false`.
Everything else is truthy.

```jsx
const MyComponent = () => {};
```

```javascript
const result = true && false;

const result = true && undefined;

const result = 5 && 6;

const result = 0 && 6;
```

```javascript
props.token && <MyComponent>
```


<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=pills%2Fconditional_rendering.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=pills%2Fconditional_rendering.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=pills%2Fconditional_rendering.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=pills%2Fconditional_rendering.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=pills%2Fconditional_rendering.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
