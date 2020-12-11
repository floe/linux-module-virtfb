# Virtual Framebuffer driver:

The VFB driver is a very basic framebuffer driver that allows creation and management
of an arbitrary number of framebuffer devices.

These framebuffers are no more than contiguous physical memory regions that
are wrapped by the standard framebuffer device interface.

### Building the kernel module

In virtual_fb source directory: 
  `make -C <path to kernel sources>  M="$(pwd)"`

### How-To

I've updated this very old standalone module to build the latest in-kernel source (`vfb.c`) from 5.6.0 instead.
To use for debugging framebuffer applications on plain Ubuntu:

  * `sudo insmod virtual_fb.ko vfb_enable=1`
  * `x11vnc -rawfb map:/dev/fb0@640x480x32`
  * `vinagre localhost:5900`
