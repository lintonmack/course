Landing
------
Now we can start to work on styling our sections. We use multiple `section` tags throughout the website, yet we will want to style each `section` differently, and therefore will need to avoid styling them using an element selector. Instead - because of their unique nature - we will use the ID selector. 

Let's add a unique `id` attribute with the value `landing` to the first `section` in our **index.html** file:

```html
<section id="landing">
  <h1>Introducing the Granny Smith Watch</h1>
  <p>
    The must have accessory for work and play.
  </p>
</section>

And now in CSS, let's center align all text in our section, and we'll give it some padding too:

```css
#landing {
  text-align: center;
  padding: 50px;
}
```

Now to make our `section` really stand out let's give it a height and add a background image:

```css
#landing {
  text-align: center;
  padding: 50px;
  height: 50vh;
  background-image: url(images/watches.jpg);
  background-size: contain;
  background-position: center 150px;
  background-repeat: no-repeat;
}
```

***
:bulb:

`vh` is short for viewport height. Each 1/100th of a browser window's height is equal to `1vh` so we're just saying "set the height to half the height of the browser window.
***

***
:bulb:

`background-size: contain` means: scale the background image to the biggest height and width (whilst maintaining aspect ratio) to fit the surrounding container.

`background-position: center 150px` means: center the background inside the container and push it down 150px (so our text in the `section` isn't overlapping the background image.
***