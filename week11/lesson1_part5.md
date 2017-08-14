:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

## The GET `/logout` route

When we go to `/logout`, we want our session to be cleared and then to be redirected back to the homepage, where we should see ourselves no longer logged in.

1. Inside `usersRoutes.js`, add a new GET route handler for `/logout` and add a callback function with `req` and `res` parameters.

2. Inside the callback, set `req.session.user` to `false`.

3. Then call `res.redirect('/')`.

***
:bulb:

As you may have guessed `res.redirect(...)` will redirect the user to whichever route is specified. 
***