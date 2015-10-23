multiverse build machine
========================

Completely automates the build process for [multiverse](https://github.com/j-cube/multiverse) by using [Vagrant](https://www.vagrantup.com/)
and [alembic-builder](https://github.com/j-cube/alembic-builder).

Let's walk the walk
-------------------

First of all, [install Vagrant](http://docs.vagrantup.com/v2/installation/index.html) if not already installed.
Secondly, [download & install Virtual Box](https://www.virtualbox.org/wiki/Downloads) if not already installed.

Then:

```
$ git clone https://github.com/j-cube/multiverse-build-machine
$ cd multiverse-build-machine
$ vagrant up
```
This will create a VM using UbuntuTrusty64 and compile multiverse with gcc 4.8

```
$ vagrant ssh
vagrant@precise64:~$ ls /opt/jcube
bin  docs include  lib  multiverse-1.5.8 share
vagrant@precise64:~$ ls /opt/jcube/multiverse-1.5.8/bin/
...
abcconvert
abcecho
abcechobounds
abchistory
abcls
abctree
...
```

Enjoy!
