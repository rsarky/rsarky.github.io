---
layout: post
title:  "Linux kernel modules"
date:   2019-08-13 17:33:39 +0530
categories: linux eudyptula
---
Linux kernel development has always fascinated me.
I have been wanting to learn about how things work under the hood for some time now.
To this end I took up the [Eudyptula Challenge](http://eudyptula-challenge.org).
This is the first among a series of posts to keep track of my progress and log
the things I learn along the way

Without further ado; Let's get to the point of this blog. `Kernel Modules`

The first challenge involves writing a simple _Hello World_ module that will
print a string to the message buffer.

## What are Kernel Modules?
A kernel module is a piece of code that can be loaded or unloaded into the kernel 
on demand (at runtime). They extend the functionality of the kernel without the need to reboot
the system.<br>
A common type of module is the device driver. A device driver abstracts a piece of hardware and provides
a uniform API for working with the device. The kernel must have a device driver for every peripheral
attached to the system from a keyboard to the usb stick that you can plug into it.

A simple kernel module:
```
#include<linux/module.h>
#include<linux/init.h>
MODULE_LICENSE("Dual BSD/GPL");

static int hello_init(void)
{
	printk(KERN_ALERT "Hello World\n");
	return 0;
}

static void hello_exit(void)
{
	printk(KERN_ALERT "Goodbye World\n");
}

module_init(hello_init);
module_exit(hello_exit);
```

Save this in a file called helloworld.c.
<br>
We have 2 functions `hello_init` and `hello_exit` for the initialisation and
deinitialisation of our module respectively.<br>
`module_init` and `module_exit` are macros defined in `linux/init.h` that add the boilerplate
code necessary to call the init/exit functions when the module is loaded/unloaded from kernel space.
<br>
We need to build this module against the running kernel so that we can load it later.
For building we will use `make`.
Here's the Makefile:
```
obj-m += helloworld.o
all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
```
Run `make`.

To load the driver into the kernel run:
>  insmod helloworld.ko

If you view the output of dmesg you will be able to view the string "Hello World"
printed by your module.
We can now remove the module by 
> rmmod helloworld

You will now be able to see "Goodbye World" on dmesg.

There we have it! We built our own kernel module!
Sadly it doesn't do anything useful now but it's a start.

Here are some resources to read more on kernel modules:
- [Linux Device Drivers Book](https://lwn.net/Kernel/LDD3/)
- [tldp](http://tldp.org/LDP/lkmpg/2.6/html/index.html)
