Shop
------
The last page will just be a page with all products and accessories, and their prices. We will display these in an unordered list, which we can style into a grid with CSS later on.

Page structure
------
Just like with our Pricing page, copy and paste the contents, remove all of the sections, amend the title and add an empty `<section>` opening and closing tags:

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Granny Smith Watch | Accessories</title>
</head>
<body>
  <header>
    <a href="index.html"><img src="images/logo.png" alt="Granny Smith Watch"></a>
    <nav>
      <ul>
        <li><a href="index.html">Home</a></li>
        <li><a href="pricing.html">Pricing</a></li>
        <li><a href="buy.html">Buy Now</a></li>
      </ul>
    </nav>
  </header>
  <section>

  </section>
  <footer>
    <p>
      &copy; Granny Smith 2017
    </p>
  </footer>
</body>
</html>
```

Product
------
Let's add a heading and our first product:

```
  <section>
    <h1>Shop</h1>
    <ul>
      <li>
        <img src="images/watch1.png" alt="Watch 1">
        <h3>Watch 1</h3>
        £999
      </li>
    </ul>
  </section>
```

***
:bulb:

Notice that we don't explicitly use a line break after the image or the `<h3>` tag. This is because the `<h3>` tag is displayed as a block by default. This simply means that it is surrounded by a 100% width invisible box, meaning any contents above is pushed over, and any contents below is pushed under.
***

![Product](https://mcr.codes/wp-content/uploads/2017/06/product.png)

Finishing off
------
To finish off, let's just add a few more products:

```
  <section>
    <h1>Shop</h1>
    <ul>
      <li>
        <img src="images/watch1.png" alt="Watch 1">
        <h3>Watch 1</h3>
        £999
      </li>
      <li>
        <img src="images/watch2.png" alt="Watch 2">
        <h3>Watch 2</h3>
        £1299
      </li>
      <li>
        <img src="images/accessory_charger.png" alt="Charging Stand">
        <h3>Charging Stand</h3>
        £99
      </li>
      <li>
        <img src="images/accessory_frames.png" alt="Colour Frame">
        <h3>Case</h3>
        £1299
      </li>
      <li>
        <img src="images/accessory_stands.png" alt="Presentation Stand">
        <h3>Display Stand</h3>
        £49
      </li>
      <li>
        <img src="images/accessory_straps.png" alt="Watch Strap">
        <h3>Colour Strap</h3>
        £129
      </li>
    </ul>
  </section>
```

Your finished page will look something like this:

![Products page](https://mcr.codes/wp-content/uploads/2017/06/finished-products.jpg)

Finished
------
That's the end of the HTML section. You should now be able to create a basic website with multiple pages, headings, links, images, lists, tables and semantic elements. 

In the next chapter we go on to cover CSS. We will completely transform the presentation of the website so it looks modern and responsive.