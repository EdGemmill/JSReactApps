# RPS Part 2

## Objectives

At the end of this section you should be able to:

- Explain how state can be shared between components by "lifting the state up"
- Implement a small React app with state shared between different components

## Single Player Rock Paper Scissors?!

Rock Paper Scissors isn't a very good game by yourself. Let's adapt it so we can
play against a computer!

We'll need a few extra parts for this:

- A way for the computer to pick a choice at random, each time the user makes a
  choice.
- A way to display the computer's choice
- A way to work out who has won, and display it to the user.

## Exercise

- Create a function called `randomChoice` inside your `RockPaperScissors`
  component, which returns at random one of the three choices in the game. This
  can be `"rock"`/`"paper"`/`"scissors"` or `0`/`1`/`2`, or whatever
  representation you've chosen for your game.
- Whenever the user presses one of the buttons available to them, the computer
  should also make a choice, which also needs to be stored as _state_. For now
  this doesn't need to be displayed to the user. You can log it to the console
  instead.

## Displaying the computer's choice to the user

Now that we have a choice for the computer, we want to be able to display it to
the user, alongside their choice. You probably could copy the code you have
already and get it to work pretty easily, but then we'd be repeating ourselves,
and besides one of the main reasons for using a library like React is so that we
can create _reusable components_.

So instead, let's create a reusable component!

# Exercise

Take the logic you've already written for displaying the user's choice, and
refactor it into a _new component_. called `Choice`.

- Create a new component called `Choice`.
- This component should take one prop, `choice`, which takes one of the three
  representations for Rock Paper and Scissors. (eg.
  `"rock"`/`"paper"`/`"scissors"` or `0`/`1`/`2` etc., whatever you've chosen
  for your game.)
- Depending on the `choice` prop passed, it should render one of the three
  emojis: 🪨📄✂️

Render this `Choice` component twice in your `RockPaperScissors` component. Once
for the user's choice, and once for the Computer's choice.


<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F07a_RPS_challenge_2.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F07a_RPS_challenge_2.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F07a_RPS_challenge_2.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F07a_RPS_challenge_2.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fjavascript-react-applications&prefill_File=react%2F07a_RPS_challenge_2.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
