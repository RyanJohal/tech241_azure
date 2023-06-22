# Commands
1. uname -v             See what shell is installed 
2. uname                To see the name of OS in use
3. uname -r             Kernel release version
4. uname -p             Name of the processor running
5. uname --help         Lists all commands to be used with 'uname'
6. uname -n             Nodename or Hostname
7. ps                   Show processes running
8. ps -p $$             Shows what shell is running
9. history              Finds all commands that have been run
10. !(command number)    Run command from history
11. history --help       Show history commands
12. -c                   Clear history list
13. ls                   Show files
14. ls -l                To see the long list with directories n permissions
15. ls -a               Show hidden files
16. cd .                Current directory
17. cd ..               Parent directory
18. cd              Root directory
19. cd home             Home directory 
20. cat > file1         To create a new file
21. cat file1           To read the contents of the named file
22. cat >>file2         To add anything to the file and use CTRL+D to exit
23. cat file1 file2 >new To copy contents of file1 and file2 to newfile
24. tac new             To read the content upside down(last line first and then all others in descending order)
25. cat file2 > file1   To copy content of file2 to file1 (content of file1 gets overwritten)
26. touch               To create new file/s
27. stat                To check the time stampfile (access time, modify time of a file)
28. stat -a             To check the access time of any file
29. vi <file_name>      To create a file with VI/VIM editor , press ESC and then :wq
30. :w to save
31. :q to quit
32. :wq                 To save and quit
33. :q!                 To force quit, no save
34. nano                To create a file with nano editor
35. Hostname            Hostname of the machine
36. Hostname –I         IP address of host machine
37. Ifconfig            IP address of host machine
38. Cat /etc/os-release Operating system release version
39. whoami              To see the name of currently logged in user
40. Ctrl +l             To clear screen
41. mv <old_name> <new_name> To rename a file
42. cp <old_name> <new_name> To copy a file from one to another
43. rm <file_name>      To remove a file
44. rm -r               To delete everything
45. file <file_name>    To find out the type of the file
46. head -2 <file_name> To display first 2 lines of the file
47. tail -2 <file_name> To display last 2 lines of the file
48. nl <file_name>      To add numbers to the lines
49. curl                
50. Tool to transfer data to and from a server

# Managing file ownership
### Why is managing file ownership important?
Managing file ownership is important for several reasons:

Security: By assigning ownership to specific users or groups, you can control who has access to the files and ensure that only authorised individuals can modify or view sensitive information.
Accountability: File ownership allows you to track changes made to files and hold users accountable for their actions.
Collaboration: Assigning ownership helps facilitate collaboration by clearly indicating who is responsible for a particular file or directory.

### What is the command to view file ownership?
The command to view file ownership is "ls -l" or "ls -al". It displays detailed file information, including the owner and group associated with the file.

### What permissions are set when a user creates a file or directory? Who does the file or directory belong to?
When a user creates a file or directory, the permissions set are determined by the umask value. The umask acts as a filter to determine which permissions are not granted by default. The file or directory will typically belong to the user who created it and their default group.

### Why does the owner, by default, not receive X permissions when they create a file?
The owner, by default, does not receive execute (X) permissions when they create a file for security reasons. This is a precautionary measure to prevent accidental execution of potentially harmful files. Users can manually add the execute permission if necessary.

### What command is used to change the owner of a file or directory?
The command used to change the owner of a file or directory is "chown". The basic syntax is: "chown new_owner file_or_directory". 


# Managing file permissions
### Does being the owner of a file mean you have full permissions on that file? 
Being the owner of a file does not automatically grant full permissions. Ownership provides certain privileges, but the specific permissions assigned to the file determine the level of access, including read, write, and execute permissions. The owner may or may not have all these permissions based on the permission settings.

### If you give permissions to the User entity, what does this mean?
Granting permissions to the User entity implies giving specific access rights to the user who owns the file or directory. These permissions dictate the actions the owner can take on the file, such as reading, writing, or executing it.

### If you give permissions to the Group entity, what does this mean?
Assigning permissions to the Group entity means allowing a specific group of users (to which the file or directory belongs) to have designated access rights. The permissions granted to the group determine the actions that members of that group can perform on the file, such as reading, writing, or executing it.

### If you give permissions to the Other entity, what does this mean?
Providing permissions to the Other entity entails defining access rights for all users who are neither the owner nor part of the assigned group. These permissions determine the actions these users can perform on the file, such as reading, writing, or executing it.

### You give the following permissions to a file: User permissions are read-only, Group permissions are read and write, Other permissions are read, write, and execute. You are logged in as the user who is the owner of the file. What permissions will you have on this file?
As the user who is the owner of the file, you will have read-only permissions because the user permissions are set as read-only. This means you can view the file's contents but cannot modify or execute it. The group permissions and other permissions, which allow write and execute access, do not apply to you as the owner.

### Here is one line from the ls -l. Extract all the information about permissions on this file or directory.
The line "-rwxr-xr-- 1 tcboony staff 123 Nov 25 18:36 keeprunning.sh" provides information about the permissions and ownership of the file "keeprunning.sh."

- The file has permissions set as "-rwxr-xr--." The first character "-" indicates that it is a regular file. The subsequent nine characters are divided into three sets of permissions: user (owner), group, and other.
- For the user (owner), the permissions are "rwx" (read, write, and execute).
- For the group, the permissions are "r-x" (read and execute).
- For others, the permissions are "r--" (read-only).
- The number "1" represents the link count, indicating how many hard links point to the file.
- "tcboony" is the username of the owner of the file.
- "staff" is the group to which the file belongs.
- "123" indicates the file size in bytes.
- "Nov 25 18:36" states the date and time of the last modification.
- "keeprunning.sh" is the name of the file or directory.

# Managing file permissions using numeric values
### What numeric values are assigned to each permission?
In Linux, the numeric values assigned to each permission are as follows:
Read: 4
Write: 2
Execute: 1

### What can you do with the values assign read + write permissions?
Assigning the values for read + write permissions (which is 6) allows the user or group to read and modify the file or directory. They can view its contents and make changes to it, such as editing or deleting the file.

### What value would assign read, write, and execute permissions?
The value that assigns read, write, and execute permissions (which is 7) grants the user or group full control over the file or directory. They can read its contents, modify it, and execute any executable files or scripts contained within it.

### What value would assign read and execute permissions?
The value that assigns read and execute permissions (which is 5) permits the user or group to view the file's contents and execute any executable files or scripts. However, they are unable to modify the file or directory.

### Often, a file or directory's mode/permissions are represented by 3 numbers. What do you think 644 would mean?
The number 644 represents the file or directory's permissions in octal notation. Breaking it down:
The first digit (6) indicates the user's permissions, which are read and write (4 + 2).
The second and third digits (4 and 4) represent the group's and others' permissions, both of which are read-only. 
Therefore, 644 means that the user has read and write permissions, while the group and others have read-only permissions.

# Changing file permissions
### What command changes file permissions?
chmod

### To change permissions on a file, what must the end user be? 
To change permissions on a file, the end user must be either the owner of the file or have appropriate superuser/administrator privileges.

### Give examples of some different ways/syntaxes to set permissions on a new file (named testfile.txt) to:
Set User to read, Group to read + write + execute, and Other to read and write only
chmod 764 testfile.txt

Add execute permissions (to all entities)
chmod +x testfile.txt

Take write permissions away from Group
chmod g-wx testfile.txt

Use numeric values to give read + write access to User, read access to Group, and no access to Other.
chmod 640 testfile.txt
