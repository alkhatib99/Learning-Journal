# Learning-Journal - 03

## Desc

Today I will focus on summarize all about files and modules and errors

## Summary 

### Brief overview of the standard library

The **standard library** consists of modules that Python comes
with. Here's a very brief overview of what it can do. All of
these modules can also do other things, and you can read more
about that in the official documentation.

#### Random numbers

The official documentation is
[here](https://docs.python.org/3/library/random.html).

```python
>>> import random
>>> random.randint(1, 3)      # 1, 2 or 3
3
>>> colors = ['red', 'blue', 'yellow']
>>> random.choice(colors)     # choose one color
'red'
>>> random.sample(colors, 2)  # choose two different colors
['yellow', 'red']
>>> random.shuffle(colors)    # mix the color list in-place
>>> colors
['yellow', 'red', 'blue']
>>>
```

### Things that are built into Python

The module name "sys" is short for "system", and it contains things
that are built into Python. The official documentation is
[here](https://docs.python.org/3/library/sys.html).

`sys.stdin`, `sys.stdout` and `sys.stderr` are [file objects](files.md),
just like the file objects that `open()` gives us.

```python
>>> import sys
>>> print("Hello!", file=sys.stdout)  # this is where prints go by default
Hello!
>>> print("Hello!", file=sys.stderr)  # use this for error messages
Hello!
>>> line = sys.stdin.readline()  # i will type hello and press enter
hello
>>> line
'hello\n'
>>>
>>> # information about Python's version, behaves like a tuple
>>> sys.version_info
sys.version_info(major=3, minor=7, micro=3, releaselevel='final', serial=0)
>>> sys.version_info[:3]  # this is Python 3.7.3
(3, 7, 3)
>>>
>>> sys.exit()  # exit out of Python
```

### Mathematics

There's no math.py anywhere, math is a built-in module like
sys. The official documentation is
[here](https://docs.python.org/3/library/math.html).

```python
>>> import math
>>> math
<module 'math' (built-in)>
>>> math.pi                  # approximate value of π
3.141592653589793
>>> math.sqrt(2)             # square root of 2
1.4142135623730951
>>> math.radians(180)        # convert degrees to radians
3.141592653589793
>>> math.degrees(math.pi/2)  # convert radians to degrees
90.0
>>> math.sin(math.pi/2)      # sin of 90 degrees or 1/2 π radians
1.0
>>>
```

## More modules!

Python's standard library has many awesome modules and I just
can't tell about each and every module I use here. Here's some of
my favorite modules from the standard library. Don't study them
one by one, but look into them when you think you might need them.
When reading the documentation it's usually easiest to find what
you are looking for by pressing Ctrl+F in your web browser, and
then typing in what you want to search for.

- [argparse](https://docs.python.org/3/howto/argparse.html):
    a full-featured command-line argument parser
- [collections](https://docs.python.org/3/library/collections.html),
    [functools](https://docs.python.org/3/library/functools.html) and
    [itertools](https://docs.python.org/3/library/itertools.html):
    handy utilities
- [configparser](https://docs.python.org/3/library/configparser.html):
    load and save setting files
- [csv](https://docs.python.org/3/library/csv.html):
    store comma-separated lines in files
- [json](https://docs.python.org/3/library/json.html):
    yet another way to store data in files and strings
- [textwrap](https://docs.python.org/3/library/textwrap.html):
    break long text into multiple lines
- [warnings](https://pymotw.com/3/warnings/):
    like [exceptions](exceptions.md), but they don't interrupt the
    whole program
- [webbrowser](https://pymotw.com/3/webbrowser/):
    open a web browser from Python

There are also lots of awesome modules that don't come with Python.
You can search for those on the [Python package index](https://pypi.org/),
or PyPI for short. It's often better to find a library that does something
difficult than to spend a lot of time trying to do it yourself.

I recommend reading [the official documentation about installing
modules](https://docs.python.org/3/installing/) from PyPI. If you're using
Linux, then also read the "Installing into the system Python on Linux"
section at the bottom.

- Most modules are files on our computers, but some of them are built
    in to Python. We can use modules in our projects by importing them,
    and after that using `modulename.variable` to get a variable from
    the module.
- Some of the most commonly used modules are random, sys, math, time
    and os.
- Avoid creating `.py` files that have the same name as a name of a
    module you want to use.
- Python comes with many modules, and we can install even more modules
    if we want to.




### Files

- Each file has a **name**, like `hello.py`, `mytext.txt` or
    `coolimage.png`. Usually the name ends with an **extension** that
    describes the content, like `py` for Python, `txt` for text or `png`
    for "portable network graphic".
- With just names identifying the files, it wouldn't be possible to have
    two files with the same name. That's why files also have a
    **location**. We'll talk more about this in a moment.
- Files have **content** that consists of
    [8-bit bytes](https://www.youtube.com/watch?v=Dnd28lQHquU).

### Directories/folders

Directories are a way to group files. They also have a name and a location
like files, but instead of containing data directly like files do they
contain other files and directories.

### Paths

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

So far we've talked about Windows paths, but not all computers run
Windows. For example, an equivalent to `C:\Users\me\hello.py` is
`/home/me/hello.py` on my Ubuntu, and if I'm in `/home`, `me/hello.py`
is same as `/home/me/hello.py`.

```
/
└── home
    └── me
        └── hello.py
```

## Writing to a file

Let's create a file and write a hello world to it.

```python
>>> with open('hello.txt', 'w') as f:
...     print("Hello World!", file=f)
...
>>>
```

Doesn't seem like it did anything. But actually it created a `hello.txt`
somewhere on our system. On Windows it's probably in `C:\Users\YourName`,
and on most other systems it should be in `/home/yourname`. You can open
it with notepad or any other plain text editor your system comes with by
opening the folder that contains the file and then double-clicking the
file.

So how does that code work?

First of all, we open a path with `open`, and it gives us a Python file
object that is assigned to the variable `f`.

```python
>>> f
<_io.TextIOWrapper name='hello.txt' mode='w' encoding='UTF-8'>
>>>
```

File objects are not the same thing as paths and filenames, so if we try
to use `'hello.txt'` like we used `f` it doesn't work.

The first argument we passed to `open` was the path we wanted to write.
Our path was more like a filename than a path, so the file ended up in
the current working directory.

The second argument was `w`. It's short for write, and that just means
that we'll create a new file. There's some other modes we can use also:

| Mode  | Short for | Meaning                                                               |
|-------|-----------|-----------------------------------------------------------------------|
| `r`   | read      | Read from an existing file.                                           |
| `w`   | write     | Write to a file. **If the file exists, its old content is removed.**  |
| `a`   | append    | Write to the end of a file, and keep the old content.                 |

But what is that `with ourfile as f` crap? That's just a fancy way to make
sure that the file gets closed, no matter what happens. As we can see,
the file was indeed closed.

```python
>>> f.closed
True
>>>
```

When we had opened the file we could just print to it. The print is just
like any other print, but we also need to specify that we want to print
to the file we opened using `file=f`.

## Reading from files

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

Trying to open a non-existent file with `w` or `a` creates the file for
us, but doing that with `r` gives us an error instead. We'll learn more
about errors [later](exceptions.md).

```python
>>> with open('this-doesnt-exist.txt', 'r') as f:
...     print("It's working!")
...
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
FileNotFoundError: [Errno 2] No such file or directory: 'this-doesnt-exist.txt'
>>>
```

So now we have the hello world in the `lines` variable, but it's
`['Hello World!\n']` instead of `['Hello World!']`. So what the heck is
that `\n` doing there?

`\n` means newline. Note that it needs to be a backslash, so `/n`
doesn't have any special meaning like `\n` has. When we wrote the file
with print it actually added a `\n` to the end of it. It's recommended
to end the content of files with a newline character, but it's not
necessary.

Let's see how that works if we have more than one line in the file.

```python
>>> with open('hello.txt', 'w') as f:
...     print("Hello one!", file=f)
...     print("Hello two!", file=f)
...     print("Hello three!", file=f)
...
>>> lines = []
>>> with open('hello.txt', 'r') as f:
...     for line in f:
...         lines.append(line)
...
>>> lines
['Hello one!\n', 'Hello two!\n', 'Hello three!\n']
>>>
```

There we go, each of our lines now ends with a `\n`. When we for
loop over the file it's divided into lines based on where the `\n`
characters are, not based on how we printed to it.

But how to get rid of that `\n`? [The rstrip string
method](https://docs.python.org/3/library/stdtypes.html#str.rstrip) is
great for this:

```python
>>> stripped = []
>>> for line in lines:
...     stripped.append(line.rstrip('\n'))
...
>>> stripped
['Hello one!', 'Hello two!', 'Hello three!']
>>>
```

It's also possible to read lines one by one. Files have [a readline
method](https://docs.python.org/3/library/io.html#io.TextIOBase.readline)
that reads the next line, and returns `''` if we're at the end of the file.

```python
>>> with open('hello.txt', 'r') as f:
...     first_line = f.readline()
...     second_line = f.readline()
...
>>> first_line
'Hello one!\n'
>>> second_line
'Hello two!\n'
```

There's only one confusing thing about reading files. If we try
to read the same file object twice we'll find out that it only gets read
once:

```python
>>> first = []
>>> second = []
>>> with open('hello.txt', 'r') as f:
...     for line in f:
...         first.append(line)
...     for line in f:
...         second.append(line)
...
>>> first
['Hello one!\n', 'Hello two!\n', 'Hello three!\n']
>>> second
[]
>>>
```

File objects remember their position. When we tried to read the
file again it was already at the end, and there was nothing left
to read. But if we open the file again, we get a new file object that
is in the beginning and everything works.

```python
>>> first = []
>>> second = []
>>> with open('hello.txt', 'r') as f:
...     for line in f:
...         first.append(line)
...
>>> with open('hello.txt', 'r') as f:
...     for line in f:
...         second.append(line)
...
>>> first
['Hello one!\n', 'Hello two!\n', 'Hello three!\n']
>>> second
['Hello one!\n', 'Hello two!\n', 'Hello three!\n']
>>>
```

Usually it's best to just read the file once, and use the
content we have read from it multiple times.

If we need all of the content as a string, we can use [the read
method](https://docs.python.org/3/library/io.html#io.TextIOBase.read).

```python
>>> with open('hello.txt', 'r') as f:
...     full_content = f.read()
...
>>> full_content
'Hello one!\nHello two!\nHello three!\n'
>>>
```

We can also open full paths, like `open('C:\\Users\\me\\myfile.txt', 'r')`.
The reason why we need to use `\\` when we really mean `\` is that
backslash has a special meaning. There are special characters like
`\n`, and `\\` means an actual backslash.

[comment]: # (GitHub's syntax highlighting screws up with backslashes.)

```
>>> print('C:\some\name')
C:\some
ame
>>> print('C:\\some\\name')
C:\some\name
>>>
```

Another way to create paths is to tell Python to escape them by
adding an `r` to the beginning of the string. In this case the `r`
is short for "raw", not "read".

```python
>>> r'C:\some\name'
'C:\\some\\name'
>>>
```

If our program is not meant to be ran on Windows and the paths
don't contain backslashes we don't need to double anything or use
`r` in front of paths.

```python
>>> print('/some/name')
/some/name
>>>
```

Doing things like `open('C:\\Users\\me\\myfile.txt', 'r')` is not
recommended because the code needs to be modified if someone wants to
run the program on a different computer that doesn't have a
`C:\Users\me` folder. Just use `open('myfile.txt', 'r')`.



