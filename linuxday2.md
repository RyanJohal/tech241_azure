# Commands
| Command   | Description                                                        |
|-----------|--------------------------------------------------------------------|
| `ls`      | Lists files and directories in the current directory.              |
| `cd`      | Changes the current directory.                                     |
| `pwd`     | Prints the current working directory.                              |
| `mkdir`   | Creates a new directory.                                           |
| `rm`      | Removes files and directories.                                     |
| `cp`      | Copies files and directories.                                      |
| `mv`      | Moves or renames files and directories.                            |
| `cat`     | Concatenates and displays the contents of files.                   |
| `grep`    | Searches for patterns in files.                                    |
| `chmod`   | Changes permissions of files and directories.                      |
| `chown`   | Changes the owner of files and directories.                        |
| `chgrp`   | Changes the group ownership of files and directories.              |
| `ssh`     | Connects to a remote server using the Secure Shell (SSH) protocol. |
| `ps`      | Lists currently running processes.                                 |
| `sudo`    | Executes a command with superuser (administrative) privileges.     |
| `history` | Lists the command history.                                         |
| `exit`    | Exits the current shell or terminal.                               |
| `uname`   | Prints system information.                                         |
| `nano`    | A text editor                                                      |
| `touch`   | Creates an empty file                                              |
| `printenv`| Prints the enviroment variables                                    |
| `echo`    | Prints a file or string                                            |
| `export`  | Creates an enviroment variable                                     |
| `source`  | Used to reload the .bashrc file                                    | 
|cat file   | grep word - Shows all lines with word in existing file


sudo apt install tree - install file tree


sudo apt update -y update all sources -y yes to everything


cp file name new file name - copy file


mv file name ~ - Move file to home directory 


rm -r Remove everything in folder recursive


VARIABLENAME=variablevalue - Make standard variable


export VARIABLENAME=variablevalue - make environment variable


printenv shows all environment variables


.bashrc - make environment variable in this folder to make it persistent


ps - show user process


ps aux - show all processes in detail

rm -rf <file_name>              To delete the named file/folder forcefully and recursively.

# nginx script
### !/bin/bash


### update
sudo apt update -y


### upgrade
sudo apt upgrade -y


### install nginx
sudo apt install nginx -y


### restart nginx
sudo systemctl restart nginx


### enable nginx - will auto start on reboot
sudo systemctl enable nginx


# Access sparta app via node.js
 ### Steps to access the Sparta_App using nodejs #####

1. curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
2. To install node.js on your local Ubuntu Linux machine - sudo apt install nodejs -y 
3. pm helps run apps in the background (PM2 is an advanced process manager for running Node.js applications. That provides an easier option to automate a Node.js application.) - sudo npm install pm2 -y
4. cd tech241_sparta_app/
5. save any specified packages into dependencies by default - npm install
node app.js                         Node.js is a platform for building fast and scalable server applications using JavaScript. Node.js is the runtime and npm is the Package Manager for Node.js modules
1. Go to azure networking and add port 3000 and TCP so that you can access the sparta_app.
2. ctrl C exit securely
ctrl  z                        is used to suspend a process. (This means that the program or command you are running will be temporarily halted and put in the background, taking up no resources. This can be useful if you need to free up RAM or CPU cycles for other tasks.)


ps aux                          To monitor processes running on your Linux system.


npm start                       To start the process again




kill -1 <PID>                   To kill process, go slow first.

kill <PID>                      To kill process forcefully

kill -9 <PID>                   To kill with brute force


### ctrl c is used to kill a process. It terminates your program.

### ctrl z is used to pause the process. It will not terminate your program, it will keep your program in background. You can restart your program from that point where you used ctrl z.


 # Inside database vm
 1. Update - sudo apt update -y
 2. Upgrade - sudo apt upgrade -y
 3. wget -qO - https://www.mongodb.org/static/pgp/server-3.2.asc | sudo apt-key add -
 4. echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list
 5. sudo apt update -y
 6. sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20
 7. change bind IP to 0.0.0.0 - sudo nano /etc/mongod.conf
 8. Check changes - cat /etc/mongod.conf
 9.  sudo systemctl status mongod






# Connect VMs
1. export DB_HOST=mongodb://<IP-ADDRESS>:27017/posts
2. Add import rule to allow port 27017
3. npm start
4. npm install
<<<<<<< HEAD

# Starting sparta app with script
Installing nginx, access node js and installing it, creating env variable to connect to db vm, using git clone to download app folder and then starting app within that folder.
```linux
#!/bin/bash


# update
sudo apt update -y


# upgrade
sudo apt upgrade -y


# install nginx
sudo apt install nginx -y


# enable nginx
sudo systemctl enable nginx


# installing sed
sudo apt install sed


# setup nginx as a reverse proxy
sudo sed -i 's@try_files .*;@proxy_pass http://localhost:3000;@' /etc/nginx/sites-available/default


# restart nginx again
sudo systemctl restart nginx


# get from url needed version of node
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -


# install nodejs
sudo apt install -y nodejs


#installing pm2 that helps run apps in the background
sudo npm install pm2 -g


# getting app folder to the VM
git clone https://github.com/RyanJohal/tech241_sparta_app repo


#getting inside app folder
cd repo/app


#Creating DB_HOST env variable
export DB_HOST=mongodb://172.31.38.156:27017/posts


# installing the app
npm install


# populates database in case there are no posts
node seeds/seed.js


# kills previous background processes
pm2 kill


# starting the app
pm2 start app.js  

```



```
# To run the app in the background with &
nohup npm start &
# nohup prevents the process from being terminated when terminal session ends, doesn't engage terminal, it always changes process ID so you need to kill previous command to run it again. Doesn't run again as port is in use.
```

# Automating the configuration of mongodb ready for app vm
Installs mongodb database and changes bind ip to 0.0.0.0 so that VMs other than this one can communicate with it.
```linux
#!/bin/bash

 

# update
sudo apt update -y

 

# upgrade
sudo apt upgrade -y

 

# download key for the right version
wget -qO - https://www.mongodb.org/static/pgp/server-3.2.asc | sudo apt-key add -

 

# source list - specify mongo db version
echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list

 

# update again
sudo apt update -y

 

# install mongo db
sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20

 

# configure bindip to 0.0.0.0
sudo sed -i 's/bindIp: 127.0.0.1/bindIp: 0.0.0.0/g' /etc/mongod.conf

 

# start mongo db
sudo systemctl restart mongod

 

# check the status
sudo systemctl status mongod

 

# enable mongo db
sudo systemctl enable mongod

```
# Putting the reverse proxy in the script
Place above nginx restart and under install so that the changes can come into place.
```
# Change nginx config
sudo sed -i 's|try_files $uri $uri/ =404;|proxy_pass http://localhost:3000;|' /etc/nginx/sites-available/default
```

