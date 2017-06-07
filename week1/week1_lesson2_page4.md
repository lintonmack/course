Exercise section
------
First of all, add an `id` of `exercise` to your exercise section.

For our exercise section, we want to have our image on the left hand side **without padding** and our content on the right hand side **with padding**. Because we only want one half to be padded, we can't achieve this by adding `padding` to the `section` itself. Therefore, we will need to nest everything that isn't the image inside a `div` with the class `content`:

```html
<section id="exercise">
  <img src="images/sports.jpg">
  <div class="content">
    <h2>Your perfect exercise companion</h2>
    <p>
      The Granny Smith Watch has built in GPS, is waterproof up to 1 metre and has a built in accelerometer and gyrometer, allowing you to track a multitude of activites.
    </p>
    <p>
      We have a variety of interchangeable sport bands allowing you to work up a sweat in comfort and style. 
    </p>
  </div>
</section>
```

Now we just need to resize our image and pad our content. We'll also add `float: left` to each so they float alongside each other:

```css
#exercise {
  overflow: hidden;
}

#exercise > img {
  width: 50vw;
  float: left;
}

.content {
  width: 50vw;
  padding: 30px;
  float: left;
  box-sizing: border-box; /* ensures box width doesn't get increased by the padding */
}
```

***
:bulb:

Floating an element that is nested inside a parent element will cause the parent element to lose track of the child element, and therefore the parent element's height won't adjust to reflect its contents. A simple hack for this is to add `overflow: hidden;` to the parent container.
***

***
:bulb:

Above we have used a class selector `.content` and we haven't given it any specificity. This is because we will want to use it in other sections so it won't be unique and we need to be able to use it anywhere.
***

Personal assistant section
------
Follow the steps above to style the personal assistant section. It's worth noting also that if two selectors have the same property/value pairs then you can merge the two using commas like so:

```css
#exercise, #assistant {
  overflow: hidden;
}

#exercise > img, #assistant > img {
  width: 50vw;
  float: left;
}
```

This is considered good practice as it cuts down the amount of code, but also makes it easier to significantly modify the website, without having to worry about changing the code in multiple places.

GrannyOS Section
------
For the GrannyOS section let's center the contents, add some `padding` and a `background-color`, and we'll shrink the image too:

```css
#grannyos {
  text-align: center;
  padding: 30px;
  background-color: #deeec3;
}

#grannyos > img {
  width: 250px;
}
```

***
:bulb:

For colours, CSS allows us to use colour names, hex codes (e.g. #deeec3) or rgb/rgba values. You can find hex codes and colour palettes on [Coolors](https://coolors.co). You can also use [0to255](http://www.0to255.com/) to find lighter/darker variations of colours.
***

Footer
------
For the footer, we can just center align and use a grey colour. Again this is a semantic element, and we only have one `footer` on the page, so we can use an element selector:

```css
footer {
  color: #999999;
  text-align: center;
}
```