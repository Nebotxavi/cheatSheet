TODO: map React things, node basics, pluggins

# GIT

General working flow where there is 

    git remote add 'origin' <link>
    
    // new branch
    git branch <branch_name>
    // change branch
    git checkout <branch_name>
    
    git add .
    git commit -m 'comment'
    // push changes to github, BEFORE USING IT, CHECK IF NEW BRANCH MUST BE CREATED IN THE REPO
    git push -u origin <branch_name>
    
    // change back to master branch
    git checkout master
    // pull changes from github
    git pull origin master
    // merge changes
    git merge <branch_name>
    // push the merged file to master
    git push origin master
    
    // remove the branch locally
    git branch -d <branch_name>
    // remove the branch from the repo
    git push origin --delete <branch_name>

# NODE BASIC

    sudo apt-get update
    sudo apt-get install nodejs
    sudo apt-get install npm

    node -v
    npm -v

# REACT

## SETUP

### CREATE REACT APP

    npx create-react-app my-app

### MINIMAL WEBPACK, BABEL, GIT

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

## Mapping

#### Forms & Validation

BookForm: https://github.com/Nebotxavi/-React_Portfolio-Book_Repo_App/blob/master/front_book_repo/src/components/bookForm.jsx

LoginForm: https://github.com/Nebotxavi/-React_Portfolio-Book_Repo_App/blob/master/front_book_repo/src/components/loginForm.jsx

Form (all validation): https://github.com/Nebotxavi/-React_Portfolio-Book_Repo_App/blob/master/front_book_repo/src/components/common/form.jsx

Input: https://github.com/Nebotxavi/-React_Portfolio-Book_Repo_App/blob/master/front_book_repo/src/components/common/input.jsx

Select: https://github.com/Nebotxavi/-React_Portfolio-Book_Repo_App/blob/master/front_book_repo/src/components/common/select.jsx


#### Context

DataProvider (createContext): https://github.com/Nebotxavi/-React_Portfolio-DRAW-Rural_cabins/blob/master/src/dataProvider.jsx

ProviderConsumer: https://github.com/Nebotxavi/-React_Portfolio-DRAW-Rural_cabins/blob/master/src/App.js

useContext: https://github.com/Nebotxavi/-React_Portfolio-DRAW-Rural_cabins/blob/master/src/pages/Cabin.jsx


#### Router DOM
NOTE THAT ROUTER DOM IS CHANGINT A LOT: https://reacttraining.com/blog/react-router-v5-1/

BrowserRoute wrapping: https://github.com/Nebotxavi/-React_Portfolio-Book_Repo_App/blob/master/front_book_repo/src/index.js

Route, Switch, Redirect: https://github.com/Nebotxavi/-React_Portfolio-Book_Repo_App/blob/master/front_book_repo/src/App.js

NavLink, Link: https://github.com/Nebotxavi/-React_Portfolio-Book_Repo_App/blob/master/front_book_repo/src/components/navBar.jsx

##### Protected routes

Summary, link that is protected (for example, if user not logged) and will redirect to another window (for example, login) and, in this case, take some action (for example, to login) and then redirect back to the protected link (now accessible). 

Route for ProtectedRoute:  https://github.com/Nebotxavi/-React_Portfolio-Book_Repo_App/blob/master/front_book_repo/src/components/navBar.jsx

ProtectedRoute: https://github.com/Nebotxavi/-React_Portfolio-Book_Repo_App/blob/master/front_book_repo/src/components/common/protectedRoute.jsx

Double redirection (protectedRoute => login =(log)=> protectedRoute): https://github.com/Nebotxavi/-React_Portfolio-Book_Repo_App/blob/master/front_book_repo/src/components/loginForm.jsx

##### Hiding links, redirections

Hiding links (ex: if not logged. Line 27): https://github.com/Nebotxavi/-React_Portfolio-Book_Repo_App/blob/master/front_book_repo/src/components/navBar.jsx

Redirect before rendering others (ex: if already logged and accessed by url. Line 12): https://github.com/Nebotxavi/-React_Portfolio-Book_Repo_App/blob/master/front_book_repo/src/components/loginForm.jsx

Redirection after action with window.location (ex: after login. Line 46): https://github.com/Nebotxavi/-React_Portfolio-Book_Repo_App/blob/master/front_book_repo/src/components/loginForm.jsx

Redirection after action with history.push (Line 73): https://github.com/Nebotxavi/-React_Portfolio-Book_Repo_App/blob/master/front_book_repo/src/components/registerForm.jsx 


#### useParams, useLocation, useHistory

useParams & useLocation: https://github.com/Nebotxavi/-React_Portfolio-DRAFT-TMDB_clone/blob/master/Desktop/Javascript/react/100daysCode/05-TheMovieDBClone/tmdb-clone/src/components/ItemsSelection.jsx

more info related to previous link: https://github.com/Nebotxavi/-React_Portfolio-DRAFT-TMDB_clone/blob/master/Desktop/Javascript/react/100daysCode/05-TheMovieDBClone/tmdb-clone/src/pages/ItemsType.jsx

more info related to previous link: https://github.com/Nebotxavi/-React_Portfolio-DRAFT-TMDB_clone/blob/master/Desktop/Javascript/react/100daysCode/05-TheMovieDBClone/tmdb-clone/src/components/MoviesLinks.jsx

Summary: 

- useParams() gets the parameters passed through a URL. Example: <Route path="/search/:type/:option" component={ItemsSelection} />

- useLocation() gets the object from the "to" part of Link. Example:  <Link
        to={{
          pathname: "/search/movie/popular",
          state: { title: "Popular Movies" }
        }}
      >

#### Data Fetching/ useEffect

Basic '3-steps' data fetching with Axios: https://github.com/Nebotxavi/-React_Portfolio-Book_Repo_App/blob/master/front_book_repo/src/components/bookForm.jsx

UseEffect for update State on different updates/events: https://github.com/Nebotxavi/React_Portfolio-Weather_App/blob/master/src/components/common/input/listSuggestions.jsx

More info for previous link + UseEffect with addListeners: https://github.com/Nebotxavi/React_Portfolio-Weather_App/blob/master/src/components/common/input/useKeyPress.jsx

#### useRef (+ handleClickOutside)

ManageClickOutside: https://github.com/Nebotxavi/React_Portfolio-Weather_App/blob/master/src/components/common/manageClickOutside.jsx

ManageClickOutside applied: https://github.com/Nebotxavi/React_Portfolio-Weather_App/blob/master/src/components/searchForm.jsx

#### HTTP service

httpService: https://github.com/Nebotxavi/-React_Portfolio-Book_Repo_App/blob/master/front_book_repo/src/services/httpService.js

Implementation of httpService: https://github.com/Nebotxavi/-React_Portfolio-Book_Repo_App/blob/master/front_book_repo/src/services/booksService.js

Call to the implementation (see doSubmit function): https://github.com/Nebotxavi/-React_Portfolio-Book_Repo_App/blob/master/front_book_repo/src/components/bookForm.jsx

#### Auth service & JWT

AuthService: https://github.com/Nebotxavi/-React_Portfolio-Book_Repo_App/blob/master/front_book_repo/src/services/authService.js

#### Local Storage

Local Storage set and get: https://github.com/Nebotxavi/-React_Portfolio-Hacker_Meaows/blob/master/src/components/settings.jsx

#### Pagination, sorting, searching, filtering + part of Table

##### Books example

Main: https://github.com/Nebotxavi/-React_Portfolio-Book_Repo_App/blob/master/front_book_repo/src/components/books.jsx

Filter menu: https://github.com/Nebotxavi/-React_Portfolio-Book_Repo_App/blob/master/front_book_repo/src/components/common/filterMenu.jsx

Search bar: https://github.com/Nebotxavi/-React_Portfolio-Book_Repo_App/blob/master/front_book_repo/src/components/common/searchBar.jsx

Pagination: https://github.com/Nebotxavi/-React_Portfolio-Book_Repo_App/blob/master/front_book_repo/src/components/common/pagination.jsx

Paginate function: https://github.com/Nebotxavi/-React_Portfolio-Book_Repo_App/blob/master/front_book_repo/src/utils/paginate.js

Main table (+ sorting): https://github.com/Nebotxavi/-React_Portfolio-Book_Repo_App/blob/master/front_book_repo/src/components/booksTable.jsx

Table (+ sorting): https://github.com/Nebotxavi/-React_Portfolio-Book_Repo_App/blob/master/front_book_repo/src/components/common/table.jsx

##### Cabins example (useContext)

Main: https://github.com/Nebotxavi/-React_Portfolio-DRAFT-Rural_cabins/blob/master/src/pages/Cabins.jsx

Data provider (filter application): https://github.com/Nebotxavi/-React_Portfolio-DRAFT-Rural_cabins/blob/master/src/dataProvider.jsx

Filters list (html elements): https://github.com/Nebotxavi/-React_Portfolio-DRAFT-Rural_cabins/blob/master/src/components/FiltersList.jsx


#### Suggestions list

Example: https://github.com/Nebotxavi/React_Portfolio-Weather_App/tree/master/src/components/common/input






# NODE

# MONGO
