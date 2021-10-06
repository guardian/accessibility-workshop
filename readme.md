# Accessibility Workshop

## Prerequisites

- [Node Version Manager](https://github.com/nvm-sh/nvm)
- [Yarn](https://yarnpkg.com/)
- [axe Devtools Extension](https://www.deque.com/axe/browser-extensions/)

## Recommended

- [Funkify Extension for Chrome](https://www.funkify.org/)
- [Color Blindness Empathy Test for Firefox](https://addons.mozilla.org/en-GB/firefox/addon/a11y-color-blindness-test/?utm_source=addons.mozilla.org&utm_medium=referral&utm_content=search)
- [Sim Daltonism (Mac app, alternative to the extensions)](https://michelf.ca/projects/mac/sim-daltonism/)
- MacOS Enhanced Dictation/Voice Control
  - Go to System Preferences > Keyboard > Dictation, turn Dictation on and select Use Enhanced Dictation
  - Go to System Preferences > Accessibility > Dictation > Dictation Commands and select Enable advanced commands
  - If you're on macOS Catalina, [use this guide instead](https://support.apple.com/en-gb/guide/mac-help/mh40719/mac)

## Setup

### Install dependencies

```sh
nvm use
yarn
```

## Workshop

Go ahead and run your local dev server (`yarn start`). Feel free to play around with the app and get familiar with it.

### Note on component structure

- `src/index.js` is the entry point to the app. It handles rendering the whole app and, when not in production, will include [`@axe-core/react`](https://www.npmjs.com/package/@axe-core/react)
- `containers/App/index.js` handles the "states" of the `<App />` component. It's sole purpose is to handle state and pass relevant props down to `components/App/index.js`
- `components/App/index.js` renders the "structure" of the app. It is where the global navigation/skip link/main elements live.
- `components/Stats/index.js` is where the recipe stats live ("X eggs used", "Y recipes made", etc.)
- `components/Recipes/index.js` is where the recipe tiles live. It also instantiates the view/edit modals for each recipe.

### Testing and fixing

The app has various issues which could cause problems for people relying on assistive technology. Work together to identify and understand the problems, and implement a fix.

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

- Images may not all need alt text if they are described by the surrounding text, but any alt text that's used should be meaningful and unique.
- Interactive elements should be announced, with a prompt from the screen reader about how to use them.
- Inputs should have clear labels, and any error messages should be descriptive and easy to understand.

#### Colour contrast

If you've downloaded Sim Daltonism and/or one of the browser extensions, switch on one of the colour blindness simulations and take a look at the app. Is there any text that's more difficult to read against its background?

Open up your devtools- you should see a tab for the axe DevTools extension. Switch to that tab and run a scan of the page. This will flag up any automatically-detectable issues with the page, including a number of colour contrast problems. Using [Who Can Use](https://whocanuse.com) to test and adjust colours, fix any issues with insufficient contrast between the text and background, then try using the colour blindness simulation again to see the difference.

### Stretch challenges

#### Switch navigation

Go to System Preferences > Acessibility on your Mac, and turn on Switch Control (it's the last item in the list on the left). You'll probably also want to increase the timing speeds of the interface- these settings can be accessed under the Navigation tab.

With switch control enabled, the space bar on your keyboard acts as a switch, similar to physical switches or 'sip and puff' switches that some disabled people may use when using a computer. You should see an interface that allows you to control various things with your space bar switch- hit the space bar to automatically toggle through the options, and hit it again to select something.

Try navigating through the app using the switch- the pointer options are useful for navigating and selecting things, and the keyboard for typing. Are elements easily selectable with the pointer controls? Does the form validation make it easy for you to go back and correct errors?

#### Voice navigation

If you're using macOS Catalina, use the guide linked above on setting up and using Voice Control. If you're using macOS Mojave, make sure you've set up Enhanced Dictation as outlined above. Turn on Dictation- the default shortcut is hitting the fn key twice- and say 'Show commands' to get a helpful list of available commands.

Try navigating around the page. 'Go to next field' should act like the tab key, and with advanced commands enabled you should be able to give commands like 'Click [button text]' to select a button or other interactive element.

Try navigating around, and maybe editing some of the recipes using voice controls

#### Unit tests

The unit tests are written with [Jest](jestjs.io/) and [Enzyme](https://enzymejs.github.io/enzyme/).

```sh
yarn test
```

Do any of them fail? Work with your partner to fix the issue(s) in the relevant components. If you've already fixed some issues in one of the sections above, try writing tests for them!
