---
title: "JSX Interpolation"
---

# JSX Interpolation

<Tagline>Let's add some data!</Tagline>

<iframe width="640" height="400" src="https://www.youtube.com/embed/eyxm_Z93rQQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

We're going to want to work with all kinds of interesting data in our React apps, not just strings. In order to use your variables or other expressions to show data in your React app, we need to <Term term="interpolation">interpolate</Term> these values into the returned <Term term="JSX">JSX structure</Term>. In order to interpolate data in JSX, we use the `{` and `}` brackets, here's what that looks like:

```tsx
function Dino() {
  const name = "T-Rex";
  return <div>Name: {name}</div>; // <-- interpolated data!
}
```

<MultiChoice
  id="js_syntax_brackets_1575498027647"
  question="Brackets `{ }` are used to denote all kinds of different things in JavaScript syntax! Which of these things are they _not_ used for though?"
  options={[
    "Array expressions",
    "Function bodies",
    "Object expressions",
    "JSX interpolation"
  ]}
  shuffle
  correctIndex={0}
/>

## Different kinds of data

You'll remember from last week that JavaScript has differents kinds of data, i.e. different _data types_:

- Numbers, for example: `0`, `78`, `-3.14`, etc.
- Strings, for example: `"Hello there!"`, `'or with single quotes'`, etc.
- Booleans: `true` and `false`
- Null and undefined, for example: `null`, `undefined`
- Arrays, that we use to collect _sequences_ of data together:

  ```tsx
  const dinos = ["T-Rex", "Diplodocus"];

  const fibonacci = [1, 1, 2, 3, 5, 8, 13, 21];

  const all_kinds_of_stuff = ["A string", 3.14, null, null, "bla"];
  ```

- And finally, objects, that we use to collect _key-value pairs_ of data together, like little dictionaries:

  ```tsx
  const santa = {
    name: "Santa Claus",
    age: 1748,
    hobbies: ["giving presents", "having fun", "laughing"]
  };
  ```

- _Actually, we even have an extra type of value: **functions**! But functions are of course not used as data, but for functionality, so we're not interested in them here._

## Interpolation exercises

We're going to play around with interpolating these different data types. First off, all _primitive_ data types (strings, numbers, booleans, null, and undefined) can be interpolated. To check this out, define a new React component in `src/components/Pokemon.js`.

```tsx
// src/components/Pokemon.js
export default function Pokemon() {
  return (
    <div>
      <h2>Pokemon name: {"Charizard"}</h2>
      <p>Weight: {90} kg</p>
      <p>Awesome: {true}</p>
      <p>Terrifying: {false}</p>
      <p>What about null? {null}</p>
      <p>And undefined? {undefined}</p>
    </div>
  );
}
```

This is just the <Term term="component definition">definition</Term> of the component, but of course we also want to include an instance of it in our app, so let's modify our `App` component:

```tsx
// src/App.js
// ...
import Title from "./components/Title";
import Pokemon from "./components/Pokemon"

function App() {
  return (
    <div className="App">
      <main>
        <Title content="Some example title" />
        <Pokemon />
      </main>

      // ...
```

Now, open the Elements tab of your browser's DevTools, and find the rendered DOM nodes for this component, which should look something like this:

![](https://p-928eb7.f4.n0.cdn.getcloudapp.com/items/jkuZEPn9/Screenshot%202020-08-24%20at%2016.52.40.png?source=viewer&v=67c3ae2948f6812cf13b37bb13d2ade1)

Only once you've solved the exercise on your own, compare your solution with [our solution](https://github.com/Codaisseur/react-week-awesomeapp/commit/0b36b69eedca4317d87243ff502282193ab27769).

<MultiChoice
  id="jsx_interpolation_1575371625172"
  question="What do you notice about the interpolation of booleans?"
  options={["They don't show up at all", "They show up as `true` and `false`"]}
  shuffle
  correctIndex={0}
/>

Now, temporarily add a new paragraph to the Pokemon component, that interpolates an _object_. _Notice that double brackets, the first surrounding pair is because we're interpolating, the inner pair is because the value is an object._

```tsx-ok
  <p>Types: {{ fire: true, water: false }}</p>
```

<MultiChoice
  id="jsx_interpolation_1575371865953"
  question="What do you notice about the interpolation of objects?"
  options={[
    "They throw big red error messages",
    "They don't show up at all",
    "Each key-value pair gets interpolated individually"
  ]}
  shuffle
  correctIndex={0}
/>

Now, add a new paragraph to the Pokemon component, that interpolates an _array_. _Notice the double brackets, the first surrounding pair is because we're interpolating, the inner pair of square brackets is because the value is an array._

```tsx-ok
  <p>Abilities: {["Blaze", "Solar power", "Tough claws", "Drought"]}</p>
```

<MultiChoice
  id="jsx_interpolation_1575372436921"
  question="What do you notice about the interpolation of arrays?"
  options={[
    "Each item gets interpolated individually",
    "They throw big red error messages",
    "They don't show up at all"
  ]}
  shuffle
  correctIndex={0}
/>

## Conditional rendering

As we've seen above, interpolating booleans doesn't really have any effect. Instead, what we typically do instead of interpolating booleans _directly_, is that we use them to <Term term="conditional rendering">conditionally render</Term> something else.

There are two kinds of _conditionals_ in JavaScript:

- The _statement_ conditional, for example:

  ```tsx
  if (happy) {
    console.log("Clap your hands!");
  } else {
    console.log("Yell out your frustration!");
  }
  ```

- The _expression_ conditional, also called the **ternary operator**:

  ```tsx
  const what_to_do = happy ? "Clap your hands!" : "Yell out your frustration!";
  ```

When we want to interpolate some value in to JSX, we can only interpolate _expressions_, so that's what we're going to use. Edit the component definition to look like this:

```tsx
// src/components/Pokemon.js
export default function Pokemon() {
  return (
    <div>
      <h2>Pokemon name: {"Charizard"}</h2>
      <p>Weight: {90} kg</p>
      <p>Awesome: {true ? "YES!" : "nope, not really"}</p>
      <p>Terrifying: {false ? "Very" : "nah, lovable"}</p>
      <p>Abilities: {["Blaze", "Solar power", "Tough claws", "Drought"]}</p>
    </div>
  );
}
```

Check your browser, does this have the expected effect?

Only once you've solved the exercise on your own, compare your solution with [our solution](https://github.com/Codaisseur/react-week-awesomeapp/commit/5b6f0daaee8334394804a3ba3a37ed8eb8db2f9c).

## Generalizing the Pokemon component

So far, we used the Pokemon component as a little test-ground for interpolation, but now let's make it actually useful, that is, reusable. A reusable component knows what it should _look like_, but doesn't contain its data. Instead, it expects to be passed the data as _props_. This way, each <Term>component instance</Term> can have different data. Edit the component definition to look like this:

```tsx
// src/components/Pokemon.js
export default function Pokemon(props) {
  return (
    <div>
      <h2>Pokemon name: {props.name}</h2>
      <p>Weight: {props.weight} kg</p>
      <p>Awesome: {props.awesome ? "YES!" : "nope, not really"}</p>
      <p>Terrifying: {props.terrifying ? "Very" : "nah, lovable"}</p>
      <p>Abilities: {props.abilities}</p>
    </div>
  );
}
```

#### ✍️ Exercise

Edit the App component to include _four_ Pokemon component instances with the following data. Hint: you'll have to pass down the necessary _props_.

| Name              | Weight | Awesome? | Terrifying? | Abilities                                |
| ----------------- | ------ | -------- | ----------- | ---------------------------------------- |
| **Charizard**     | 90 kg  | yes      | no          | Blaze, Solar power, Tough claws, Drought |
| **Bulbasaur**     | 6.9 kg | yes      | no          | Overgrow, Chlorophyll                    |
| **Mewtwo**        | 122 kg | yes      | yes         | Pressure, Unnerve, Steadfast, Insomnia   |
| **Mega beedrill** | 65 kg  | no       | yes         | Intimidate, Unnerve                      |

Only once you've solved the exercise on your own, compare your solution with [our solution](https://github.com/Codaisseur/react-week-awesomeapp/commit/893ed2e4d7ceaa26a7ada956422bada45a0c8400).
