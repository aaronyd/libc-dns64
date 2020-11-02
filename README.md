For Glibc, 3 files included:
* getaddrinfo.c
* netdb.h
* Makeconfig

Replace them in following directories:

/glibc-2.1*/sysdeps/posix/getaddrinfo.c

/glibc-2.1*/resolv/netdb.h

/glibc-2.1*/Makeconfig

Notice: 
because the heuristic function calls a couple of functions that are 
defined as libc_hidden_pro, we need to change the Makeconfig file and 
include "-lresolv" to get around the PLT linkage issue.

check the Makeconfig if you have questions.

Recompile the glibc. 
Test has been done on linux kernel 2.6.35 with glibc 2.13 stable.

-----

For ecdysis-bind-9.7.2, plz copy 'query.c' to directory
ecdysis-bind-9.7.2/bin/named/

Then, recomplie the dns64 server:

make distclean

configure --args

make

make install
