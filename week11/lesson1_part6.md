:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

## Styling

You should now work on making the website more aesthetically pleasing.

You have already specified a `public/` folder where you can store CSS and image files, and you have a `main.hbs` layout file, which encapsulates your templates. 

Try and be creative and move around the existing HTML to make your work your own. Consider adding a navigation bar or menu for accessing Login / Register / Logout links. If HTML/CSS isn't your thing, then by all means bring in Bootstrap, but if you are comfortable then try and do it without Bootstrap. Look at other websites you like and use your Developer Tools to see how they do their CSS.

Be sure to utilise [Google Fonts](https://fonts.google.com/) and [Font Awesome](http://fontawesome.io/). 

[Coolors](https://coolors.co/) and [0to255.com](http://www.0to255.com/) are also very good for colours.

## Passing data to the layout file

When you pass data to a template, it automatically becomes available inside the header. Therefore, if you want current user information to display in the header then you should pass `{ currentUser: req.session.user }` into all of your `res.render` calls as a second argument.