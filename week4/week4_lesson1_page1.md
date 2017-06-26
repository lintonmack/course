# Till

What we'll be making
------
We'll be making a simple till. The user will be able to choose from different products to put through the till and every time a product is added, a grand total will be calculated.

Preparation - both people to do this
------
1) Create a new folder inside your local **Projects** folder called **till**.
2) Change directory into your **till** folder ***then*** initialise a Git repository (`git init`).
3) Create a new repository on GitHub called **till** (**DON'T create with readme**).
4) Set up your remotes. You want to set an origin linking to your remote repository, and another remote with your pair's name, linking to their repository (use the link in the address bar):

```bash
git remote add origin <linkToYourGitHubRepo>
git remote add <partnerName> <linkToPartnerGitHubRepo>
```

:twisted_rightwards_arrows: **Decide initial driver and navigator roles between you. Remember: The driver shouldn't be looking at the walkthrough, and the navigator shouldn't be typing any code!!!**

File structure
------
In previous walkthroughs, we have used the internal method of adding JavaScript to our documents. This is okay for small scripts, but as we write more and more code we should think about moving this JavaScript into a separate **.js** file. 

1) Create a new **index.html** file and populate with a !DOCTYPE and the basic HTML structure.
2) Before the closing `body` tag, add opening and closing `script` tags. Give the opening tag an attribute of `type` with a value of `text/javascript` and an `src` of `till.js`.
3) We also want to add Bootstrap to our document to make our till application a little more appealing. Inside your `head` tags add the following:
```html
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">
```

Your **index.html** file should look like this:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Till</title>
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">
</head>
<body>
  <script type="text/javascript" src="till.js"></script>
</body>
</html>
```

4) Create the **till.js** file in the same folder as your **index.html** file.

5) Stage both files on your local repository and commit:

```bash
git add index.html
git add till.js
git commit -m "Initial commit"
```

**DON'T SWAP ROLES YET!!** We're just committing before we make any significant changes.

***
:bulb:

You may have noticed that we always include the JavaScript at the bottom of our HTML files. The reason for this is so we wait for all of the elements on the page to load, before using JavaScript on these elements. 
***

Creating our products
------

We're going to use objects for our products. The properties of the object will be the product's `name` and `price`. We will store these objects in an array, which we will loop over later to display buttons for each product.

1) First of all, define a new variable called `apples` and assign it an empty *object literal*:

```js
var apples = {}
```

2) Give the object literal a name/value pair where the name is `name` and the value is `Apples` (String):

```js
var apples = {
  name: 'Apples'
}
```

3) Add another name/value pair where the name is `price` and the value is `0.99` (Number) (don't forget to add a comma after the first name/value pair):

```js
var apples = {
  name: 'Apples',
  price: 0.99
}
```

4) Now define an additional variable called `products` and assign it an array containing the variable `apples`:

```js
var products = [apples]
```

5) Create **at least 4** more product objects and add them into the array.

6) Add the `till.js` to your staging environment (hint: `git add <file>`), commit with a suitable message (hint: `git commit -m "<message>"`) and push to your origin. As this is your first push on this repository, you will need to set your upstream to master (`git push -u origin master`).

:twisted_rightwards_arrows: **Driver and Navigator switch roles**