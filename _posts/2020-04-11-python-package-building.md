---
title: "Creating and Uploading Python Package to PYPI"
date: 2020-04-11
categories:
  - python
  - msc
classes: wide
excerpt: Let us assume we want to create a simple python package called calculator
---

## Creating Package

### Directory Structure

Let us assume we want to create a simple python package called `calculator`

Our directory will be like:

```
calculator\
    calculator\
        __init__.py
        calc.py
    license
    README.md
    setup.py

```

### Creating `setup.py` File

`setup.py` file contains settings and details about your package. 

Here is a sample `setup.py` file.

```py

import codecs
import setuptools


setuptools.setup(
    name="calculator", # your package name. Choose unique package name by searching pypi.org
    version="1.0",
    author="Sagor Sarker", # your name
    author_email="sagorhem3532@gmail.com", # your email
    description="A simple calculator to do calculation", # simple intro
    long_description=codecs.open("README.md", encoding="utf-8").read(),
    long_description_content_type="text/markdown",
    url="https://github.com/sagorbrur/calculator", # pacakge git link
    license="MIT", # license type
    packages=setuptools.find_packages(),
    classifiers=[
        "Programming Language :: Python :: 3",
        "License :: OSI Approved :: MIT License",
        "Operating System :: OS Independent",
    ],
    python_requires='>=3.5', # python version
    install_requires=[ # dependecies package
        'numpy`,
    ],
)

```

* `name`: Name your package. Choose unique package name using search box of pypi.org . Otherwise it can't be upload in pypi if it contradict with other package. Example: search `calculator` at in pypi.org . If `calculator` exist then you need to change package name, which not exist in pypi.org search.



### Creating `license` file

You need to create a `license` file for proper license of your package.

Here is an example of `MIT` license.

```
MIT License

Copyright (c) 2019 Sagor Sarker

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

You have done the initial settings of your package.

## Uploading Package

* Upgrade setuptools
    ``` 
    python3 -m pip install --user --upgrade setuptools wheel
    ```
* Build `setup.py` using setuptools

    ```
    python3 setup.py sdist bdist_wheel
    ```

    After successfully building you will see two new directory `build` and `dist`. Where `dist` directory contains your package wheel file.

* upgrade twine

    ```
    python3 -m pip install --user --upgrade twine
    ```

* Upload your package to pypi
    ```
    !python3 -m twine upload dist/*
    ```

    It will ask your pypi account `user-name` and `password`. Now fill that two field and you will get your package link like this: 

    https://pypi.org/project/calculator/