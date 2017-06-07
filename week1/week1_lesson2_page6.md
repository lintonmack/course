Buy Now page
------
Firstly, give the `section` an `id` of `buynow`. In CSS, add padding to the section of 15px. 

List styling
------
Just like we did for the `nav ul` links, we need to remove the standard list styling:

```css
#buynow ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}
```

And now let's set our items to show inline:

```css
#buynow ul > li {
  display: inline-block;
}
```

Lastly, set the image widths so they are all the same:

```css
#buynow li > img {
  width: 250px;
}
```