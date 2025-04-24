# 🐧 Linux Fundamentals

This file contains notes on fundamental Linux concepts, distributions, setup, and package managemer.

### 🔧 Linux Concepts

- **Operating System (OS)**: A collection of applications and programs that run together, allowing users and applications to interact with hardware.
- **Hardware**: Physical components like CPU, storage, memory, and networking interfaces.
- **Users and Applications**: Entities that interact with hardware.
- **Applications**: Perform tasks such as process management, memory management, and network management.
- **OS as a Bridge**: Acts as an intermediary between users and hardware.

### 🖥️ Types of Operating Systems
#### 1. Graphical User Interface (GUI)

- Applications
- Shell
- System Packages and System Libraries
- Kernel
- Hardware
#### 2. Command Line Interface (CLI)

- Shell
- System Packages and System Libraries
- Kernel
- Hardware
  ### 🐧 Linux Distributions

Linux is open-source, allowing companies to create their own distributions by adding custom functionalities. Examples include:

- **Ubuntu**: Popular and beginner-friendly.
- **CentOS**
- **Red Hat**

Since the underlying system packages and libraries are consistent, applications running on Ubuntu are likely to run on Red Hat as well.
###🏗️ Structure of Linux

#### 🖥️ Hardware

- Consists of the physical components required to run a machine.

#### 🧠 Kernel

- Converts high-level language to low-level language and vice versa, enabling user interaction with the hardware.
- Manages interactions with hardware, including:
  - Process management
  - Memory management
  - Disk management
  - Network management

#### 📚 System Packages and System Libraries

- A **system library** is a collection of pre-written code that developers can use to perform common tasks in their programs, such as displaying text, handling files, or performing calculations.
- These libraries provide a way for applications to interact with the operating system's core functions without needing to write complex code from scratch.

#### 🖥️ Shell

- A small program that provides a command-line interface to the user.
- The point where the OS accepts and validates commands.

#### 🧩 Application

- Converts graphical gestures into command-line instructions and vice versa.
### 🧾 Commands

- **Command**: An instruction or set of instructions that must be executed to produce a valid output.

#### `ls` Command

- **`ls`**: Lists the files in the current directory.
- **`ls -a`**: Lists all files, including hidden ones (those starting with a dot).
- **`ls -l`**: Provides a detailed listing of files, including permissions, ownership, size, and modification date.
#### Prompt Symbols

- **`#`**: Indicates execution as the root user, who has full administrative privileges.
- **`$`**: Indicates execution as a normal user with limited access.
#### Example 

```bash
root@localhost dir1#
```
### 🖥️ History of Operating Systems


- **1960 – UNIX**
  - First operating system developed.

- **1970 – MINIX**
  - Partially open-source.

- **1980 – Microsoft Windows**
  - Microsoft released Windows OS with a GUI, making interaction easy.

- **1990 – Linux Kernel**
  - First popular open-source OS that is competitive with Windows or better at some levels.

- **2025 – Linux Dominance**
  - 90% of production workloads operate on Linux OS.
### Why Linux?

#### Reasons to Choose Linux

1. **Open Source**
   - Linux is open-source, allowing users to view, modify, and distribute the source code freely.

2. **Community-Driven Development**
   - Instead of being backed by a single company, Linux is supported by a global community of developers. Their active contributions ensure that Linux remains secure and up-to-date.

3. **Enhanced Security**
   - Linux is considered more secure compared to other operating systems due to its transparent development process and robust permission structures.

---

#### Linux Distributions

- **Popular Distributions**: CentOS, Ubuntu, Red Hat, etc.

- **Customization**
  - Since Linux is open-source, companies can modify and add their own functionalities, resulting in various tailored distributions.

- **Compatibility**
  - The underlying system packages and libraries are consistent across distributions, so an application running on Ubuntu will most likely run on Red Hat as well.

- **User-Friendly**
  - Ubuntu is known for its popularity and beginner-friendly interface, making it a great choice for newcomers to Linux.





### ⚙️ Linux Setup

#### On AWS

- Spin up an EC2 instance with Ubuntu OS.

#### On Windows

- Install Windows Subsystem for Linux (WSL):
  ```bash
  .wsl --install:this command install and creates a linux like environment in our windows machen
  .do restart
  .in cli : run wsl--> this strats ubuntu
  ```
### PACKAGE MANAGER


- Companies often build upon open-source Linux by adding their own libraries and package managers, resulting in new distributions.


#### Package Manager Functions

- **Installation**: Deploy or install dependencies (e.g., install Java, Python).
- **Upgrade**: Update to newer versions of packages.
- **Removal**: Delete specific versions of packages.
- **Maintenance**: Manage and maintain software packages.

#### Ubuntu's Package Manager: `apt`

- **Installation Example**:
  ```bash
  sudo apt install python3
  ```

