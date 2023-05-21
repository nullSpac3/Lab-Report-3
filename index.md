## Researching Commands


`find`

* `-mtime` - source: ChatGPT*
    
     `find ../technical -type f -mtime -3`
      
     Searches for files in ../technical that have been modified in the last 3 days
      
      $ find ../technical -type f -mtime -3
      ../technical/ground.txt
      ../technical/test1/file.txt
      ../technical/test1/water.txt
      
     `find ../technical -type d -mtime +5`
     
     Searches for directories in ../technical that have been modified more than 5 days ago
     
      $ find ../technical -type d -mtime +5  
     The reason there is no output from the previous input is because there were no files in the directory that were modified more than 5 days ago.
     
     `-mtime` can be used to sort files depending on "last modified" period. I would like to assume that this options is used in file management, for instance, I think of it as the sort button in windows' file explorer
<br>

* `-empty` - [source]( https://stackoverflow.com/questions/2810838/finding-empty-directories)

     `find ../technical -type f -empty`
     
     Searches for empty files; can be used with `-delete` to delete empty files
     
      $ find ../technical -type f -empty
      ../technical/ground.txt
      ../technical/test1/file.txt
      
     
     `find ../technical -type d -empty`
     
     Searches for empty directories; can be used with `-delete` to delete empty directories 
     
      $ find ../technical -type d -empty
      ../technical/dir2
      
     
     `-empty` can be used with other `find` modifiers such as delete to delete empty files or directories. It could help find unneccesary files and directories to prevent a cluttered workspace and confusion that can arise with having numerous empty files or directories
<br>

* `-delete` - [source]( https://stackoverflow.com/questions/2810838/finding-empty-directories)

    `find ../technical -name "*.txt" -type f -delete`
   
    Deletes files found containing the extension ".txt" 
    
      $ find ../technical -name "*.txt" -type f -delete

    Directory before and after the command was run:
    
      $ ls
      dir2/  fire.txt  test1/  water.txt
      
      $ ls
      dir2/  test1/
    
    Deletes empty directories 
    
      $ $ find . -type d -delete
   
    Directory before and after the command was run:  
      
      $ ls
      dir2/  test1/
      
      $ ls
      
      
    `-delete` can be used with modifiers such as `-empty` to delete target files or directories. Similar to `-empty`, it can be used to nullify confusion. Additionally, it helps remove multiple files of the same extension at once, as oppose to navigating to delete multiple files consecutively. 
     
 <br>
 
* `-type` - source: ChatGPT*

     `find ./technical -type f`
     
     Finds items of f (file) specification
     
      $ find ../technical -type f
      ../technical/air.txt
      ../technical/ground.txt
      ../technical/water.txt
      
     `find ../technical -type d -name "dir2"`
     
     Finds items of d (directory) specification that have the name "dir2"
     
       $ find ../technical -type d -name "dir2"
       ../technical/dir2
    
     `-type` is followed by a character, such as `f` which denotes a file, that represents a file type. It can be used to navigate for specific file types throughout a directory. It can also be combined with the latter two options to execute operations on more specific files

<br>
<br>

## ChatGPT

* For this report, I consulted ChatGPT. The queries I supplied revolved around asking it for options which can be used with the command find. Additionally, I asked it to elaborate on some of those options to further my understanding of each. Here are my queries and ChatGPT's responses: 

<br>

`command line options for find (bash)`
* Here I was just looking for an idea of what interesting options are available to use alongside the find command and I think ChatGPT hit the mark. I ended up utlizing `-mtime` and `-type` because I think they could be used regularly in file management stuff.

<br>

     In Bash, the `find` command is a powerful utility used to search for files and directories within a specified directory hierarchy. It provides a wide range of command-line options to customize the search criteria. Here are some commonly used options for the `find` command:

     1. Search directory:
        ```
        find /path/to/directory
        ```

     2. Specify file type:
        ```
        find /path/to/directory -type f
        ```

     3. Specify directory type:
        ```
        find /path/to/directory -type d
        ```

     4. Search by name (exact match):
        ```
        find /path/to/directory -name "filename"
        ```

     5. Search by name (case-insensitive):
        ```
        find /path/to/directory -iname "filename"
        ```

     6. Search by file extension:
        ```
        find /path/to/directory -name "*.extension"
        ```

     7. Search by file size:
        ```
        find /path/to/directory -size +10M
        ```

     8. Search by modified time (in days):
        ```
        find /path/to/directory -mtime -7
        ```

     9. Execute a command on each found file:
        ```
        find /path/to/directory -exec command {} \;
        ```

     10. Combine multiple search criteria with logical operators:
         - AND operator:
           ```
           find /path/to/directory -name "filename" -type f
           ```

         - OR operator:
           ```
           find /path/to/directory \( -name "file1" -o -name "file2" \)
           ```

         - NOT operator:
           ```
           find /path/to/directory ! -name "filename"
           ```

     These are just a few examples of the options available for the `find` command. You can find more options and detailed information in the `find` command's manual page by running `man find` in your terminal.

<br>

`what does -delete do in bash`
* For this and the following query, I was looking for clarification and examples of using the respective options

<br>

     In Bash, the `-delete` option is used with the `find` command to delete files and directories that match the specified criteria. When combined with the `find` command, the `-delete` option removes the found items from the file system.

     Here's an example of how to use the `-delete` option:

     ```bash
     find ./technical -name "*.txt" -type f -delete
     ```

     In this example, the command searches for regular files (`-type f`) within the `./technical` directory that have the extension ".txt" (`-name "*.txt"`) and then deletes them (`-delete`).

     It's important to exercise caution when using the `-delete` option because it directly removes the matched files or directories from the file system without confirmation. Make sure to double-check the search criteria and be certain of the files or directories you want to delete before using this option.

<br>

`how about -type`

     The `-type` option in the `find` command is used to specify the type of items to search for within the specified directory hierarchy. It allows you to narrow down the search to specific types of files, directories, or other items. Here are some commonly used arguments for the `-type` option:

     - `-type f`: This searches for regular files.
     - `-type d`: This searches for directories.
     - `-type l`: This searches for symbolic links.
     - `-type b`: This searches for block special files (usually devices).
     - `-type c`: This searches for character special files (usually devices).
     - `-type s`: This searches for socket files.
     - `-type p`: This searches for named pipes (FIFOs).

     Here's an example to illustrate the usage of the `-type` option:

     ```bash
     find ./technical -type f -name "*.txt"
     ```

     In this example, the command searches for regular files (`-type f`) within the `./technical` directory that have the extension ".txt" (`-name "*.txt"`). It will only match and display regular files with the specified name pattern.

     By utilizing the `-type` option, you can customize your search to focus on specific types of files or directories within the given directory hierarchy.
