:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

## Users can edit their profiles

### Test

```js
test('can edit profile', function () {
  var user = {
    emailAddress: 'email@example.com',
    password: 'password123'
  }

  User.register(user, function () {
    User.editProfile(user, function (error, result) {
      expect(error).toBeFalsy()
      expect(result).toBeTruthy()
    })
  })
})
```

### Schema

We add two extra fields to the schema: `homeTown` and `bio`. We set them to `required: false`, as we don't need them when users first register accounts.

```js
var UserSchema = new mongoose.Schema({
  emailAddress: {
    type: String,
    required: [true, 'Email address is required.'],
    validate: [function (value) {
      return validator.isEmail(value)
    }, 'Email address isn\'t valid.']
  },
  password: String,
  homeTown: {
    type: String,
    required: false
  },
  bio: {
    type: String,
    required: false
  }
})
```

### User.js static method

```js
editProfile: function (user, callback) {
  User.update(user._id, {
    $set: {
      bio: user.bio,
      homeTown: user.homeTown
    }
  }, callback)
}
```

***
:bulb:

`<Collection>.update` takes the document's ID you wish to update as the first argument. The second argument is a **modifier**. We can pass in operators such as `$set` (change the value of), `$push` (add to array) and `$pull` (pull from array). [$set on MongoDB](https://docs.mongodb.com/manual/reference/operator/update/set/)
***

### Routes

```js
app.get('/editprofile', function (req, res) {
  User.findOne({ _id: req.session.user._id }, function (error, result) {
    if (error) {
      res.send('An error occurred')
    } else {
      res.render('editprofile', { currentUser: result })
    }
  })
})

app.post('/editprofile', urlencodedParser, usersControllers.editProfile, function (req, res) {
  res.redirect('/editprofile')
})
```

***
:bulb:

The user session only stores the user's email address, password and _id (as this is what we set in our `User.login` call). Therefore we pass the user's `_id` to `User.findOne` to get back the user's full document, which we then pass to the `editprofile` template.
***

### Controller

```js
editProfile: function (req, res, next) {
  const user = {
    _id: req.session.user._id,
    bio: req.body.bio,
    homeTown: req.body.homeTown
  }
  User.editProfile(user, next)
}
```

### editprofile.hbs

```html
<form method="post">
  <h2>Edit Profile</h2>
  <div>
    Bio:
    <textarea name="bio">{{currentUser.bio}}</textarea>
  </div>
  <div>
    Home Town:
    <input type="text" name="homeTown" value="{{currentUser.homeTown}}">
  </div>
  <button type="submit">Edit Profile</button>
</form>
```

[Continue to part 9](lesson1_part9.md)