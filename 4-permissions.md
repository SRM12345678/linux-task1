Linux File Permissions
Permissions determine who can access files

And specify who can read, write, modify files/directories on a system

Note : Use following commands to check File/Dir permissions

ls -l
ll
to check particular Dir permission

ll -d dirname
to check particular file permission

ll filename
ls -ltr
image
No.	Attribute	Description
1	File Type	Indicates the type of file (normal file, directory, link, block, character, pipe).
2	Owner Permissions	Permissions granted to the owner of the file/directory (read, write, execute).
3	Group Permissions	Permissions granted to the group associated with the file/directory.
4	Other User Permissions	Permissions granted to other users (not owner or group).
5	Link Count	The number of links or references to the file.
6	Owner of File/Directory	The username of the owner.
7	Group Owner of File/Directory	The group associated with the file/directory.
8	File Size	Size of the file in bytes.
9	Creation Date and Time	The date and time when the file or directory was created or last modified.
10	File/Directory Name	The name of the file or directory.
File Types in Linux
Symbol	File Type	Description
-	Normal file	Text files, binary files, etc.
d	Directory	Represents a folder containing other files/folders.
l	Link file	Symbolic link pointing to another file or folder.
b	Block device file	Used for block storage devices like hard disks.
c	Character device file	Handles data character by character, e.g., keyboard.
P	Pipe	Used for inter-process communication.
Ownership in Linux
In Linux, file ownership is divided into three categories:

Owner: The user who created the file.
Group: The primary group of the file owner.
Other: All other users on the system.
Permission Breakdown
Permission	Symbol	Value	Description
Read	r	4	Open, view, or list the file/directory.
Write	w	2	Edit or modify the file.
Execute	x	1	Run the file as a program.
Example: Change Ownership
Scenario
The directory demo is owned by user root. To change ownership to user abhi, use the following commands:

Change Owner
syntax: chown username filename

chown abhi demofile.txt
Change Group Owner
syntax: chgrp groupname filename

chgrp dev demofile.txt
Change Owner and Group Simultaneously
chown user:Grp demofile.txt
Umask
Default Permissions
The umask command is used to set default permissions for files and directories.

Root User: umask 022
File Permissions: 644 → rw- r-- r--
Directory Permissions: 755 → rwx r-x r-x
Example (Directory):
Maximum permission - Default permission = umask

777
−
755
=
022
777
−
032
=
745
Example (File):
Maximum permission - Default permission = umask

666
−
644
=
022
Local User: umask 002
File Permissions: 664 → rw- rw- r-- → 
666
−
664
=
002
Directory Permissions: 775 → rwx rwx r-x → 
777
−
775
=
002
Root User:
File Permissions: 644 → rw- r-- r--
Directory Permissions: 755 → rwx r-x r-x
Local User: 
File Permissions: 664 → rw- rw- r--
Directory Permissions: 775 → rwx rwx r-x
Root User
File Permissions: 
644
 (
rw- r-- r--
)
Symbolic Mode:
chmod u=rw,g=r,o=r demo.txt
Numeric Mode:
chmod 644 demo.txt
Directory Permissions: 
755
 (
rwx r-x r-x
)
Symbolic Mode:
chmod u=rwx,g=rx,o=rx <directory>
Numeric Mode:
chmod 755 <directory>
Local User
File Permissions: 
664
 (
rw- rw- r--
)
Symbolic Mode:
chmod u=rw,g=rw,o=r demo.txt
Numeric Mode:
chmod 664 demo.txt
Directory Permissions: 
775
 (
rwx rwx r-x
)
Symbolic Mode:
chmod u=rwx,g=rwx,o=rx <directory>
Numeric Mode:
chmod 775 <directory>
ACL: Access Control List
Access Control List (ACL) is used to grant specific permissions to users for particular files or directories.

Commands:
Set Permissions:
  setfacl -m u:username:rwx filename
View Permissions

getfacl filename
Remove Permissions:

setfacl -x u:username filename
Comparison of Hard Link (HL) and Soft Link (SL)
image

Aspect	Hard Link (HL)	Soft Link (SL)
Purpose	Acts as a backup.	Acts as a shortcut.
File Size	Same as the original file.	Different from the original file.
Inode Number	Same as the original file.	Different from the original file.
File Deletion	The hard link remains unaffected if the original file is deleted.	The soft link becomes invalid if the original file is deleted.
Directories	Hard links to directories are not possible.	Soft links to directories are possible.
Link Count	Affects the link count (increases or decreases by 1.	Does not affect the link count.
Hard Link Command
ln filename hardlink
Soft Link File
ln -s filename softlink
