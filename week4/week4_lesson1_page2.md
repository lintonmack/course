:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

Driver pulls
------
The driver will need to pull down from their partner's remote master branch:

```bash
git pull <partnerName> master
```

Bootstrap
------
In order to make our till app somewhat presentable, we'll need to add in a few essential Bootstrap components to our `index.html` file. Let's add a [container](http://getbootstrap.com/css/#grid-intro) and a [page header](http://getbootstrap.com/components/#page-header):

```html
<body>
  <div class="container">
    <div class="page-header">
      <h1>Till</h1>
    </div>
  </div>
</body>
```

HTML Elements
------
We are going to need to append product buttons, till items and the total to our document through JavaScript. Therefore, we will need to have HTML elements that we can append to.

1) Inside the `body` tags in your `index.html`, create a `div` element with a `class` of `row` (we'll be using columns inside this `div`) an `id` attribute of `buttons`:

```html
    <div class="row" id="buttons">
    </div>
```

2) Underneath create a `ul` element with an `id` of `tillItems` and a class of `list-group`:

```html
    <ul id="tillItems" class="list-group">
    </ul>
```

3) Finally, underneath this, add a new `div` element with a class of `text-right`. Inside this `div` tag create a `h2` element with the text `Total £0.00`:

```html
    <div class="text-right">
      <h2>Total: £0.00</h2>
    </div>
```

4) Now we have a total but we only want to update the `0.00` part. To have JavaScript populate the `Total: £` would just be unnecessary and would affect performance. To ensure we can update the `0.00`, enclose it inside opening/closing `span` tags, and give the opening tag an `id` attribute of `total`:

```html
    <div class="text-right">
      <h2>Total: £<span id="total">0.00</span></h2>
    </div>
```

Your HTML should look like this:

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
  <div class="container">
    <div class="page-header">
      <h1>Till</h1>
    </div>
    <div class="row" id="buttons">
    </div>
    <ul id="tillItems" class="list-group">
    </ul>
    <div class="text-right">
      <h2>Total: £<span id="total">0.00</span></h2>
    </div>
  </div>
  <script type="text/javascript" src="till.js"></script>
</body>
</html>
```

We have 3 `id` attributes that we can hook into with JavaScript: `buttons`, `tillItems` and `total`.

Document Object Model (the **DOM**)
------
In JavaScript, most things are objects, even HTML documents. If you go into the console on your Chrome developer tools and type `document` followed by the Enter key, you will get back the HTML for your page. Don't be mistaken - `document` isn't a string. If you type `typeof document` in the console it will confirm to you that it is indeed an object. 

As you may have seen in a previous walkthrough, we can call methods on the `document` object, which will allow us to find specific `div` elements on our HTML document. We can then change the `innerHTML` of these elements. The HTML document is treated as an object, but also the HTML elements themselves are objects nested inside of this object.

First of all, we want to be able to append some buttons to the `div` element that has the `id` of `buttons`. We already have an array of products we are to sell, so the logical approach would be to loop through these and to append them to the DOM one by one.

1) At the end of your **till.js** file, create a new `for` loop with a variable `productIndex` that loops through every product in the `products` array:

```javascript
for (var productIndex = 0; productIndex < products.length; productIndex++) {

}
```

2) Now we want to append our HTML. Let's keep it simple to start off with. Inside the `for` block, call the method `getElementById` on the object `document`, and pass in an argument of `buttons`. Assign this to a variable called `buttonsContainer`. All of this terminology will be confusing but you are aiming for the following:

```javascript
  var buttonsContainer = document.getElementById('buttons')
```

3) Now on a new line, we want to set the value of the `innerHTML` property of `buttonsContainer`. We want to use the `+=` assignment operator to append to the contents of the element. For now, just assign the `productIndex` var:

```javascript
  buttonsContainer.innerHTML += productIndex
```

If you view your **index.html** now in the browser, you should have something along the lines of `01234` (or longer if you have more than 5 products).

4) Now we need to amend our assignment so we're actually appending something useful to the `buttonsContainer.innerHTML`. Above that line, define a new variable called `product` and assign it a value of `products[productIndex]`:

```javascript
  var product = products[productIndex]
```

This retrieves an object from our `products` array (based on the current productIndex in our loop) and assigns the resulting object to the variable `product`.

5) We can now use dot-notation on our `product` variable to access the product name and price. For now change: 
```javascript
  buttonsContainer.innerHTML += productIndex
```
to
```javascript
  buttonsContainer.innerHTML += '<p>' + product.name ' ' + product.price + '</p>'
```

6) This is now looking a bit better. The more HTML we append though, the messier this will get. Assign the string to a variable called `buttonsHTML` above and assign this to `buttonsContainer.innerHTML` instead:

```js
  var buttonsHTML = '<p>' + product.name + ' ' + product.price + '</p>'

  buttonsContainer.innerHTML += buttonsHTML
```

7) Lastly, add opening/closing `button` tags after the closing `p`. Give the `button` text of `Add`. Add to the opening tags the following attributes: `type` with the value `button`, `class` with the value `btn btn-primary` and `onclick` with the value `transaction.add(\'' + product.name + '\')` (we're going to create a `transaction` object with an `add` method next):

```js
  var buttonsHTML = '<p>' + product.name + ' ' + product.price + '</p>'
  buttonsHTML += '<button type="button" class="btn btn-primary" onclick="transaction.add(\'' + product.name + '\')">Add</button>'

  buttonsContainer.innerHTML += buttonsHTML
```

8) Now let's swap out the HTML for Bootstrap's column and panel (please copy and paste this. We will look at nicer ways of doing this in the future):

```js
  var buttonsHTML = '<div class="col-md-2">'
  buttonsHTML +=      '<div class="panel panel-default">'
  buttonsHTML +=        '<div class="panel-heading">'
  buttonsHTML +=          '<h3 class="panel-title">' + product.name + '</h3>'
  buttonsHTML +=        '</div>'
  buttonsHTML +=        '<div class="panel-body">'
  buttonsHTML +=          '<p>'
  buttonsHTML +=            '<strong>Price: </strong> £0.99'
  buttonsHTML +=          '</p>'
  buttonsHTML +=          '<button type="button" class="btn btn-primary" onclick="till.add(\'' + product.name + '\')">Add</button>'
  buttonsHTML +=        '</div>'
  buttonsHTML +=      '</div>'
  buttonsHTML +=    '</div>'
```

Your finished for loop should like like this:

```js
for (var productIndex = 0; productIndex < products.length; productIndex++) {
  var buttonsContainer = document.getElementById('buttons')
  var product = products[productIndex]

  var buttonsHTML = '<div class="col-md-2">'
  buttonsHTML +=      '<div class="panel panel-default">'
  buttonsHTML +=        '<div class="panel-heading">'
  buttonsHTML +=          '<h3 class="panel-title">' + product.name + '</h3>'
  buttonsHTML +=        '</div>'
  buttonsHTML +=        '<div class="panel-body">'
  buttonsHTML +=          '<p>'
  buttonsHTML +=            '<strong>Price: </strong> £0.99'
  buttonsHTML +=          '</p>'
  buttonsHTML +=          '<button type="button" class="btn btn-primary" onclick="transaction.add(\'' + product.name + '\')">Add</button>'
  buttonsHTML +=        '</div>'
  buttonsHTML +=      '</div>'
  buttonsHTML +=    '</div>'

  buttonsContainer.innerHTML += buttonsHTML
}
```

9) Apologies for this has been a long one! Add your files to staging, commit with a meaningful message and push to your origin remote (set the upstream again as this will be the first push to your remote).

:twisted_rightwards_arrows: **Driver and Navigator switch roles**