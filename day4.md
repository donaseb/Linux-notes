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
### Fields of /etc/passwd:
username : pwd :Uid : gid: gecos : homedir: loginshell


** how to check if the user is created:
- all the deatils of the user will be added inside the /etc/passwd file
- open this /etc/passwd file and check the entry for the user
** how to open the file
  ``` vim filename ```
  -using vim you can see the contents as well as you can edit the file
  -to just display the contents of the file
  ``` cat filename ```
  
