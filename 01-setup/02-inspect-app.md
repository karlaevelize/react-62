---
title: Inspecting React
description: Let's have a look around the app to see how it works
tags:
  - React
---

# Inspect the React App

Let's inspect the code of our fresh React App. Open up the project's folder in VS Code (either by opening the folder through VS Code, or using the command `code .` from a new terminal in the right folder). Make sure you open up the <Term>project folder</Term> itself, that is, the folder that contains the `package.json` file. This will probably make your life a bit easier :)

Let's start at the beginning. Check out the `index.html` file in the `public` folder.

The HTML file contains a lot of comments, but for the rest is mostly empty! All it has is a simple header and a body with a `div`.

```html
<div id="root"></div>
```

![](https://p-928eb7.f4.n0.cdn.getcloudapp.com/items/qGuNRXk6/Screenshot%202020-08-24%20at%2016.27.36.png?source=viewer&v=d243c89e33af7bbd648dd74b4ca8dea7)

Ok, so where does that **"Learn React"** text come from for instance? Check out `src/index.js`, that is where we find this line.

```jsx
ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById("root")
);
```

![](https://p-928eb7.f4.n0.cdn.getcloudapp.com/items/Qwu029P2/Screenshot%202020-08-24%20at%2016.28.28.png?source=viewer&v=a636013d44689a1477110196cb64e2a4)

There. What do you think that does?

Now open the `src/App.js` file, which will look like this:

```jsx
import logo from "./logo.svg";
import "./App.css";

function App() {
  return (
    <div className="App">
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
```

✍️ **Exercise**

1.  Search for **"Learn React"** in the code, and change it to something else, for example **"Hello World!"**

    Our _development server_ (which we started with `npm run start` and should still be running in the background) will automatically detect that a file was changed, and reload the app. Your change should automatically show up in Chrome.

2.  Play around a bit with the HTML-like content of this `App` component: maybe remove the `<header>` tag entirely, and replace it with a `<p>` tag describing how you feel about JavaScript or React :)

Only once you've solved the exercise on your own, compare your solution with [our solution](https://github.com/Codaisseur/react-week-awesomeapp/commit/5ec741e88cdaafca9e555d72f132030c3a41acb6).
