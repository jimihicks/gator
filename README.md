# gator

local server to gather rss feeds to view your favorite blogs recent posts!

## Prereqs

You have install go and postgressql to run this locally. 

[install go](https://go.dev/doc/install)

install postgres on macOS
```sh
brew install postgresql@15
```

install on linux/WSL. Here are the [microsoft docs](https://learn.microsoft.com/en-us/windows/wsl/tutorials/wsl-database#install-postgresql)

```sh
sudo apt update
sudo apt install postgresql postgresql-contrib
```

for linux you need a password DON'T FORGET

```sh
sudo passwd postgres
```

check to make sure it's installed.

```sh
psql --version
```

start the postgres server in the background.
mac: 
```sh
brew services start postgresql@15
```
linux: 
```sh
sudo service postgresql start
```

Now you can install gator 
```sh
go install github.com/JimiHicks/gator
```

You can now use multiple different commands, I would recommend by registering and logging in on a user.

```sh
gator register <user name>
gator login <user name>
```
You can confirm you are logged by checkings users

```sh
gator users
```

Now time to add a feed, let's say you wanted to follow hacker news 
```sh
gator "Hacker news" "https://news.ycombinator.com/rss"
```

this command has two arguments <name of blog> <url>

check to make sure it was added. 

```sh
gator feeds
``` 

When that looks good you will now open a second terminal and run 
```sh 
gator agg 15m
```

agg takes a time argument, you can set it to anything really but you don't want to go crazy sending request. This grabs all the recent post from the feeds for you to look at, you'll see a message telling you it was successful. 

```
2025/02/14 13:32:42 Found a feed to fetch!
2025/02/14 13:32:43 Feed boot dev collected, 371 posts found
```

Go back to your other terminal and use the "browse" command.
```sh
gator browse
```
you'll see a description, plus a link to the post! 
