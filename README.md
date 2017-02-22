# React rails test

This is a playground project to experiment with the following tech stack:

* Rails 5.0
* ReactJS
* Webpack 2+ (via Rails' webpacker gem)
* Yarn - node module dependency management
* Jest
* es2015

## Links

* webpacker - https://github.com/rails/webpacker
* webpacker-react - https://github.com/renchap/webpacker-react

# Setup

1. Install all ruby gems

    `bundle install`

2. Install all node\_modules 

    `bin/yarn`

# Development

## Running the app

1. Start the rails server and webpack dev server

    `foreman start`

2. Navigate to: http://localhost:3000.  You should see a page rendered that has a few sample react components on it.

## Javascript
All application javascript is kept in `app/javascript`.  This is the default location as setup by the webpacker gem.

[Webpack entrypoints](https://webpack.js.org/concepts/entry-points/)
are defined in `app/javascript/packs`.  See `packs/application.js` for an example of how to define a 
react component for use in a view through the `<%= react_component 'mycomponent' %>` view helper.

React components are defined in `app/javascript/components`.

When you make changes to files managed by webpack, the webpack dev server will automatically reload the changed
components.  Neat!

## Adding node\_modules

Do you have a fancy node module that you'd like to reference in your application code?  It's easy to add it, like so:

`bin/yarn add lodash`

This will add the module and update the `vendor/package.json` file, so that others on your team will be able to easily
pick up the module.

Reference lodash in your JS code like so:

`import _ from "lodash"`;

And you can get at lodash functions by writing JS like:

`_.map([1,2], this.print)`

Notice that node modules live in the `vendor/node_modules` directory, rather than at the project root.  This is the 
standard set forth by the webpacker gem.  It differs from what you might see in a typical NodeJS project setup.

# Testing

Tests for react components are written in [Jest](https://facebook.github.io/jest/docs/tutorial-react.html).

Tests live in `spec/javascript`.

Run the tests by executing `bin/yarn test`.
