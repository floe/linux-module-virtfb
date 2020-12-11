# Virtual Framebuffer driver:

The VFB driver is a very basic framebuffer driver that allows creation and management
of an arbitrary number of framebuffer devices.

This is a basic driver which allows the user to create N virtual framebuffers.
These framebuffers are no more than contiguous physical memory regions that
are wrapped by the standard framebuffer device interface.

Further information regarding this driver can be found at the Freescale community.
https://community.freescale.com/message/292215#29221

Building the kernel module:
In virtual_fb source directory: 
  make -C <path to kernel sources>  M=`pwd`

Use:
The kernel module takes a single argument vfbcount which is an integer
number of virtual framebuffers which will be created. The default size of the
framebuffers is 128x128 16bpp, but this can be reconfigured using fbset after
the module is loaded. Most preferable way would be having it in userspace.

# How-To

I've updated this very old standalone module to build the latest in-kernel source (vfb.c) from 5.6.0 instead.
To use for debugging framebuffer applications on plain Ubuntu:

  * sudo insmod virtual_fb.ko vfb_enable=1
  * x11vnc -rawfb map:/dev/fb0@640x480x32
  * vinagre localhost:5900
