# CLP documentation

### NOTE: The information in this file might not yet include the changes introduced with the switch to the autotools.

* To build Clp see INSTALL file
* To use Clp you need the Clp and Coin libraries
* To make standalone executable do 'make Clp' in the Clp directory. This creates an executable clp in Clp/src. 
* To run unitTest do 'make unitTest' in the Clp directory. This will execute some minimal testing.

* To run clp on all netlib problems do `make unitTest NETLIBDIR=<dirname>`

where dirname should be the path to the directory containing all the
netlib files. If you have compiled Clp without zlib support then the
files must be uncompressed.

Running `clp` gives you some hints.  It can do:

* a unit test with `clp -unitTest`
* solve netlib problems with `-netlib or -netlibp` using primal.  It can also solve problems and set tolerances etc.  

## CLP 
 
and then try ? or setting various stuff.

```bash
clp filename   # reads file, does presolve and dual algorithm
clp filename -primalsimplex would use primal instead
```

On Linux clp can do file completion and line editing if it can find history, readline and termcap..  

If you want to stress the code you can set various stuff e.g. dantzig pricing
 and then go into netlib testing.  I do not guarantee that it will solve all 
netlib if you get too creative.  For instance using presolve makes netlib 
solve faster - but pilot87 prefers a large infeasibility weight.  So

```bash
clp -presolve on -dualbound 1.0e10 -netlib
```

works well.

There are samples in `./Samples`.  To create an executable - testit do

```bash
make DRIVER=minimum to use minimum.cpp
```

or whichever driver you want.  A list is in Makefile.

## Examples

* `minimum.cpp` : This is the simplest possible program to read an mps file.
* `defaults.cpp` : This does not do much more, but it does it in much more  complicated way by specifically setting defaults so it does give more useful information.  It also prints a solution in a format "similar" to that of MPSX.
* `presolve.cpp` : This is a good driver for larger problems.

Other ones can get complicated so start simple and work your way up.

