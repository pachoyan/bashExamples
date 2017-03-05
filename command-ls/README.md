## Command ls

The examples have been done with the directory `dir` of this section.
The directory `dir`has the next files:
- `file1.txt` with content 'Hello World!'
- `file2.txt` with content 'Hello World 2!'
- `.file1.txt` with content 'Hello World Hide!'
- `file1.txt~` backup file with content 'Hello World!'
- `directory` with content file_directory.txt

----
### man ls

Shows the manual.

### ls

List directory contents

- Output:
```
      directory  file1.txt  file1.txt~  file2.txt
```      

### ls -a 

It is a shortening of `ls --all` which does the same.
List directory contents and don't ignore hidden files (files which starts with `.`) including `.` and `..`.

- Output:
```
    .  ..  directory  .file1.txt  file1.txt  file1.txt~  file2.txt
```
- Notes: 

   -  `.`  represents the actual directory (It is created automatically with the directory)
  
   -  `..` represents the parent directory (It is also created automatically with the directory)
   
   - `.file1.txt` is a hidden file  starts with dot (`.`) 
   

### ls -A

It is a shortening of `ls --almost-all` which does the same.
List directory contents and list hidden files  but it doesn't list `.` and `..`.

- Output:
```
      directory  .file1.txt  file1.txt  file1.txt~  file2.txt
```     

### ls -l --author

It goes with `-l` command and list the author of each file.
- Output: 

   ```
   total 16
drwxrwxr-x 2 osboxes osboxes osboxes 4096 Mar  4 10:53 directory
-rw-rw-r-- 1 osboxes osboxes osboxes   13 Mar  4 10:36 file1.txt
-rw-rw-r-- 1 osboxes osboxes osboxes   13 Mar  4 13:00 file1.txt~
-rw-rw-r-- 1 osboxes osboxes osboxes   15 Mar  4 10:50 file2.txt
   ```


### ls -b

It is a shortening of `ls --escape` which does the same.
It prints C-style escapes for nongraphic characters
 
- Output
```
      directory  file1.txt  file1.txt~  file2.txt
``` 
 
- Notes:
 
**At the moment** I've tried with some files with names like: 

    \*\?\¿\º\ª\?\¿\&\%\$\·SpecialCharacterfile.txt
    
and the output with `ls -b` lists the same as `ls`. The output is the filename with the special characters. So the file above will be list like next:

    *?¿ºª?¿&%$·SpecialCharacterfile.txt
  

### ls -l --block-size={SIZE}

It goes with `-l` command and scales size. SIZE is an integer and optional unit. 
Units are `K, M, G, T, P, E, Z, Y` or `KB, MB, GB, TB,...`

Rounds to the high, in case we put MB and it is less than 1MB it will show 1MB.

- Output (With K or KB: `ls -l --block-size=K`)


   ```
   total 16K
drwxrwxr-x 2 osboxes osboxes 4K Mar  4 10:53 directory
-rw-rw-r-- 1 osboxes osboxes 1K Mar  4 10:36 file1.txt
-rw-rw-r-- 1 osboxes osboxes 1K Mar  4 13:00 file1.txt~
-rw-rw-r-- 1 osboxes osboxes 1K Mar  4 10:50 file2.txt
   ```
   
- Notes:

  - With M or MB lists 1M in all files because are less than 1MB - It will be the same with G, T and so on.
  
    ```
   total 1M
drwxrwxr-x 2 osboxes osboxes 1M Mar  4 10:53 directory
-rw-rw-r-- 1 osboxes osboxes 1M Mar  4 10:36 file1.txt
-rw-rw-r-- 1 osboxes osboxes 1M Mar  4 13:00 file1.txt~
-rw-rw-r-- 1 osboxes osboxes 1M Mar  4 10:50 file2.txt
    ```
  - If it is used without -l the list, for example `ls --block-size=K` the output will be the same as `ls`
  

### ls -B
  
It is a shortening of `ls --ignore-backups` which does the same.
It doesn't list files ending with `~`.
  
- Output:
```
  directory  file1.txt  file2.txt
```
### ls -c

It sorts the list by time, newest first.

- Output:
```
  file1.txt~  directory  file2.txt  file1.txt
```
  
### ls -lt -c

It sorts the list by time using the long format.

- Output:

```
total 16
-rw-rw-r-- 1 osboxes osboxes   13 Mar  4 13:00 file1.txt~
drwxrwxr-x 2 osboxes osboxes 4096 Mar  4 10:53 directory
-rw-rw-r-- 1 osboxes osboxes   15 Mar  4 10:50 file2.txt
-rw-rw-r-- 1 osboxes osboxes   13 Mar  4 10:39 file1.txt
```

### ls -l -c

It shows the ctime and sorts by name using the long format.

- Output:

```
total 16
drwxrwxr-x 2 osboxes osboxes 4096 Mar  4 10:53 directory
-rw-rw-r-- 1 osboxes osboxes   13 Mar  4 10:39 file1.txt
-rw-rw-r-- 1 osboxes osboxes   13 Mar  4 13:00 file1.txt~
-rw-rw-r-- 1 osboxes osboxes   15 Mar  4 10:50 file2.txt
```

### ls -C

It lists entries by columns. 

- Output:
``` 
   directory  file1.txt  file1.txt~  file2.txt`
```
- Notes:

  - It is possible that the output will be the same as the simple `ls`. So if you want to see how it works use a pipeline with <a href="https://github.com/pachoyan/bashExamples/tree/master/command-less">less</a> like next `ls -C | less`. The output will be:
```  
     directory  file1.txt  file1.txt~  file2.txt
```
  - But if you use the same command above without -C, like `ls | less`  it will be list by lines:
  
```
directory  
file1.txt  
file1.txt~  
file2.txt
```
### ls --color={WHEN}

Colorize the output. The available values are:  `always`, `yes`, `force`, `never`, `no`, `none`, `auto`, `tty`, `if-tty`.

Output (`ls --color=never`):

``` 
   directory  file1.txt  file1.txt~  file2.txt`
```

- Notes:

  - Using color to distinguish file types is disabled both by  default  and with  `--color=never`.  
  
  - With `--color=auto`, ls emits color codes only when standard output is connected to a terminal. 
  
  - The `LS_COLORS`  environment variable can change the settings. Use the <a href="https://github.com/pachoyan/bashExamples/tree/master/command-dircolors">dircolors</a> command to set it.
  
  
### ls -d

It is a shortening of `ls --directory` which does the same.
It lists the directory entries instead of contents, and do not derefrence symbolic links.

If you use ls -d you'll see the output `.` which is the current folder.
It can be used to see a folder adding a parameter of the folder name: `ls --directory anydirectory`

An useful example of how use it could be adding the `-l` argument, so you'll see more info about the current folder or the folder you pass an argument.

So if you use `ls -ld`.

- Output (`ls -ld`):

   `drwxrwxr-x 3 osboxes osboxes 4096 Mar  5 09:20 .`
   
- Output (`ls -ld directory`)

    `drwxrwxr-x 2 osboxes osboxes 4096 Mar  4 10:53 directory/`

- Notes: 
   - If you want to use list the directories in the current folder you could use `ls -d */` 
      - Output: 
      
         `directory/`       
