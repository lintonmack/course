Continuing on from last week.

:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

## Setting up Express

1. Create an `app.js` file in your project's root folder.

2. Inside `app.js` require in `express` and assign the exported object to a variable named `express`:

```js
var express = require('express')
```

3. Install `express-handlebars` with npm, saving to dependencies.

4. Now on line 2 of `app.js` (after our `express` `require`), require in `express-handlebars` and assign it to a variable named `exphbs`:

```js
var exphbs = require('express-handlebars')
```

5. On a new line, declare a variable named `app` and assign to it `express()`:

```js
var app = express()
```

6. After the assignment to `app`, add the following to set Handlebars as the default templating engine:

```js
app.engine('.hbs', exphbs({
  extname: '.hbs',
  defaultLayout: 'main'
}))
app.set('view engine', '.hbs')
```

7. Now add the following to set the public folder:

```js
app.use(express.static('public'))
```

8. Finally, to fire up the webserver, call `listen` on `app` and pass an argument of `3000`:

```js
app.listen(3000)
```

9. Create a `views` folder, and inside of it create a `layouts` folder.

10. Inside the `layouts` folder, create a new file called `main.hbs`. Populate with the basic HTML structure (`!` `Tab`), change the title and add `{{{body}}}` in between the `body` tags:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Social Network</title>
</head>
<body>
  {{{body}}}
</body>
</html>
```

## Connecting to the database

Previously, we made a database specifically for use in tests. Now we need to create a database for development and connect to it inside of `app.js`.

1. Inside *Robo3T*, connect to `localhost:27017` and create a new database called `social_network_development`. 

2. Add a new line to your `settings.env` file:

```bash
DATABASE_URL=mongodb://localhost:27017/social_network_development
```

3. Add the following in `app.js` at the very top of the file:

```js
var path = require('path')

require('dotenv').config({
  path: path.join(__dirname, 'settings.env')
})
```

4. Under the `dotenv` require, require in mongoose and assign to a new variable `mongoose`:

```js
var mongoose = require('mongoose')
```

5. Then underneath add the following:

```js
mongoose.connect(process.env.DATABASE_URL, {
  useMongoClient: true
})
```

## Add, commit and push

:twisted_rightwards_arrows: **Driver and Navigator switch roles**

[Continue to part 2](lesson1_part2.md)