---
title: Get Started
description: Create your first React app
tags:
  - React
---

# Get Started


<iframe width="640" height="400" src="https://www.youtube.com/embed/uXjBGspnabw" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

To set up our initial project, we will use <Term>create-react-app</Term>. This is a command-line tool that makes it easier to setup a new React project, and we'll be using it a lot. You can check out their website [here](https://create-react-app.dev/docs/getting-started).

To get a React project set up, follow these steps.

1.  For your own organization, it's useful to put your projects together somewhere, where you'll be able to find them later.

    ```bash
    $ mkdir -p ~/codaisseur/week-2
    $ cd ~/codaisseur/week-2
    ```

2.  Use the `create-react-app` command with the `npx` helper that you'll have installed together with `npm`:

    ```bash
    $ npx create-react-app awesomeapp
    ```
    
    This might take a few minutes to run.

3.  The new project will be initialized in the new folder "awesomeapp". Let's `cd` into it, and then open up the project folder with VS code:

    ```bash
    $ cd awesomeapp
    $ code .
    ```

## It's a Git repository

You'll notice that the tool also set your new folder up to be a Git repository. If you run the command `git log`, you can see that the repository already has been initialized, and the current files have already been committed. Also, a `.gitignore` file has already been added for you.

## npm project dependencies

The project is set up and the dependencies are installed automatically by `create-react-app`. The dependencies are listed in our package descriptor file (`package.json`).

## Starting the dev server

We're going to be making a _front-end app_, which essentially means a bunch of HTML, CSS and JavaScript. But, React comes with some additional "infrastructure", in particular our JavaScript code will be <Term>transpiled</Term>. This way, we can use "modern" features of JavaScript, and at the same time support older browsers which don't have these features yet.

To ease the development workflow, `create-react-app` gives us a <Term>development server</Term>, which automatically does the transpiling and reloading and whatnot whenever we edit our source code files.

Let's start the development server:

```bash
npm run start

# Compiled successfully!
#
# You can now view awesomeapp in the browser.
#
#  Local:            http://localhost:3000/
#  On Your Network:  http://192.168.1.54:3000/
#
# Note that the development build is not optimized.
# To create a production build, use yarn run build.
```

This will start and open your development version of your React app.

> The `start` script is configured in the `scripts` section of the `package.json`
> file.

Now visit [http://localhost:3000](http://localhost:3000)

![](https://p95.tr4.n0.cdn.getcloudapp.com/items/E0uEbeJq/Screenshot+2019-12-16+at+18.27.52.png?v=4f955f0540e02475ff913ee06688306a)

Underwhelmed? Me too. But let's have a look at the code, because that is pretty cool.

> **A common error!** When working with JavaScript projects, the development mode commonly monitors our source files for changes. This way, when we edit our JavaScript files, our application reloads automatically. However, there is a limit imposed by the operating-system on how many files can be monitored. If you hit that limit you will see an error message containing the error-code `ENOSPC`. _If you do_ (not everyone will), come back to this page and click [this link](https://stackoverflow.com/questions/22475849/node-js-what-is-enospc-error-and-how-to-solve/32600959#32600959). It contains instructions on how to resolve the problem.
