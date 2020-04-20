---
layout: post
title:  "Python 3 - Working with files"
date:   2020-04-20 09:43:04 -0500
categories: python
featured-image: roll-up-doors.jpg
permalink: /python/files
---

## Open , Read, and Close a file

```
# open the file
file = open("file.txt")


# will print the first line and then each time it is ran print the next line
print(file.readline())  

# will print the remaining lines in the file
print(file.read()) 

# close the file
file.close()

# if you use with block you do not have to close the file since python does it automatically at the end of the block
with open("file.txt") is file:
    print(file.readline())

```

## Iterating through file
```
### making all caps
with open("file.txt") as file:
    for line in file:
        print(line.upper())

# removing empty lines from output
with open("file.txt") as file:
    for line in file:
        print(line.strip().upper())
        

## read file contents into list

file = open("file.txt")
# list of lines
lines = files.readlines()
file = close()
print(lines)
```

           
## writing files
```
r = read only
w = write only
x = exclisive creation - fail if faile already exists
a = append - to end of file
+ = read write
```

w mode will over write existing file content. Make sure to use append if you want to keep existing file content.

```

with open("file.txt","w") as file:
    file.write("This was written by python script")
    
```
