## Setup
- OS - Ubuntu 18.04, 64-bit
- RAM - 8GB
- DISK - 40GB
- Install with defult options
- check for the kernel: uname -r

## Setting up Ubuntu 18.04
- run command: sudo apt update
- install: sudo apt installopen-vm-tools-desktop (for doing various operations from host to VM)
- reeboot the system

## install different kernel and developement environment
- The rootkits we will develpoe here will be compiled against a version of kernel and will work only on that specific.
- we will download latest kernel sources from kernel.org
- compile and install that kernel in Ubuntu 18.04 LTS machine
- sudo apt install build-essentials vim fakeroot bison flex ccache kernel-package ghex libncurses5-dev libssl-dev

### install kernel
- we will install kernel version 4.16.7 from kernel.org. just go there right click and copy link location. then open terminal and type

    ~wget past the copied link location~

- make a new folder where we will copy the source code of kernel
- untar the source code in new folder using command : tar xf linux-4.16.7.tar.xz
- move isde the source code
- to compile the kernel, here we will use the config fill of inatalled ubuntu.
- we can get the config file from /boot/config-4.15.0-20-generic
- copy this config file as .config file in our untared source code. use the command **cp source .config**
- after copying .config use command:  ~yes '' | make olddeconfig~
    
