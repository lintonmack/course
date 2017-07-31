:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

## Deleting

We will need to be able to mark our to-dos as complete. The easiest way to do that is to delete them when they're done. 

1. Inside `ToDos.js`, add a new method to the prototype called `removeItem` - it should take a parameter of `id`:

```js
  removeItem: function (id) {
    
  }
```

2. Now we need to find an item inside the `_items` array with an `id` property matching the argument passed to the `id` parameter. Normally we would use a `for` loop for this, but JavaScript has a nicer method introduced in the ES6 standard: [filter()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter). It allows us to filter an array. Add the following:

```js
  removeItem: function (id) {
    this._items = this._items.filter(function (item) {
      return item.id !== id
    })
  }
```

***
:bulb:

First of all we call `.filter` on our array. It takes a callback function, and the current element in the array being iterated over is passed as the first argument (in this case `item`). If the callback returns `true` then the current element will be kept in the array, otherwise it will be removed. 

Above, the current element (assigned to `item`) is always an object with an `id` property and a `task` property. When the item's `id` isn't equal to the `id` passed into the method, then return true. Otherwise, we return false to strip the item from the array.
***

## Client-side JavaScript (the front-end)

All of our JavaScript so far has been server-side. Now we actually need some JS on the front-end (client) to be able to handle deleting of to-dos. 

1. Create a new folder in `public` called `js` and create a new file called `main.js`.

2. Inside `main.hbs` add a `script` tag right before the closing `body` tag:

```html
<script src="js/main.js" type="text/javascript"></script>
```

3. Inside `main.js`, find all of the `li` elements on the page and assign them to `listItems`:

```js
var listItems = document.querySelectorAll('li')
```

***
:bulb:

`querySelectorAll` will find all elements on a page that match the given CSS selector, and will return them in a *NodeList* - an array of DOM elements. [Read more on MDN](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll).
***

4. Now we'll use another ES6 function [forEach](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach) to loop through our `listItems` array. forEach takes a callback function - the first argument passed to the callback is the current item in the array:

```js
toDoItems.forEach(function (item) {

})
```

`item` here refers to a single DOM element from the `listItems` NodeList.

5. Now inside the forEach block, we want to attach a click event listener to each item:

```js
toDoItems.forEach(function (item) {
  item.addEventListener('click', function (event) {

  })
})
```

***
:bulb:

`element.addEventListener('click', ...)` is the non-jQuery way of doing `$(element).click(...)`

[addEventListener on MDN](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener)
***

6. Now inside the `addEventListener` callback, assign the `data-id` attribute of the element to a new variable named `id`:

```js
toDoItems.forEach(function (item) {
  item.addEventListener('click', function (event) {
    var id = event.target.dataset.id
  })
})
```

7. Lastly, we make an AJAX `DELETE` request to `/<id>`:

```js
toDoItems.forEach(function (item) {
  item.addEventListener('click', function (event) {
    var id = event.target.dataset.id

    var request = new XMLHttpRequest()

    request.onreadystatechange = function () {
      if (request.readyState === 4 && request.status === 200) {
        location.href = '/'
      }
    }
    request.open('DELETE', '/')
    request.setRequestHeader('Content-type', 'application/x-www-form-urlencoded')
    request.send('id=' + id)
  })
})
```

***
:bulb:

We've seen some of this before. The key difference here is we're specifying `DELETE` now instead of `GET`. We're also telling the server we're sending data to (in this case our own server) that the content-type is urlencoded (form data). Lastly, in our `send` method, we actually provide some data to send to the server (the server expects data on POST and DELETE requests as they are manipulating actions). The format for sending form data is `propertyname=propertyvalue` (for multiple properties, join with `&`).
***

8. Now we just need a `delete` route handler. Inside `toDoController.js`, after the `app.post` block, call `app.delete` and pass in `/`, `urlencodedParser` and a callback function with the params `req` and `res`:

```js
app.delete('/', urlencodedParser, function (req, res) {

})
```

9. Inside the callback, call `removeItem` on `toDos` and pass in `req.body.id`:

```js
  toDos.removeItem(req.body.id)
```

10. Finally, render the list again:

```js
  app.delete('/', urlencodedParser, function (req, res) {
    toDos.removeItem(req.body.id)

    res.render('home', {
      toDos: toDos.getItems()
    })
  })
```

11. Try in your browser. Your to-do list should now be fully functional.