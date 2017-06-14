Initialising a Git repository
------
To create a Git repository, 'cd' into your project folder (visit-manchester) and type 'git init'. 

Creating a remote
------
Login to GitHub, click + in the navigation bar and select New Repository (both people should do this).

Link the remote repo to your local:
git remote add origin git@github.com:<username>/<repo_name>.git
git push -u origin master

Overriding Bootstrap CSS
------
Firstly, create your own style.css file and include it in your head tags. IMPORTANT We want to override Boostraps's CSS - because CSS is cascading, make sure you place the link tag for your style.css after your Bootstrap CDN link include.

Open up your index.html file in Chrome (download Chrome if you don't already have it installed!!).

Right click on the page and select Inspect. The Chrome developer tools will open.

In the open HTML editor select the nav element. Below in the CSS editor you should see the CSS rules for the element. Copy the selector into your style.css (double click) and add property/value pairs for 'border: 0px;', 'border-radius: 0px;', background-color: #000;' and 'color: #FFF;'. 

In your command line do 'git add style.css' to stage the file to your index, and then do 'git commit -m "Header styling changed"' to commit the staged file to your repository. Then do a 'git push origin master'. Your pair will need to clone down the repository from GitHub ('git clone <url_of_repository>') and then you should swap.

Between you and your pair work to restyle all of the Visit Manchester website. You've already styled the navigation. On the homepage why not try giving the jumbotron a different background color or image? How about giving the background and border colours on the Things To Do page a different colour?

Try as much as you can to make the website your own. Just select every element on the page inside of your developer tools to find out what styles the element is using and then copy that selector and add duplicate rules to override the originals. After ever significant change (e.g. styling an element) you should add, commit and push, then swap driver and navigator roles (VERY IMPORTANT - you should be switching roles every 15 minutes).

Before you both finish, make sure you've both got the same files in your local repository (a.k.a you have pulled from the repo after the last commit, or you were the last person to commit. This will ensure both pairs have the same files on their system.