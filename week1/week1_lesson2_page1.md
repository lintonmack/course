Getting started
------
We're going to be using the external stylesheet method to style our HTML so we're going to need to create a CSS file and include it into our HTML files:

1) First create a new file called `style.css` in the same folder as your HTML files.
2) Inside `index.html`, `pricing.html` and `buy.html` add the following before the closing `head` tag:

```html
<link rel="stylesheet" type="text/css" href="style.css">
```

Styling the body tag
------
Everything we see on our HTML page is located inside the body tag. Most browsers - by default - will add a margin to this content. However, we want our HTML elements to touch the edges of the page and therefore we will set the margin to 0:

```css
body {
  margin: 0;
}
```

The browser also sets a default font. We will override this also. Add a new line to the `body` selector with the property `font-family` and the value `Helvetica Neue, Arial, sans-serif`.

***
:bulb:

The `font-family` property can be passed one or many fonts separated by commas. The browser will use the first one it finds on the user's computer (going from left to right). It's good to provide additional fonts for the browser to fall back on, as not everybody will necessary have your first choice installed.
***

