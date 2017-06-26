:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

Partner pulls
------
Again, the person who is now driving will need to pull their partner's changes. They to will need to add their partner's GitHub repo as a *remote* and pull down:
```
git remote add <partnersName> https://github.com/<username>/toDoList
git pull <partnersName> master
```

Handling the form input
------
When a user submits the form, we want to add the contents (or the current *value*) of the text input to an array of to-do items.

1) Inside the `script` tags, define a new variable called `toDoItems` and assign the variable an empty array (`[]`). 

```javascript
var toDoItems = []
```

2) Define a new function called `addToDoItem`.

```javascript
function addToDoItem () {

}
```

3) Inside the function block, define a new variable called `toDoItem` and assign it `document.getElementById('toDoItem').value`.

```javascript
function addToDoItem () {
  var toDoItem = document.getElementById('toDoItem').value
}
```

***
:bulb:

`document.getElementById('toDoItem').value` will look very unfamiliar at this point. That's okay. For now just know that it looks for an element with the id `toDoItem` in the document and it returns the value of that element's `value` attribute. This is our to-do text that we enter in the box.
***

4) Now - still inside the function block, and on a new line - add `toDoItems.push(toDoItem)`:

```javascript
function addToDoItem () {
  var toDoItem = document.getElementById('toDoItem').value
  toDoItems.push(toDoItem)
}
```

5) To finish this function off, add another line with `console.log(toDoItems)` (so we can check in our browser console that the array is being updated), and a final line to `return false` out of the function.

```javascript
function addToDoItem () {
  var toDoItem = document.getElementById('toDoItem').value
  toDoItems.push(toDoItem)

  console.log(toDoItems)
  return false
}
```

***
:bulb:

We have to `return false` here because we are going to call this function when we submit the form, and returning `false` to a `form` prevents the default action of the form, which is to reload the page. If we allow the page to reload then our array items will be removed from memory, which we don't want.
***

6) Lastly, we have to wire this function up to the form. Add a new attribute to your `form` tag of `onsubmit` with a value of `return addToDoItem()`.

```html
<form method="post" onsubmit="return addToDoItem()">
  <input id="toDoItem" type="text" placeholder="New to-do item">
  <input type="submit" value="Add">
</form>
```

***
:bulb:

The `onsubmit` attribute takes JavaScript code as it's value, and it executes this code when the form submission event happens. `addToDoItem()` evaluates to `false` as this is the `return` value we gave the function. Once `addToDoItem()` has evaluated as `false` we're just returning it again so it reaches the form element and halts the submission.
***

7) Save the file and open in your browser. Try adding items to the form. You should see the array update in your browser console.

8) Add, commit to *local* and push changes to *remote*:

```bash
git add index.html
git commit -m "add to-do item to array on form submit"
git push
```

:twisted_rightwards_arrows: **Driver and Navigator switch roles**

[Next: Displaying Array Items](https://github.com/MCRcodes/course/blob/master/week3/week3_lesson2_page3.md)