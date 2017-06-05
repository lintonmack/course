Pricing
------
For the pricing page, we'll be using a table to layout comparison information for 2 differing Granny Smith watches. You'll need to create a new file called `pricing.html` in the same folder as your `index.html` file.

Page structure
------
We want the HTML structure, the header and the footer to remain the same as our home page. Therefore, you can copy and paste the contents of your `index.html` file and remove all of the `<section>` tags. We'll also add ` | Pricing` to our `<title>` tag:

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Granny Smith Watch | Pricing</title>
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
  <footer>
    <p>
      &copy; Granny Smith 2017
    </p>
  </footer>
</body>
</html>
```

Pricing section
------
Our pricing page will only have one section, which will contain the comparison table. Add a pair of opening and closing `<section>` tags on a new line after the closing `<header>` tag. We'll also add a heading for the page:

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Granny Smith Watch | Pricing</title>
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
    <h1>Pricing</h1>
  </section>
  <footer>
    <p>
      &copy; Granny Smith 2017
    </p>
  </footer>
</body>
</html>
```

Table
------
Our table will have 2 columns. The table headings will be the watch versions, with the following rows containing some product information.

Firstly lets enter our `<table>` tags:

```
  <section>
    <h1>Pricing</h1>
    <table>
      
    </table>
  </section>
```

Next we'll add a row to our table:

```
    <table>
      <tr>
        
      </tr>
    </table>
```

And then we'll add three table heading (`<th>`) columns (we'll keep the first one empty as this will be the column for our product attribute titles):

```
    <table>
      <tr>
        <th></th>
        <th>Watch 1</th>
        <th>Watch 2</th>
      </tr>
    </table>
```

Your table should look like this:

![Table](https://mcr.codes/wp-content/uploads/2017/06/table.png)

Lets go ahead and add another row with 3 columns. We'll add in product images:

```
    <table>
      <tr>
        <th></th>
        <th>Watch 1</th>
        <th>Watch 2</th>
      </tr>
      <tr>
        <td>Image</td>
        <td><img src="images/watch1.png" alt="Granny Smith Watch 1"></td>
        <td><img src="images/watch2.png" alt="Granny Smith Watch 2"></td>
      </tr>
    </table>
```

![Table with images](https://mcr.codes/wp-content/uploads/2017/06/tablewimages.png)

Now we'll add some more columns with some features:

```
    <table>
      <tr>
        <th></th>
        <th>Watch 1</th>
        <th>Watch 2</th>
      </tr>
      <tr>
        <td>Image</td>
        <td><img src="images/watch1.png" alt="Granny Smith Watch 1"></td>
        <td><img src="images/watch2.png" alt="Granny Smith Watch 2"></td>
      </tr>
      <tr>
        <td>Battery Life</td>
        <td>1 hour</td>
        <td>1.5 hours</td>
      </tr>
      <tr>
        <td>Storage</td>
        <td>64 MB</td>
        <td>128 MB</td>        
      </tr>
      <tr>
        <td>WiFi</td>
        <td colspan="2">Yes</td>
      </tr>
      <tr>
        <td>Bluetooth</td>
        <td>No</td>
        <td>Yes</td>
      </tr>
      <tr>
        <td></td>
        <td>£999</td>
        <td>£1,299</td>
      </tr>
    </table>
```

***
:bulb:

Notice on the WiFi row we have only 2 `<td>` tags, and the second one has an attribute `colspan` with a value of `2`. This is essentially saying: make this column span 2 columns. In our example, it does appear as though it is still one column, but later on when we centre the contents of the column, the text will sit across the two.
***

Your finished section should look something like this:

![Pricing section](https://mcr.codes/wp-content/uploads/2017/06/table-complete.png) 