Jumbotron
------
The jumbotron is a component designed to grab the user's attention. Let's add one after our closing `nav` tag:

```html
<div class="jumbotron">
    <h1>Things to do in Manchester</h1>
    <p>Manchester is full of great things to do.</p>
    <p><a class="btn btn-primary btn-lg" href="thingstodo.html">The Top 10 »</a></p>
</div>
```

Columns
------
After our closing `div` tag for our jumbotron, we'll add 3 columns. Our columns need to be nested directly inside a `row`:

```html
<div class="row">
    <div class="col-md-4">

    </div>
    <div class="col-md-4">
      
    </div>
    <div class="col-md-4">
      
    </div>
</div>
```

The `col-md-4` means "take up 4 of 12 available columns" and because it's `md` it means that the column will fill 100% width on mobile (`xs`) and tablets (`sm`).

Now lets add some content:

```html
<div class="row">
    <div class="col-md-4">
        <h2>Restaurants</h2>
        <p>Manchester has many different restaurants and cuisines to choose from.</p>
        <p><a class="btn btn-default" href="restaurants.html">View restaurants »</a></p>
    </div>
    <div class="col-md-4">
        <h2>Hotels</h2>
        <p>Kick back and relax in luxury in Manchester's amazing hotels.</p>
        <p><a class="btn btn-default" href="hotels.html">View hotels »</a></p>  
    </div>
    <div class="col-md-4">
        <h2>Things to do</h2>
        <p>Manchester is full of great things to do.</p>
        <p><a class="btn btn-default" href="thingstodo.html">View attractions »</a></p>  
    </div>
</div>
```

Footer
------
For the footer we'll just add a horizontal rule (`<hr>`) and a paragraph after our columns above:

```html
<hr>
<footer>
    <p>&copy; Visit Manchester 2017</p>
</footer>
```

That's a basic homepage finished. Bootstrap allows us to create responsive websites much quicker than we'd be able to do without.