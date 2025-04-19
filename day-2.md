# File and Folder Structure in Linux

## Admin User 

- **Admin User**: `root` user
- **Example**: `root@ubuntu-dev:/#`
  - `.root` - admin
  - `@ ubuntu-hostname`
  - `-dev:` is the path of the present working directory (pwd)
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
- `/home` - inside `/home`, we create a directory for every user in the Linux system.


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
sudo su
cd /
ls -ltr
```


## Directories

### 1. `/sbin`

- Has system binaries, which are the commands or the binary files that can be used to manage the system as an administrator.
- Contains commands that can be executed only by the root user by default.
- `useradd` is in `/sbin`, so when a person tries to create users using this command, it first goes to `/sbin`, finds the binaries of the command `useradd`, and executes the command so the user is created.

### 2. `/bin`

- Has user binaries.
- Contains binaries to manage users.
- Has all the commands that can be executed by any users.

- Both `bin` and `sbin` are under the parent directory `/usr`.
  - So if we do `/usr/sbin` - admin command binaries, and `/usr/bin` has user command binaries.
  - `sbin` is a shortcut for `/usr/sbin`, and `bin` is a shortcut for `/usr/bin`.

### 3. `/home`

- Contains the home directories of all the users' default home directories.
- `useradd` and `adduser` both are used for creating users, but `useradd` creates a user without the home directory.
- So whenever a user is created using `adduser`, within `/home`, a user folder is created.

### 4. `/lib`

- Is the library folder.
- Inside, it has different kinds of libraries which are used by the Linux kernel. So as a user, you don't use these libraries, but they are used by the kernel to make system calls with hardware to execute actions.

### 5. `/etc`

- Contains configuration files of the machine, i.e., config files have all the settings required for a service to run.
- It is like `C:/` in Windows.

