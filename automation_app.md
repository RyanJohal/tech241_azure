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


# restart nginx
sudo systemctl restart nginx


# status nginx
sudo systemctl status nginx


# enable nginx - will auto start on reboot
sudo systemctl enable nginx


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
cd /home/adminuser/app/app2


# install node js in folder
npm install -y


# Run app in the background using PM2
pm2 start app.js --name "sparta app"






# To run the app in the background with &
nohup npm start &
# nohup prevents the process from being terminated when terminal session ends, doesn't engage terminal, it always changes process ID so you need to kill previous command to run it again. Doesn't run again as port is in use.
```