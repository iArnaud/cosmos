# Cosmos [![Build Status](https://travis-ci.org/skidding/cosmos.svg?branch=master)](https://travis-ci.org/skidding/cosmos) [![Coverage Status](https://coveralls.io/repos/skidding/cosmos/badge.svg?branch=master)](https://coveralls.io/r/skidding/cosmos?branch=master)

Cosmos is a [React](http://facebook.github.io/react/) development utility built
on top of:

1. [ComponentTree](https://github.com/skidding/react-component-tree) —
Serialize and reproduce the state of an entire tree of React components
2. [ComponentPlayground](https://github.com/skidding/react-component-playground)
— Minimal frame for loading and testing React components in isolation

> Working with ComponentPlayground improves the component design because it
surfaces any implicit dependencies. It also forces you to define sane inputs
for every component, making them more predictable and easier to debug down the
road.

There's no such thing as *controllers* or *pages* when working with Cosmos,
just *components.* The UI is a tree of components consisting of a root
component and its descendants. Moreover, any component can be loaded
full-screen as the root element.

![Component Playground](https://cloud.githubusercontent.com/assets/250750/7422140/0670e9f4-ef93-11e4-9647-7757793a1da5.png)

### Requirements

- [x] You should already be using CommonJS modules to structure your code and
[webpack](http://webpack.github.io/) to bundle your modules for the browser
- [x] Your React components should be fully encapsulated. They should have no
global dependencies and rely exclusively on _props_ for input. Including styles,
which means you need to be using
[style-loader](https://github.com/webpack/style-loader).
- [x] You must create component fixtures for ComponentPlayground to load. The
component and fixture files should be nested as in the folder structure below.
See the [example repo](https://github.com/skidding/cosmos-example) for a better
picture.

### Installing

- Install the Cosmos package through npm `npm install cosmos-js`
- Run the ComponentPlayground executable `node_modules/.bin/component-playground`
- Open [localhost:8989](http://localhost:8989)

### Under the hood

Running the ComponentPlayground executable will:

1. Start a [webpack dev server](http://webpack.github.io/docs/webpack-dev-server.html),
serving an instance of ComponentPlayground at `localhost:8989`
2. Scan the current folder for components and fixtures and feed them to
ComponentPlayground

The webpack build bundles modules from both the current folder and the Cosmos
package. It is currently compatible with React classes, ES6 classes, JSX and
CSS/LESS modules. In the future the [webpack config](component-playground/webpack.config.js)
should be configurable.

This is the file structure Cosmos expects:
```
|
+-- components
|   +-- FooComponent.jsx
|   +-- namespace
|   |   +-- BarComponent.jsx
+-- fixtures
|   +-- FooComponent
|   |   +-- default.js
|   |   +-- active.js
|   +-- namespace
|   |   +-- BarComponent
|   |       +-- default.js
|   |       +-- paused.js
```

If the _components_ and _fixtures_ folders are not siblings, their paths can be
specified via cli args:

```bash
node_modules/.bin/component-playground --components-path src/components --fixtures-path tests/fixtures
```

Finally, Cosmos includes [React Hot Loader](http://gaearon.github.io/react-hot-loader/) and has webpack's [hot module replacement](http://webpack.github.io/docs/hot-module-replacement.html) enabled so you can tweak the components and their styles without refreshing the browser:

![React Hot Loader in Cosmos](https://cloud.githubusercontent.com/assets/250750/7526576/5c725b16-f51b-11e4-95ef-312c6fd7bcc7.gif)

### Thank you for your interest!

[![Join the chat at https://gitter.im/skidding/cosmos](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/skidding/cosmos?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

Explore the [wiki](https://github.com/skidding/cosmos/wiki) for more info on
the Cosmos project.
