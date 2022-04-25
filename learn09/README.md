# Learning-Journal - 09

Today I have learned about RegEx

Summary :

When you have imported the re module, you can start using regular expressions:


```python
import re

txt = "The rain in Spain"
x = re.search("^The.*Spain$", txt)
```

## Regex Functions 

The `re` module offers a set of functions that allows us to search a string for a match:

|**Function**   | **Description**  |
|---|---|
|*findall*   | Returns a list containing all matches
  |
| *Search*  | Returns a Match object if there is a match anywhere in the string  |
|  *Split* |  Returns a list where the string has been split at each match
 |
|  *Sub* |	Replaces one or many matches with a string. |
