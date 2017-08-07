:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

## Creating the login controller

1. Create a new folder in your project route folder called `controllers`.

2. Inside `controllers/`, create a new file called `usersControllers.js`.

3. Create an empty object literal inside the file, and assign it to a variable named `usersControllers`.

4. Underneath, export the object on `module.exports`.

5. Now add a method to the `usersControllers` object, named login.

6. Run your test again. You should now have an error along the lines of:

```bash
Expected spy to have been called with:
["hello@world.com", "password123"]
But it was not called.
```

8. Firstly, add `req` and `res` parameters to the `login` method if you haven't already done so, as we pass arguments into this method from our test, and Express will need to pass objects to this method also.

7. The spy refers to `User.login`, so require in the `User` model into your `usersControllers.js` file, and assign the exported object to `User`.

8. Now inside your method, call `User.login` and pass in a `req.body` argument.

9. Run your tests. You should pass.

## Add, commit and push

:twisted_rightwards_arrows: **Driver and Navigator switch roles**

[Continue to part 6](lesson1_part6.md)