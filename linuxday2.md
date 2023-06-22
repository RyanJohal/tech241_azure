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


cat file | grep word - Shows all lines with word in existing file


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

 