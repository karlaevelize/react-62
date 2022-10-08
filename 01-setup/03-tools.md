---
title: Setup tools
---

# Tools

<iframe width="640" height="400" src="https://www.youtube.com/embed/XH-49Xcj7iI" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## React DevTools

Install the <Term>React DevTools</Term> for [Chrome](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi) or [Firefox](https://addons.mozilla.org/en-US/firefox/addon/react-devtools/). This is a must-have for developing React apps, just as Chrome's (or Firefox's) DevTools is a must-have to developing any web-app. It'll appear as a new tab in the developer tools. Do take some time to play around with it, you'll be using it a lot!

Here's where you can find it and what it will look like for you:

![](https://p95.tr4.n0.cdn.getcloudapp.com/items/jkunlp0k/Screenshot+2019-12-16+at+18.37.50.png?v=876f57cad7f2ec4e092419a4a337a41c)

## Linters and Prettier

When working on code, especially in larger teams, it is incredibly useful to style your code well and consistently. This starts with correct indentation, but also applies to naming of variables, and more.

There are a variety of ways to deal with this, such as styleguides and linters. Below we will guide you through installing **Prettier** and **eslint**. These are similar tools that do similar jobs, but both are useful and can be used in unison to help you while writing code.

You can read this [very brief comparison of prettier vs linters](https://prettier.io/docs/en/comparison.html) to get a better understanding of what they both do.

You can also configure these tools on a per-project basis, so that you can make sure that they behave in the same way regardless of who is interacting with the tools and how their editor is setup. If you ever want to setup a project to leverage both these tools you can read up how to do so on [official documentation on how to setup both together](https://prettier.io/docs/en/integrating-with-linters.html).

### Prettier

An upcoming and popular technique to help with styling issues is to use automated tools like [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) to indent your code _for you_, every time you save your code. This can feel a bit awkward at first, because Prettier is very opiniated, and you might not feel comfortable with your code being rearranged. But if you get a hang of it, it can be a useful tool. If this seems interesting to you, you can get started like this:

1.  Find the "Prettier - Code formatter" plugin in VS Code by searching for it in the "Extensions" sidebar tab, then install it

    ![](https://p-928eb7.f4.n0.cdn.getcloudapp.com/items/rRu7WGJ8/Screenshot%202020-08-24%20at%2016.30.59.png?source=viewer&v=ae8588a32f2a3c948c9facb264a95aef)

2.  Open the command palette in VS Code (Mac: <kbd>Cmd</kbd>-<kbd>Shift</kbd>-<kbd>P</kbd>, Linux: <kbd>Ctrl</kbd>-<kbd>Shift</kbd>-<kbd>P</kbd>), and search for "Settings (UI)":

    ![](https://p-928eb7.f4.n0.cdn.getcloudapp.com/items/o0u876jv/Screenshot%202020-08-24%20at%2016.31.58.png?source=viewer&v=071422e33b51f82b9396d798fc98160b)

3.  Find the "Format on Save" setting and check it:

    ![](https://p-928eb7.f4.n0.cdn.getcloudapp.com/items/RBuOEYPn/Screenshot%202020-08-24%20at%2016.32.39.png?source=viewer&v=ca3ca1cf743b00595c7bc4c9d0cca974)

4.  Set the "Default Formatter" to `esbenp.prettier-vscode`, if that isn't already automatically applied.

    ![](https://p-928eb7.f4.n0.cdn.getcloudapp.com/items/WnuJkYAv/Screenshot%202020-08-24%20at%2016.33.25.png?source=viewer&v=306f5fad143fa11469b9aa196fe86240)

5.  Make sure that the "require config" option is disabled. (Usually it is disabled by default, but sometimes it isn't).

    ![](https://p78.f0.n0.cdn.getcloudapp.com/items/2NuEv1Jj/c3d5cb09-7f10-4bd8-a91e-f22d453078c6.png?source=viewer&v=e075677b00da486a9c6be75a7263bcf8)

### ESLint

Linters, like [ESLint](https://eslint.org/), not only help you maintain a consistent style but will also help you spot simple errors directly in the IDE before shipping your code or even trying to run it.

To install the "ESLint" plugin in VS Code, just find the "ESLint" plugin in VS Code by searching for it in the "Extensions" sidebar tab.

![](https://p78.f0.n0.cdn.getcloudapp.com/items/4guJr4NR/Image%202020-10-23%20at%203.06.34%20PM.png?v=bbd5550b0e16f0b3e2bdc3d6eac0642c)

ESLint should now just work out of the box, highlighting basic errors and warnings in your IDE. You can hover over a squiggly red or yellow line to view a tooltip, or you can see an overview of all errors and warnings in the "Problems" tab.

![](https://p78.f0.n0.cdn.getcloudapp.com/items/nOunXXAw/Screenshot%202020-10-23%20at%2014.05.41.png?v=08af28e989fe2d80e5c84b9ebdbe0d32)

**Advanced**: If you want to customise which errors eslint will check for, it is best to do that on a per-project basis (not globally or in your editor settings) by adding an [`.eslintconfig` file](https://eslint.org/docs/user-guide/configuring#using-configuration-files-1) to your project.

## React Snippets

Perhaps you're already using a lot of shortcuts that exist in vs-code. If you start to type `function` or `if` vs-code offers suggestions and shortcuts to help you with syntax.

You can get the same type of help for `React` syntax if you install:

[This vs-code integration](https://marketplace.visualstudio.com/items?itemName=dsznajder.es7-react-js-snippets)

#### 2 shortcuts to get you started

`clg` + <kbd>tab</kbd> -> autocompletes to:

A console log statement
`console.log(object)`

`rfc` + <kbd>tab</kbd> -> autocompletes to:

A React component (find out more about components in the next section)

```tsx-
export default function App() {
  return (
    <div>

    </div>
  )
}
```
