# Learning-Journal - 08

## What is true?

Now we understand how code like this works.

```python
message = input("Enter something: ")
if message == '':
    print("You didn't enter anything!")
else:
    print("You entered:", message)
```

But most Python programmers would write that code like this
instead:

```python
message = input("Enter something: ")
if message:
    print("You entered:", message)
else:
    print("You didn't enter anything!")
```

Python converted our message to a Boolean and then checked if
the Boolean it ended up with was True. But when will it be true?

## Converting to Booleans

We can convert things to Booleans like Python did by doing
`bool(things)`. Let's try that with strings.

```python
>>> bool('hello')
True
>>> bool('there')
True
>>> bool('True')
True
>>> bool('False')    # this isn't special in any way
True
>>>
```

As we can see, the Boolean value of most strings is True. The
only string that has a false Boolean value is the empty string,
`''` or `""`:

```python
>>> bool('')
False
>>>
```

None and zero are also falsy, but positive and negative numbers
are treated as True.

```python
>>> bool(None)
False
>>> bool(0)
False
>>> bool(0.0)
False
>>> bool(1)
True
>>> bool(-1)
True
>>>
```

Most other things are also treated as True.

```python
>>> bool(OSError)
True
>>> bool(print)
True
>>>
```

## When and why should we use Boolean values of things?

We could improve the code by checking against different empty
things.

```python
>>> def is_this_empty(thing):
...     if thing == [] or thing == () or thing == '' or thing == {}:
...         print("It's empty!")
...     else:
...         print("It's not empty.")
...
>>>
```

But Python has many other data types that can be empty and we
haven't talked about in this tutorial. Trying to check all of
them would be pointless because functions like this already
work with all of them:

```python
>>> def is_this_empty(thing):
...     if thing:
...         print("It's not empty.")
...     else:
...         print("It's empty!")
...
>>>
```

There's also cases when we should not rely on the Boolean value.
When we're doing things with numbers and None it's best to
simply compare to None or zero. Like this:

```python
if number != 0:
    print("number is not zero")

if value is not None:
    print("value is not None")
```

Not like this:

```python
if number:
    print("number is not zero")

if value:
    print("value is not None")
```

We used `is not` instead of `!=` in the first example because
the official style guide recommends it. The reason is that it's
possible to create a value that isn't really None but seems like
None when we compare it with None using `==` or `!=`, and we want
to make sure that we don't treat values like that as None.

So here's how we should check if something is None:

```python
if not value: ...      # not good if we want to check if it's None
if value == None: ...  # better
if value is None: ...  # best
```

## Summary

- `if thing:` does the same thing as `if bool(thing):`. This also
    works with while loops and most other things that are usually used
    with Booleans.
- `bool()` of most things is True, but `bool()` values of None,
    zero and most empty things are False.
- Use `is` and `is not` when comparing to None, `==` and `!=` when
    checking if a number is zero and rely on the Boolean value
    when checking if something is empty.
