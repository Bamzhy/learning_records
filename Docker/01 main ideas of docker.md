### a quick demo
```
/*excute these commands in order*/
$ docker pull centos:8
$ docker run -it centos:8 /bin/bash
/ #
/ # ps
PID  USER  TIME  COMMAND
 1   root  0:00  /bin/sh
 19  root  0:00  ps
```
- /bin/bash is the first process inside the container(PID=1)
- And the container just contains two processes
- That means /bin/bash and ps is isolated by docker

### namespace
- Namespaces are one of a feature in the Linux Kernel and fundamental aspecct of containers on Linux.
- Namespaces provide a layer of isolation
```
/*create a process in linux*/
int pid = clone(main_function, stack_size, SIGCHLD, NULL)
/*specify the CLONE_NEWPID argument*/
int pid = clone(main_function, stack_size, CLONE_NEWPID|SIGCHLD, NULL)
```
- The newly created process will 'see' a new namespace, and in this namespace, its PID is 1.
- But in **Real Process Space** in its host, the PID of this process is still real number, like 1061, not 1.
- Except PID Namespace, Linux provide other namespaces
```
```
