# user management:
#### Topics covered;
1.user management
2.file management
3.vi shortcuts
## User management:
- user management is required for the accpountability and also for making your linux environment secure.
- as part of the user mamagement you will create users and groups.
- for all the employess in an organisation who needs to access the server you can create user,andfor each users you can give permissions based on what they do in an 
 organisation
### Creating users and groups:
- create a linux ec2 instance in aws and then ssh into it
** Command to create user:
  ``` useradd username```
  - example
   useradd dona
  - a user with name dona is created
** how to check if the user is created:
- all the deatils of the user will be added inside the /etc/passwd file
- open this /etc/passwd file and check the entry for the user
** how to open the file
  ``` vim filename ```
  -using vim you can see the contents as well as you can edit the file
  -to just display the contents of the file
  ``` cat filename ```
  
