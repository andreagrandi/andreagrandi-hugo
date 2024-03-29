---
title: "Writing Python bindings of existing C libraries – (3) – Building and Installing with distutils"
date: 2009-08-13
categories: 
- HowTo
- Igalia
- Linux
- Maemo (EN)
- Programmazione
- Python
tags: 
- binding
- distutils
- library
- maemo
- Python
- setup
slug: "writing-python-bindings-of-existing-c-libraries-building-and-installing-with-distutils"
draft: false
---

In the last post of this series, we saw how to write a simple binding
and we finished to build and install it manually. This is of course not
a good way to manage the building/installation procedure.

In Python we can use a library called **distutils** that let us to
automatize the building and installing process. I'll use the **foo**
source code to create the package, so it will be easier to understand.

## Using distutils

All we have to do is to write a **setup.py** file similar to this one:

```python
from distutils.core import setup, Extension

foomodule = Extension('foo', sources = ['foo.c'])

setup (
    name = 'Foo',
    version = '1.0',  
    description = 'This is a package for Foo',  
    ext_modules = [foomodule]
)
```

As you can see, we have to first import needed modules with: **from
distutils.core import setup, Extension**  
then we create an entry for each module we have (in this case just one,
"foomodule"). We then call the **setup()** method passing it all the
parameters and our **setup.py** is complete.

## Building and installing

To test it we can try to build the package in this way:

```shell
python2.5 setup.py build
```

if we want to install the module in our system:

```shell
python2.5 setup.py install
```

## References

- Official Python documentation: <http://docs.python.org/extending/building.html>


