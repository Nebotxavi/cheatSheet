# GIT

# NODE BASIC

# REACT
    mkdir EXAMPLE && cd EXAMPLE && mkdir src && mkdir public && touch src/index.js && touch src/App.js && touch public/index.html 

    npm init -y
    npm install nodemon --save-dev
    npm install --save-dev @babel/core @babel/preset-env
    npm install --save-dev babel-loader
    npm install --save-dev @babel/preset-react
    npm install --save-dev react-hot-loader
    npm install --save react react-dom

    touch .babelrc && touch webpack.config.js

    touch .gitignore

package.json

    {
  
    "name": "EXAMPLE",
      "version": "1.0.0",
      "description": "",
    "main": "index.js",
    "scripts": {
    "start": "webpack-dev-server --config ./webpack.config.js --mode development",
    "test": "echo \"Error: no test specified\" && exit 1"
    },
    "keywords": [],
  
    "author": "",
  
    "license": "ISC",
  
    "devDependencies": {
    "@babel/core": "^7.8.4",
    "@babel/preset-env": "^7.8.4",
    "@babel/preset-react": "^7.8.3",
    "babel-loader": "^8.0.6",
    "react-hot-loader": "^4.12.19",
    "webpack": "^4.41.6",
    "webpack-cli": "^3.3.11",
    "webpack-dev-server": "^3.10.3"
      },
    "dependencies": {
      "react": "^16.12.0",
      "react-dom": "^16.12.0"
      }
    }

webpack.config.js

    const webpack = require("webpack");

    module.exports = {
      entry: "./src/index.js",
      module: {
    rules: [
        {
          test: /\.(js|jsx)$/,
          exclude: /node_modules/,
          use: ["babel-loader"]
        }
      ]
    },
    resolve: {
      extensions: ["*", ".js", ".jsx"]
    },
    output: {
      path: __dirname + "/public",
      publicPath: "/",
      filename: "bundle.js"
    },
    plugins: [new webpack.HotModuleReplacementPlugin()],
    devServer: {
      contentBase: "./public",
      hot: true
      }
    };

.babelrc

    {
      "presets": ["@babel/preset-env", "@babel/preset-react"]
    }

index.html
    
    <!DOCTYPE html>
    <html>
       <head>
          <title>Hello React</title>
       </head>
       <body>
         <div id="app"></div>
         <script src="./bundle.js"></script>
      </body>
    </html>

index.js

    import React from "react";
    import ReactDOM from "react-dom";

    import App from "./App";

    ReactDOM.render(<App />, document.getElementById("app"));

    module.hot.accept();

app.js

    import React from "react";
    const App = () => <div>React App!</div>;
    export default App;

.gitignore

    # See https://help.github.com/articles/ignoring-files/ for more about ignoring files.

    # variables, keys, etc
    .env
    .env.*
    .env.development
    .env.production
    .env.example

    # dependencies
    /node_modules
    /.pnp
    .pnp.js

    # testing
    /coverage

    # misc
    .DS_Store
    .env.local
    .env.development.local
    .env.test.local
    .env.production.local

    npm-debug.log*
    yarn-debug.log*
    yarn-error.log*

git init







# NODE

# MONGO
