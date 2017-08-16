:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

## Password hashing

It's **very** important that we hash our passwords. You may hear of the terms *hashing* and *encryption*. With both, we take some plain text, pass it through an algorithm and we get a different meaningless string back. 

The difference between hashing and encryption is that it is possible to decrypt encrypted text - that is, if you have the key used to encrypt the text in the first place. However, hashes are designed to be one-way. 

We will use the hashing algorith *bcrypt* to hash a user's password. As we are unable to decrypt, we will need to hash the password when the user registers (storing the hash in the database in place of the plain text password), and when they login we will need to hash the password they enter, comparing it against the hash stored in the database.

### Hashing when a password goes into the database

We want to catch the password right before it goes into the database, so we will add logic to our User model's `register` static method.

1. Firstly - if you have registered an account/multiple accounts on your application - go into Robo3T, double click your `social_network_development` database, and double click `Collections`. Right click on `users` and select `Remove All Documents...`.

2. Install the npm package `crypto`, saving it to your project's dependencies.

3. Inside `models/User.js`, require in the `crypto` package, and assign the exported object to a new variable named `crypto`.

4. Find the `register` method, and add the following at the start of the method:

```js
var hash = crypto.createHash('sha256')
hash.update(user.password)
user.password = hash.digest('hex')
```

This does the following:

* Creates a new Hash instance to store the hash
* Updates the hash based on the text we provide (`user.password`)
* Get's the hashed version of the string back (the `digest`)

### Hashing when we login

Now we've hashed the string that goes into the database, but our login method currently checks a plain text password against a hash, which will fail as they aren't equal strings. Therefore, we also need to hash the password on login before the comparison takes place.

Find the login method and - again - add the following to the top of the method:

```js
var hash = crypto.createHash('sha256')
hash.update(user.password)
user.password = hash.digest('hex')
```

### Passing the tests

The tests will likely now fail with something along the lines of `Error: Uncaught, unspecified "error" event. (Error: expect(received).toBeTruthy()`. With a bit of investigating - a.k.a searching the `User.test.js` code for `.toBeTruthy()` - we can identify `can login if registered` as the test that is breaking.

The reason it is breaking is because objects in JavaScript are *mutable*. That is, they pass by reference. We pass `user` to `User.register` and inside that method, `user.password` gets changed to a hash. Therefore, when we later pass `user` to `User.login`, we set `user.password` to a hash of the original hash (we hash it twice). Because it has been hashed twice, it won't match the string that was stored in the database, as that string was only hashed once.

We therefore need to clone our user object and ensure that different objects go to `User.register` and `User.login`. We could just copy and paste the object, but a much more elegant way in the latest JS standard (ES6) is to use `Object.assign`. `Object.assign` merges two or more objects (each object is passed as a separate argument). The most notable thing is that if you pass an empty object as the first argument, then the returned object will always be unique (as each set of `{}` object literals always equals a unique object).

Change your test to:

```js

  test('can login if registered', function (done) {
    var user = {
      emailAddress: 'hello@world.com',
      password: 'password123'
    }
    var userClone = Object.assign({}, user)

    User.register(user, function () {
      User.login(userClone, function (error, result) {
        expect(error).not.toBeTruthy()
        expect(result).toBeTruthy()
        done()
      })
    })
  })
```

Here we've used `Object.assign` to create a clone of the `user` object. Any changes to `user` won't be reflected in `userClone`, as `userClone` is now a completely unique object. We pass `userClone` to `User.login` instead of `user` as `user.password` has been modified at this point.
