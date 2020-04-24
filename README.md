# Initializing the project

* Run `npm init -y`
* Run `npm i webpack webpack-cli --save-dev`
* Create file package.json
* Put the following code into package.json
```javascript
"scripts": {
  "build": "webpack --mode production"
}
```
* Run `npm i @babel/core babel-loader @babel/preset-env @babel/preset-react --save-dev`
* Create file .babelrc
* Put the following code into .babelrc
```javascript
{
  "presets": ["@babel/preset-env", "@babel/preset-react"]
}
```
* Create file webpack.config.js
* Put the following code into webpack.config.js
```javascript
module.exports = {
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: {
          loader: "babel-loader"
        }
      }
    ]
  }
};
```
* Run `npm i react react-dom`
* Run `npm run build`
* Run `npm i html-webpack-plugin html-loader --save-dev`
* Update the contents of webpack.config.js
```javascript
const HtmlWebPackPlugin = require("html-webpack-plugin");

module.exports = {
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: {
          loader: "babel-loader"
        }
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
* Run `npm run build`
* Open up /dist/index.html
