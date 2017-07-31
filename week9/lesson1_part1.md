## Prep - both partners

1. Create an empty (no README) remote repository on GitHub called `todo-list`.
2. Create a new folder `todo-list` in your `Projects` folder, `cd` into it and initialise a new Git repository.
3. Configure the local repository to point to you and your partner's remotes:

```bash
git remote add origin <linkToYourGitHubRepo>
git remote add <partnerName> <linkToPartnerGitHubRepo>
```

:twisted_rightwards_arrows: **Decide initial driver and navigator roles between you.**

## Installing Nodemon - both partners

We will be using Express to create a webserver. Because the server will always need to be listening to requests, our Node.js process will need to run continuously.

The issue when running apps with the `node` command is that everytime we make a change to our code, we have to kill the running Node.js process and restart it to see our changes. Instead, we can install a tool called *nodemon*, which will detect changes to our files and restart Node.js automatically. To install it run:

```
npm install -g nodemon
```

If it doesn't work, try again with `sudo`.

## Initial setup

1. Firstly, run `npm init` in the command line and go through the wizard to generate a `package.json` file for your project.

2. Now install Express and save it to your package.json dependencies:

```bash
npm install --save express
```

3. Create a `.gitignore` folder add add:

```
node_modules/
```

4. Create an `app.js` file in your project's root folder.

## Firing up an Express webserver

1. Inside `app.js` require in `express` and assign the exported object to a variable named `express`:

```js
var express = require('express')
```

2. On a new line, declare a variable named `app` and assign to it `express()`:

```js
var app = express()
```

3. Now to test everything is working, add a new `get` route handler for `/` and inside the function callback, send a response of `Hello World`:

```js
app.get('/', function (req, res) {
  res.send('Hello World!')
})
```

4. Finally, to fire up the webserver, call `listen` on `app` and pass an argument of `3000`:

```js
app.listen(3000)
```

5. In the command line, run `nodemon app.js`, then go to your web browser and visit `localhost:3000`. You should see `Hello World!`.

## Controller

1. Create a folder called `controllers` and inside create a file called `toDoController.js`.

2. Inside `toDoController.js`, create a function named `toDoController` and give it a single parameter of `app`:

```js
function toDoController (app) {

}
```

3. After the function block, set the `module.exports` object to the function:

```js
module.exports = toDoController
```

4. **Cut** the route handler for `/` from `app.js` and paste it inside our `toDoController` function block:

```js
function toDoController (app) {

  app.get('/', function (req, res) {
    res.send('Hello World!')
  })

}
```

5. Now inside `app.js`, above the `app.listen`, `require` in `toDoController.js` and call it straight away, passing in app:

```js
require('./controllers/toDoController.js')(app)
```

6. Refresh your browser window. If you still see `Hello World!` then you've done everything correctly.

## Add, commit and push

:twisted_rightwards_arrows: **Driver and Navigator switch roles**

[Next](lesson1_part2.md)