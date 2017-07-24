:twisted_rightwards_arrows: **No driving/navigating just yet**

## Node.js - Installing on Mac

1. Unfortunately, for Node.js to work on a Mac, we need to have Xcode installed. [Install Xcode from the Mac App Store](install XCode from the App Store).

2. Once Xcode has been installed, we also need to add the Xcode command line tools. Type the following in Terminal:

```bash
xcode-select --install
``` 

3. We're going to install Node.js using the package manager *Homebrew*. Visit [HomeBrew](https://brew.sh/) and follow instructions under *Install Homebrew*.

***
:bulb:

Homebrew is a package manager for OS X that allows us to easily install new commands in the command line with minimal configuration. We're going to install Node.js with Homebrew, because it does all the hard work for us.
***

4. In the command line run:

```
brew install node
```

5. Then check to see you have Node.js and npm installed by typing:

```
node -v
npm -v
```

If installation is successful then these commands should both output version numbers.

## Node.js - Installing on Linux

Fortunately for Linux users running on Ubuntu (or a Ubuntu based OS), installing Node.js should be fairly straightforward, as Ubuntu already has a package manager - *apt* - built in. Just enter the following commands:

```
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
sudo apt-get install -y build-essential
sudo apt-get install -y nodejs
```

Then check to see you have Node.js and npm installed by typing:

```
node -v
npm -v
```

## Node.js - Installing on Windows

Download and run the v6... LTS executable available from the [Node.js website](https://nodejs.org/en/).

Then check to see you have Node.js and npm installed by typing:

```
node -v
npm -v
```

[Continue to part 2](lesson1_part2.md)