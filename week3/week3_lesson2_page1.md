# ToDo List

What we will be making
------
We will create a todo list which we can add items to.

For this walkthrough, each person in the pair/group of three will have their own remote (GitHub repository).

Preparation - everybody to do this
------
In the command line, change directory into your **Projects** folder and create a new folder called **toDoList**.  

Change directory into this folder and initialise a local Git repository (hint: `git init`).

On GitHub, add a new repository (the + icon). Give your repository the same name as your folder (toDoList). **Don't** tick the checkbox for "Initialize this repository with a README". Click **Create repository**.

Now you need to link your *local* repository to your *remote* repository (replacing `<username>` with your username):
```bash
git remote add origin git+ssh://git@github.com/<username>/toDoList.git
```

Verify your remote is set up correctly with `git remote -v`.

:twisted_rightwards_arrows: **Time to pair. Choose between you who is to be driver and navigator first. The person driving shouldn't need to look at the walkthrough - it is the job of the navigator to instruct the driver as to what to do!**

Create the index.html file
------
1) Create an **index.html** file (in the command line with `code`), save the file, and populate the basic HTML structure (`!` then `Tab`). 

2) Inside your `body` tags, add a pair of opening and closing `script` tags. 

3) Give the opening tag an attribute of `type` with the value `text/javascript`.

You should have the following:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
</head>
<body>
  <script type="text/javascript">

  </script>
</body>
</html>
```

4) Now we want to take the **index.html** file from our *working tree* and *stage* it to our *index*: 
```
git add index.html
```

5) Now **commit** the changes to the *local* repository: `git commit -m "initial commit"` (*initial commit* is a common first commit message). 

6) Finally, push the changes to your *remote*. As this is your first commit you have to tell GitHub which branch you want to push up. You should be working on **master** so you can set the upstream to this on your first push: 
```
git push -u origin master
```

***
:bulb:

The `-u` set's the upstream to `origin master`. In future you can just use `git push` as you've already set the upstream.
***

:twisted_rightwards_arrows: **Driver and Navigator switch roles**

Partner pulls
------
1) Firstly the person who is now driving will need to pull their partner's changes. To do this, they will need to add their partner's GitHub repo as a *remote* (replacing `<partersName>` with your partner's name/nickname (one word!!)):
```
git remote add <partnersName> git+ssh://git@github.com/<username>/toDoList.git
```

2) Now do `git pull <partnersName> master` to pull from your partner's master branch.

HTML Forms
------
We're going to handle adding, removing and displaying of to-do items inside the document (no prompts or alerts). To do this we need to create a HTML form. A form usually comprises of text inputs, checkboxes, dropdowns and buttons (which usually submit the form).

1) Inside the `body` tags, before the opening/closing `script` tags, add a new pair of opening and closing `form` tags. Give the opening `form` tag an attribute of `method` with the value `post`.

2) Inside the `form` tags - on a new line - create an `input` tag. This tag is self-closing so no closing tag is required. Give it an `id` attribute with the value `toDoItem`, a `type` attribute with the value `text` and a `placeholder` attribute with the value `New to-do item`.

3) Still inside the `form` tag, after the `input` tag, add another `input` tag. This input will be our submit button. Give it a `type` attribute with the value `submit` and a `value` attribute with the value `Add`.

4) Save the file and open it up in your browser. You should see:

![Add to-do item form](https://mcr.codes/wp-content/uploads/2017/06/addToDo.png)

```html
<form method="post">
  <input id="toDoItem" type="text" placeholder="New to-do item">
  <input type="submit" value="Add">
</form>
```

5) Stage your changes: 
```
git add index.html
```

6) Commit to local repository: 
```
git commit -m "created form for adding to-do items"
```

7) Now you'll need to set the upstream origin to your *remote* repository, as you pulled down from your partner's previously: 
```
git push -u origin master
```

:twisted_rightwards_arrows: **Driver and Navigator switch roles**

[Next: Handling Form Input](https://github.com/MCRcodes/course/blob/master/week3/week3_lesson2_page2.md)