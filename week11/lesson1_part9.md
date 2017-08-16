:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

## Users can view a list of profiles

### Route

```js
var User = require('../models/User')
```

```js
app.get('/profiles', function (req, res) {
  User.find({}, function (error, result) {
    if (error) {
      res.send('An error occurred')
    } else {
      res.render('profiles', { users: result })
    }
  })
})
```

***
:bulb:

`<Collection>.find` will look for multiple records that match the passed selector (in this case `{}`, which simply returns all records). We then pass the results to the `profiles` template.
***

### profiles.hbs

```html
<ul>
  {{#each users}}
    <li><a href="/profiles/{{_id}}">{{emailAddress}}</a></li>
  {{/each}}
</ul>
```

***
:bulb:

`{{#each arrayOfItems}}` loops over an array. If the array contains objects then you can access object properties inside the `{{each}}` block by their name e.g. `{{emailAddress}}`.
***

## Users can view a single profile

### Route

```js
app.get('/profiles/:userId', function (req, res) {
  var userId = req.params.userId
  User.findOne({ _id: userId }, function (error, result) {
    if (error) {
      res.send('An error occurred')
    } else {
      res.render('profile', { user: result })
    }
  })
})
```

***
:bulb:

`:userId` here is a URL parameter, meaning whatever is passed in its place in the user's address bar will be parsed and added to the `req.params` object. If our url was `/profiles/abc123` then `req.params.userId` will be equal to `abc123`. 
***

### profile.hbs

```html
<div>
  <strong>Bio</strong> {{user.bio}}
  <strong>Home Town</strong> {{user.homeTown}}
</div>
```

## Exemplar

You can find an exemplar for these walkthroughs [here](https://github.com/MCRcodes/social-network-exemplar).