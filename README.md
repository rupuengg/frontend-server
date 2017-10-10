# Frontend Application Server Using Webpack

This application is used to create server for frontend application.
Make Sure you have install update **nodejs**

Check the version

> node -v

> npm -v

## Step - 1

Create project directory

> mkdir [PROJECT_DIR]

> cd [PROJECT_DIR]

## Step - 2

Initialize npm

> npm init

Output look like This
```
{
  "name": "Application Name",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Rupendra",
  "license": "ISC"
}
```

## Step - 3

Install webpack dependencies and save as dev dependencies

> npm install webpack webpack-dev-server --save-dev

## Step - 4

Create **webpack.config.js** file and place the code

```
var path = require('path');

var SRC_PATH = path.resolve(__dirname, 'src');
var DST_PATH = path.resolve(__dirname, 'dist');

var config = {
  entry: SRC_PATH + '/app/index.js',
  output: {
    path: DST_PATH + '/app',
    filename: 'bundle.js',
    publicPath: '/app/'
  }
};

module.exports = config;
```

Here you define the webpack configuration.

## Step - 5

Set the build command in **Package.json** file in **scripts**

```
"start": "npm run build",
"build": "webpack -d && cp src/index.html dist/index.html && webpack-dev-server --content-base src/ --inline --hot --port 3030"
```

First line build the project with **npm**
Second line copy the src/idnex.html to dist/index.html and start webpack-dev-server

## Step - 6

Create Directory Structures

- src
  - app
    - index.js
  - index.html

And Place the html in **index.html** file

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, user-scalable=no, intial-scale=1.0, maximum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>ReactJS Basic</title>
    <!-- <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-beta/css/bootstrap.min.css" integrity="sha384-/Y6pD6FV/Vv2HJnA6t+vslU6fwYXjCFtcEpHbNJ0lyAFsXTsjBbfaDjzALeQsN6M" crossorigin="anonymous"> -->
  </head>
  <body>
    Hello World
    <div id="root"></div>
    <script src="app/bundle.js"></script>
  </body>
</html>
```

## Step - 7

Run the Server

> npm start

Open the link in broswer [http://localhost:3030/](http://localhost:3030/).

You can also change port in **webpack.config.js**
