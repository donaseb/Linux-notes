# user management:
#### Topics covered
1.user management  
- creating user
- fields of /etc/passwd
- delete user
- modify 
2.group management
- create group
- fields of /etc/group
- delete gropu
3.vi shortcuts  
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
  - grpid- <username>  
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
** how to open the file
  ``` vim filename ```
  -using vim you can see the contents as well as you can edit the file
  -to just display the contents of the file
  ``` cat filename ```
  
