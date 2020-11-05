# ES6 Boilerplate

Essential starting package to work with es6 modules using webpack and babel.


## Starting from scratch

These are the steps for those who want to have this same boilerplate working without having to download the project.

### Installing dependencies

The command below will install the packages that are needed to generate your project bundle.
```
npm i webpack webpack-cli webpack-dev-server -D
```

The command below is optional, use if you need your project to work in old environments or browsers.
```
npm i babel-loader @babel/core @babel/preset-env -D
```

### Webpack config

Webpack needs a configuration file, so create a file at the root of your project called `webpack.config.js` and put the following code:
```js
const path = require('path');

module.exports = {
    mode: 'development',
    entry: './src/index.js',
    devtool: 'inline-source-map',
    output: {
        path: path.resolve(__dirname, 'dist'),
        filename: 'app.js'
    }
}
```

To run easily in a browser, add this extra configuration:
```js
devServer: {
    contentBase: path.join(__dirname, 'dist'),
    compress: true,
    port: 8000
}
```

To work in old environments or browsers add this extra configuration:
```js
module: {
    rules: [
        {
            test: /\.js$/,
            exclude: /node_modules/,
            use: {
                loader: 'babel-loader',
                options: {
                    presets: ['@babel/preset-env']
                }
            } 
        }
    ]
}
```

## Running

To create your project bundle, run in the terminal:
```
webpack
```

For webpack bundle your project automatically when any project file changes, run in the terminal:
```
webpack --watch
```

If it is a web project, the simplest way to run it is using `devServer`, run in the terminal:
```
webpack-dev-server --inline --hot --watch
```

It is possible to keep these commands saved to be executed easier, paste the code below in the file `package.json`.
```
"scripts": {
    "build": "webpack",
    "watch": "webpack --watch",
    "browser": "webpack-dev-server --inline --hot --watch"
}
```

To exemplify, to run the application in the browser using the devserver would be like this:
```
npm run browser
```