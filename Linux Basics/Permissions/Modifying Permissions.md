Changing permission can be done with `chmod (change mode)`.
Pick the set of permissions you want to change, user, group other. `+` is used to add the permission and `-` to remove those.
## Adding Permissions

```bash
$  ls -l myfile

-rw-r--r-- 1 yash yash 0 Jun 23 15:09 myfile

$  chmod u+x myfile

$  ls -l myfile
-rwxr--r-- 1 yash yash 0 Jun 23 15:09 myfile

```
The above command i.e. `chmod u+x` is saying that change mode to user permission add the permission to **execute** the file.

## Removing Permissions

```bash
$  chmod u-x myfile

$  ls -l myfile

-rw-r--r-- 1 yash yash 0 Jun 23 15:09 myfile

```
Opposite of adding we are removing the permission of execute using `-` sign.

## Adding Multiple Permission Bits on File

```bash
$  chmod ug+w myfile

$  ls -l myfile

-rw-rw-r-- 1 yash yash 0 Jun 23 15:09 myfile
```
Here we are adding **execute** permission to user and group both at same time.

## Adding Permissions Numerically

This method allows you to change permissions all at once. Instead of using r, w, or x to represent permissions, you'll use a numerical representation for a single permission set.
So no need to specify the group with g or the user with u.
The numerical representations are seen below:

- 4: read permission
- 2: write permission
- 1: execute permission

for e.g.
```bash
$  chmod 755 myfile

$  ls -l myfile

-rwxr-xr-x 1 yash yash 0 Jun 23 15:09 myfile
```

Here , the `7` represents the user bit and why *7*?
So , 7 is basically addition of all the permission i.e. 
4 (read) + 2 (write) + 1 (execute) = 7  (rwx)
For *5*?
4 (read) + 1 (execute) = 5 (r-x)
So the output is:
```bash
-rwx | r-x | r-x 
```

