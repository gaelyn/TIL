If you have a commit and you want to see what changed from the previous commit:
`commit abc123`  

`$ git checkout abc123~`  
This will checkout the commit just before this one.  
`$ git diff abc123` will show the diff between `abc123` and the previous commit. 
