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
- sudo apt install build-essentials vim fakeroot bison flex ccache kernel-package ghex libncurses5-dev libssl-dev libelf-dev

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
- use command : ~make clean~
- ~make nconfig~
- check for the number of CPU we have. we will use some or all CPUY for compilation. command: ~echo $(nproc)~
- command for compile: ~make -j4 deb-pkg LOCALVERSION=-rootkit~
- after compilation if we go one directory up we can find the deb pakages for installation
- command to install kernel:  sudp dpkg -i  NON_DEBUG_IMAGE_NAME
- command to install kernel header: sudo dpkg -i linux-headers...
- command to install libc:  sudo dpkg -i linux-libc....
- possible we will not able to see grub prompt therefor we are going to do some changes in **/etc/default/grub**
- ~vim /etc/default/grub~ and there we will comment out  *GRUB_HIDDEN_TIMEOUT* and *GRUB_HIDDEN_TIMEOUT_QUIET*
- ~sudo update grub~  to uodate the grub
- ~reboot~
    
    
## Making kernel module
### intro
A linux system is majorly divided into 3 parts:
1. User space 
2. Kernel space
3. Hardware

user space can interact to hardware via kernel. And kerenl does it with device drivers.
*linux kerenl is monolithic* but modules can be written and attached with kernel in-order to enhance functionality. These type of modules are called lodable kernel modules(LKM)
Examples of kernel modules:
1. Device Drivers
2. File system drivers
3. Security product, and our special
4. Rootkits
