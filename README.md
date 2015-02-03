# lodash-express

[![npm package](https://nodei.co/npm/lodash-express.png?downloads=true&downloadRank=true&stars=true)](https://nodei.co/npm/lodash-express/)

Use Lodash templates easily in Express.

(Note: This is a very minor variation of Casey Foster's underscore-express.)

## Install

This package is registered in npm as `lodash-express`, so a simple...

```bash
npm install lodash-express
```

...will do it.

## Usage

In your Express app setup...

```js
// replace 'html' below with your favorite template extension
var app = express();
require('lodash-express')(app, 'html'); 
app.set('view engine', 'html');
```

...and that's it!

## Including Subtemplates

`lodash-express` comes with a baked-in _include_ method. Here's an example...

**views/header.html**
```html
<html>

  <head>
    <title>Header!</title>
  </head>

  <body>
```

**views/footer.html**
```html
  </body>
</html>
```

**views/index.html**
```html
<%= include('header') %>
    Welcome to my homepage!
<%= include('footer') %>
```

**app.js**
```js
res.render('index');
```

**RESULT**
```html
<html>

  <head>
    <title>Header!</title>
  </head>

  <body>
    Welcome to my homepage!
  </body>
</html>
```

`include` is relative to the file it is called from. Feel free to use relative paths like `../../some/other/subtemplate`.
