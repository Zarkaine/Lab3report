## Lab 3: find command-line options

# option 1: -type

-type d:

-type f:

Using $ find -type d results in the terminal displaying a list of all directories that are in the current directory. 
$ find -type f displays a list of all files in the current directory. This is useful because you can see all the subdirectories in the current directory. 
Or you can see all the files in the entire directory, including the files in the subdirectory. Calling ls -d or ls -f would only give you a list of files/directories
that are in the current directory.

# option 2: -maxdepth

This is useful if you only want to search a certain number of sub directories. Using find -type f would list all files in the directory, including the ones in the
subdirectory. But that can be a lot of files, like with written_2. If you only want to see the files in the first few levels, you would use this. For instance,
in written_2, there are 227 files total. But in the first two levels, there are only 2 files (2 of which are not in the director by default, they are files I created).

# option 3: -size

-size +100k:

-size +100k -size -75k:

This option lets you search for files based on the size. + means that you want files larger than the given size, - means smaller. 
If you want to search in a range, you need to call -size, and do the minimum first. This is useful because you can search a directory, 
and all the subdirectories for files of a certain size. You need to include the units too, c for byte, k for kilobyte, M for megabyte, and G for gigabyte.

# option 4: mtime, ctime, and ntime

-mtime:

-ctime:

-atime:

These options allow you to search the directory for all files based on the last modification time (mtime), creation time (ctime), or the last time the 
file was accessed (atime). The number that comes after is the number of days. This can be useful if you want to see what files were updated or accessed recently.




Source used: [linuxhandbook.com](https://linuxhandbook.com/find-command-examples/)
