Restaurants
------
Just as before, copy the contents of your **thingstodo.html** or **index.html** file to a new file called **restaurants.html**. Remove everything aside from the header and footer, and change the active menu item to **Restaurants**. 

Carousel
------
Bootstrap's carousel adds a left/right content gallery to the page. Read about how it works [here](http://getbootstrap.com/javascript/#carousel).

Let's add one with some restaurants:

```html
<div id="carousel-restaurants" class="carousel slide" data-ride="carousel">
    <!-- Indicators -->
    <ol class="carousel-indicators">
        <li data-target="#carousel-restaurants" data-slide-to="0" class="active"></li>
        <li data-target="#carousel-restaurants" data-slide-to="1"></li>
        <li data-target="#carousel-restaurants" data-slide-to="2"></li>
    </ol>

    <!-- Wrapper for slides -->
    <div class="carousel-inner">
        <div class="item active">
            <img src="images/iberica.jpg" alt="Iberica">
            <div class="carousel-caption">
                <h3>Iberica</h3>
                <p>Airy space with long bar and mezzanine open kitchen, for classic and modern Spanish-Asturian dishes.</p>
            </div>
        </div>
        <div class="item">
            <img src="images/hawksmoor.jpg" alt="Hawksmoor">
            <div class="carousel-caption">
              <h3>Hawksmoor</h3>
              <p>'A place to blur day with night over cocktails and the country's finest meat' Time Out Manchester</p>
            </div>
        </div>
        <div class="item">
            <img src="images/tattu.jpg" alt="Tattu">
            <div class="carousel-caption">
                <h3>Tattu</h3>
                <p>Modern Chinese cuisine and cocktails in sophisticated, dark wood bar/restaurant with carved screens.</p>
            </div>
        </div>
    </div>

    <!-- Controls -->
    <a class="left carousel-control" href="#carousel-restaurants" data-slide="prev">
        <span class="glyphicon glyphicon-chevron-left"></span>
    </a>
    <a class="right carousel-control" href="#carousel-restaurants" data-slide="next">
        <span class="glyphicon glyphicon-chevron-right"></span>
    </a>
</div>
```

Notice we have the `data-` attributes again? Bootstrap's JavaScript hooks events on the page to these attributes e.g. when it sees `data-ride="carousel"` it knows the `div` with that attribute is a carousel container. It knows that when an attribute with `data-slide-to="0"` is clicked, that the carousel should go to the first slide, and the `data-target` will tell it what carousel to navigate.

Wrapping up
------
By now you've been able to practise the grid system, as well as some of Bootstrap's CSS and Components. Go ahead and finish the website by making **hotels.html**. Use the 3 other pages to help you structure, or look at Bootstrap's documentation for more ideas:

[CSS](http://getbootstrap.com/css/)
[Components](http://getbootstrap.com/components/)