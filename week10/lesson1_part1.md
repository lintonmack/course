## User Authentication

We're going to be building a social network, starting with a user registration and login system.

## Installing MongoDB

### Mac OS X

Install MongoDB with Homebrew:

```bash
brew update
brew install mongodb
```

Create the `/data/db` directory that MongoDB will write to. You'll need to use `sudo` as `/` is the root of your hard drive:

```bash
sudo mkdir -p /data/db
```

You'll need to change the `/data/db` directory's owner to your logged in user. First find out your username:

```bash
id -un
```

Then change the owner with `chown` (replacing `<username>` with your username):

```
sudo chown -R <username> /data/db
```

### Ubuntu (and Ubuntu-based distributions)

Add the MongoDB package signature to apt package manager:

```bash
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 0C49F3730359A14518585931BC711F9BA15703C6
```

If you don't know your Ubuntu version:

```bash
lsb_release -a
```

Add the MongoDB repository to the apt package manager:

**Ubuntu 16.04 and above**

```bash
echo "deb [ arch=amd64,arm64 ] http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list
```

**Ubuntu 14.04**

```bash
echo "deb [ arch=amd64 ] http://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list
```

**Ubuntu 12.04**

```bash
echo "deb [ arch=amd64 ] http://repo.mongodb.org/apt/ubuntu precise/mongodb-org/3.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list
```

Update apt to reflect the changes to its repositories/signatures:

```bash
sudo apt-get update
```

Install MongoDB:

```bash
sudo apt-get install -y mongodb-org
```

### Windows

See sections on MongoDB docs:

[Get MongoDB Community Edition](https://docs.mongodb.com/master/tutorial/install-mongodb-on-windows/#get-mongodb-community-edition)
[Install MongoDB Community Edition](https://docs.mongodb.com/master/tutorial/install-mongodb-on-windows/#install-mongodb-community-edition)

## Starting the MongoDB service

We need to keep the MongoDB service running in the background always so it's always available for our applications to access. Therefore, after running the commands below, ensure the terminal running the process is left open (minimising the window or moving ot over to a different workspace is recommended so you don't accidentally close it).

### Mac OS X

```bash
mongod
```

Ctrl-C on the open terminal to kill the process.

### Ubuntu

Start the service: 

```bash
sudo service mongod start
```

Stop the service:

```bash
sudo service mongod stop
```

### Windows

See [Run MongoDB Community Edition](https://docs.mongodb.com/master/tutorial/install-mongodb-on-windows/#run-mongodb-community-edition) on MongoDB Docs.

[Continue to part 2](lesson1_part2.md)