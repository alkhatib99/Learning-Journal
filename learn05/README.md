# Learning-Journal - 05 

Today I have learned  about files, Paths

Directories and files have a path, like `C:\Users\me\hello.py`. That just
means that there's a folder called `C:`, and inside it there's a folder
called `Users`, and inside it there's a folder called `me` and inside it
there's a `hello.py`. Like this:

```
C:
└── Users
    └── me
        └── hello.py
```

`C:\Users\me\hello.py` is an **absolute path**. But there are also
**relative paths**. For example, if we are in `C:\Users`, `me\hello.py`
is same as `C:\Users\me\hello.py`. The place we are in is sometimes
called **current directory**, **working directory** or
**current working directory**.
#### Writing to a file

Let's create a file and write a hello world to it.

```python
>>> with open('hello.txt', 'w') as f:
...     print("Hello World!", file=f)
...
>>>
```


#### Reading from files

After opening a file with the `r` mode we can for loop over it, just
like it was a list. So let's go ahead and read everything in the file
we created to a list of lines.

```python
>>> lines = []
>>> with open('hello.txt', 'r') as f:
...     for line in f:
...         lines.append(line)
...
>>> lines
['Hello World!\n']
>>>
```
