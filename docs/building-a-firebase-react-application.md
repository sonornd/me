## Start from scratch and inizialize a blank project:

```
npm init -y
```

`-y` flag stands for yes for setting all properties to default

## Create A Minimal React Application

```
npm i react react-dom
```

To Make code more organized, we could create an `src` folder to hold `index.html` and `index.js`.

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <title>Building A Firebase React Application</title>
</head>
<body>
    <h1>Building A Firebase React Application</h1>
    <div id="root"></div>
</body>
</html>
```

```
import React from "react";
import ReactDOM from "react-dom";

const App = () => <div>This is an app created with React</div>;

ReactDOM.render(
    <App />,
    document.getElementById('root')
  );
```

## Set Up React App With Webpack, HTML Webpack Plugin And Babel

```
npm i --save-dev webpack webpack-cli webpack-dev-server html-webpack-plugin html-loader @babel/core babel-loader @babel/preset-env @babel/preset-react
```

Although starting Webpack 4, a config file is not mandatory any more, we need to customize our webpack.config.js as we have html loader and babel loader.

```
// webpack.config.js
const HtmlWebPackPlugin = require("html-webpack-plugin");

module.exports = {
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: {
          loader: "babel-loader",
          options: {
            presets: ["@babel/preset-env", "@babel/preset-react"]
          }
        },
      },
      {
        test: /\.html$/,
        use: [
          {
            loader: "html-loader"
          }
        ]
      }
    ]
  },
  plugins: [
    new HtmlWebPackPlugin({
      template: "./src/index.html",
      filename: "./index.html"
    })
  ]
};
```

`"@babel/preset-env"` compiles Javascript ES6 code down to ES5
`"@babel/preset-react"` compiles JSX and other stuff down to Javascript

And last `package.json` should specify the scripts we want to use to start our project.

```
"scripts": {
  "start": "webpack-dev-server --open --mode development",
  "build": "webpack --mode production"
},
```

So that we could start development with

```
npm start
```
