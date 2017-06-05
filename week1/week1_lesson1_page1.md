What you'll be making
------
We're going to make a product website for the completely fictional **Granny Smith Watch**. We'll cover the basic HTML needed, then in the CSS chapter we'll go on to style the page.
 
Creating a project folder
------
It's good practice to give each project its own folder. For the duration of the course we will assume that every project folder you create is stored in a parent folder called **Projects**, located in your home folder. Let's go ahead and create a **granny-smith-watch** folder in the command line:

```bash
cd ~/Projects
mkdir granny-smith-watch
cd granny-smith-watch
```

***
:bulb: 

The `~` symbol, otherwise known as a tilda, is the location of your computer user's home directory.
***

Creating our index.html file
------
We've created our project folder. Now lets create our `index.html` file.

1. In the command line, create a new file called **index.html** and open it in VS Code: `code index.html`.
2. Save the file (Mac: `⌘S`, Linux: `Ctrl-S`).
3. Open **index.html** in Chrome through the command line: `open index.html`. A new Chrome tab (or window) should open with a blank page.

Every time you make a change to index.html in VS Code, save the file and then refresh your Chrome browser to see the changes.

Basic HTML structure
------
As you should now know, every HTML file should have a single `<!DOCTYPE html>` tag, as well as opening and closing `<html>`, `<head>` and `<body>` tags. We can get VS Code to pre-populate this basic structure for us by typing `!` followed by `Tab` in our open `index.html` file:

![Prepopulate HTML Structure](https://mcr.codes/wp-content/uploads/2017/06/vscode-doctype.gif)

***
:bulb: 

You may notice that VS Code has also added some `<meta>` tags. These aren't necessary, but do provide helpful instructions to smartphone browsers and Internet Explorer on how to render the page correctly, so we can keep these here.
***

Change the title from `Untitled` to `Granny Smith Watch`.

Page structure
------
We have our project folder set up, with an `index.html` file that's ready to add content to. Let's lay out some sections. For the home page we'll have a header, 4 sections and a footer:

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Granny Smith Watch</title>
</head>
<body>
  <header>

  </header>
  <section>

  </section>
  <section>

  </section>
  <section>

  </section>
  <section>

  </section>
  <footer>
    
  </footer>
</body>
</html>
```

Header
------
The first thing we should do is create a header for our page. This will have our logo and a navigation menu.

Firstly, let's add our logo. It should go to the home page when clicked, so we'll wrap it in anchor (`<a>`) tags. We'll also give our `<img>` tag an `alt` attribute with the website title:

```
  <header>
    <a href="index.html"><img src="images/logo.png" alt="Granny Smith Watch"></a>
  </header>
```

You won't be able to see the logo text, as the logo is designed for a black background, and it will be quite large. Don't worry about this for now - we will be making everything look nice when we come to cover CSS!

Now let's add our navigation links. We'll use the semantic `<nav>` tags to tell anybody viewing our code that this is a navigation component, and we'll nest an unordered list (`<ul>`) inside for our links:

```
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
```

Save the file and refresh the page in Chrome. You should see:

![Header](https://mcr.codes/wp-content/uploads/2017/06/header.png)

Section
------
We use the semantic `<section>` tag to tell the person reading our code that the enclosed contents is a section of the page. Let's add some heading text and a paragraph to the first set of `<section>` tags:

```
  <section>
    <h1>Introducing the Granny Smith Watch</h1>
    <p>
      The must have accessory for work and play.
    </p>
  </section>
```

![Section](https://mcr.codes/wp-content/uploads/2017/06/section.png)

We'll be setting the height of this section, adding a background image and laying out these elements in the CSS section later on.

Let's go ahead and populate our other sections. We'll add some images also (the image tags are in different places, as we will be aligning them left and right in the CSS chapter):

```
  <section>
    <h1>Introducing the Granny Smith Watch</h1>
    <p>
      The must have accessory for work and play.
    </p>
  </section>
  <section id="moreinfo">
    <img src="images/sports.jpg">
    <h2>Your perfect exercise companion</h2>
    <p>
      The Granny Smith Watch has built in GPS, is waterproof up to 1 metre and has a built in accelerometer and gyrometer, allowing you to track a multitude of activites.
    </p>
    <p>
      We have a variety of interchangeable sport bands allowing you to work up a sweat in comfort and style. 
    </p>
  </section>
  <section>
    <h2>Your personal assistant</h2>
    <p>
      Make day-to-day life easier with the Granny Smith Watch. Instantly set reminders, get public transport information, view boarding passes and pay in-store.
    </p>
    <img src="images/work.jpg">
  </section>
  <section>
    <img src="images/grannyos.png">
    <h2>GrannyOS</h2>
    <p>
      GrannyOS is the most powerful smartwatch OS. Built-in apps include GrannyMaps, GrannyWallet and GrannyMail. The Granny Smith Market Stall has thousands of applications available including games, banking and transport. The Granny Smith watch also features the Granny Smith voice assistant.
    </p>
  </section>
```

Footer
------
For our footer we'll just add a paragraph with a copyright notice:

```
  <footer>
    <p>
      &copy; Granny Smith 2017
    </p>
  </footer>
```

***
:bulb:

`&copy;` is a HTML symbol for the copyright &copy;. You can find more [here](http://www.ascii.cl/htmlcodes.htm).
***

Your finished home page should look something like this:

![Home page](https://mcr.codes/wp-content/uploads/2017/06/finishedpage.png)

***
:bulb: 

Notice how the above code examples are indented a.k.a we split everything onto a new line and we indent 1 tab. 

Anything enclosed inside opening and closing tags should be indented one tab. If there are opening/closing tags nested inside other opening/closing tags (we refer to as a child tag) then we should indent the child tag's contents one further.

The main exception to this rule is that you don't usually need to indent if the tag's contents are just plain text (a.k.a no nested HTML tags) e.g. `<title>Granny Smith Watch</title>`.

**Indentation is extremely important**, as it makes your code easier to read. Please get into the habit of doing it - it will be brought up in code reviews.
***