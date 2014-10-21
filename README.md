Run Wayland in QEMU
===================


This repository helps you run wayland in qemu. For now it juts runs the tizen image, but this will hopefully change soon.

To run, you will need internet connectivity, then:

```
./build_qemu
./run_wayland
```

How it works (in progress)
--------------------------

Seems VIGS is the emulated video hardware, and this can have a GL command
stream, which gets rendered by the YaGL part - no idea what the acronyms stand
for yet.

On the device side for Wayland, you need
 - the modified libdrm with VIGS support (link below)
 - a kernel with the VIGS DRM driver
 - all the bits in emulator-yagl.git except the xf86 drivers
   - GBM plugin
   - hacked wayland-drm
   - hacked wayland-egl
   - GLES/EGL libaries

I *think* this works much the same as the GL transport in the google emulator,
marshalling the GL calls and then demarshalling on the host and rendering in a
sort of GLES(1/2) emulator.

Reading
-------

Some useful reading to get a handle on how this works:

 https://wiki.tizen.org/wiki/Emulator
 https://lists.tizen.org/pipermail/dev/2014-March/002118.html
 https://review.tizen.org/git/?p=sdk/emulator-yagl.git;a=tree;h=8f237e3be1d7f1376ba37b20bfe95e5a622f2729;hb=8f237e3be1d7f1376ba37b20bfe95e5a622f2729
 https://review.tizen.org/git/?p=sdk/emulator/emulator-kernel.git;a=summary
 https://review.tizen.org/git/?p=platform/adaptation/emulator/libtbm-vigs.git;a=summary
 https://review.tizen.org/git/?p=platform/adaptation/emulator/xf86-misc-vigs.git;a=summary
 https://review.tizen.org/git/?p=platform/adaptation/emulator/xf86-video-vigs.git;a=summary
 https://review.tizen.org/git/?p=platform/upstream/libdrm.git;a=summar
