:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

Driver pulls
------
The driver will need to pull down from their partner's remote master branch:

```bash
git pull <partnerName> master
```

Updating the DOM
------
We now have a `transaction.items` array that we can populate with products. Now we just need to display the contents of that array in our document, and update our total.

1) We want to update the DOM every time the user clicks 'Add' on a product, but we may also want to update the DOM on other user actions. Therefore, we should add the code that does this to a function so it's reusable. Define a new function at the end of **till.js** and name it `updateDOM`:

```javascript
function updateDOM () {

}
```

2) Now we want to "flush" the current state of our DOM. That is, if we already have some transaction items on the screen then we should set the parent `div`'s `innerHTML` to `''` so we can add from scratch:

```js
var tillItems = document.getElementById('tillItems')
tillItems.innerHTML = ''
```

3) Now just like we did with our product buttons, we want to loop over an array and update the DOM for each item. The only difference is that we now want to do it on the `transaction.items` array:

```javascript
  for (var itemIndex = 0; itemIndex < transaction.items.length; itemIndex++) {

  }
```

4) First thing we want to do is to append our `transaction.items` to the `tillItems` element:

```javascript
    var currentItem = transaction.items[itemIndex]

    var itemsHTML = '<li class="list-group-item">'
    itemsHTML += '<span class="badge">' + currentItem.price + '</span>'
    itemsHTML += currentItem.name
    itemsHTML += '</li>'

    tillItems.innerHTML += itemsHTML
```

5) Then we want to add up all of our `price` properties. Above the `for` loop, define a new variable called `total` and set the value to `0.00` (Number). Then inside of the `for` loop, set `total` to `total` plus `currentItem.price`:

```js
function updateDOM () {
  var tillItems = document.getElementById('tillItems')
  tillItems.innerHTML = ''

  var total = 0.00

  for (var itemIndex = 0; itemIndex < transaction.items.length; itemIndex++) {
    var currentItem = transaction.items[itemIndex]

    var itemsHTML = '<li class="list-group-item">'
    itemsHTML += '<span class="badge">' + currentItem.price + '</span>'
    itemsHTML += currentItem.name
    itemsHTML += '</li>'

    tillItems.innerHTML += itemsHTML
    total += currentItem.price
  }
}
```

6) Now the last thing to do on the till is just to display the new price. After the `for` loop use `document.getElementById('total')` to get our `total` HTML element and then set the `innerHTML` to `total.toFixed(2)` (call the `toFixed` method on total to convert it to 2 decimal places):

```js
function updateDOM () {
  var tillItems = document.getElementById('tillItems')
  tillItems.innerHTML = ''

  var total = 0.00

  for (var itemIndex = 0; itemIndex < transaction.items.length; itemIndex++) {
    var currentItem = transaction.items[itemIndex]

    var itemsHTML = '<li class="list-group-item">'
    itemsHTML += '<span class="badge">' + currentItem.price + '</span>'
    itemsHTML += currentItem.name
    itemsHTML += '</li>'

    tillItems.innerHTML += itemsHTML
    total += currentItem.price
  }

  document.getElementById('total').innerHTML = total.toFixed(2)
}
```

7) Now add a call to `updateDOM()` inside the `transaction.add` method:

```js
transaction.add = function (productName) {
  for (productIndex = 0; productIndex < products.length; productIndex++) {
    var currentProduct = products[productIndex]

    if (currentProduct.name === productName) {
      var selectedProduct = currentProduct
      break
    }
  }

  if (selectedProduct) {
    var newItem = {
      id: Math.floor(Math.random() * 100000),
      name: selectedProduct.name,
      price: selectedProduct.price
    }

    this.items.push(newItem)
    
    updateDOM()
  }
}
```

Exemplar Files
------
**index.html**

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

**till.js**

```js
var apples = {
  name: 'Apples',
  price: 0.99
}

var bananas = {
  name: 'Bananas',
  price: 0.45
}

var oranges = {
  name: 'Oranges',
  price: 0.12
}

var products = [apples, bananas, oranges]

for (var productIndex = 0; productIndex < products.length; productIndex++) {
  var buttonsContainer = document.getElementById('buttons')
  var product = products[productIndex]

  var buttonsHTML = '<div class="col-md-2">'
  buttonsHTML += '<div class="panel panel-default">'
  buttonsHTML += '<div class="panel-heading">'
  buttonsHTML += '<h3 class="panel-title">' + product.name + '</h3>'
  buttonsHTML += '</div>'
  buttonsHTML += '<div class="panel-body">'
  buttonsHTML += '<p>'
  buttonsHTML += '<strong>Price: </strong> £0.99'
  buttonsHTML += '</p>'
  buttonsHTML += '<button type="button" class="btn btn-primary" onclick="transaction.add(\'' + product.name + '\')">Add</button>'
  buttonsHTML += '</div>'
  buttonsHTML += '</div>'
  buttonsHTML += '</div>'

  buttonsContainer.innerHTML += buttonsHTML
}

var transaction = {}
transaction.items = []
transaction.add = function (productName) {
  for (productIndex = 0; productIndex < products.length; productIndex++) {
    var currentProduct = products[productIndex]

    if (currentProduct.name === productName) {
      var selectedProduct = currentProduct
      break
    }
  }

  if (selectedProduct) {
    var newItem = {
      id: Math.floor(Math.random() * 100000),
      name: selectedProduct.name,
      price: selectedProduct.price
    }

    this.items.push(newItem)
    updateDOM()
  }
}

function updateDOM () {
  var tillItems = document.getElementById('tillItems')
  tillItems.innerHTML = ''

  var total = 0.00

  for (var itemIndex = 0; itemIndex < transaction.items.length; itemIndex++) {
    var currentItem = transaction.items[itemIndex]

    var itemsHTML = '<li class="list-group-item">'
    itemsHTML += '<span class="badge">' + currentItem.price + '</span>'
    itemsHTML += currentItem.name
    itemsHTML += '</li>'

    tillItems.innerHTML += itemsHTML
    total += currentItem.price
  }

  document.getElementById('total').innerHTML = total.toFixed(2)
}
```