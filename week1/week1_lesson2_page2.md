Header
------
One of the advantages of using semantic HTML elements such as `header` is that because of their unique names, we can style them directly with an element selector. Let's give the header a black background and set it to a height of 50px:

```css
header {
  background-color: black;
  height: 50px;
}
```

Navigation
------
It would look more sleek if our navigation menu was floated on the right hand side of the header. Add a float to the `nav` element:

```css
nav {
  float: right;
}
```

The `nav` element should now be aligned right inside the `header` element.

Navigation menu items
------
We are using an unordered list `ul` inside of our `nav` element to display our navigation links. However, they are being rendered with the browser's default style, which isn't very appealing. 

We can remove the bullet points by setting `list-style-type` to `none`, and we can also set `margin` and `padding` to `0`:

```css
nav > ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}
```

***
:bulb:

`nav > ul` above is an example of specificity in CSS. It is essentially saying "find a `ul` element that is a direct child of `nav` and apply the following properties/values".

This specificity allows us to modify how some HTML elements look on some parts of the webpage/website, whilst maintaining their default (or a different) styles on other parts of the webpage/website.
***

Our menu items are currently sitting underneath each other. This is because, by default, they are displaying in `block` format, which essentially means that they are all 100% wide and therefore push the next item underneath.

We can change the `display` property on each menu item to `inline-block`. This will set the width of the item to wrap the contents (unless you specifically state a width otherwise):

```
nav li {
  display: inline-block;
}
```

The items should now sit side by side. To space them out, on another line add the property `padding` and set it's value to `18px`.

***
:bulb:

Notice with `nav li` we haven't used a `>`. This is because without `>` the browser will look for all elements matching `li` within the `nav` tag. 
***

Link styling
------
Browsers render anchor tags/links by default in a blue colour with an underline. This is considered very much out of fashion in terms of design, so we should change it.

Let's go ahead and change the colour to white. We'll remove the underline too by setting the property `text-decoration` to the value `none`, and let's also bolden the text by setting `font-weight` to `bold`:

```css
nav li > a {
  color: white;
  text-decoration: none;
  font-weight: bold;
}
```

Fixed header
------
You should now have a header with a right-aligned menu bar. It would be a nice feature if the `header` could stay at the top of the page whilst we scroll. To do this we can set it's `position` to `fixed`. `fixed` essentially means "fix this element at this exact point on the page". We have to provide it with `top`, `right`, `bottom` and/or `left`:

```css
header {
  background-color: black;
  height: 50px;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: auto;
}
```

***
:bulb:

`auto` in this scenario basically tells the browser to use all remaining space after the height of the element is taken into account.

E.g. if our `header` is 50px high and our browser is 600px high then `auto` would calculated as 550px by the browser. The browser would then ensure the element was pushed up from the bottom of the window by 550px.
***

One important thing to note is that by making our `header` fixed, we took it outside of the structure of the page (i.e it will now overlap the content at the top). To resolve this, we can set a top margin on the `body` tag equal to the height of the `header`:

```css
body {
  margin: 0;
  margin-top: 50px;
}
```

***
:bulb:

Notice how `margin` is set to `0` then we specifically set just `margin-top` to `50px`. CSS is cascading, which means the browser will set the top, right, bottom and left margins of `body` to `0`, and then when it reaches the next line of CSS it will override the top margin with the new value of `50px`.
***