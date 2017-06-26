:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

Driver pulls
------
The driver will need to pull down from their partner's remote master branch:

```bash
git pull <partnerName> master
```

The `transaction` object
------
We need to create a new object for our till that keeps track of what has been purchased. We will call this object a `transaction`. Our `transaction` will understand adding new products, removing products and storing products. 

1) At the end of **till.js**, define a new variable called `transaction` and assign it an empty object literal:

```js
var transaction = {}
```

2) Now on a new line, create a property on the transaction object called `items` and give it a value of an empty array (`[]`). On another new line, create a method on transaction called `add` that has a parameter of `productName`:

```js
var transaction = {}
transaction.items = []
transaction.add = function (productName) {

}
```

Our `add` method will work as follows: we will loop through the products array until we find a product with a `name` matching `productName`; we will then define a new object that copies the properties from the resulting product and also adds an `id` name/value pair; and finally we will add this new object to `transaction.items`.

4) "we will loop through the products array until we find a product with a `name` matching `productName`".  Let's use a for loop on the `products` array to go through every item, assigning a matching product to a variable called `selectedProduct`:

```js
transaction.add = function (productName) {
  for (productIndex = 0; productIndex < products.length; productIndex++) {
    var currentProduct = products[productIndex]

    if (currentProduct.name === productName) {
      var selectedProduct = currentProduct
      break
    }
  }
}
```

***
:bulb:

We haven't seen the `break` keyword before. It essentially just *breaks* out of a loop a.k.a stops it from running. In this scenario, we've found a matching product, so there's no need to keep the loop going.
***

5) Underneath our `for` loop, but still inside our `add` function, we want to check that `selectedProduct` is defined (that there was a match), and if it is then "we will then define a new object that copies the properties from the resulting product and also adds an `id` name/value pair". We will assign this object to a variable called `newItem`:

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
      id: (Math.random() * 100000),
      name: selectedProduct.name,
      price: selectedProduct.price
    }

    this.items.push(newItem)
  }
}
```

***
:bulb:

You may be wondering why we're creating a new object...why not just pass the object we found from the `products` array directly into our `transaction.items` array? The reason is that, unlike variables, objects in JavaScript pass by reference. That is to say that if we assign an object to different variables and we manipulate the object using one of those variables, then the object will be changed on all 3. If we didn't create a new object in this scenario then the `id` property would get set on the original products.
***

***
:bulb:

You'll also notice here that we're using `Math.random()` to generate an `id` property. The reason for this is that we're likely to have each product added to the transaction more than once. If we wanted, for example, to be able to remove a product then we could only work out what to remove based on the product's `name` or `price`, and thus we'd have to remove all transaction items for that product. If we add a unique identifier to each object in our `transaction.items` then we can just remove items based on that `id`. 
***

6) Lastly, we want to push the `newItem` into our `transaction.items` array. We can access our `transaction` object inside a method with `this`, so we can just call: 

```js
this.items.push(newItem)
```

Your **till.js** should now look something like this:

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
    console.log(this.items)
  }
}
```

(I've added a `console.log` to the `transaction.add` method so you can check your `transaction.items` is being updated).

Your **index.html** should look like this:

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

:twisted_rightwards_arrows: **Driver and Navigator switch roles**