# Doxygen

[Doxygen](http://www.doxygen.nl/) is the de facto standard tool for generating documentation from annotated C++ sources, but it also supports other popular programming languages such as C, Objective-C, C#, PHP, Java, Python, IDL (Corba, Microsoft, and UNO/OpenOffice flavors), Fortran, VHDL, Tcl, and to some extent D.


## Local build
```bash
docker build . --rm --tag doxygen/doxygen:alpine -f alpine/Dockerfile
docker build . --rm --tag doxygen/doxygen:debian -f debian/Dockerfile
docker build . --rm --tag doxygen/doxygen:centos -f centos/Dockerfile
```
