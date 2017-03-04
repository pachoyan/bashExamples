## Command ls

The examples have been done with the directory `dir` of this section.
The directory `dir`has the next files:
- `file1.txt` with content 'Hello World!'
- `file2.txt` with content 'Hello World 2!'
- `.file1.txt` with content 'Hello World Hide!'
- `directory` with content file_directory.txt

----
### man ls

Shows the manual.

### ls

List directory contents

- Output:

    `directory file1.txt file2.txt`

### ls -a, -all

List directory contents and don't ignore hidden files (files start with `.`)

- Output:

  `. .. directory .file1.txt file1.txt file2.txt`
  
- Notes: 

   -  `.`  represents the actual directory (It is created automatically with the directory)
  
   -  `..` represents the parent directory (It is also created automatically with the directory)
   
   - `.file1.txt` is a hidden file  starts with dot (`.`) 
  
