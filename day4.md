# user management:
#### Topics covered
 
## User management:
- user management is required for the accpountability and also for making your linux environment secure.
- users are required for authentication (log -in)
- users are alos needed to define autherization (permissions)
- every file or directory must and shoud have an owner defined by user
- every process running on machiene also should have an owner defined by a user
- user is anybody who has a valid credentials tolog into the system
- two types of users admin user and non admin user
- admin user is the root user
- non admin user : has system user and normal user
- root user : it is default administrative account of the machienewhich has complete access irrespective of the permissions
- system user : are user accounts createdby the os mainly to take ownership of a process .system user does not has a valid username or shell
- normal user : there are the user accounts created by root user so that user can log into the machiene with limited access
- user id : are unique numbers allocated to every single userfor the system's reference
- userid of root user = 0
- userid of system users = (1-999)
- userid of normal users = (1000-60,000)
- username is for our reference and userid is for the systems reference
- as part of the user mamagement you will create users and groups.
- for all the employess in an organisation who needs to access the server you can create user,andfor each users you can give permissions based on what they do in an  organisation
### Creating users :
- create a linux ec2 instance in aws and then ssh into it
** Command to create user:
  ``` useradd username```
  - example
   useradd dona
  - a user with name dona is created
 - /etc/passwd : contains all the users information
 - create password for this user dona for this ```passwd dona``` then enter the password for this user
 - How to check if password is created for the user :
    ``` cat /etc/shadow ```
   for this user we could find the encrypted password
- if the user lost the password could you decrypt the password or retrieve the lost password of the user:
   no, we cant decrypt or retrieve ,because it is highly encrpted,so it is one way encryption,so once a person lost we cant retrieve the password
### Fields of /etc/passwd:
username : pswd :Uid : gid: gecos : homedir: loginshell  
1.username : name allocated to every user for user's reference  
2 passsword (x): it defines that the  password is set and the information is stored in /etc/shadow  
3 uid: user id unique number allocated to every user for system's reference  
4 gid : group id is  te primary group of that particular user  
5 gecos : is an optional field for a user that describes a user  
 - it is not mandatory to define gecos ,it is only for users reference
6 Home Directory : it defines the home directory allocated to a purticular user
7 Loginshell : it defines the login shell allocated to a user ie bash,kshell,cshell etc 
- create user and set password for that user:
- ``` useradd dona``` create user
- ```passwd dona ```set password for this user
- if we dont create user with providing the values for all the options other than username and password then the system will assign some default values
- all the fields excet gecos in /etc/passwd is mandatory fields needs to provided while creating user ,if not  system gives default values
  *Default values:
  - uid -previous user's id +1
  - grpid- username  
  - homedirectory - /home/username
  - loginshell - /bin/bash
- ** how to check if the user is created:
- all the deatils of the user will be added inside the /etc/passwd file
- open this /etc/passwd file and check the entry for the user
### Creating user with specific values :
- ``` useradd -u <uid> -g <primary group> -G <seconadry group > -c <gecos> -d <home directory> -s <loginshell>  <new username> ```
- ```passwd <username>```
- -u : defines the userid
- -g : primary group
- -G :seconary group
- -c : defines the optional fieldfor users reference
-```id username ``` : gives the groups to which it belongs
### modify the user :
``` usermod -u <userid> -g<primary group> -G <secondary group> -c <gecos> -d <home dir> -s <loginshell> <existing username>```  
``` passwd <existing username > ```
### Delete auser
- ``` userdel <existing username> ``` this will delete the user
- ``` userdel -r <existing username > ``` : will delete the user account and home directory and all the files and directories related to this user
- check if deleted  in the /etc/passwd, the entry for the deleted user and we will find that it is deleted
- 
### useradd :
- this command is used to create a user
- ```useradd <username > ```
- if you do  ```ls /home  ``` we will find that the home directory for the user is not created
- so in useradd only the user is created and the it does not create the home directory fo user .
- useradd is usefull to create user in scripts
- to create a user along with home directory usin useradd : ``` useradd -m username```
- To specify a shell:```useradd -s /bin/bash username```
### adduser :
- ``` adduser username ``` this command also creates user
- the difference between useradd and adduser is that ,while using adduser along with the creation of user a home directory for the user is created and also users details will also be asked .
- the other details of the user will also be added
** command to change the password of user every 90 days :
  - ``` chage -M 90 username ```
  - to lock a user account : ``` passwd -l username ```
  - to unlock the user account : ``` passwd -u username ```
** how to create password to the user :
- ``` passwd username ```
### Modifying Users
- Change the username ``` usermod -l new_username old_username```
- Change the home directory: ```usermod -d /new/home/directory -m username```
- Change the default shell ```usermod -s /bin/zsh username```

** how to open the file
  ``` vim filename ```
  -using vim you can see the contents as well as you can edit the file
  -to just display the contents of the file
  ``` cat filename ```
## Group management :  
- A group is the collection of similar types of users which is grouped together to arrange them easily.
- any permission applied to the group will be applied to the entire users of that group
- mainly used to manage multiple users simultaneously
- all groups information will be stored inside /etc/group
### Fields inside /etc/group :  
- 4 fields are inslde the /etc/group :  
* groupid : is the unique number allocated to every group for systems reference.
* group_name: It is the name of group. If you run ls -l command, you will see this name printed in the group field
* Password: Generally password is not used, hence it is empty/blank. It can store encrypted password. This is useful to implement privileged groups
* Group List: It is a list of user names of users who are members of the group. The user names, must be separated by commas.
### create group :
- to create group with default values : ``` groupadd <new groupname > ```
- Adding Users to Groups :
  ```usermod -aG groupname username```
- Viewing Group Memberships:
   ```groups username```
- Changing Primary Group
  ````usermod -g new_primary_group username```  
- the default groupid will be the previous groupid +1
- to create a group with a specific group id  for example a group of name developer  and id of 2000  ```groupadd -g 2000 developer```
- ``` groupadd -g <newgroupid> <new group name > ``` : to create a new group with a particular id
- to modify the groupid :``` groupmod -g <newgroupid> <group name> ```
- to delete a group : can be deleted only if the primary group of the users in this group is changed
- to delete group ``` groupdel <group name >```
#### Sudo Access and Privilege Escalation :
- Adding a User to Sudo Group
- 1.On Debian-based systems: ```usermod -aG sudo username```
- 2.On RHEL-based systems:```usermod -aG wheel username```
### How to login to linux machiene:
- once the user is created the username and password along with ip of the machiene will be given to you then using that you will ssh into the machiene  
- ```ssh username@ipaddress```
-  it will asks for the password provide that and you will be logged into the machiene as a user
-  if you cannot log in using ssh it might be because the password authentication will be kept as no  so to change that the admin has to log into the system ,then do ```cat /etc/ssh/sshd_config.d.60-cloudimg-settings.conf``` then inside the file editthe password authentication from no to yes
- then do ```sudo systemctl restart ssh ```
- if password authentication is disabled then how to log in: for this use pem file

  
