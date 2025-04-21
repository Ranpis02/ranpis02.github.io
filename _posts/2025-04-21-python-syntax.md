---
title: 'Python syntax'
date: 2025-04-21 01:24:14 +0800
categories: [python]
tags: [syntax]
---

## Type annotations

`Type annotations` introduced in PEP484, Python3.5+, allow developers to specify the excepted types of variables, function parameters, and return values in Python code. The following points should be noted:

- The annotations use a colon `:` for variables and parameters, and an arrow `->` for function return types.
- The supported types include built-in types(e.g., `str`, `int`), custom classes, or types from `typing` module(e.g., List, Optional)

1. Specify the types of function arguments and return values

   ```python
   from typing import List
 
   # The input parameter is restricted to the `List[int]` type, and the return value is restricted to the `int` type
   def sum_numbers(numbers: List[int]) -> int:
     return sum(numbers)
   ```

2. Specify more flexible types, such as collections

   ```python
   from typing import Dict
 
   def get_value(d: Dict[str, int], key: str) -> int:
      return d.get(key, 0)
 
   my_dict = dict([('age', 18), ('salary', 20000)])
   get_value(my_dict, 'age')
   ```

3. Union Type: when a parameter can accept more than one type, we can use `Union`

   ```python
   from typing import Union
 
   # this function accepts either a string or a list and returns its length
   def get_length(s: Union[str, list]) -> int:
       return len(s)
   ```

4. Optional Type: this is a  shorthand for a `Union` and `None`. It's commonly used when a parameter is either a specific type or `None`

   ```python
   from typing import Optional
 
   def get_first_element(lst: Optional[List[int]]) -> Optional[int]:
       if lst:
           return lst[0]
       return None
   ```

## Forward Reference

The `Forward Reference` occurs when a type annotation refers to a type that is not yet defined at the point of the annotation.

This is common in cased of circular dependencies, external module importts, or when a class references itself.

Create an object Tree, and have it reference iteself in the initialization function:

```python
from typing import List

class Tree:
  def __init__(self, value: int, children: List['Tree']) -> None:
    self.value = value
    self.children = children
```

Key Points:

- String literals are resolved by type checkers during static analysis.
- Forward references are necessary when the type is not yet available at the time the annotation is parsed.
- Since Python 3.7+ with `deferred evluation`, forward references can use the actual type name directly

   ```python
   from typing import List 
   class Tree:
     def __init__(self, value: int, children: List[Tree]) -> None:
       self.value = value
       self.children = children 
   # Create child nodes
   child_1 = Tree(2, [])
   child_2 = Tree(3, []) 
   # Create the root node of the tree and add child nodes
   root = Tree(1, [child_1, child_2]) 
   # print the root node's value and Travrse the values of child nodes
   print(f"root value: {root.value}")
   for i, child in enumerate(root.children, start=1):
       print(f"child {i} value: {child.value}")
   ```
