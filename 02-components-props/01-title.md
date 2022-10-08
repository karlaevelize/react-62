---
title: "Title Component"
---

# Title component

To work with props in React we'll now create a simple `<Title />` component that takes a single prop: `content`. Components _receive props_ just like a normal JavaScript function _receives arguments_: props are the data the component is supposed to _render_, or "display".

## Simple component

Create a new file in `src/components/Title.js`. Create an empty component in the file:

```jsx
// src/components/Title.js
function Title() {
  return <h1>Hi there!</h1>;
}
```

> 🎩 Note that we use PascalCasing for components and component filenames. That means we have the Title component in `Title.js` and the App component in `App.js`.

A great first step, but we want to show our Title component in our main component. The App component is our main component (you can check this in `index.js`) so we want to add the Title component in the App component.

First let's export our Title component as default export.

```jsx
// src/components/Title.js
export default function Title() {
  return <h1>Hi there!</h1>;
}
```

We use default [exports](https://developer.mozilla.org/en-US/docs/web/javascript/reference/statements/export) in most if not all component files. This means we don't use brackets (_destructuring_) while importing the class.

Add the import to `App.js` and add the Title component to the `App` component's contents:

```jsx
// src/App.js
// ...
import Title from "./components/Title";

function App() {
  return (
    <div className="App">
      <main>
        <Title />
      </main>

      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
  );
}

export default App;
// ...
```

If you did everything well, your React app now shows "Hi there!" just above the header. Change the text and see if it changes. Notice that you don't have to refresh your app, that happens automatically!

Only once you've solved the exercise on your own, compare your solution with [our solution](https://github.com/Codaisseur/react-week-awesomeapp/commit/ffef2150070af1cc363e98739e57f0ca4dc19726).

## Using props

Components make it possible to split functionality of an app into small pieces that should be reusable. However, if every component needs to contain everything to show itself it would not be possible to make a reusable Title component. You want to give a prop some information. This is how React works, the parent component (in our case the App component) can pass on properties to child components (in this case the Title component). Let's make that happen!

Let's return a prop called `content` in our Title component inside an `<h1>` tag.

```jsx
// src/components/Title.js
export default function Title(props) {
  return <h1>{props.content}</h1>;
}
```

If you now look at your app you don't see anything, because the `content` prop is not set. That's done in our parent component, the App component. Let's adjust our render method:

```jsx
<main>
  <Title content="Some Simple Title" />
</main>
```

Your first proper component, be proud!

Only once you've solved the exercise on your own, compare your solution with [our solution](https://github.com/Codaisseur/react-week-awesomeapp/commit/c101275f6a284667f4b1002cac5a47ddcc6e85eb).

## Exercises

<MultiChoice
  id="distinction_component_instance"
  question="What is the difference between the _definition_ and an _instance_ of a component?"
  options={[
    "The definition is a function, the instance is what React makes from a bit of JSX",
    "There is no difference",
    "The instance is reusable, the definition is the function",
    "The definition is written like `<Hello` and the instance like `function Hello(props) {... }`"
  ]}
  shuffle
  correctIndex={0}
/>
<MultiChoice
  id="props_look_like_attrs"
  question="What is true of passing _props_?"
  options={[
    "You pass props down to a component instance, and they just look like html attributes",
    "Props are passed between components, so that they can communicate with each other"
  ]}
  shuffle
  correctIndex={0}
/>
