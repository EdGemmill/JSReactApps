# Test-driving components

## Objectives

At the end of this section you should be able to:
 * Write a unit test for an existing component
 * Test-drive a new component having props

## Using the Testing Library

@TODO

## Writing Tests for Components

When testing "manually" (as a human) your web application, you will usually follow the same process intuitively:
 * Opening the web application
 * Maybe doing something, like clicking on a button, or filling a form
 * Then verifying that the page looks like it should (it "works" or it doesn't)

Most of the automated tests for components will follow a same structure:
 * Setup — rendering a component using the built-in `render` function.
 * Doing something — simulating a click on a button, or something different.
 * Asserting the web page has a certain element or some specific content.

```js
// file: src/App.test.js

import React from 'react'
import {render, screen} from '@testing-library/react'
import '@testing-library/jest-dom'
import Profile from './Profile'

test('renders with the correct title ', () => {
    // Setup - rendering the component on the page
    render(<Profile />)

    // Assert
    expect(screen.getByRole("heading")).toHaveTextContent('Quackie Makers')
});
```

## Exercise

Write at least two tests for the `Profile` component created in the previous sections.

## Challenge

Test-drive and implement a new component `Recipe`, having three props:

```jsx
<Recipe
    title="Finnish cinammon buns"
    type="dessert"
    duration={60} />
```

You're free to choose the final HTML structure for this component, as long as your test uses correct assertions for it. 


[Next Challenge](05_state.md)

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F04_testing_components.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F04_testing_components.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F04_testing_components.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F04_testing_components.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F04_testing_components.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
