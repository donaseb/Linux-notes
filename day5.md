# File Permissions :
- permissions are applied on files and directories which defines the level of access for a particular user or group
- 3 parts of permissions :  
  1.read(r): to view the contents of the files and directories  
  2.write(w) : to create /modify/delete the contents of the file or directory  
  3.execute(x) : to execute  a script / install a package  
- permissions can be of 3 categories:  
  1.owner (u) : By default who created the files and directories are reffered to as owner    
  2. group (g): by default the primary group of the owner is defined as the group of the file or directory  
  3.other (o): apart from owner,and group members all other users and groups are reffered to as others
- whenever you create a file ,linux server will setup a basic permissions to the files and even to folders by default,if we need to modify the default permissions  you need  commands like chmod,chown
- Example of Permission Structure:
Permissions are displayed using the ls -l command in the following format:
```
-rwxr-xr--  1 user1 group 0 date /home/user1/file.txt
```
- The first character: - for files or d for directories.

- The next three characters: Owner's permissions (read, write, execute).

- The next three characters: Group's permissions (read, write, execute).

-The last three characters: Others' permissions (read, write, execute).

- So, for example, the permissions rw-r--r-- would indicate:

- Owner has read and write permissions.

- Group has read-only access.

- Others have read-only access.
- so if you have 2 users ,user1 and user2 in your server and then by default the files created by  user1 can only be read by the other ,the  user2 cannot update the file or delete the files created by the other user1.
- to check the permissions ``` ls-ltr``` this will lists all the files and folders inside the present working directory along with its permissions
- so if you create a file test in your home directoy and do ls-ltr you could find  the permissions of this file created
- files are denoted by -rwx|rwx|rwx| and folders drwx|rwx|rwx
- so for example permissions of my file test is rw-|r--|r-- ,in this the first part represents the owner or user who created the file,the second part of rwx denotes the users in the primary group of this user,and 3rd part of rwx denotes the permissions to every other users ie users who are not the owner or not in the primary group of the user cretaed the file
- for example there are 2 users dona and demo,these users are in different  groups,so user dona created a file test.sh inside the home directory with permissions -rwx|r--|r--,this means that owner or dona who created this file has full read ,write and execute permissions,the users in the group and other has only read permission
- other user can access the file only if that user has access to home directory of user dona
- for example if the permisssions of home directory of dona  is drwx|rw-|---, means  dona has full read ,write and execute permissions,user in same group has read and write permissions  and other has no permissions
- so users who have access to the folder could only acces tthe file inside it,so here the file is inside the home directory so who has access to home directory can only access the file
- if file has rwx|rwx|rwx but the home directory has permisssion drwx|r--|---,only people in group has read access and the other users hasnot access ,ebven though there is full access in the file it folows the permission of the folder 

  
  
