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
      
     `-mtime` can be used to sort files depending on "last modified" period
<br>

* `-empty` - [source]( https://stackoverflow.com/questions/2810838/finding-empty-directories)

     `find ../technical -type f -empty`
     
     Searches for empty files; can be used with `-delete` to delete empty files
     
      $ find ../technical -type f -empty
      ../technical/ground.txt
      ../technical/test1/file.txt
      
     
     `find ../technical -type d -empty`
     
     Searches for empty files; can be used with `-delete` to delete empty directories 
     
      $ find ../technical -type d -empty
      ../technical/dir2
      
     
     `-empty` can be used with other `find` modifiers such as delete to delete empty files or directories
<br>

* `-delete` - [source]( https://stackoverflow.com/questions/2810838/finding-empty-directories)

    `find ../technical -name "*.txt" -type f -delete`
   
    Deletes files found containing the extension ".txt" 
    
      $ find ../technical -name "*.txt" -type f -delete

    Deletes empty directories 
    
      $ find ../techincal -type d -empty -delete
      
    `-delete` can be used with modifiers such as `-empty` to delete target files or directories
     
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


<br>
<br>

* For this report, I consulted ChatGPT. The queries I supplied revolved around asking it for options which can be used with the command find. Additionally, I asked it to elaborate on some of those options to further my understanding of each. Here are my queries and ChatGPT's responses: 

`command line options for find (bash)`

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


`what does -delete do in bash`

     In Bash, the `-delete` option is used with the `find` command to delete files and directories that match the specified criteria. When combined with the `find` command, the `-delete` option removes the found items from the file system.

     Here's an example of how to use the `-delete` option:

     ```bash
     find ./technical -name "*.txt" -type f -delete
     ```

     In this example, the command searches for regular files (`-type f`) within the `./technical` directory that have the extension ".txt" (`-name "*.txt"`) and then deletes them (`-delete`).

     It's important to exercise caution when using the `-delete` option because it directly removes the matched files or directories from the file system without confirmation. Make sure to double-check the search criteria and be certain of the files or directories you want to delete before using this option.
