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

## Exercise

Modify the previous component `Profile` to use three props for the name, the birthdate, and the job. Modify your component tree in `App.js` to pass these props to the component.

## Challenge

@TODO

[Next Challenge](04_testing_components.md)

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F03_props.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F03_props.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F03_props.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F03_props.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F03_props.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
