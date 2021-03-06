:warning: This is the client-side app for a two part NodeJS application
> [Voting-server-screencast][votingServerLink]

# TUTORIAL NOTES

> View the [screencast][screencastLink] for this tutorial.
> Visit my web development blog [web development blog][bloglink].

# 22/Nov/2016

  - Create react app tool

    Create React App is a new officially supported way to create single-page React applications. It offers a modern build setup with no configuration.

    Create React App uses both Webpack and Babel under the hood.
    
    The console output is tuned to be minimal to help you focus on the problems.

    ESLint is also integrated so lint warnings are displayed right in the console.

    > ref: https://facebook.github.io/react/blog/2016/07/22/create-apps-with-no-configuration.html

    > ref: https://github.com/facebookincubator/create-react-app#getting-started


  - Webpack

    Concepts
    Webpack is a module bundler for modern JavaScript applications. It is incredibly configurable, however, there are Four Core Concepts we feel you should understand before you get started!

    Entry
    Webpack creates a graph of all of your application's dependencies. The starting point of this graph is known as an entry point. The entry point tells webpack where to start and follows the graph of dependencies to know what to bundle. You can think of your application's entry point as the contextual root or the first file to kick off your app.

    In webpack we define entry points using the entry property in our webpack configuration object.

    module.exports = {
      entry: [
        'webpack-dev-server/client?http://localhost:8080',
        'webpack/hot/only-dev-server',
        './src/index.js'
      ],

    Output
    Once you've bundled all of your assets together, we still need to tell webpack where to bundle our application. The webpack output property describes to webpack how to treat bundled code.

    output: {
      path: __dirname + '/dist',
      publicPath: '/',
      filename: 'bundle.js'
    },

    In the example above, through the output.filename and output.path properties we are describing to webpack the name of our bundle, and where we want it to be emitted to.

    Loaders
    The goal is to have all of the assets in your project to be webpack's concern and not the browser's. (This doesn't mean that they all have to be bundled together). webpack treats every file (.css, .html, .scss, .jpg, etc.) as a module. However, webpack only understands JavaScript.

    Loaders in webpack transform these files into modules as they are added to your dependency graph.

    At a high level, they have two purposes in your webpack config.

    1. Identify what files should be transformed by a certain loader. (test property)
    
    2. Transform that file so that it can be added to your dependency graph (and eventually your bundle). (use property)

    Plugins
    Since Loaders only execute transforms on a per-file basis, plugins are most commonly used (but not limited to) performing actions and custom functionality on "compilations" or "chunks" of your bundled modules (and so much more). The webpack Plugin system is extremely powerful and customizable.

    In order to use a plugin, you just need to require() it and add it to the plugins array. Most plugins are customizable via options. Since you can use a plugin multiple times in a config for different purposes, you need to create an instance of it by calling it with new.

    var webpack = require('webpack');
    ...
    plugins: [
     new webpack.HotModuleReplacementPlugin()
    ]

    > ref: http://webpack.github.io/
    > ref: https://webpack.js.org/concepts/


  - NPM install packages globally?

    There are two ways to install npm packages: locally or globally. You choose which kind of installation to use based on how you want to use the package.

    If you want to use it as a command line tool, something like the grunt CLI, then you want to install it globally. On the other hand, if you want to depend on the package from your own module using something like Node's require, then you want to install locally.

    > ref: http://devdocs.io/npm/getting-started/installing-npm-packages-globally


  - JSX syntax

    JSX is a XML-like syntax extension to ECMAScript without any defined semantics. It's NOT intended to be implemented by engines or browsers. It's NOT a proposal to incorporate JSX into the ECMAScript spec itself. It's intended to be used by various preprocessors (transpilers) to transform these tokens into standard ECMAScript.

    This specification does not attempt to comply with any XML or HTML specification. JSX is designed as an ECMAScript feature and the similarity to XML is only for familiarity.

    > ref: https://facebook.github.io/jsx/


  - Babel

    Babel has support for the latest version of JavaScript through syntax transformers. These plugins allow you to use new syntax, right now without waiting for browser support. Check out our Latest preset to get started.

    > ref: https://babeljs.io/


# 24/Nov/2016

  - npm install --save-dev

    Installs a package.
    -D, --save-dev: Package will appear in your devDependencies.

    > ref: http://devdocs.io/npm/cli/install


  - Testing react on Jsdom

    React allows you to create components that will render UI for your application. If your UI is of any complexity, you’ll likely want to test that it functions correctly and allows for future refactors. There are numerous ways to do this. One way that you might appreciate is using jsdom, an in-JavaScript implementation of the DOM.

    What is jsdom?

    Jsdom is an in-JavaScript implementation of the DOM. The DOM is the document object model, which is the tree of nodes that make up the UI for documents shown in web browsers.

    Because jsdom is implemented in JavaScript, we can have a DOM-like API to work with without needing a browser. That means that we don’t have to capture a browser in order test, a la Karma. That means that we can run our tests in environments without browsers, like in Node or in continuous integration environments.

    By not using real browsers, we’re also essentially saying that we believe the problems in our client JavaScript will not be browser-dependent (again, because we’re not capturing real browsers).

    > ref: http://jaketrent.com/post/testing-react-with-jsdom/
    > ref: https://github.com/tmpvar/jsdom


  - Karma

    The main goal for Karma is to bring a productive testing environment to developers. The environment being one where they don't have to set up loads of configurations, but rather a place where developers can just write the code and get instant feedback from their tests. Because getting quick feedback is what makes you productive and creative.

    > ref: http://karma-runner.github.io/0.13/index.html
    
    Karma is essentially a tool which spawns a web server that executes source code against test code for each of the browsers connected. The results for each test against each browser are examined and displayed via the command line to the developer such that they can see which browsers and tests passed or failed.
    A browser can be captured either
    manually, by visiting the URL where the Karma server is listening (typically http://localhost:9876/),
    or automatically by letting Karma know which browsers to start when Karma is run (see browsers).

    > ref: http://karma-runner.github.io/0.13/intro/how-it-works.html


  - Global object
    
    global#

    Added in: v0.1.27
    <Object> The global namespace object.
    In browsers, the top-level scope is the global scope. That means that in browsers if you're in the global scope var something will define a global variable. In Node.js this is different. The top-level scope is not the global scope; var something inside an Node.js module will be local to that module.

    > ref: https://nodejs.org/api/globals.html#globals_global


  - glob

    Glob Primer

    "Globs" are the patterns you type when you do stuff like ls *.js on the command line, or put build/* in a .gitignore file.

    Before parsing the path part patterns, braced sections are expanded into a set. Braced sections start with { and end with }, with any number of comma-delimited sections within. Braced sections may contain slash characters, so a{/b/c,bcd} would expand into a/b/c and abcd.
    
    > ref: https://github.com/isaacs/node-glob

  - npm run test -- --watch

    Run arbitrary package scripts.

    npm run-script <command> [-- <args>... ]
    alias: npm run

    Description

    This runs an arbitrary command from a package's "scripts" object. If no "command" is provided, it will list the available scripts. run[-script] is used by the test, start, restart, and stop commands, but can be called directly, as well. When the scripts in the package are printed out, they're separated into lifecycle (test, start, restart) and directly-run scripts.

    As of npm@2.0.0, you can use custom arguments when executing scripts. The special option -- is used by getopt to delimit the end of the options. npm will pass all the arguments after the -- directly to your script:

    npm run test -- --grep="pattern"
    The arguments will only be passed to the script specified after npm run and not to any pre or post script.

    The env script is a special built-in command that can be used to list environment variables that will be available to the script at runtime. If an "env" command is defined in your package it will take precedence over the built-in.

    In addition to the shell's pre-existing PATH, npm run adds node_modules/.bin to the PATH provided to scripts. Any binaries provided by locally-installed dependencies can be used without the node_modules/.bin prefix. For example, if there is a devDependency on tap in your package, you should write:

    "scripts": {"test": "tap test/\*.js"}
    instead of "scripts": {"test": "node_modules/.bin/tap test/\*.js"} to run your tests.

    If you try to run a script without having a node_modules directory and it fails, you will be given a warning to run npm install, just in case you've forgotten.

    > ref: http://devdocs.io/npm/cli/run-script

    Test a package.

      npm test [-- <args>]
      npm tst [-- <args>]

    This runs a package's "test" script, if one was provided.

    To run tests as a condition of installation, set the npat config to true.

    > ref: http://devdocs.io/npm/cli/test


  - "Pure components"

    1. A pure component receives all its data as props, like a function receives all its data as arguments. It should have no side effects, including reading data from anywhere else, initiating network requests, etc.

    2. A pure component generally has no internal state. What it renders is fully driven by its input props. Rendering the same pure component twice with the same props should result in the same UI. There's no hidden state inside the component that would cause the UI to differ between the two renders.

    > ref: https://www.youtube.com/watch?v=1uRC3hmKQnM&feature=youtu.be&t=13m10s

  - What is react-hot-loader?

    Introduction

    Hot Module Replacement (HMR) exchanges, adds, or removes modules while an application is running without a page reload.

    How does it work?

    Webpacks adds a small HMR runtime to the bundle, during the build process, that runs inside your app. When the build completes, Webpack does not exit but stays active, watching the source files for changes. If Webpack detects a source file change, it rebuilds only the changed module(s). Depending on the settings, Webpack will either send a signal to the HMR runtime, or the HMR runtime will poll webpack for changes. Either way, the changed module is sent to the HMR runtime which then tries to apply the hot update. First it checks whether the updated module can self-accept. If not, it checks those modules that have required the updated module. If these too do not accept the update, it bubbles up another level, to the modules that required the modules that required the changed module. This bubbling-up will continue until either the update is accepted, or the app entry point is reached, in which case the hot update fails.

    > ref: https://www.youtube.com/watch?v=1uRC3hmKQnM&feature=youtu.be&t=13m10s
    > ref: https://www.youtube.com/watch?v=xsSnOQynTHs


  - react-hot vs react-hot-loader/webpack

    $ webpack-dev-server
    
    ERROR MESSAGE:

    ERROR in ./src/index.js
    
    Module build failed: Error: React Hot Loader: The Webpack loader is now exported separately. If you use Babel, we recommend that you remove "react-hot-loader" from the "loaders" section of your Webpack configuration altogether, and instead add "react-hot-loader/babel" to the "plugins" section of your .babelrc file. If you prefer not to use Babel, replace "react-hot-loader" or "react-hot" with "react-hot-loader/webpack" in the "loaders" section of your Webpack configuration.
    at Object.warnAboutIncorrectUsage (/home/daniel/github/voting-client-screencast/node_modules/react-hot-loader/lib/index.js:7:11)
    @ multi main
    webpack: bundle is now VALID.

    > ref: https://teamtreehouse.com/community/anyone-else-getting-an-error-when-including-react-hot-loader-in-the-webpack-config
    > ref: https://github.com/maxfarseer/redux-ru-tutorial/issues/2


# 25/Nov/2016

  - Feedback loop
    
    What is a feedback loop?

    A feedback loop is the path your assumptions travel before they are validated or invalidated. Naturally you will have different feedback loops for different assumptions. In this post we will discuss three levels of feedback loops that should be easily recognizable. They are:

    The unit test loop
    Your assumption is that the code you have written does work. A fast way to validate this is to have a harness of units test that can give you this feedback fast.

    The functional test loop
    The functional test loop helps you verify that the implemented solution fulfils the tasks acceptance criteria. This is traditionally done by testers working their way through test scripts, but as the tools are getting better there are ways to automate this as well.

    The from idea to validated learning loop
    This is the loop surrounding the whole of your product/project. If you have validated that your solution works as intended, the only thing you need to worry about is that the intention solves a problem worth solving. This loop is addressed in the Lean Startup methodology.

    > ref: https://blog.iterate.no/2012/10/01/know-your-feedback-loop-why-and-how-to-optimize-it/


  - JSX Syntax highlighting
    Install Babel package in Sublime Text 3 (not supported by ST2)

    > ref: https://github.com/babel/babel-sublime


  - JSX Linter - DEPRECATED!

    Use:

      ESLint

      ESLint is an open source project originally created by Nicholas C. Zakas in June 2013. Its goal is to provide a pluggable linting utility for JavaScript.

      > ref: http://eslint.org/

      
      SublimeLinter-eslint

      This linter plugin for SublimeLinter provides an interface to ESLint. It will be used with files that have the “javascript” syntax.

      **REQUIRES SUBLIMELINTER**

      https://github.com/roadhump/SublimeLinter-eslint


      SublimeLinter

      SublimeLinter itself is only a framework for linters. The linters are distributed as independent Sublime Text 3 plugins.

      SublimeLinter (and the linter plugins) can be installed via a plugin called Package Control or from source. I strongly recommend that you use Package Control! Not only does it ease installation, but more importantly it automatically updates the plugins it installs, which ensures you will get the latest features and bug fixes.

      http://sublimelinter.readthedocs.io/en/latest/installation.html


  - renderIntoDocument
    > ref: https://facebook.github.io/react/docs/test-utils.html#renderintodocument

    renderIntoDocument()
    renderIntoDocument(element)
    
    Render a React element into a detached DOM node in the document. This function requires a DOM.

    Note:
    You will need to have window, window.document and window.document.createElement globally available before you import React. Otherwise React will think it can't access the DOM and methods like setState won't work.


  - scry...
    > ref: https://facebook.github.io/react/docs/test-utils.html#scryrendereddomcomponentswithtag

    scryRenderedDOMComponentsWithTag()
    scryRenderedDOMComponentsWithTag(
      tree,
      tagName
    )
    
    Finds all DOM elements of components in the rendered tree that are DOM components with the tag name matching tagName.

  - simulate

    Simulate
    Simulate.{eventName}(
      element,
      [eventData]
    )

    Simulate an event dispatch on a DOM node with optional eventData event data.

    Simulate has a method for every event that React understands.

    > ref: https://facebook.github.io/react/docs/test-utils.html#simulate

  - ...this.props

    Unsure... wait until we see it in action.

    Pass this component's props into a component being called into this one.

    > ref: http://devdocs.io/react/react-component#props

  - ref

    The ref Callback Attribute
    
    React supports a special attribute that you can attach to any component. The ref attribute takes a callback function, and the callback will be executed immediately after the component is mounted or unmounted.

    > ref: https://facebook.github.io/react/docs/refs-and-the-dom.html

# 6/Dec/2016

  - Autoprefixer-loader

    An autoprefixer loader for webpack.

    :warning: This module is deprecated. Autoprefixer official page recommends using postcss-loader instead.

    > ref: https://github.com/passy/autoprefixer-loader


  - Auto-prefixer

    PostCSS plugin to parse CSS and add vendor prefixes to CSS rules using values from Can I Use. It is recommended by Google and used in Twitter, and Taobao.

    Autoprefixer will use the data based on current browser popularity and property support to apply prefixes for you.

    > ref: https://github.com/postcss/autoprefixer


  - PostCSS-loader

    PostCSS loader for webpack to postprocesses your CSS with PostCSS plugins.

    > ref: https://github.com/postcss/postcss-loader


  - PostCSS

    PostCSS is a tool for transforming styles with JS plugins. These plugins can lint your CSS, support variables and mixins, transpile future CSS syntax, inline images, and more.

    > ref: https://github.com/postcss/postcss


  - Style-Loader

    > ref: https://github.com/webpack/style-loader


  - fsevents warning

    MESSAGE IN TERMINAL:

    daniel@slayer ~/github/voting-client-screencast $ npm install -save classnames
    voting-client-screencast@1.0.0 /home/daniel/github/voting-client-screencast
    └── classnames@2.2.5 

    npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@^1.0.0 (node_modules/webpack/node_modules/watchpack/node_modules/chokidar/node_modules/fsevents):
    npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.0.15: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})
    npm WARN voting-client-screencast@1.0.0 No description
    npm WARN voting-client-screencast@1.0.0 No repository field.

    > ref: http://stackoverflow.com/questions/35644708/what-does-npm-mean-by-skipping-failed-optional-dependency

    Explanation:
      This is not an error. It is a warning that fseventsd, which is Mac OS specific, cannot be installed on Linux.

      There is no need to be alarmed, and the package that needs fsevents will still work - that's why it's an optional dependency.

      Since many people are confused about this (particularly since this used to be a real error, not a warning) there's an open bug to make the current warning into an INFO instead


  - fsevents

    Native Access to Mac OS-X FSEvents
    
    The FSEvents API in OS X allows applications to register for notifications of changes to a given directory tree. It is a very fast and lightweight alternative to kqueue.

    This is a low-level library. For a cross-compatible file watching module that uses fsevents, check out Chokidar.


# 7/Dec/2016

  - React-router

    React Router is a complete routing library for React.

    React Router keeps your UI in sync with the URL. It has a simple API with powerful features like lazy code loading, dynamic route matching, and location transition handling built right in. Make the URL your first thought, not an after-thought.

    > ref: https://github.com/ReactTraining/react-router


  - React-router tutorial

    Quick lessons for getting up-to-speed with React Router.

    See Lesson 1 - Setting Up to get started.

    Each lesson is a fully runnable app with all code from the previous lesson, so you can cd lessons/<lesson-folder>, npm install, and then run the appropriate NPM scripts for each lesson from within the lesson folder.

    > ref: https://github.com/ReactTraining/react-router


  - React.cloneElement()

    cloneElement()
    
    React.cloneElement(
      element,
      [props],
      [...children]
    )
    Clone and return a new React element using element as the starting point. The resulting element will have the original element's props with the new props merged in shallowly. New children will replace existing children. key and ref from the original element will be preserved.

    React.cloneElement() is almost equivalent to:

    <element.type {...element.props} {...props}>{children}</element.type>
    However, it also preserves refs. This means that if you get a child with a ref on it, you won't accidentally steal it from your ancestor. You will get the same ref attached to your new element.

    This API was introduced as a replacement of the deprecated React.addons.cloneWithProps().

    > ref: https://facebook.github.io/react/docs/react-api.html#cloneelement


  - Chai assertions

    expect().to.contain

    .include(value)

    @param { Object | String | Number } obj
    @param { String } message _optional_
    The include and contain assertions can be used as either property based language chains or as methods to assert the inclusion of an object in an array or a substring in a string. When used as language chains, they toggle the contains flag for the keys assertion.

    expect([1,2,3]).to.include(2);
    expect('foobar').to.contain('foo');
    expect({ foo: 'bar', hello: 'universe' }).to.include.keys('foo');

    > ref: http://devdocs.io/chai/api/bdd/index#method_equal


  - expect().to.be.ok

    .ok

    Asserts that the target is truthy.

    expect('everything').to.be.ok;
    expect(1).to.be.ok;
    expect(false).to.not.be.ok;
    expect(undefined).to.not.be.ok;
    expect(null).to.not.be.ok;

    > ref: http://devdocs.io/chai/api/bdd/index#method_equal


# 8/Dec/2016

  - merge()

    Returns a new Map resulting from merging the provided Iterables (or JS objects) into this Map. In other words, this takes each entry of each iterable and sets it on this Map.

    > ref: https://facebook.github.io/immutable-js/docs/#/Map/merge


  - switch (action.type)

    The switch statement evaluates an expression, matching the expression's value to a case clause, and executes statements associated with that case.

    > ref: http://devdocs.io/javascript/statements/switch
  

  - createStore(reducer)

    createStore(reducer, [preloadedState], [enhancer])

    Creates a Redux store that holds the complete state tree of your app.

    *There should only be a single store in your app.*

    Arguments

    reducer (Function): A reducing function that returns the next state tree, given the current state tree and an action to handle.
    "[preloadedState]" (any): The initial state. You may optionally specify it to hydrate the state from the server in universal apps, or to restore a previously serialized user session. If you produced reducer with combineReducers, this must be a plain object with the same shape as the keys passed to it. Otherwise, you are free to pass anything that your reducer can understand.
    "[enhancer]" (Function): The store enhancer. You may optionally specify it to enhance the store with third-party capabilities such as middleware, time travel, persistence, etc. The only store enhancer that ships with Redux is applyMiddleware().
    Returns

    (Store): An object that holds the complete state of your app. The only way to change its state is by dispatching actions. You may also subscribe to the changes to its state to update the UI.

    > ref: http://devdocs.io/redux/api/createstore

  - React-redux

    Official React bindings for Redux.
    Performant and flexible.

    Installation

    React Redux requires React 0.14 or later.

    npm install --save react-redux
    This assumes that you’re using npm package manager with a module bundler like Webpack or Browserify to consume CommonJS modules.

    If you don’t yet use npm or a modern module bundler, and would rather prefer a single-file UMD build that makes ReactRedux available as a global object, you can grab a pre-built version from cdnjs. We don’t recommend this approach for any serious application, as most of the libraries complementary to Redux are only available on npm.

    > ref: https://github.com/reactjs/react-redux

  - connect(mapStateToProps)(SomeComponent)

    connect([mapStateToProps], [mapDispatchToProps], [mergeProps], [options])

    Connects a React component to a Redux store.

    It does not modify the component class passed to it.
    Instead, it returns a new, connected component class, for you to use.

    Arguments

    "[mapStateToProps(state, [ownProps]): stateProps]" (Function): If specified, the component will subscribe to Redux store updates. Any time it updates, mapStateToProps will be called. Its result must be a plain object*, and it will be merged into the component’s props. If you omit it, the component will not be subscribed to the Redux store. If ownProps is specified as a second argument, its value will be the props passed to your component, and mapStateToProps will be additionally re-invoked whenever the component receives new props (e.g. if props received from a parent component have shallowly changed, and you use the ownProps argument, mapStateToProps is re-evaluated).

    > ref: https://github.com/reactjs/react-redux/blob/master/docs/api.md#api


# 9/Dec/2016

  - socket.io-client

    Realtime application framework (client) http://socket.io

    How to use

    A standalone build of socket.io-client is exposed automatically by the socket.io server as /socket.io/socket.io.js. Alternatively you can serve the file socket.io.js or socket.io.min.js found in the dist folder.

    > ref: https://github.com/socketio/socket.io-client


  - Path module fix for webpack.config.js

    Webpack is an amazing tool. It calls itself a "module bundler" but it is much more than that: it provides an infrastructure for building, transforming, and live updating modules. While its wall of configuration options may not be your style, this approach works really well for the problem it's solving.

    The target: 'node' option tells webpack not to touch any built-in modules like fs or path.

    But there is a problem. Webpack will load modules from the node_modules folder and bundle them in.

    > ref: http://jlongster.com/Backend-Apps-with-Webpack--Part-I#Getting-Started


  - path.join(__dirname, 'build')

    The path module provides utilities for working with file and directory paths. It can be accessed using:

    const path = require('path');

    ...

    path.join([...paths])#

    ...paths <String> A sequence of path segments
    Returns: <String>

    The path.join() method joins all given path segments together using the platform specific separator as a delimiter, then normalizes the resulting path.

    Zero-length path segments are ignored. If the joined path string is a zero-length string then '.' will be returned, representing the current working directory.

    > ref: https://nodejs.org/api/path.html

    > ref: https://nodejs.org/api/path.html#path_path_join_paths


# 13/Dec/2016

  - 'Action creators' in Redux

    Actions

    First, let's define some actions.

    Actions are payloads of information that send data from your application to your store. They are the only source of information for the store. You send them to the store using store.dispatch().

    Here's an example action which represents adding a new todo item:

    const ADD_TODO = 'ADD_TODO'

    ...
    
    {
      type: ADD_TODO,
      text: 'Build my first Redux app'
    }

    Actions are plain JavaScript objects. Actions must have a type property that indicates the type of action being performed. Types should typically be defined as string constants. Once your app is large enough, you may want to move them into a separate module.

    import { ADD_TODO, REMOVE_TODO } from '../actionTypes'


    Action Creators

    Action creators are exactly that—functions that create actions. It's easy to conflate the terms “action” and “action creator,” so do your best to use the proper term.

    In Redux action creators simply return an action:

    function addTodo(text) {
      return {
        type: ADD_TODO,
        text
      }
    }

    This makes them portable and easy to test.

    In traditional Flux, action creators often trigger a dispatch when invoked, like so:

    function addTodoWithDispatch(text) {
      const action = {
        type: ADD_TODO,
        text
      }
      dispatch(action)
    }
    In Redux this is not the case.

    Instead, to actually initiate a dispatch, pass the result to the dispatch() function:

    dispatch(addTodo(text))
    dispatch(completeTodo(index))

    FOR FURTHER READING:
      http://redux.js.org/docs/recipes/ReducingBoilerplate.html

    > ref: http://redux.js.org/docs/basics/Actions.html
    > ref: http://redux.js.org/docs/basics/Actions.html#action-creators


    redux-action-creator
    Reduce boilerplate code in your action creators and types

    > ref: https://www.npmjs.com/package/redux-action-creator


# 15/Dec/2016

  - Redux middleware

    Redux middleware solves different problems than Express or Koa middleware, but in a conceptually similar way. It provides a third-party extension point between dispatching an action, and the moment it reaches the reducer. People use Redux middleware for logging, crash reporting, talking to an asynchronous API, routing, and more.

    > ref: http://redux.js.org/docs/advanced/Middleware.html
    
    Blog article to read:
    > ref: https://medium.com/@meagle/understanding-87566abcfb7a#.87dpjbgoz
    
    Instructions.
    > ref: https://www.codementor.io/reactjs/tutorial/beginner-s-guide-to-redux-middleware

  - Arrow functions

    Arrow functions – also called “fat arrow” functions, from CoffeeScript (a transcompiled language) are a more concise syntax for writing function expressions. They utilize a new token, =>, that looks like a fat arrow. Arrow functions are anonymous and change the way this binds in functions.

    Arrow functions make our code more concise, and simplify function scoping and the this keyword. They are one-line mini functions which work much like Lambdas in other languages like C# or Python. (See also lambdas in JavaScript). By using arrow function we avoid having to type the function keyword, return keyword (it’s implicit in arrow functions), and curly brackets.

    > ref: https://www.sitepoint.com/es6-arrow-functions-new-fat-concise-syntax-javascript/

  - Currying

    In mathematics and computer science, currying is the technique of translating the evaluation of a function that takes multiple arguments (or a tuple of arguments) into evaluating a sequence of functions, each with a single argument. Currying is related to, but not the same as, partial application.

    > ref: https://en.wikipedia.org/wiki/Currying

  - applyMiddleware

    Middleware is the suggested way to extend Redux with custom functionality. Middleware lets you wrap the store's dispatch method for fun and profit. The key feature of middleware is that it is composable. Multiple middleware can be combined together, where each middleware requires no knowledge of what comes before or after it in the chain.

    > ref: http://devdocs.io/redux/api/applymiddleware

# 22/Dec/2016

  - Fix React.propTypes error in console while client app is running in browser:

    > React router version 2.5.2 or greater is required to fix this bug.
    > ref: https://github.com/ReactTraining/react-router/issues/3695

    Go into package.json and replace the react-router version number with an asterisk and run 'npm update --save' in the terminal.  This will automatically update the package to the latest version.  Run the app in the client again and the error should be cleared.


# About Daniel :godmode:

I am a computer programmer and web developer from Scarborough, Ontario.  My interest is in the Rails framework and Node, and full-stack multi platform web development.


> Follow my [blog][bloglink] for updates on this tutorial and any upcoming tutorial videos.
> Visit my [LinkedIn][linkedinlink] profile.


<!-- Web Links -->

  [LearnyounodeLink]: <https://github.com/workshopper/learnyounode>
  [bloglink]: <https://medium.com/coding-and-web-development/learnyounode-92487f382e01#.4xabu4beh>
  [screencastLink]: <https://www.youtube.com/watch?v=SZ4-rHL0cl0&list=PLX-RIZuCBJBJLDb3ilr7GVTUWEY-7qDw7>
  [bloglink]: <https://medium.com/@pereirawebdev>
  [votingServerLink]: <https://github.com/pereiradaniel/voting-server-screencast>