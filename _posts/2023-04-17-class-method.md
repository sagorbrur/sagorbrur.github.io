---
title: "Python class method"
date: 2023-04-17
categories:
  - python
classes: wide
excerpt: In this blog I will try to share some use cases of python classmethod
---

Let's say, we want to use a function or method from a class without initializing the class.
How can we do that?

Python `@classmethod` decorator here to help.

Let's start with an example.

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    @classmethod
    def print_something(cls, input):
        print(input)

Person.print_something('hello')
```
Here if we want to use inside function of `Person` we have to initialize it, right?
But using the `@classmethod` decorator we can call `print_something` method without initializing the Person class.
Here `cls` means the class itself.

Let's see another use cases.

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    @classmethod
    def from_dict(cls, input_dict):
        return cls(**input_dict)

input_dict = {'name': 'Sagor', 'age': 28}
person = Person.from_dict(input_dict)
```

We are creating a person instance from the classes and dynamically setting the hyper-parameters from input dict using the class method itself.
