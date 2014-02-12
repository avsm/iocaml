IOCaml
======

*An OCaml kernel for IPython.*

Latest release tag: v0.2

[Example](http://nbviewer.ipython.org/github/andrewray/iocaml/blob/master/notebooks/iocaml-test-notebook.ipynb)

# Installation

## Installing IPython

IOCaml is currently being developed against IPython 1.1. To set this up on Ubuntu 13.10 64 bit do;

```
$ sudo apt-get install libzmq3-dev python-dev ipython ipython-notebook \
   python-pip python-setuptools python-jinja2 m4 zlib1g-dev
```

Then update the following python packages;

```
$ sudo pip install -U ipython pyzmq
```

At the time of writing this should get IPython 1.1 installed.

```
$ ipython console
> Python 2.7.5+ (default, Sep 19 2013, 13:48:49) 
"copyright", "credits" or "license" for more information.

IPython 1.1.0 -- An enhanced Interactive Python.
?         -> Introduction and overview of IPython's features.
%quickref -> Quick reference.
help      -> Python's own help system.
object?   -> Details about 'object', use 'object??' for extra details.
```

For development testing you can download IPython packages or the github repository then run

```
$ python -m IPython [args]
```

from the directory the package in unpacked to.

## Installing IOCaml

### Via opam 

```
opam remote add iocaml git://github.com/andrewray/opam.git
opam install iocaml
```

Note that this will upgrade the opam version of ocaml-zmq to use the branch from [here](https://github.com/issuu/ocaml-zmq).

### Manually

Install required packages.

```
$ opam install atdgen cryptokit uuidm ounit uint oasis ocamlnet
```

Clone the repositories we need to compile

```
$ git clone https://github.com/issuu/ocaml-zmq.git
$ git clone https://github.com/andrewray/iocaml.git
```

Compile ocaml-zmq

```
$ cd ocaml-zmq
$ oasis setup
$ make all
$ make install
```

compile IOCaml

```
$ cd iocaml
$ make all
$ make install
```

## Setting up IOCaml

Run IPython to setup a new iocaml profile

```
$ ipython profile create iocaml
```

Copy the contents of 'profile/' into the the ipython profile directory '~/.config/ipython/profile_iocaml' (or '~/.ipython/profile_iocaml' if you've run 2.0-dev).

```
$ cp -r profile/* ~/.config/ipython/profile_iocaml/
```

Now you can run iocaml with

```
$ ipython notebook --profile=iocaml
```

## Command line options

There are a few command line options to iocaml which are set up in the ipython_config.py configuration file.

```
$ iocaml.top --help
iocaml kernel
  -log <filename>             open log file
  -connection-file <filename> connection file name
  -suppress {stdout|stderr|compiler|all}
                              suppress channel at start up
  -package <package>          load package at startup
  -help                       Display this list of options
  --help                      Display this list of options
```

The defualt configuration loads the iocaml package at startup.

