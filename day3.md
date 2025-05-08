# Basic commands:
1.date : displays the current date and time  
2.cal : Displays current month calender  
3.uname : Displays the type of the of os,uname diplays the machiene type  
- uname -r : displays the version of the kernel  
- uname -v : displays the release date of the kernel  
- uname -m : displays the machienes architecture  
- uname -n: displays the machienes name (host name)  
- uname -p : displays the processor's architecture  
- uname -o : displays the type of os  
- uname -a : displays all the system parameters
4. whoami : displays the current logged in username
5. pwd : displays present working directory
6. history : displays the commands executed till now ,used by a purticular user,history is user specific
7. cd : change directory
  ```cd <dirname>```
  to go to a purticular directory
  - to go a directory inside another one  
    ``` cd dir1/dir2 ```
    here dir2 is inside the dir1
  - command to take you to the parent directory of the present working directory
   ``` cd ..```
  -to go to the previous used directoy
  ``` cd - ```
 - to go to the home directoy of the current loggedin user
   ``` cd ~ ```
8.ls: llist the files or folders  
- ls <dirname> : this lists the files and the folders inside the directory
- ls : lists files in the present working directory
- ls -a : lists all the files including hidden files under present worrking directory
- any file or directory name starting with a dot is refferred as hidden file or hidden directory
- ls -i : to list all files and directories with their inod numbers
- index node number is a unique number allocated to every single file or directory by the os for its reference.
- ls -t : list all files and directories based on time stamp(new to old)
- time stamo always defines the last  modified date and time of a file.
- ls -tr : list all files and directories based on time stamp(new to old)
- ls -F : lists all the file names in which the one which is just file names are the normal files,the names that ends with a / is directory, and the names that ends with @ is linked file, and one that ends with * si executable file.
- ls -l : lists the files and folders in long listing format with complete details
- for example ```` -/rwxrwxrwx.!root root 48 march 7.28  file1```
-  -reprensents file,d represents directory,l represents link file
-  rwxrwxrwx : means permissions
-  . represents ACL,access control list
-  root represents the owner
-  root represents the group
-  48 size (kb)
-  time stamp
-  filename
# Files and directories management:
## Creating files:
- touch  filename : creates an empty or zero bit file
- touch existing filename : to changfe the time stamp of the existing file to current tie without altering or modifing data  
- cat > new filename: creates new file and add data in it,after adding data into this file to save and exit ```ctrl + d``` to sAve and exit
- cat existing filename : shows or displays the contents of the file
- cat > existing filename : the existing contents of this file will be overwritten by this new contents added to this file,save and exit and after this when we display the contents this new data is shown
- cat >> existing filename : appends or add the new content to the existing file,thec ctrl +d
- vim filename : to create file and also to add contents to this file
- vim existing filename : this shows the contents inside the file and also allows to edit or add new data to it
- vim file name : opens the editor ,to add inot the file press ``` esc + i ```  this makes the file in insert mode
-  to exit without saving ``` esc + : q!```
-  to save and exit ``` esc + :wq! ```
## Creating directories :
- mkdir directory name : crates new directory
- mkdir dir1 dir2 dir3 : creates multiple directories together
## Copying -cp
- ```cp <source file  > <destination file > ``` : copies the contents from source to destination file
- if destination file does not exist it creates a file and then copies data into it
- cp -r <source file or directoy > < destination file or direc> : copy contents from source to destination recursively
## move mv:
- mv <source> <destination> : cut from the source and paste it in destination
- to rename a file or directory : mv <old name> <new name>
## Deleting files and directories:
- rm <filename> : to delete the file
- rm -rf <dirname> : to delete directory 


