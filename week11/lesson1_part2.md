:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

## Routes

1. Create a new folder in your project's root folder called `routes`. Inside `routes/` create a new file called `usersRoutes.js`.

2. Inside `usersRoutes.js`, declare a new function named `usersRoutes` and give it a parameter of `app`.

3. Set the `module.exports` for the file to the `usersRoutes` function (but don't call it).

4. Now back in `app.js`, require in the `usersRoutes.js` file at the top, and assign the exported object to a new variable named `usersRoutes`.

5. Now - above the `app.listen` - call `usersRoutes` and pass in an argument of `app` (a.k.a our Express instance).

## `body-parser`

1. At the top of `usersRoutes.js`, require in `body-parser`, assigning the exported object to a variable named `bodyParser`:

```js
var bodyParser = require('body-parser')
```

2. Install the `body-parser` npm package and save it to your dependencies.

3. Before the `usersRoutes` function, add: 

```js
var urlencodedParser = bodyParser.urlencoded({ extended: false })
```

## The `/` route

For now, when the user visits `/`, they should either be greeted and should be given the option to log out, or if they aren't logged in then they should be given links to login and registration.

1. Inside `usersRoutes.js`, in the `usersRoutes` function, add a new `get` route handler for `/`:

```js
app.get('/', function (req, res) {
  
})
```

2. Inside the route handler, render the template `home`:

```js
res.render('home')
```

3. Now inside `views/` create a file called `home.hbs`, add the following:

```html
{{#if currentUser}}
  Hello {{currentUser.emailAddress}}! <a href="/logout">Logout</a>.
{{else}}
  You must be logged in to view this page. <a href="/login">Login</a> or <a href="/register">Register</a>.
{{/if}}
```

## The `currentUser` object

Previously - inside the login controller - we've set the value of `session.user` on Express's `req` object to the logged in user's database document. We now need to enable sessions and then we will pass a `currentUser` property to our `home` template, which we will set to our session.

1. To enable `client-sessions`, in `app.js` add a new `require` for `client-sessions` and assign the exported object to a variable named `sessions`.

2. Underneath, add the following (don't type the exact same thing for the value for `secret` - just ensure you have a random string of numbers and letters):

```js
app.use(sessions({
  cookieName: 'session',
  secret: '6k534rtf546tredgdsyjyujvgbxdarw4te453w'
}))
```

***
:bulb:

`client-sessions` works by storing a cookie on a user's computer that is encrypted with a "secret" (set above). The cookie can only be decrypted with the key, and therefore this method of storing cookies is secure as only the server has the key.
***

3. Now back inside `usersRoutes.js` - in the `/` get route handler - pass a second argument to `res.render` with a `currentUser` property set to `req.session.user`:

```js
res.render('home', { currentUser: req.session.user })
```

## Add, commit and push

:twisted_rightwards_arrows: **Driver and Navigator switch roles**

[Continue to part 3](lesson1_part3.md)