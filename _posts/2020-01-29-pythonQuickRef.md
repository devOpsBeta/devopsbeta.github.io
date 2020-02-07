---
layout: post
title:  "Python 3 Quick Reference Guide"
date:   2020-01-29 09:43:04 -0500
categories: python
featured-image: roll-up-doors.jpg
permalink: /python/guide
---

## Installing tk for python GUIs
```
dnf install python3-tkinter
```

## Making virtual enviroment

This keeps modules in a container so system python modules are not touched. It is good practice to use virutal environments when using non native modules.

```
# make virtual enviroment - relative path
python3 -m venv ./venv

# sourcing virtual env
. ./venv/bin/activate

# in your python scripts reference the venv you that it uses
Your shebang line < the line at the top of the script, This allows you to run with ./script.py vs python3 script.py > :
    #!/data/venv/bin/python

    I have my vevn located in data. Please change to match your venv

```

## Making requirements.txt and using requirements.txt to install python modules
```
1. install modules you need with pip
2. pip freeze > requirements.txt

To install in on another venv or system
pip install -r requirements.txt

```



## general python syntax
```
# Setting string varible 
var = "vaule"

# Setting var to list
listvar = ["value1","value2","value3"]



# if / else
if <true>:
  # printing string
  print('result is true')
else: 
  print('result is false')


# while
i = 0
while i < 23:
  print("tick")
  i += 1




```

Will be updated further...
