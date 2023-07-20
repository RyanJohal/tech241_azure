# Starting sparta app with script
Installing nginx, access node js and installing it, creating env variable to connect to db vm, using git clone to download app folder and then starting app within that folder.

1. Update system - We use "sudo apt update" to refresh the package list with the latest information on a Linux system.
``` sudo apt update -y```

2. Upgrade system - We use "sudo apt upgrade" to upgrade installed packages on a Linux system.
``` sudo apt upgrade -y```

3. Install nginx
``` sudo apt install nginx -y```

4. Restart nginx - We use "sudo systemctl restart nginx" to restart the Nginx web server with administrative privileges.
``` sudo systemctl restart nginx ```

5. Check status of nginx
``` sudo systemctl status nginx ```

6. Enable nginx - We use "sudo systemctl enable nginx" to enable the Nginx service to start automatically on system boot.
``` sudo systemctl enable nginx ```

7. This command downloads and executes a script that sets up the Node.js 12.x repository on a Debian-based system with administrative privileges.
``` curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -``` 


8. The command sets the DB_HOST environment variable to the specified MongoDB connection string, allowing other processes or scripts to access and use it.
```export DB_HOST=mongodb://172.187.177.225:27017/posts```


9. This command installs Node.js on a Linux system using the apt package manager with administrative privileges, automatically answering "yes" to all prompts.
```sudo apt install nodejs -y```


10. This command installs the pm2 package globally using npm with administrative privileges, ensuring it is accessible system-wide.
```sudo npm install -g pm2```


11. This command clones the repository located at https://github.com/RyanJohal/tech241_sparta_app.git into a local directory named app.
```git clone https://github.com/RyanJohal/tech241_sparta_app.git app```


12. This command changes the current working directory to /home/adminuser/app/app2.
```cd /home/adminuser/app/app2```


13. This command installs the dependencies of the Node.js application located in the current directory (/home/adminuser/app/app2) using npm, automatically answering "yes" to all prompts.
```npm install -y```


14. This command starts the Node.js application (app.js) using pm2 and assigns it the name "sparta app". pm2 will manage the application, ensuring it remains running even after system reboots or crashes.
```pm2 start app.js --name "sparta app"```


```
#!/bin/bash

# update
sudo apt update -y


# upgrade
sudo apt upgrade -y


# install nginx
sudo apt install nginx -y


# status nginx
sudo systemctl status nginx


# enable nginx - will auto start on reboot
sudo systemctl enable nginx


# install sed
sudo apt install sed -y


# Change nginx config
sudo sed -i 's|try_files $uri $uri/ =404;|proxy_pass http://localhost:3000;|' /etc/nginx/sites-available/default

sudo systemctl restart nginx

# access correct node source
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -


# add in env
export DB_HOST=mongodb://172.187.177.225:27017/posts


# install node.js
sudo apt install nodejs -y


# install pm2
sudo npm install -g pm2


# copy app folder
git clone https://github.com/RyanJohal/tech241_sparta_app.git app


# cd into app folder
cd app/app


# install node js in folder
npm install -y


# Run app in the background using PM2
pm2 start app.js --name "sparta app"




```

# DB script

## Command Descriptions

1. `sudo apt update -y`: Updates the package lists for upgrades and installations.
2. `sudo apt upgrade -y`: Upgrades installed packages to their latest versions.
3. `wget -qO - https://www.mongodb.org/static/pgp/server-3.2.asc | sudo apt-key add -`: Downloads the GPG key for the MongoDB repository and adds it to the system's trusted key list.
4. `echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list`: Adds the MongoDB repository to the system's package sources list.
5. `sudo apt update -y`: Updates the package lists again after adding the MongoDB repository.
6. `sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20`: Installs specific versions (3.2.20) of MongoDB packages.
7. `sudo sed -i 's/bindIp: 127.0.0.1/bindIp: 0.0.0.0/g' /etc/mongod.conf`: Modifies the MongoDB configuration file (`/etc/mongod.conf`) to bind MongoDB to all available network interfaces (`0.0.0.0`) instead of just localhost.
8. `sudo systemctl restart mongod`: Restarts the MongoDB service to apply the new configuration.
9. `sudo systemctl status mongod`: Checks the status of the MongoDB service.
10. `sudo systemctl enable mongod`: Enables the MongoDB service to start automatically on system boot.

These commands are used to update, upgrade, install MongoDB 3.2.20, configure its network binding, restart the service, and enable it to start on system boot.
