## Lab 3: find command-line options

# option 1: -type

1) type d:
Input:
```
[cs15lwi23asi@ieng6-202]:written_2:487$ find -type d
```
Output:
```
.
./non-fiction
./non-fiction/OUP
./non-fiction/OUP/Abernathy
./non-fiction/OUP/Berk
./non-fiction/OUP/Castro
./non-fiction/OUP/Fletcher
./non-fiction/OUP/Kauffman
./non-fiction/OUP/Rybczynski
./travel_guides
./travel_guides/berlitz1
./travel_guides/berlitz2
```

2) type f:
too many files, so changed directory first
Input:
```
[cs15lwi23asi@ieng6-202]:written_2:488$ cd ./non-fiction/OUP/Berk
[cs15lwi23asi@ieng6-202]:Berk:492$ find -type f
```
Ouput:
```
./CH4.txt
./ch1.txt
./ch2.txt
./ch7.txt
```

Using $ find -type d results in the terminal displaying a list of all directories that are in the current directory. 
$ find -type f displays a list of all files in the current directory. This is useful because you can see all the subdirectories in the current directory. 
Or you can see all the files in the entire directory, including the files in the subdirectory. Calling ls -d or ls -f would only give you a list of files/directories
that are in the current directory.

# option 2: -mindepth & -maxdepth

1) -maxdepth 2
Input:
```
[cs15lwi23asi@ieng6-202]:written_2:510$ find -maxdepth 2
```
Output:
```
.
./non-fiction
./non-fiction/OUP
./travel_guides
./travel_guides/berlitz1
./travel_guides/berlitz2
./t.txt
./s.txt
```
2) -mindepth 
Too many files, so added -type d to only show directories. Using -mindepth 2 means that it will go down 2 levels before searching.
Input:
```
[cs15lwi23asi@ieng6-202]:written_2:517$ find -mindepth 2 -type d
```
Ouput:
```
./non-fiction/OUP
./non-fiction/OUP/Abernathy
./non-fiction/OUP/Berk
./non-fiction/OUP/Castro
./non-fiction/OUP/Fletcher
./non-fiction/OUP/Kauffman
./non-fiction/OUP/Rybczynski
./travel_guides/berlitz1
./travel_guides/berlitz2
````

This is useful if you only want to search a certain number of sub directories. Using find -type f would list all files in the directory, including the ones in the
subdirectory. But that can be a lot of files, like with written_2. If you only want to see the files in the first few levels, you would use this. For instance,
in written_2, there are 227 files total. But in the first two levels, there are only 2 files (2 of which are not in the director by default, they are files I created). Or if you want to search in a certain range, you can use both -mindepth and -maxdepth to search a specific range of levels.

# option 3: -size

1) -size +100k:

2) -size +100k -size -75k:

This option lets you search for files based on the size. + means that you want files larger than the given size, - means smaller. 
If you want to search in a range, you need to call -size, and do the minimum first. This is useful because you can search a directory, 
and all the subdirectories for files of a certain size. You need to include the units too, c for byte, k for kilobyte, M for megabyte, and G for gigabyte.

# option 4: mtime, ctime, and ntime

1) -mtime:
Input:
```
[cs15lwi23asi@ieng6-202]:written_2:533$ find -type f -mtime -1   
```
Ouput:
```
./t.txt
./s.txt
```

-mtime means modification time. -1 means less than 1 day. +1 would return files that were last modfied longer than a day ago.

2) -ctime:
Input:
```
[cs15lwi23asi@ieng6-202]:written_2:549$ find -type f -ctime -4 
```
Ouput:
```
./t.txt
./s.txt
```

-ctime means creation time. -4 means in the last four days, so +4 would return files that were last created more than 4 days ago, which would be all files besides these two


3) -atime:
Input:
```
[cs15lwi23asi@ieng6-202]:written_2:552$ find -type f -atime -4
```
Ouput:
```
./t.txt
./s.txt
```

-atime means access time. -4 means in the last four days, so +4 would return files that were last accessed longer than 4 days ago.

These options allow you to search the directory for all files based on the last modification time (mtime), creation time (ctime), or the last time the 
file was accessed (atime). The number that comes after is the number of days. This can be useful if you want to see what files were updated or accessed recently.



# Sources used: 
* For options 1, 2, and 4- [linuxhandbook.com](https://linuxhandbook.com/find-command-examples/)
* For option 3 [geeksforgeeks.org](https://www.geeksforgeeks.org/mindepth-maxdepth-linux-find-command-limiting-search-specific-directory/)
