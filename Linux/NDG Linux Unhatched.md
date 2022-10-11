# NDG Linux Unhatched

This chapter will cover the following exam objectives:

**2.1: LPI Linux Essentials 010-160: Command Line Basics**

Weight: 3

Basics of using the Linux command line.

**Key Knowledge Areas:**

-   Command Line Syntax  
    [Section 2](https://content.netdevgroup.com/contents/unhatched/400/2) | [Section 2.1](https://content.netdevgroup.com/contents/unhatched/400/2.1) | [Section 2.2](https://content.netdevgroup.com/contents/unhatched/400/2.2)

**2.3: LPI Linux Essentials 010-160: Using Directories and Listing Files**

Weight: 2

Navigation of home and system directories and listing files in various locations.

**Key Knowledge Areas:**

-   Files, Directories  
    [Section 3](https://content.netdevgroup.com/contents/unhatched/400/3) | [Section 4](https://content.netdevgroup.com/contents/unhatched/400/4) | [Section 5](https://content.netdevgroup.com/contents/unhatched/400/5)
-   Absolute and Relative Paths  
    [Section 4](https://content.netdevgroup.com/contents/unhatched/400/4)

**2.4: LPI Linux Essentials 010-160: Creating, Moving, and Deleting Files**

Weight: 2

Create, move and delete files and directories under the home directory.

**Key Knowledge Areas:**

-   Files and Directories  
    [Section 10](https://content.netdevgroup.com/contents/unhatched/400/10) | [Section 11](https://content.netdevgroup.com/contents/unhatched/400/11) | [Section 11.1](https://content.netdevgroup.com/contents/unhatched/400/11.1) | [Section 12](https://content.netdevgroup.com/contents/unhatched/400/12)

**3.2: LPI Linux Essentials 010-160: Searching and Extracting Data from Files**

Weight: 3

Search and extract data from files in the home directory.

**Key Knowledge Areas:**

-   Basic Regular Expressions  
    [Section 14.1](https://content.netdevgroup.com/contents/unhatched/400/14.1)

**3.3: LPI Linux Essentials 010-160: Turning Commands Into a Scripts**

Weight: 4

Turning repetitive commands into simple scripts.

**Key Knowledge Areas:**

-   Awareness of common text editors  
    [Section 21](https://content.netdevgroup.com/contents/unhatched/400/21)

**4.3: LPI Linux Essentials 010-160: Where Data is Stored**

Weight: 3

Where various types of information are stored on a Linux system.

**Key Knowledge Areas:**

-   Processes  
    [Section 17](https://content.netdevgroup.com/contents/unhatched/400/17)

**4.4: LPI Linux Essentials 010-160: Your Computer on the Network**

Weight: 2

Querying vital networking configuration and determining the basic requirements for a computer on a Local Area Network (LAN).

**Key Knowledge Areas:**

-   Internet  
    [Section 16](https://content.netdevgroup.com/contents/unhatched/400/16)
-   Network  
    [Section 16](https://content.netdevgroup.com/contents/unhatched/400/16)

**5.1: LPI Linux Essentials 010-160: Basic Security and Identifying User Types**

Weight: 2

Various types of users on a Linux system.

**Key Knowledge Areas:**

-   Root Users  
    [Section 6](https://content.netdevgroup.com/contents/unhatched/400/6)
-   System Users  
    [Section 19](https://content.netdevgroup.com/contents/unhatched/400/19)

**5.3: LPI Linux Essentials 010-160: Managing File Permissions and Ownership**

Weight: 2

Understanding and manipulating file permissions and ownership settings.

**Key Knowledge Areas:**

-   File and Directory Permissions  
    [Section 7](https://content.netdevgroup.com/contents/unhatched/400/7) | [Section 8](https://content.netdevgroup.com/contents/unhatched/400/8)
-   File and Directory Ownership  
    [Section 9](https://content.netdevgroup.com/contents/unhatched/400/9)


> Linux is operating system software that runs on a hardware computer system. An operating system is software that allows other programs like word processors and web browsers to be installed and run on a computer

> **The Linux command-line is a text-based interface that accepts commands that you type into it**.

## Content

### Printing Working Directory
### Changing Directories
### Listing Files
`ls`
### Administrative Access 	
`su -`, 	`sudo`
### Permissions
### Changing File Permissions 
`chmod [<SET><ACTION><PERMISSIONS>]... FILE`
### Changing File Ownership
`chown [OPTIONS] [OWNER] FILE`
### Viewing Files
```bash
	cat [OPTIONS] [FILE]
	head -n number_of_lines [OPTIONS] [FILE]
	tail -n number_of_lines [OPTIONS] [FILE]
```
### Copying Files
`cp [OPTIONS] SOURCE DESTINATION`

>**Consider This**
> 
	Permissions can have an impact on file management commands, such as the `cp` command. In order to copy a file, it is necessary to have execute permission to access the directory where the file is located and the read permission for the file being copied.
	It is also necessary to have write and execute permission on the directory the file is being copied to. Typically, there are two places where you should always have write and execute permission on the directory: your home directory and the `/tmp` directory.

The `dd` command is a utility for copying files or entire partitions at the bit level.
`dd [OPTIONS] OPERAND`

### Moving Files
`mv SOURCE DESTINATION`

>**Consider This**
Permissions can have an impact on file management commands, such as the `mv` command. Moving a file requires write and execute permissions on both the origin and destination directories.

### Removing Files
`rm [OPTIONS] FILE`

>**Consider This**
Permissions can have an impact on file management commands, such as the `rm` command.
To delete a file within a directory, a user must have write and execute permission on a directory. Regular users typically only have this type of permission in their home directory and its subdirectories.

### Filtering Input
`grep [OPTIONS] PATTERN [FILE]`

### Regular Expressions

### Basic Patterns

### Shutting Down 
`shutdown [OPTIONS] TIME [MESSAGE]`

### Network Configuration
`ifconfig [OPTIONS]`

The `ifconfig` command can also be used to temporarily modify network settings. Typically these changes should be permanent, so using the `ifconfig` command to make such changes is fairly rare.

The `ping` command is used to verify connectivity between two computers. It does this by sending packets to another machine on a network. If the sender receives a response it should be possible to connect to that machine.

By default, the `ping` command will continue sending packets until the break command (**CTL** + **C**) is entered at the console. To limit how many pings are sent, use the `-c` option followed by the number of pings to be sent. The example below shows `ping` being limited to 4 iterations with `-c 4`.

### Viewing Processes
`ps [OPTIONS]`

Instead of viewing just the processes running in the current terminal, users may want to view every process running on the system. The `-e` option will display every process

Typically, the `-f` option is also used as it provides more detail in the output of the command, including options and arguments. Look for the `ps` command on the last line, the `CMD` column now includes the options used

### Package Management
> Package management is a system by which software can be installed, updated, queried or removed from a filesystem. In Linux, there are many different software package management systems, but the two most popular are those from Debian and Red Hat. The virtual machines for this course use Ubuntu, a derivative of Debian.

At the lowest level of the Debian package management system is the `dpkg` command. This command can be tricky for novice Linux users, so the Advanced Package Tool, `apt-get`, a front-end program to the `dpkg` tool, makes management of packages even easier.

```bash
sudo apt-get update
apt-cache search [keyword]
apt-get install [package]
apt-get remove [package]
apt-get purge [package]
```

The `apt-get` command is able to either remove or purge a package. The difference between the two is that purging deletes all package files, while removing deletes all but the configuration files for the package.

An administrator can execute the `apt-get remove` command to remove a package or the `apt-get purge` command to purge a package completely from the system.

### Updating User Passwords
`passwd [OPTIONS] [USER]`

### Redirection
When it comes to command input and output there are three paths, or “tracks”. These paths are called file descriptors. The first file descriptor is standard input, abbreviated as STDIN. Standard input is the information the command receives and processes when it is executed, essentially what a user types on the keyboard. The second file descriptor is standard output, abbreviated as STDOUT. Standard output is the information that the command displays, the output of the command. The last file descriptor is standard error, abbreviated as STDERR. STDERR, are the error messages generated by commands that are not correctly executed. 

### Text Editor
- Command Mode Movement
- Command Mode Actions
- Insert Mode 
- Ex Mode
- 