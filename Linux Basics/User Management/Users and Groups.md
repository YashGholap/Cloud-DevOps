In any traditional operating system, there are users and groups. They exist solely for access and permissions. When running a process, it will run as the owner of that process whether that is Jane or Bob. File access and ownership is also permission dependent. You wouldn't want Jane to see Bob's documents and vice versa.

## Root
This is the main user or system user which have the access of the system. we can use `su` to switch from other user to root. we need to know the password to the root.

*Note: The system doesn't let every single Joe Schmoe run commands as the superuser, so how does it know? There is a file called the /etc/sudoers file, this file lists users who can run sudo. You can edit this file with the **visudo** command.*

## /etc/passwd
Remember that usernames aren't really identifications for users. The system uses a user ID (UID) to identify a user. To find out what users are mapped to what ID, look at the /etc/passwd file.
```bash
sudo cat /etc/passwd
```
This file shows you a list of users and detailed information about them. For example, the first line in this file most likely looks like this:
```bash
root:x:0:0:root:/root:/bin/bash
```
There are many fields separated by colons that tell you additional information about the user, let's look at them all:
	1. Username
	2. User's password - not stored in this file. Stored in `/etc/shadow`. If `x` that means the password is stored in the /etc/shadow file, a `*` means the user doesn't have login access and if there is a blank field that means the user doesn't have a password.
	3. The user ID
	4. he group ID
	5. GECOS field
	6. User's home directory
	7. User's shell

## /etc/shadow
The /etc/shadow file is used to store information about user authentication. It requires superuser read permissions.
```bash
sudo cat /etc/shadow
```
You'll notice that it looks very similar to the contents of /etc/passwd, however in the password field you'll see an encrypted password. The fields are separated by colons as followed:
1. Username
2. Encrypted password
3. Date of last password changed - expressed as the number of days since Jan 1, 1970. If there is a 0 that means the user should change their password the next time they login
4. Minimum password age - Days that a user will have to wait before being able to change their password again
5. Maximum password age - Maximum number of days before a user has to change their password
6. Password warning period - Number of days before a password is going to expire
7. Password inactivity period - Number of days after a password has expired to allow login with their password
8. Account expiration date - date that user will not be able to login
9. Reserved field for future use

## /etc/group
Another file that is used in user management is the /etc/group file. This file allows for different groups with different permissions.
```bash
$ cat /etc/shadow

root:*:0:pete
```
Very similar to the /etc/password field, the /etc/group fields are as follows:
1. Group name
2. Group password - there isn't a need to set a group password, using an elevated privilege like sudo is standard. A "*" will be put in place as the default value.
3. Group ID (GID)
4. List of users - you can manually specify users you want in a specific group

## User Management tool
1. **Adding Users**:
	- You can use the adduser or the useradd command. The adduser command contains more helpful features such as making a home directory and more.
```bash
sudo useradd bob
```
You'll see that the above command creates an entry in /etc/passwd for bob, sets up default groups and adds an entry to the /etc/shadow file.
2. **Removing Users**:
	 - remove a user, you can use the userdel command.
```bash
sudo userdel bob
```
This basically does its best to undo the file changes by useradd.
3. **Changing Passwords**:
```bash
passwd bob
```
This will allow you to change the password of yourself or another user (if you are root).
