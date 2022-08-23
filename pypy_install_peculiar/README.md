# PyPy installation in Ubuntu
(PyPy runs faster python programs on x86 due to its Just-in-Time compiler)
Normally standard procedure works:

$ sudo apt-get update
$ sudo apt-get -y install pypy3

!Problems:

> Problem 1. 'apt-get update' fails: 
Most likey, you are using an outdated/Old Ubuntu Release/ your Ubuntu has reached EOL [keeps happening to even some beloved versions in time, particularly for related ROS users]. 
Why not upgrade the OS? you might be in a docker image using Old Ubuntu Release, a virtual env?, or some other reason that keeps you from doing it!

> Solution:
In sources list in '/etc/apt/' change archive.ubuntu.com and security.ubuntu.com to old-releases.ubuntu.com.

```
$ sed -i -re 's/([a-z]{2}\.)?archive.ubuntu.com|security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list
```

or

```
$ sudo vi /etc/apt/sources.list
```

Change archive.ubuntu.com and security.ubuntu.com to old-releases.ubuntu.com.

Now you should be able to install pypy3, and further use it to install other libs (Numpy!?)

> Problem 2. 'apt-get update' runs, can install pypy3, but this pypy3 version is old: 
This can be expected with an outdated Ubuntu and using its 'old-releases.ubuntu'
Check version:
$ pypy3 --version

> Solution 2. Download pypy3 standalone(or any such package actually), remove the old pypy3 installation, create a symlink to the new pypy3 executable.

do. download tar/zip from https://www.pypy.org/download.html#  (select a newer version ,,pypy3.8 means with python 3.8)
Extract:
```
$ tar xf pypy3.8-v7.3.9-linux64.tar.bz2
```

As soon as it is extracted, you can use pypy3 or pypy by running the corresponding executable file, no need of different installation
```
$ ./pypy3.8-v7.3.9-linux64/bin/pypy3
Python 3.8.13 (4b1398fe9d76ad762155d03684c2a153d230b2ef, Mar 29 2022, 07:08:24)
[PyPy 7.3.9 with GCC 10.2.1 20210130 (Red Hat 10.2.1-11)] on linux
Type "help", "copyright", "credits" or "license" for more information.
```

Remove the previously installed pypy3 from your OS/env/docker_image
```
$ apt-get -y autoremove --purge pypy3
```
Create a symlink in /usr/bin to new exectuable for pypy3 in the extracted tar
```
$ ln -s /pypy3.8-v7.3.9-linux64/bin/pypy3 pypy3
```
*(everytime you run pypy3 in the venv/docker this will be called now!)


(Can run pypy3 to verify!)
```
$ pypy3
Python 3.8.13 (4b1398fe9d76ad762155d03684c2a153d230b2ef, Mar 29 2022, 07:08:24)
[PyPy 7.3.9 with GCC 10.2.1 20210130 (Red Hat 10.2.1-11)] on linux
Type "help", "copyright", "credits" or "license" for more information.
```
