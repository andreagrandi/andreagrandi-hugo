---
title: "Using QML qt-components with QtQNX for BlackBerry PlayBook"
date: 2012-03-30
categories: 
- HowTo
- Programmazione
- Qt
slug: "using-qml-qt-components-with-qtqnx-for-blackberry-playbook"
draft: false
---

With BlackBerry PlayBook you can now use Qt libraries to develop your
applications. The problem is that QML components are not available yet
(they will be available with CascadesUI in the near future), but you can
use Symbian qt-components to develop your application UI. This should
also make the porting of an existing Symbian Qt application easier.

We suppose you have already built and installed **QtQNX** under this
directory: **`~/QtQNX/ARM/`** (please change it matching the folder where
you installed it).  
At this point you have to get qt-components sources using this command:

```shell
git clone git://gitorious.org/qt-components/qt-components.git
qt-components  
```

Now enter the directory you just checked and compile the components:

```shell
cd qt-components  
QTDIR=\~/QtQNX/ARM/  
./configure -symbian  
make  
```

Whend you complete all the previous operations, you'll have two
directories inside **qt-components/imports**, please copy them inside
the QtQNX installation directory:

```shell
cp -R imports/Qt \~/QtQNX/ARM/imports/  
cp -R imports/com \~/QtQNX/ARM/imports/  
```

That's all for now. In the next posts I'll show you how to use these
components, providing a small code example. In the mean time you can
find more informations
here <http://supportforums.blackberry.com/t5/Native-SDK-for-BlackBerry-Tablet/QML-symbian-qt-components-for-PlayBook/td-p/1574275>

