Pricing
------
Firstly, in **pricing.html** give your `section` padding of 15px (hint: you'll need to assign it an id and reference to it in your CSS file with the appropriate selector).

Pricing table
------
Let's start by setting our `table`'s `width` to `100%` so it fills the `section`:

```css
table {
  width: 100%;
}
```

And now let's resize our images to 100%:

```css
table > img {
  width: 100%;
}
```

This will ensure our images get bigger and smaller when the window resizes (our page will be responsive).

Now let's style our table cells/`td`. We'll give some padding and a border:

```css
table td {
  padding: 10px;
  border: 1px solid #dadada;
}
```

Now we have borders, but they aren't touching. We can fix this by setting `border-collapse` to `collapse` on the `table`:

```css
table {
  width: 100%;
  border-collapse: collapse;
}
```