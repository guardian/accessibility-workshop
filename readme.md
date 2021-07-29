# Accessibility Workshop

## Prerequisites

- [Node Version Manager](https://github.com/nvm-sh/nvm)
- [Yarn](https://yarnpkg.com/)
- [axe Devtools Extension](https://www.deque.com/axe/browser-extensions/)

## Setup

### Install dependencies

```sh
nvm use
yarn
```

## Workshop

Go ahead and run your local dev server (`yarn start`). Feel free to play around with the app and get familiar with it.

### Component structure

- `src/index.js` is the entry point to the app. It handles rendering the whole app and, when not in production, will include [`@axe-core/react`](https://www.npmjs.com/package/@axe-core/react)
- `containers/App/index.js` handles the "states" of the `<App />` component. It's sole purpose is to handle state and pass relevant props down to `components/App/index.js`
- `components/App/index.js` renders the "structure" of the app. It is where the global navigation/skip link/main elements live.
- `components/Stats/index.js` is where the recipe stats live ("X eggs used", "Y recipes made", etc.)
- `components/Recipes/index.js` is where the recipe tiles live. It also instantiates the view/edit modals for each recipe.

### Unit tests

The unit tests are written with [Jest](jestjs.io/) and [Enzyme](https://enzymejs.github.io/enzyme/).

```sh
yarn test
```

Some of them will fail. Work with your partner to identify the problems, and fix the components so the tests pass.

### axe DevTools

Once the unit tests are passing, open the app in your browser at `http://localhost:1235`, and open up your devtools. You should see a tab for the axe DevTools extension- switch to that tab, and run a scan of the page.

You'll see a number of 'serious' and 'critical' issues flagged up, which you can look through using the arrow buttons in the top right. Most will have a clear explanation of how to fix the problem- work through these with your pair. A few will be flagged up as needing review, due to the limitations of the automated tooling- in the context of this workshop, these issues can be safely ignored.

### Manual testing

Automated testing can do a lot to help flag up accessibility issues, but manual testing with assistive technologies is the best way to find problems with the way a page actually feels to use. Make sure you check through all the features of the app, including the recipe edit form. When you've identified a problem, try writing a unit test to cover it!

#### Initial sense check

In looking at the page and through the code so far, have you already noticed any issues? For example, does the page title look right to you? Talk to your pair about anything you've already spotted, and how you can fix it.

#### Keyboard navigation

Try navigating around the app just using your keyboard.

- Can you always easily keep track of which element has keyboard focus?
- Is there anything you can interact with using your mouse, but not with your keyboard?

It may help to use the Inspect tab in your devtools to take a look at the markup and focus styling of particular elements.

#### Using a screen reader

You may find this easiest to do in Safari. Start VoiceOver, and try navigating around the page just like you did with the keyboard. Focus on what you're hearing, and not what you can already see. Are you getting all the same information as you would using the page visually?

Some areas to focus on:

- Images may not all need alt text if they are described by the surrounding text, but any alt text should be meaningful and unique.
- Interactive elements should be announced, with a prompt from the screen reader about how to use them.
- Inputs should have clear labels, and any error messages should be descriptive and easy to understand.
