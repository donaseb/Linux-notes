# File and Folder Structure in Linux

## Admin User 

- **Admin User**: `root` user
- **Example**: `root@ubuntu-dev:/#`
  - `.root` - admin
  - `@ ubuntu-hostname`
  - `/` is the path of the present working directory (pwd)
  - `'#'` indicates root user

## User Management and Default Paths

- Teams set up different users, and access for the users will be granted accordingly.
- When you log into an EC2 instance, you will automatically be logged in as the username `ubuntu`.
  - It will be the default user with which you will be logged in.
- By default, you get a storage path as `/`.
  - All files and folders will be created by default in this location `/`.
  - `/` means at the root of the filesystem.
- **EC2 Example**: `ubuntu@hostname:~$`
  - `"~"` represents `/home/ubuntu`.
  - So in EC2, the default path is `~`, i.e., `/home/ubuntu/`.
  - `~` is the home directory of any user that is logged in.
    - If the user is `dona`, then `~` means `/home/dona`.
- So normally, `/` is the default location.
- `/home` - inside `/home`, we create a directory for every user in the Linux system,here ubuntu  is the default user created by the ec2.


## FILES AND DIRECTORIES

##### `ls -ltr`

- Will find files and directories.
- `ls` means list.

**How does Linux know that typing the command `ls` means listing all files?**

- The package for defining each of the commands is stored in one of the folders.
- If the Linux environment already has installed the packages in one of its directories, Linux will understand each command.

- `ls` - list
- `mkdir dir1` - creates a directory named `dir1`

In the structure of the OS, there are system packages and system libraries along with the shell. So all the system libraries and utilities are stored in one of the directories.

In EC2:

```bash
sudo su -
cd /
ls -ltr
```


## Directories

### 1. `/sbin`

- Has system binaries, which are the commands or the binary files that can be used to manage the system as an administrator.
- Contains commands that can be executed only by the root user by default.
- `useradd` is in `/sbin`, so when a person tries to create users using this command, it first goes to `/sbin`, finds the binaries of the command `useradd`, and executes the command so the user is created.
- System binaries for administrative commands (linked to /usr/sbin).
- -/sbin -> /usr/sbin

### 2. `/bin`

- Has user binaries.
- Contains binaries to manage users.
- Essential user binaries (linked to /usr/bin).
- Has all the commands that can be executed by any users.
- /bin -> /usr/bin

- Both `bin` and `sbin` are under the parent directory `/usr`.
  - So if we do `/usr/sbin` - admin command binaries, and `/usr/bin` has user command binaries.
  - `sbin` is a shortcut for `/usr/sbin`, and `bin` is a shortcut for `/usr/bin`.

### 3. `/home`

- Contains the home directories of all the users' default home directories.
- Default location for user home directories.
- `useradd` and `adduser` both are used for creating users, but `useradd` creates a user without the home directory.
- So whenever a user is created using `adduser`, within `/home`, a user folder is created.

### 4. `/lib`

- Is the library folder.
- has Shared libraries and kernel modules (linked to /usr/lib).
- Inside, it has different kinds of libraries which are used by the Linux kernel. So as a user, you don't use these libraries, but they are used by the kernel to make system calls with hardware to execute actions.
- /lib -> /usr/lib
  
### 5. /usr:
- /bin,/lib,/sbin all are inside the directory /usr
- /usr also has /share: which is a locaton we use as a common loaction while using this linux environment for sharing some files ,it is used as a common storage location
- /src :it is loction to store common source code
- the most imprtant ones are /lib,/bin,/sbin.

### 6. `/boot`:
- for booting your linux machiene ,ie for starting and restarting machiene
- while starting or restarting the things inside the /boot folder helps to start,has commands to execute and also the actions needed to execute during the start of the machiene
- Stores files needed for booting the system
  
### 7. `/srv`:
- means servers
- contains config files and other information related to web servers
- so by default while creating webservers some files are stored inside the /srv

### 8. `/opt`:
- Used for installing optional third-party software.
- when you need to install any 3rd party tool or a particular version of java or anything you will go to /opt
- inside /opt you will create a folder for your tool and all the configuration and all files realted to this is stored inside the /opt/directory
- act as a common location for all the 3rd party tools
### 9. `/mnt`:
-  Temporary mount point for external filesystems.
-  mnt means mount
-  linux admins will have tasks like adding more space to the filesystem,for example initally there is 20 gb and you need to add another 30 Gb to it for this a 30 GB disk will be mounted to the temporary mounting point /mnt and from there it will be added to file system
-  /mnt is a folder that linux admins use to mount new volumes or disks.
### 10. `/var`:
- var Stores logs, caches, and temporary files that change frequently.
- /var has folders like /log,/lib , /cache etc
- so when you check /var/log it has logs of the system
- so when you intsall any 3rd party apps or any webservers its logs will be saved inside /var/log and followed by any folder

### 11. `/data`:
- if i have data related to oraganisation or any people etc it will be stored inside /data
- any data that could be shared with other admins of the organisation is stored inside /data

### 12 . `volatile folders`: stores temporary files
  #### 1. /proc: Virtual filesystem for process and system information.
  #### 2./tmp: Temporary files (cleared on reboot).
  #### 3./sys: Virtual filesystem for hardware and kernel information.
  #### 4./dev: Contains device files (e.g., /dev/null, /dev/sda).
  #### 5./run:Holds runtime data for processes.

### 13. `/root`:Home directory for the root user.

### 14 . `/etc`

- Contains configuration files of the machine, i.e., config files have all the settings required for a service to run.
- It is like `C:/` in Windows.
- Stores system configuration files.

#### system configuration files:
1./sbin
2./bin
3./lib
#### Important System Directories:
1./boot
2./usr
3./var
4./etc
#### User & Application-Specific Directories:
1./home
2./opt
3./srv
4./root
#### Temporary & Volatile Directories:
1./proc
2./tmp
3./sys
4./dev
5./run
#### Mount Points
1./mnt
2./data
3./media



