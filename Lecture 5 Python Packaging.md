# Python Packaging

> How to share my code with the world?

What should I do so that other can type `import package_name` to import my code?

## Jupyter Notebook

| Good                                      | Bad                                    |
| ----------------------------------------- | -------------------------------------- |
| Can combine Markdown cells and Code cells | Not working great with version control |
| Promoting reproductivity                  | Harder to reuse, just duplicate        |
| Can run remotely                          | Hard to test code                      |

### Using `sys.argv` in Python

#### `sys.argv` is a list

1. `sys.argv[0]` is the script name
2. `sys.argv[1]` is the additional arguments

#### `!` pass the command to the command shell rather than python interpreter

```python
!python rot13.py "Uryyb rirelobql!" 
```

## Python Modules

### What is a Module?

- A Python module is a file containing Python code that defines functions, classes, and variables.
- It is intended to be **imported** and reused

### Why Modules?

- Code Organization: keep code into manageable and testable sections
- Reusability
- Namespace Management

> [!WARNING]
>
> Define the same function multiple times in different files will lose mark!

### Import and Run

```python
import codecs
import sys


def rot13(original):
    return codecs.encode(original, "rot_13")

    
if __name__ == "__main__":
    if len(sys.argv) > 1:
        input_text = sys.argv[1]
    else:
        input_text = "Vg'f n frperg!"
    encoded_text = rot13(input_text)
    print(encoded_text)
```

The code under `if __name__ == "__main__"` will only be run when the file is run as a script, i.e. `python rot13_module.py`. <u>Test codes should be written undet this.</u>

However, when **importing** this module, it automatically run the whole file from top to bottom (but ignore the code under `if __name__ == "__main__"`)

#### Example

In potato.py:

```python
def add(a, b):
    return a + b
print(add(1, 2))
print("Potato")
```

In tomato.py:

```python
import potato
print(potato.add(1, 1))
```

If we run `tomato.py`, the result will be:

`3
Potato
2`

The `import` statement automatically run the `potato.py` file.

If we change the code in `potato.py` to:

```python
def add(a, b):
    return a + b
if __name__ == "__main__":
    print(add(1, 2))
    print("Potato")
```

When run `tomato.py` again, we get the output:

`2`

That is what we want.

#### Reloading import

``importlib.reload(module)``

When changing the code in the imported file, we need to use `importlib.reload(module)` to apply changes made to the module **without restarting the Python Interpreter**.

#### Reseting Namespace (in Jupyter)

`%reset -f`

An Ipython magic command used to clear the entire namespace.

```python
x = 7
print(x)
%reset -f
print(x)
```

The <u>second</u> print will cause a NameError, since x is not defined after using `%reset -f`

## Documentation

### Docstrings

Start with `"""` or `'''`

```python
def add(a, b):
    """
    Adds two numbers and returns the result.
    
    Parameters
    ----------
    a : int or float
        The first number.
    b : int or float
        The second number.
    
    Returns
    -------
    int or float
        The sum of `a` and `b`.
    """
    return a + b
```

How to access the docsctrings?

`print(func_name.__doc__)`

### README.md

1. **Project Title**: The name of the project.
2. **Description**: A brief overview of the project’s purpose and features.
3. **Installation**: Step-by-step instructions for setting up the project.
4. **Usage**: Examples of how to use the project or run scripts.
5. **Contributing** (optional): Guidelines for contributing to the project.
6. **License**: Information on how the project is licensed.

## Creating a Package

