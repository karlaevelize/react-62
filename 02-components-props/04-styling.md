---
title: "Styling intermezzo"
---

# Styling intermezzo

Time for a styling intermezzo! Our app already contains quite some structure and features, but isn't really presentable yet. In this section, we're going to add some "basic industry standard defaults", just to get started quickly. That being said, there's lots of other (more interesting?) options out there, so keep your eyes open!

## Bootstrap

Instead of writing too much handcrafted CSS, we're going to leverage a well-known <Term>CSS framework</Term> called [Bootstrap](https://getbootstrap.com/). This way, we can quickly set up a responsive and reasonably beautiful app with almost no effort. But don't worry: later on in the course, we'll spend more time customizing and handcrafting more awesome CSS.

**👉 Install Bootstrap**

```sh
npm install bootstrap
```

## Sass

Instead of writing <Term>vanilla CSS</Term> (just ordinary CSS), we're going to use a slightly _enhanced version_ of CSS called <Term term="Sass">[Sass](https://sass-lang.com/)</Term>. This will make it a bit easier to customize the overall theme of our app, because Sass has _variables_ which CSS does not. Bootstrap is built with Sass and uses a bunch of variables that we can override in order to customize it.

**👉 Install Sass**

```sh
npm install sass
```

## Global style: Sass-customized Bootstrap

First off, we're going to add some global styling to the app. Add a new folder `src/style` and add two new files `_config.scss` and `global.scss` into this folder. In the first file, we import some pleasing fonts from the web and override some of Bootstrap's Sass variables to customize Bootstrap to use these fonts.

```scss
// src/style/_config.scss

@import url("https://fonts.googleapis.com/css?family=Roboto+Slab:800|Libre+Baskerville:400,400i,700,700i&display=swap");

$headings-font-family: "Roboto Slab", serif;
$headings-font-weight: 800;

$font-family-base: "Libre Baskerville", serif;
```

_If you're interested, the underscored filename has a technical reason: this way the "bundler" knows that it's a Sass helper file with just some variables, and is able to more efficiently "optimize" the bundled code._

In the second file, we actually import Bootstrap, but not before importing our customizations.

```scss
// src/style/global.scss

@import "./config";
@import "~bootstrap";
```

_The absence of the file extension and understore is intended. Don't worry about the technical reasons too much for now._

Finally, we import this `global.scss` in our `index.js` _entry file_, replacing it for the `index.css` import:

```diff
-import "./index.css";
+import "./style/global.scss";
```

Now, if you look at your App, it should present itself with the new font.

Only once you've solved the exercise on your own, compare your solution with [our solution](https://github.com/Codaisseur/react-week-awesomeapp/commit/d735b9870275e41db0f512963a5290799fe2fd63).

## Adding some Bootstrap classes

Bootstrap provides a whole bunch of _CSS classes_ that we can use to add style to HTML elements. Roughly speaking, these fall into four categories. Per category, we're going to add some style to our app.

### 1. Layout (adaptive/responsive grid)

_[Bootstrap documentation page](https://getbootstrap.com/docs/4.4/layout/overview/)_

Arguably one of the most important aspects of an app design is its _layout_. Bootstrap ships with a _12-column responsive grid layout_. This means that the primary means of organizing content is by horizontally dividing the page into columns, row by row, and deciding how wide (in 1/12th fractions) each column should be.

Let's update the `App` component to display its contents in a grid structure. First off, we need the `.container` class to surround _all_ the content. This visually centers the content in the middle of the screen. Then, we want to place the Pokemon in a grid. So, we first add a `.row` around all the Pokemon, and add each Pokemon separately into a column.

For each column, we specify _how wide_ that column should be, depending on the _screen size_ of the browser the user is using. This makes the design <Term term="responsive web design">responsive</Term>: it adapts to the size of the user's screen. Bootstrap has four "break-off" points, making it an <Term>adaptive grid</Term>: small (≥ 576px wide), medium (≥ 768px wide), large (≥ 992px wide), and extra large (≥ 1200px wide).

In this case, we're telling Bootstrap to give each Pokemon a column that is:

- Either the full width of the container (the "default case")
- Or, if the screen is at least medium size (≥ 768px wide), then 6/12 = 1/2 of the width of the container
- Or, if the screen is at least large size (≥ 992px wide), then 4/12 = 1/3 of the width of the container

```tsx-ok
  return (
    <main className="container">
      <Title content="Some Simple Title" />
      <div className="row">
        {all_pokemon.map((pokemon, index) => (
          <div key={index} className="col-md-6 col-lg-4">
            <Pokemon
              name={pokemon.name}
              weight={pokemon.weight}
              awesome={pokemon.awesome}
              terrifying={pokemon.terrifying}
              abilities={pokemon.abilities}
            />
          </div>
        ))}
      </div>
    </main>
  );
```

### 2. Content / typography

_[Bootstrap documentation page](https://getbootstrap.com/docs/4.4/content/typography/)_

Arguably, there's not really much to say about this, usually it just works, if we use the right <Term>semantic HTML tags</Term>. For example, `<h1>` through `<h6>` for headings (`<h1>` being the most important, `<h2>` second-most, etc.), and `<p>` for paragraphs of text, `<ul>` and `<ol>` and `<li>` for lists, etc., etc.

### 3. Components

_[Bootstrap documentation page](https://getbootstrap.com/docs/4.4/components/card/)_

These are _not the same thing as React components_, but rather "typical visual elements" that designers talk about when discussing a design. For example, the _Card_, or the _Breadcrumb_, or the _Tooltip_. Typically, one of these _visual components_ is built from a little combination of HTML elements nested in a particular way. For example, a _Card_ might look like this:

```html
<div class="card">
  <div class="card-body">
    <h5 className="card-title">Bulbasaur</h5>
    <p>Some content</p>
    <p>Some more content</p>
  </div>
</div>
```

Let's turn each Pokemon component instance into a card (with a _list group_ inside of it)!

```tsx
// src/components/Pokemon.js
export default function Pokemon(props) {
  return (
    <div className="card">
      <div className="card-body">
        <h5 className="card-title">{props.name}</h5>
        <h6 className="card-subtitle">
          {props.awesome ? "An awesome Pokemon" : "Not awesome"}
        </h6>
        <p>
          Weight: {props.weight} kg
          <br />
          Terrifying: {props.terrifying ? "Very" : "nah, lovable"}
          <br />
          {props.abilities.length} abilities
        </p>
      </div>
      <ul className="list-group list-group-flush">
        {props.abilities.map((ability, index) => {
          return (
            <li key={index} className="list-group-item">
              {ability}
            </li>
          );
        })}
      </ul>
    </div>
  );
}
```

_Indeed, you'll have noticed that in React we need to write `className` whereas the HTML attribute is called `class`. This is an unfortunate (though substantiated) design decision of the React team, that we'll just have to live with..._

### 4. Utility classes (mainly: spacing utilities)

_[Bootstrap documentation page](https://getbootstrap.com/docs/4.4/utilities/spacing/)_

Apart from layout, typography and components, we still need to manage lots of minor visual details. We can do this by adding custom lines of CSS code, but Bootstrap also provides a number of helper <Term term="utility class">utility classes</Term>. This way, it can be easier to stick to a <Term>design system</Term> of consistently styled elements.

Most importantly in this category are the _spacing utilities_. These are helper classes that you can use to add _margin_ and _padding_ to your elements. The CSS <Term>box model</Term> describes how each HTML element has a _margin_ ("breathing space around the element"), a _border_, and then a _padding_. Take a look at this box model in your browser's DevTools!

![](https://p95.tr4.n0.cdn.getcloudapp.com/items/QwuGl69O/Screenshot+2019-12-17+at+01.14.53.png?v=23d07054e572b6929c0046ea4227afb5)

Let's improve the Pokemon component a bit by adding some of these spacing utilities where necessary, and a card shadow, and some colors.

```tsx
// src/components/Pokemon.js
export default function Pokemon(props) {
  return (
    <div className="card shadow-sm mb-4">
      <div className="card-body pb-0">
        <h5 className="card-title">{props.name}</h5>
        <h6 className="card-subtitle mb-3 text-primary">
          {props.awesome ? "An awesome Pokemon" : "Not awesome"}
        </h6>
        <p className="mb-0">
          Weight: {props.weight} kg
          <br />
          Terrifying: {props.terrifying ? "Very" : "nah, lovable"}
          <br />
          {props.abilities.length} abilities
        </p>
      </div>
      <ul className="list-group list-group-flush">
        {props.abilities.map((ability, index) => {
          return (
            <li key={index} className="list-group-item">
              {ability}
            </li>
          );
        })}
      </ul>
    </div>
  );
}
```

Your app should now look roughly like this:

![](https://p-928eb7.f4.n0.cdn.getcloudapp.com/items/lluYkoXD/Screenshot%202020-08-24%20at%2017.17.39.png?source=viewer&v=bdd3dcc81c3ddd442fa1691b7dede356)

#### ✍️ Exercise

We still have some spacing issues. Use the `.my-5` spacing utility class to add some vertical margin around the entire page's contents. Use the `.mb-4` spacing utility class to add some margin between the page title and the Pokemon cards.

Only once you've solved the exercise on your own, compare your solution with [our solution](https://github.com/Codaisseur/react-week-awesomeapp/commit/1e179524e66232b444320d5a0a91cc268b7c2f1a) and all of the above sections.

## Add some special-case handcrafted styles

Let's add something more specific and fun! It would be nice to have a hover effect, so that when you hover over a card with your mouse, it animates a bit. Bootstrap doesn't give us anything here, so we're going to add some custom CSS.

React is all about _component-based UI design_, which means that the primary way that we _break up and modularize our code_ is by separating out reusable pieces of UI that we call "components". As a "bit of UI", each component is entitled to have a slice of everything involved in making a UI:

- **HTML structure** — this is the JSX we return from the function that defines the component
- **JS behaviour** — our components don't have too much behavior just yet, that's a topic for tomorrow
- **CSS styles** — if the component needs to be styled, we're going to _colocate_ that CSS (or Sass) code close together with the component definition

The new styling feature is a feature of the Pokemon component, which means we want to _colocate_ the CSS code near the component definition.

Add a `Pokemon.scss` file next to your `Pokemon.js` component file.

```scss
// src/components/Pokemon.scss

.Pokemon {
  transition: transform 0.2s ease;
}
.Pokemon:hover {
  transform: scale(1.02) translate(0, -3px);
}
```

#### ✍️ Exercise

Make the two remaining changes to complete the hover-effect feature: (1) import the `Pokemon.scss` file in the Pokemon component file, and (2) add the `.Pokemon` class to the `.card` div.

Only once you've solved the exercise on your own, compare your solution with [our solution](https://github.com/Codaisseur/react-week-awesomeapp/commit/e81bb92d8889bb05113fadc2dc2c64dbea463830).

#### ✍️ Exercise

This might not be sensible from a design-perspective, but let's have some fun: can you figure out how to make the card _rotate_ when the user hovers their mouse over the card?

_Hint: use Google! For example, you could search for "css rotate how do I rotate a div on hover". Googling tips: include some basic keywords, as well as a little question that you imagine others in your position would have formulated._

Only once you've solved the exercise on your own, compare your solution with [our solution](https://github.com/Codaisseur/react-week-awesomeapp/commit/dcfb9b02558da6d3fc78f94088426c0c7de4e305).
