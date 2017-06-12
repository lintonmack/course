What we're making
------
We're going to make a Visit Manchester website, where people can find out about things to do, places to eat and where to stay in Manchester. It will be responsive (a.k.a will work on desktop, tablet and mobile).

Try and avoid copying and pasting the code - work from the outside in and learn what each element and class attached actually does.

Getting started
------
First `cd` into your `Projects` folder and create a new directory (`mkdir`) called `visit-manchester`. Then `cd` into the new folder and create an **index.html** file (`code index.html`). In the open VS Code editor type `!` followed by `Tab` to populate the DOCTYPE and necessary HTML. Change the title to **Visit Manchester**.

There are also some images that you will need to download and extract into the folder. You can download these [here]().

Including Bootstrap
------
Include the below right before your closing `head` tags:

```html
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">
```

And the following right before your closing `body` tags:

```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.4/jquery.min.js"></script>
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js" integrity="sha384-Tc5IQib027qvyjSMfHjOMaLkfuWVxZxUPnCJA7l2mCWNIpG9mGCD8wGNIcPD7Txa" crossorigin="anonymous"></script>
```

***
:bulb:

We haven't yet seen the `script` tag. This is a way to include JavaScript files into your project. We'll explore it further in later lessons. You'll notice also that we've included jQuery. This is just because Bootstrap's features that utlitise JavaScript are dependent on jQuery (jQuery is a *dependency* of Bootstrap). We'll also explore jQuery in more depth in later lessons.
***

***
:bulb:

You'll notice the above two tags point to absolute URLs. This is because we are including in CSS and JavaScript files remotely from a Content Delivery Network (commonly referred to as a CDN). Content Delivery Networks deliver content to the user from a server close to their geographical location, meaning it reaches the user faster.
***

The container
------
Because we intend on using Bootstrap's grid system to layout our content, it's important that we have a container surrounding it so that our Bootstrap elements are padded and spaced correctly. Add opening and closing `div` tags inside of your `body` tags and give the `div` element a class of `container`:

```html
<body>
  <div class="container">
  </div>
</body>
```

Everything we see on our page from this point will go inside this `div.container` element.

Navigation
------
Navigation bars are lengthy in Bootstrap, but very powerful as they will collapse into a hamburger menu on mobile and tablet. Please type out the below (it's better to work from the outside tags inwards, rather than line by line), paying attention to the comments on what each element does:

```html
<!-- Our main navigation wrapper (using semantic nav element). Sets border and background colour. -->
<nav class="navbar navbar-default">
     <!-- Logo container, and - if on mobile or tablet - hamburger button for dropdown menu -->
     <div class="navbar-header">
          <!-- Hamburger button. data-toggle is the action to perform when clicked and the target is the CSS selector of the element to affect -->
          <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#navbar">
               <!-- Show on screen readers only -->
               <span class="sr-only">Toggle navigation</span>
               <!-- Three icon bars that make up a 'hamburger' -->
               <span class="icon-bar"></span>
               <span class="icon-bar"></span>
               <span class="icon-bar"></span>
          </button>
          <!-- Logo -->
          <a class="navbar-brand" href="index.html">Visit Manchester</a>
     </div>
     <!-- Navigation items. Will be hidden if on mobile or tablet until hamburger is clicked. -->
     <div id="navbar" class="navbar-collapse collapse">
          <ul class="nav navbar-nav">
               <!-- We can set class equal to active on a list item for a darker button -->
               <li class="active"><a href="index.html">Home</a></li>
               <li><a href="thingstodo.html">Things to do</a></li>
               <li><a href="restaurants.html">Restaurants</a></li>
               <li><a href="hotels.html">Hotels</a></li>
          </ul>
     </div>
</nav>
```
Save the above, open your file in your web browser and resize your browser window to different widths to see how the navigation menu responds.