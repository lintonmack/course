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

### Routes

```js
app.get('/editprofile', function (req, res) {
  res.render('editprofile', { currentUser: req.session.user })
})

app.post('/editprofile', urlencodedParser, usersControllers.editProfile, function (req, res) {
  res.redirect('/editprofile')
})
```

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