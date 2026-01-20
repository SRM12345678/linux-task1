Archiving: compile all folders and files in one file
Compression: reduce size of file
c – create new archive
v – verbose
f – filename
z – gzip (reduce file size)
j – bzip2 compression
J – xz compression
x – extract
C – extract at different location
🔍 Check size of a file/directory
du -sh /etc
💾 To create backup with gzip
tar -cvzf backup.tar.gz /etc
🔽 To extract gzip archive
tar -xvzf backup.tar.gz -C /opt
💾 To create backup with bzip2
tar -cvjf backup.tar.bz2 /etc
🔽 To extract bzip2 archive
tar -xvjf backup.tar.bz2 -C /opt
💾 To create backup with xz
tar -cvJf backup.tar.xz /etc
🔽 To extract xz archive
tar -xvJf backup.tar.xz -C /opt
💾 To zip a folder
zip -r backup.zip /etc
🔽 To unzip a folder
unzip backup.zip -d /opt
