
# Implementation example: Unix file permissions
- Everything is treated as a file—directories, disks, rinters, network sockets, etc
- Every file is owned by a group and a user
- Three sets of permissions for every file: user, group, and other
    - Notation: `rwxrwxrwx`, sets of 3 for user, gorup and other
        - Dashes for permissions that are not granted
    - Files can have only one user and one group permission specified
- Special treatment for directories
    - Read: list files
    - Write: create/delete/rename files
    - Execute: enter and rwx files inside the directory

## Lookup
- UID 0 is privileged and can access regardless of permissions
- Subject's _effective_ uid (euid) is matched against the file owners
    - uid can be temporarily elevated
- Best match is applied—user, then group, then other
- You can be denied access even if you match another set; for example, if your access as a user is denied, but your access as a group is allowed, you will still be denied.

## Special Permissions
- "sticky": in a sticky directory, only the owner can delete/rename a file
- "set UID" (suid): always executes a program as the file's _owner_'s uid
    - Example: `passwd` command—allows users to change their password by executing the program as root
- "set GID" (sgid): executes program with egid = the owner's gid

## Unix Permission Commands

### `chmod`
- `u`, `g`, `o` — specify which part to modify permissions of
- `+`, `-`, `=` — specify how to modify permissions
> Example: `chmod g+w file.txt` — adds write permission for the group to file.txt

You can also specify octal digits
- First octal digit is special permissions—`1` is sticky, `2` is setgid, `4` is setuid
- Second, third, and fourth octal digits are for user, group, and other respectively
> Example: `chmod 0644 file` sets permissions to `rw-r--r--`

### `newgrp`
- New files are created with your current working group
- `newgrp` command allows you to change your current working group

### `chown`
- Changes the owner of a file
- Only root can use this command

### `chgrp`
- Changes the group owner of an existing file
- Only the owner of the file can do this, and they can only change it to another group they are a part of

### `umask` variable
- The `umask` determines the permissions to give to new files
- The new files' permissions are `0666 & ~umask`, i.e. mask by the inverse of the umask
- Ex. `umask=022`, file has mode `0644`
