:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

Firstly, do a `git pull <partnerName> master` so you have your partner's changes.

Displaying to-do items
------
We now have an array of `toDoItems` which we can add to with a form. Now we need to update our document (page) every time that array changes (every time somebody submits the form).

We need to use JavaScript to manipulate our document. In order to do so we have to create an element that JavaScript can push content into.

1) In your `body` above the opening `form` tag add opening and closing `ul` tags, and give the opening tag an `id` attribute with a value of `toDoItems`.

2) Below the `addToDoItem` function, define a new function called `updateToDoItems`.

```javascript
function updateToDoItems () {

}
```

3) Inside the function block, create a `for` loop that goes through every element inside the `toDoItems` array and assigns that element's index to `toDoIndex`:

```javascript
function updateToDoItems () {
  for (toDoIndex in toDoItems) {

  }
}
```

4) Now we want to find the current item in the array inside our loop, using the `toDoIndex` variable, assigning it to a new variable `toDoItem`.

```javascript
function updateToDoItems () {
  for (toDoIndex in toDoItems) {
    var toDoItem = toDoItems[toDoIndex]
  }
}
```

5) Lastly, whilst still inside the `for` block, we want to append `toDoItem` to our `ul` which we gave an `id` of `toDoItems`. We do that as follows:

```javascript
document.getElementById('toDoItems').innerHTML += '<li>' + toDoItem + '</li>'
``` 

***
:bulb:

There are a few things going on here. We've briefly mentioned `document.getElementById(...)` already. `innerHTML` refers to the enclosed contents in an opening/closing pair of tags. `+=` says take the String we already have and append this String on the right to it. `'<li>' + toDoItem + '</li>'` is just string concatenation - we're using + to append 3 different strings together.
***

6) Add a `return` after the `for` block to finish the function.

```javascript
function updateToDoItems () {
  for (toDoIndex in toDoItems) {
    var toDoItem = toDoItems[toDoIndex]
    document.getElementById('toDoItems').innerHTML += '<li>' + toDoItem + '</li>'
  }
  
  return
}
```

7) Now all that's left to do is to call our `updateToDoItems` function inside the `addToDoItem` function. Remove the `console.log` (we don't need it now) and put `updateToDoItems()` in its place. Give it a go in the browser.

8) You've probably noticed that it's adding duplicate items. This is because we are looping over the `toDoItems` array every time we add to the document, and we are **appending** to the document. You can add the following line at the top of your `updateToDoItems` function to fix this:

```javascript
document.getElementById('toDoItems').innerHTML = ''
```

9) Add, commit and push.

Complete code
------
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
</head>
<body>
  <ul id="toDoItems">
  </ul>

  <form method="post" onsubmit="return addToDoItem()">
    <input id="toDoItem" type="text" placeholder="New to-do item">
    <input type="submit" value="Add">
  </form>

  <script type="text/javascript">
    var toDoItems = []

    function addToDoItem () {
      var toDoItem = document.getElementById('toDoItem').value
      toDoItems.push(toDoItem)

      updateToDoItems()

      return false
    }

    function updateToDoItems () {
      document.getElementById('toDoItems').innerHTML = ''
      
      for (toDoIndex in toDoItems) {
        var toDoItem = toDoItems[toDoIndex]
        document.getElementById('toDoItems').innerHTML += '<li>' + toDoItem + '</li>'
      }

      return
    }
  </script>
</body>
</html>
```