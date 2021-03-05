Any issues, drop a mail at pranjal.mittal1999@gmail.com .
Thanks

This is to make you install Access Noxim in your system. 
One thing is to be noted that this is exclusively for linux Ubuntu platform. May be it can work on other linux system.

We need system C to use Access Noxim. The version used is for version 0.3 of Access Noxim.
Individual folder in Full Setup contains the Individual readme for helping you in installation.
1st install system C and then Noxim

Clone or download this whole repo in your local machine
Steps to install SystemC


A. Installation of SystemC


STEP 1:

First of all open terminal (ctrl+alt+T), and type:

$ sudo apt-get install build-essential

this will download and install all the necessary compiler tools in your system.

STEP 2:

Bring the current working directory in terminal to current repo

$ cd FullSetup/systemc-2.3.3/

$ sudo mkdir /usr/local/systemc-2.3.3
$ mkdir objdir
$ cd objdir

$ sudo ../configure --prefix=/usr/local/systemc-2.3.3

$ sudo make

$ sudo make install

STEP 3:

You can skip this part 


Now as we have not installed the package in usual place. So we need to tell the system where to find the package when required.

For this type this in terminal:

$ export SYSTEMC_HOME=/usr/local/systemc-2.3.3/

Now whatever we have done will work until we log out. So to make it permanent we need to change the path variables. For this open terminal and type:

$ sudo gedit /etc/environment

This will open a text file in gedit. In that file add following line in the end:

$ SYSTEMC_HOME=”/usr/local/systemc-2.3.3/”

before saving please check that the double inverted comma used above should be proper.

STEP 4:

Now to check please download sample systemC code from http://www.asic-world.com/systemc/first1.html

To compile it from terminal use this code:

:~$ g++ -I. -I$SYSTEMC_HOME/include -L. -L$SYSTEMC_HOME/lib-linux64 -o out sample.cpp -lsystemc -lm

:~$ ./out

It will print hello world as output.




BUG FIXING

If this compilation and execution of code is throwing some error regarding linking of libraries viz, “-lsystemc not found” etc, then please read following two additional things which I have added after feedback of other systemc users who were very humble while giving these useful suggestions and time. 

While executing the code if some problem occurs like: cannot find -lsystemc etc then don’t worry it is because of linking error. To get rid of it you need to set path in LD_LIBRARY_PATHS which can be done as follows:

Two solutions:
For setting your LD_LIBRARY_PATH.
     export LD_LIBRARY_PATH=/usr/local/systemc-2.3.3/lib-linux64:$LD_LIBRARY_PATH
or, if your default LD_LIBRARY_PATH is empty
      export LD_LIBRARY_PATH=/usr/local/systemc-2.3.3/lib-linux64



It may happen that still your code is not running as not able to locate.

So what best you can do is 


:~$ g++ -I. -I$/usr/local/systemc-2.3.3/include -L. -L$SYSTEMC_HOME/lib-linux -o out sample.cpp -lsystemc -lm

This is place where system.h file is located "/usr/local/systemc-2.3.3/include"




B. Installation of Access Noxim



1. Download the Access Noxim and upload to your workstation

2. Modify the file, “Makefile.defs”, in /bin. Put the correct path of SystemC in line 8

SYSTEMC = <your SystemC install path>

3. Modify the file, “Makfile”, in /bin. Put the correct path of TARGET_ARCH in line 1

It is set to linux64 if your system is 64 bit. 
if your system is 32 bit then TARGET_ARCH=linux

$ cd bin
sudo make clean
sudo make


C. Execute the Access Noxim

1. After execute “make” command, there’s a executable file called “noxim” in the /bin
directory. Execute Noxim directly with default parameters.

$ ./noxim


Now you can follow the pdfs present in AccessNoxim_v0.3 folder from 1 to 5.