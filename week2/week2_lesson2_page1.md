Initialising a Git repository - only one person to do this!
------
To create a Git repository, `cd` into your project folder (visit-manchester) and type `git init`. 

Set up SSH keys for GitHub - Both people need to do this
------
To push and pull from GitHub (our remote) you will need to generate an SSH key on your machine and link it to your GitHub account. GitHub have a detailed guide on how to do this [here](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/). Be sure to click the link on the last step to link your account.

Creating a remote - only the person who initialised the repo to do this
------
Login to GitHub, click + in the navigation bar and select New Repository (both people should do this).

Link the remote repo to your local:
```
git remote add origin git@github.com:<username>/<repo_name>.git
git push -u origin master
```

Adding a collaborator - only the person who initialised the repo to do this
------
The person who isn't the owner of the repository will need to be added as a collaborator. On your repo page on GitHub, click Settings then Collaborators and search for your pair and click Add collaborator. Your pair will need to check their email inbox to accept the invitation before they can contribute to the repository.

Overriding Bootstrap CSS - only the person who initialised the repo to do this
------
Firstly, create your own **style.css** file and include it in your head tags. **IMPORTANT** We want to override Boostraps`s CSS - because CSS is cascading, make sure you place the link tag for your **style.css** after your Bootstrap CDN link include.

Open up your **index.html** file in Chrome (download Chrome if you don`t already have it installed!!).

Right click on the page and select Inspect. The Chrome developer tools will open.

In the open HTML editor select the nav element (`<nav class="navbar navbar-default">`). Below in the CSS editor you should see the CSS rules for the element. Here you can click the checkboxes next to each property/value pair to see what effect it has on the page. Copy the selector into your **style.css** (double click) and add property/value pairs for `border: 0px;`, `border-radius: 0px;`, `background-color: #000;` and `color: #FFF;`. 

Reflecting the change in your repository
------
In your command line do `git add style.css` to sstage the file to your index, and then do `git commit -m "Header styling changed"` to commit the staged file to your repository. Then do a `git push origin master`. Your pair will need to clone down the repository from GitHub (`git clone <url_of_repository>`) and then you should swap.

Pairing
------
Between you and your pair work to restyle all of the Visit Manchester website. Only one of you should be working on the website at any given time (the driver). The other pair (the navigator) should be reading the walkthroughs and telling the driver what to do. You`ve already styled the navigation. On the homepage why not try giving the jumbotron a different background color or image? How about giving the background and border colours on the Things To Do page a different colour?

Try as much as you can to make the website your own. Just select every element on the page inside of your developer tools to find out what styles the element is using and then copy that selector and add duplicate rules to override the originals. After ever significant change (e.g. styling an element) you should add, commit and push, then swap driver and navigator roles (VERY IMPORTANT - you should be switching roles every 15 minutes).

Swapping after the initial clone
------
After the initial `git clone` all future changes pushed up to the remote will need to be pulled down with `git pull origin master`. Your pair will then make a change and add, commit and push back up.

Finishing up
------
Before you both finish, make sure you`ve both got the same files in your local repository (a.k.a you have pulled from the repo after the last commit, or you were the last person to commit. This will ensure both pairs have the same files on their system.
