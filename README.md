multiverse build machine
========================

Completely automates the build process for [multiverse](https://github.com/j-cube/multiverse) by using [Vagrant](https://www.vagrantup.com/)
and [alembic-builder](https://github.com/j-cube/alembic-builder).

Note that we have multiple branches supporting multiple Linux versions (and `gcc` versions that match the [VFX reference platform](http://www.vfxplatform.com))

| Branch                               | O/S              | gcc    |
|--------------------------------------| ---------------- | ------ |
| master                               | ubuntu precise64 | 4.6    |
| ubuntu-trusty64-gcc48-multiverse-1.5 | ubuntu thrusty64 | 4.8    |
| (coming soon)                        | centos 6.5       | 4.8.2  |


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
This will create a VM using Vagrant and build multiverse in it, now login an check the product of the compilation.
 
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
