# Props

## Objectives

At the end of this section you should be able to:
 * Explain how props can be used to make a component render differently
 * Implement a component using props

We use "props" to customise the way a component looks. Props are passed to a component as attributes, similar to HTML attributes. When in the component code, props are given as an argument to the function, and is an object containing the different passed properties.

```jsx
<Post title="A random post" postedAt="Yesterday" />
```

```jsx
// We can also use more than one lines for readability
<Post
    title="A random post"
    postedAt="Yesterday" />
```

```jsx
const Post = (props) => {

    // props is an JavaScript object 

    return (<div className="post">
        <p>{props.title}</p>
        <p className="posted-at">{props.postedAt}</p>
    </div>)
}

export default Post
```

Note that we use curly braces `{}` to insert JavaScript values or expressions into the HTML tree.

## On JSX syntax

The JSX syntax allows up to write HTML inside JavaScript files. It also allows us to insert JavaScript values in the HTML attributes or content.

Here are some examples:

```jsx
const name = 'Anna'

return (<p>{name}</p>)
```

This one is a bit more complex, pay close attention to matching brackets.
```jsx
const names = ['Anna', 'Jose', 'Lila'];

return (
    <div>
        {names.map(name => (
            <p>{name}</p>
        ))}
    </div>
)
```

When using components, we can use the same syntax to pass values. Assuming we have a component `Post`, we could write the following:

```jsx
const title = 'My post'

return (<div>
    <Post title={title}>
</div>)
```

## Exercise

Modify the previous component `Profile` to use three props for the name, the birthdate, and the job. Modify your component tree in `App.js` to pass these props to the component.

Use the React Developer tools to inspect the component and the props it's rendered with.

## Challenge

Write a new component `Product` having the following props: `name`, `description`, and `price`. 

Use at least two instances of this component in your `App` root component to display them in your app.

```jsx
<Product
    name="Air Fryer K2000"
    description="The best air fryer to fry all things, even Mars bars"
    price={2000}>
```

Note that we need to use the curly brackets to pass a numeric value as a prop, instead of quotes. 

[Next Challenge](04_testing_components.md)

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F03_props.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F03_props.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F03_props.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F03_props.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F03_props.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
