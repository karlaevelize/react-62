---
title: "Interpolating arrays with `.map`"
---

# Interpolating arrays with `.map`

In the previous section, we succesfully interpolated arrays of strings into JSX. However, it didn't look all too well, because React will just interpolate each string separately _without adding any extra space in between_:

![](https://p-928eb7.f4.n0.cdn.getcloudapp.com/items/7KuLAoDZ/Screenshot%202020-08-24%20at%2017.05.05.png?source=viewer&v=9d9aabe827d76dc9f6ede70e57847d74)

However, we can take advantage of the fact that React simply interpolates **each item separately** when it interpolates an array, if we can first **transform each item into some JSX** of our choice. This is where the JavaSript `.map` array method comes in handy.

## Some small exercises with `.map`

The `.map` array method can take some time getting used to, it's OK if this does not come naturally to you. That's why we'll start off with a few smaller exercises.

Run the following JavaSript code wherever you like. For example, your teacher's current favorite is to just open up the Console tab of the browser's DevTools. Or, you can put your code in a plain `.js` file and run it with Node like this: `node test.js`.

```tsx
const res = ["Eszter", "Violeta", "Rein", "Danny"].map((name) => {
  return name.length;
});
```

<MultiChoice
id="map_exercises_1575387308053"
question="What do you predict the value of the variable `res` will be? (You can try console.log-ging it)"
options={[
"`[6, 7, 4, 5]`",
"`undefined`",
"`[1, 1, 1, 1]`",
"`['Eszter', 'Violeta', 'Rein', 'Danny']`"
]}
shuffle
correctIndex={0}
/>

```tsx
const all_pokemon = [
  { name: "Charizard" },
  { name: "Mewtwo" },
  { name: "Mega beedrill" },
];

const res = all_pokemon.map((pokemon) => {
  return pokemon.name;
});
```

<MultiChoice
id="map*exercises_1575387534593"
question="What do you predict the value of the variable `res` will be? (You can try console.log-ging it)"
options={[
"`['Charizard', 'Mewtwo', 'Mega beedrill']`",
"`'Charizard'`",
"`[true, true, true]`"
]}
shuffle
correctIndex={0}
/>
<MultiChoice
id="map_exercises_1575387954657"
question="And the value of `all_pokemon` after running the code?"
options={[
"`[ { name: 'Charizard' }, { name: 'Mewtwo' }, { name: 'Mega beedrill' } ]`",
"`['Charizard', 'Mewtwo', 'Mega beedrill']`"
]}
shuffle
correctIndex={0}
/>
<MultiChoice
id="map_exercises_1575387772123"
question="What does the `.map` method do?"
options={[
"It makes a _new_ array, by transforming each item separately with the given _callback_ function",
"It _updates_ the array by applying the given _callback_ function to each item separately"
]}
shuffle
correctIndex={0}
/>

#### ✍️ Exercise

Use the `.map` method and `console.log` to print an _array_ of the weights of each of these Pokemon to the Console:

```tsx
const all_pokemon = [
  { name: "Charizard", weight: 90 },
  { name: "Bulbasaur", weight: 6.9 },
  { name: "Mewtwo", weight: 122 },
  { name: "Mega beedrill", weight: 65 },
];
```

Only once you've solved the exercise on your own, compare your solution with [our solution](https://github.com/Codaisseur/react-week-awesomeapp/commit/aacd1a3fe97019b9d75c4051047b5aa471edb5ec).

#### ✍️ Exercise

Use the `.map` method and `console.log` to print an _array_ of the name + weights of each of these Pokemon to the Console, like so: `"Charizard: 90 kg"`, etc.

```tsx
const all_pokemon = [
  { name: "Charizard", weight: 90 },
  { name: "Bulbasaur", weight: 6.9 },
  { name: "Mewtwo", weight: 122 },
  { name: "Mega beedrill", weight: 65 },
];
```

Only once you've solved the exercise on your own, compare your solution with [our solution](https://github.com/Codaisseur/react-week-awesomeapp/commit/c4dc58e9d435d7a7281d59f9c7f9438cc7c857f2).

## Using `.map` to render JSX

Now let's apply our newfound mapping techniques and refactor the way we are displaying each pokemon's abilities, we are currently rendering all of the abilities into a single `<p>` JSX element. <br>
We will start by mapping over the _abilities array_ instead, in order to turn each ability into it's own piece of JSX, in this case, a `<li>` element. Each `<li>` will in turn be displayed inside the wrapping `<ul>` element.

<!-- Now let's apply our newfound mapping techniques to interpolate an array of items in the `Pokemon` component, and render each item into a piece of JSX separately. In order, we start with an array of strings, which is then turned into an array of JSX items, which are then each separately interpolated into the `<ul>` JSX structure. -->

```tsx
// src/components/Pokemon.js
export default function Pokemon(props) {
  return (
    <div>
      <h2>Pokemon name: {props.name}</h2>
      <p>Weight: {props.weight} kg</p>
      <p>Awesome: {props.awesome ? "YES!" : "nope, not really"}</p>
      <p>Terrifying: {props.terrifying ? "Very" : "nah, lovable"}</p>
      <p>Abilities:</p>
      <ul>
        {props.abilities.map((ability, index) => {
          return <li key={index}>{ability}</li>;
        })}
      </ul>
    </div>
  );
}
```

Verify that this results in a DOM structure that looks like this. It might not look like much yet, but the HTML structure is way better workable this way!

![](https://p-928eb7.f4.n0.cdn.getcloudapp.com/items/mXuyPKjP/Screenshot%202020-08-24%20at%2017.09.01.png?source=viewer&v=f85e2e3b37a5610e9584e6831aa416f5)

> NOTE: when rendering elements or components with `.map`, React requires that each element/component that is returned within the callback of `.map` has a unique `key` prop. This `key` prop must be something unique that we can identify this element with - ideally an ID, but an index will suffice if don't have an ID. For more information: https://reactjs.org/docs/lists-and-keys.html#keys

#### ✍️ Exercise

Change the code a bit, so that we don't only see the list of abilities of each Pokemon, but also the total number of abilities:

![](https://p-928eb7.f4.n0.cdn.getcloudapp.com/items/mXuyPKm4/Screenshot%202020-08-24%20at%2017.10.17.png?source=viewer&v=7b863fdabd65798c30cb3bd4191f95aa)

Only once you've solved the exercise on your own, compare your solution with [our solution](https://github.com/Codaisseur/react-week-awesomeapp/commit/f747c3e2c8d66518101b5ec62b7803d33a62b296).

#### ✍️ Exercise

So far, we've mapped over any individual Pokemon's abilities. But we've "hardcoded" the four Pokemon in the first place. Let's change that. Use the code starter below, where we have an array of Pokemon in the App component. Map over this array, and for each item, render a `<Pokemon ... />` component instance, passing in the right props.

```tsx:collapse
// src/App.js
import "./App.css";

import Title from "./components/Title";
import Pokemon from "./components/Pokemon";

const all_pokemon = [
  {
    name: "Charizard",
    weight: 90,
    awesome: true,
    terrifying: false,
    abilities: ["Blaze", "Solar power", "Tough claws", "Drought"]
  },
  {
    name: "Bulbasaur",
    weight: 6.9,
    awesome: true,
    terrifying: false,
    abilities: ["Overgrow", "Chlorophyll"]
  },
  {
    name: "Mewtwo",
    weight: 122,
    awesome: true,
    terrifying: true,
    abilities: ["Pressure", "Unnerve", "Steadfast", "Insomnia"]
  },
  {
    name: "Mega beedrill",
    weight: 65,
    awesome: false,
    terrifying: true,
    abilities: ["Intimidate", "Unnerve"]
  }
];

function App() {
  return (
    <div className="App">
      <main>
        <Title content="Some Simple Title" />
        {/* TODO map over the pokemon here */}
      </main>
    </div>
  );
}

export default App;
```

Only once you've solved the exercise on your own, compare your solution with [our solution](https://github.com/Codaisseur/react-week-awesomeapp/commit/4d5ad6348cc1e704ef115c49becbdc9fd0b1128c).
