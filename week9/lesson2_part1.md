## mLab - Both partners

It is possible to run a MongoDB server locally on your computer, but for this week we will be using [mLab](https://mlab.com/) who provided managed MongoDB hosting (or *Database As A Service*).

You can signup and create a MongoDB database for free (up to 500GB) - it isn't a trial and you don't need payment details. 

1. Create an account on [mLab](https://mlab.com/). You will need to verify your email address before you can create a database.

2. In your account dashboard under **MongoDB Deployments**, select **Create new**.

3. For **Cloud Provider**, select **amazon web services**.

4. For **Plan Type**, select **Sandbox** (**FREE**), and click **Continue**.

6. Select the **eu-west-1** region, and click **Continue**.

7. Enter **todo-list** as the database name and click **Continue**.

8. Click **Submit Order** and wait patiently for your database to be created. When it is ready, select it from the table.

10. Click the **Users** tab, and **Add database user**. Fill in the fields and click **CREATE**.

11. Keep the window open and make sure you remember your user credentials. We'll need this information later on.

## Back to pairing

:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

## Mongoose

We're going to use [Mongoose](http://mongoosejs.com/) - an ODM (Object Document Mapper) - to talk to our database. Install it and save it to your package.json dependencies:

```bash
npm install --save mongoose
```

## dotenv

We're going to need to use our database connection URL inside our code. The issue with this is that if we push our code up to GitHub, then our security credentials will be available for anybody to see. [People can and do make it their mission to find these credentials](https://www.theregister.co.uk/2015/01/06/dev_blunder_shows_github_crawling_with_keyslurping_bots/).

Fortunately there is a solution, which is to use environment variables. Environment variables exist on our computers but not in the codebase itself - the code will look to the machine it is being executed on for the variables. We can add environment variables to our computers by editing our command line profile, but a more elegant way is to use `.env` files.

`.env` files allow us to store environment variables in a file in the project root. We can then use the `dotenv` npm module to look in this file for the variables we want. We can then `.gitignore` this file so it stays on our local machines but doesn't get pushed up to the remote (and thus isn't available to view online).

Install dotenv:

```bash
npm install --save dotenv
```

## Add credentials to a .env file

Create a `settings.env` file in your project's root folder then add:

```bash
DATABASE_URL=<insert your database URL here>
```

Your database URL can be found on mLab on your database's dashboard. Replace `<dbuser>` and `<dbpass>` with your user details (not your mLab login, but the user you created under the Users tab).

Next open up your `.gitignore` file, and on a new line add:

```
settings.env
```

Save, and run `git status` in the command line to ensure `settings.env` isn't being tracked (if it doesn't show then all is well).

## Including dotenv

Add the following in `app.js` at the very top of the file:

```js
var path = require('path')

require('dotenv').config({
  path: path.join(__dirname, 'settings.env')
})
```

It doesn't need to be assigned to a variable, as it executes straight away, looking for `.env` files and assigning the variables to the global `process.env` object. We specify a `path` property so we only include the environment variables inside `settings.env` (it will look for any `.env` file in our folder by default).

## Mongoose - connecting to the database

In `app.js`, under the `dotenv` require, require in mongoose and assign to a new variable `mongoose`:

```js
var mongoose = require('mongoose')
```

Underneath add the following:

```js
mongoose.connect(process.env.DATABASE_URL, {
  useMongoClient: true
})
```

This will connect to our database. It should stay connected throughout our application unless we explicitly disconnect from it. The `process.env.DATABASE_URL` will evaluate to the value of our environment variable we set just now. The second argument tells Mongoose to use the Node.js Mongo driver to establish the connection - we will get a warning if we don't provide this. 

## Add, commit and push

:twisted_rightwards_arrows: **Driver and Navigator switch roles**

[Continue to part 2](lesson2_part2.md)