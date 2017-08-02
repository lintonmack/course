:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

## settings.env file

After you pull down, you'll probably notice the driver doesn't have the settings.env file. This is because it wasn't deployed to GitHub. Create a settings.env file using your own database connection URL.

## Model

Currently our model is an instance of our `ToDos` object. It's what we're currently using to store and manipulate data in our application. Now we have a database we don't need this.

1. Create a new file in `models/` called `ToDo.js`.

2. Require in mongoose and assign to `mongoose`:

```js
var mongoose = require('mongoose')
```

3. Now we need to specify the schema for a ToDo. A schema is essentially a way of us to specify which fields can be added to a document, and what type their values can have. Let's create a new schema for a `ToDo`, allowing a field of `task` with a type of `String`. We'll assign it to the variable `toDoSchema`:

```js
var toDoSchema = new mongoose.Schema({
  task: String
})
``` 

4. Now we can create our model. In Mongoose, this is as simple as passing a model name to `mongoose.model` and we pass in our schema as a second argument to *attach* it to the model:

```js
var ToDo = mongoose.model('ToDo', toDoSchema)
```

5. Lastly, we'll just set `ToDo` as our `module.exports` object:

```js
module.exports = ToDo
```

6. Delete `ToDos.js` from the `models/` folder. We won't be needing it now as we'll be solely be using the `ToDo` model.

## Add, commit and push

:exclamation: It's worth noting that our code doesn't work at this stage. Usually it is bad practise to push broken code up to GitHub - we're just doing it so we can break down the problem.

:twisted_rightwards_arrows: **Driver and Navigator switch roles**

[Continue to part 3](lesson2_part3.md)