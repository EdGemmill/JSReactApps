# Testing components

## Objectives

At the end of this section you should be able to:

- Write a unit test for an existing component
- Test-drive a new component having props

## Using the Testing Library

We will be using React Testing Library, a library which contains matchers which
specifically help us to test react components. This contains a number of useful
functions for us, and more details can be found in the
[Testing Library Docs](https://testing-library.com/)

#### Queries

Such as `.getByRole` or `.findByText`. More information about these can be found
here: https://testing-library.com/docs/queries/about#types-of-queries

#### Screen

`screen` allows us to write tests to test the document body. For example, using
`screen.findByLabelText(name)` will search the whole HTML body for an element
that has a `name` label attached to it.

#### Render

React Testing Library's `render` method allows us to render specific React
components, and test against them, without needing to load a whole application.

## Writing Tests for Components

When testing "manually" (as a human) your web application, you will usually
follow the same process intuitively:

- Opening the web application
- Maybe doing something, like clicking on a button, or filling a form
- Then verifying that the page looks like it should (it "works" or it doesn't)

Most of the automated tests for components will follow a same structure:

- Setup — rendering a component using the built-in `render` function.
- Doing something — simulating a click on a button, or something different.
- Asserting the web page has a certain element or some specific content.

```js
// file: src/Profile.test.jsx

import React from "react";
import { render, screen } from "@testing-library/react";
import "@testing-library/jest-dom";
import Profile from "./Profile";

test("renders with the correct title ", () => {
  // Setup - rendering the component on the page
  render(<Profile />);

  // Assert
  expect(screen.getByRole("heading")).toHaveTextContent("Quackie Makers");
});
```

> **Note:** The example above won't work as it is, because we currently aren't
> passing any props to the Profile component. Can you update the Setup part of
> the test so that it passes the assertion?

## Exercise 1

Write at least two tests for the `Profile` component created in the previous
sections.

## Exercise 2

Re-implement the `Profile` component, this time test-driving it (write the test
first, see it fail, then write the component code).

## Exercise 3

Test-drive and implement a new component `Recipe`, having three props:

```jsx
<Recipe title="Finnish cinammon buns" type="dessert" duration={60} />
```

You're free to choose the final HTML structure for this component, as long as
your test uses correct assertions for it.

## Challenge

Write a test for the Gig component from the previous section, making sure that
all the information passed as props is displayed on the page.


[Next Challenge](05_state.md)

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F04_testing_components.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F04_testing_components.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F04_testing_components.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F04_testing_components.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F04_testing_components.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
