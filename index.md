## Researching Commands


`find`

* `-mtime`

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

* `-empty`

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

* `-delete`

    `find ../technical -name "*.txt" -type f -delete`
   
    Deletes files found containing the extension ".txt" 
    
      $ find ../technical -name "*.txt" -type f -delete

    Deletes empty directories 
    
      $ find ../techincal -type d -empty -delete
      
    `-delete` can be used with modifiers such as `-empty` to delete target files or directories
     
 <br>
 
* `-type`

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
