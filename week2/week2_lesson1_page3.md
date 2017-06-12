Things to do
------
Copy the contents of your **index.html** into a new file called **thingstodo.html**. Remove everything after the closing `nav` tag and before the `hr` tag (so you should just have a navigation bar and a footer). In your navigation bar, make sure the `li` for **Home** does not have the active class, and that **Things to do** does.

Panel
------
Bootstrap's `panel` class gives us a box with a shadow and bottom margin. We can add a dark grey border by adding `panel-default` and some inner padding with a nested element with the `panel-body` class:

```html
<div class="panel panel-default">
    <div class="panel-body">

    </div>
</div>
```

Inside our panel we want 2 columns - one for an image and one for a title and a paragraph. Let's go for a column of 4/12 and a column of 8/12 - both will be 100% wide on tablet and below:

```html
<div class="panel panel-default">
    <div class="panel-body">
        <div class="row">
            <div class="col-md-4">
                
            </div>
            <div class="col-md-8">

            </div>
        </div>
    </div>
</div>
```

In our first column, add an image tag with two classes: `img-responsive` and `img-rounded`:

```html
<img src="images/johnrylands.jpg" alt="The John Rylands Library" class="img-responsive img-rounded">
```

`img-responsive` sets the width to 100%. `img-rounded` rounds the corners of the image.

In our second column add the following:

```
<h3><span class="label label-default">1</span> The John Rylands Library</h3>
<p>Booky.</p>
```

The `label` class gives us a rounded square around the 1 and the `label-default` gives it the colour grey.

Other panels
------
We also want panels for Manchester's other 4 top attractions (in ascending order):

* Science Museum
* Breakout
* Etihad Stadium
* The Manchester Museum

Repeat the above steps for these attractions. There are corresponding images in the images folder.