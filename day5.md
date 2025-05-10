
## File Permissions?

Permissions are applied on **files** and **directories** to define access levels for:

- The file owner
- Members of the owner's group
- All other users (others)

---

##  Types of Permissions

Each permission is represented by a single letter:

| Permission | Symbol | Meaning                                             |
|------------|--------|-----------------------------------------------------|
| Read       | `r`    | View contents of a file or list a directory         |
| Write      | `w`    | Modify or delete the file or directory contents     |
| Execute    | `x`    | Run a file/script or access a directory             |

---

##  Categories of Users

1. **Owner (u)**  
   The user who created the file/directory.

2. **Group (g)**  
   The primary group of the owner. By default, new files inherit the owner’s primary group.

3. **Others (o)**  
   All users who are not the owner or in the group.

---

## ⚙️ Default Permissions

When a file or directory is created, Linux assigns default permissions based on the user's umask value. You can modify these permissions using:

- `chmod` – change permissions
- `chown` – change ownership

---

##  Example of Permission Structure

Using `ls -l`:
```bash
-rwxr-xr--  1 user1 group1 0 Jan 1 00:00 /home/user1/file.txt
```
###  Breakdown of the Fields

| Section         | Description                                                                 |
|-----------------|-----------------------------------------------------------------------------|
| `-` or `d`      | Indicates the type: `-` for a **file**, `d` for a **directory**             |
| `rwx` (Owner)   | Owner's permissions: read (`r`), write (`w`), execute (`x`)                 |
| `r-x` (Group)   | Group's permissions: read (`r`), no write (`-`), execute (`x`)              |
| `r--` (Others)  | Others' permissions: read (`r`), no write/execute (`--`)                    |

---

###  Example Permission: `rw-r--r--`

This permission string means:

- **Owner** has **read and write** permissions (`rw-`)
- **Group** has **read-only** access (`r--`)
- **Others** also have **read-only** access (`r--`)


>  **Tip:** Even if a file has `rwxrwxrwx` permissions, it cannot be accessed unless the **directory** it’s in also grants appropriate permissions.


##  File Permissions and Multiple Users

###  User-to-User Access

When multiple users exist on a Linux server, file access depends on:
- **File Permissions**
- **Directory Permissions**
- **Group Membership**

For example, consider the users `user1` and `user2`. Based on the permissions of files created by `user1`, `user2` may have read, write, and execute access.

To check the permissions of files or directories, use the following command:

```bash
ls -ltr
```
This will display the files and directories along with their permission structure.
### Example: File and Directory Permissions
####File Permissions
-Files are denoted by the following structure:

```bash

-rwxrwxrwx
```
Owner's Permissions: The first part (rwx) represents the owner's permissions (read, write, execute).

Group's Permissions: The second part (rwx) represents the group's permissions (read, write, execute).

Others' Permissions: The third part (rwx) represents the permissions for others (read, write, execute).

### Directory Permissions
#### Directories are denoted by:

```bash

drwxrwxrwx
```
d indicates that this is a directory.

The rest (rwxrwxrwx) follows the same permission structure as files.
#### Example:
-File: test.sh

 * Owned by: dona

 * Permissions: rwx|rw-|rw- (i.e., 764)

  -This means:

* dona (owner): can read, write, execute

* group: can read and write

* others: can read

- Directory: /home/dona

 - Permissions: rwx|r--|--- (i.e., 740)

This means:

- dona: full access

- group: can read only

- others: no access at all

### Can demo access test.sh?:
- No, because,Even though test.sh is world-readable, the /home/dona directory has --- for "others" — and if a user can’t execute a directory, they cannot traverse it to reach any file inside.
- To allow user demo to access test.sh, /home/dona directory needs at least execute (x) permission for others or for the group that demo is in.
- Grant 'execute' permission to 'others' on /home/dona:
-
  ``` chmod o+x /home/dona ```
- This allows all users to "enter" the directory
- Better security: Add demo to a group and change /home/dona group accordingly, then set appropriate permissions — more secure and specific.
- Who can make this change?  :  Only root or dona (the owner of /home/dona) can change the permissions of /home/dona.
### Changing permissions:

#### 1 . Symbolic method (Relative method ) :  
- called symbolic becuse we use symbols
- called Relative method because we could  give new permissions only if we know previous permission
- so there is a dependency of previous permission .So calledrelative
- if in a file test  r--|r-x|rwx → existing permission,how to change the permission to rwx|rw-|r--
- ``` chmod u+wx,g+w,g-x,o-wx test ```
- to check permission ls-l
- if to add execute to all u,g,o
- ```chmod ugo+x test ```
- or ``` chmod a+x test ```  
#### 2 . Numeric (Absolute ) method : 
- if in a file test  r--|r-x|rwx → existing permission,how to change the permission to rwx|rw-|r--
- r = 4,w = 2,x =1 ,rwx=7
- ``` chmod 764 test ``` →  rwx|rw-|r--  → 7-rwx of owner,6-rw of grop,4 - r of other
- no dependencies on previous permissions
- just apply the permissions you required ,so that is why called absolute method
## Access Control List :
- The disadvantageof chmod is permissions can be applied onlyy for  3 major categories 9 owner,group, and others ).
- ACL is used so that to define permissions to specific users and groups without affecting other users and groups
- so if in a group  sales there are users u1,u2,u3 and group finanace u4,u5,u6 
- if you want to change the permission of the specific user without affecting the permission of the other users then use ACL
- ``` setfacl -m u:u3 :r-- /logic ```  here we are are giving read access to /logic directry without affecting permissions of other users in the group
- ``` setfacl -m u:u1 : r-x /logic ```
- apply acl to group ``` setfacl -m g : sales -w- /logic ```
- setfacl is to apply ACL
- getfacl is to view to
  





  
  
