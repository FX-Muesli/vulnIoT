Exploitable IoT project
====
IoTSploitable is a reference environment to conduct research in the area of Intrusion detection on IoT devices. It is inspired by the [Metasploitable](https://docs.rapid7.com/metasploit/metasploitable-2) from Rapid7. We aim to provide a virtual machine and a flashable image containing an embedded Linux with a collection of Vulnerabilities. Different than the Metasploitable we do not provide a VM with an desktop environment, but the configuration files necessary to build the target from scratch. Therefore we use the [Yocto Project](https://www.yoctoproject.org/) as a build system.

This brings several advantages:
- reproducibility: 
Each build produces an deterministic target. This is the same as providing a snapshot of an VM. 
- adaptability: 
Vulnerabilities and attacks are rapidly changing. Providing build files instead of a VM allows faster editing and makes changes visible.
-  minimalism: 
IoT devices have a limited memory and computing capacity, that is why the installed software should be reduced to only necessary programs. 
- based on actual use cases. 
If you look up the sponsors of the yocto project, you will se that it is used in different industy sectors in the IoT domain.
- Virtualization and Hardware: 
building the Qemu target (todo) for fast testing is possible as well as deploying it on a Raspberry Pi.

Currently supported Vulnerabilities: 
- [OWASP Mutillidae 2](https://github.com/webpwnized/mutillidae) 
- [Damn Vulnerable Web application](https://github.com/digininja/DVWA)
- weak password login via ssh

This project was created during my masters thesis. I want to use this place to thank Volkswagen Infotainment for supporting this work and allowing me to make it publicly accessible.

Contribution Guidelines
-----------------------

Currently this is an one man project. Feel free to open an issue or pull request. Some patience might be required.

Yocto references
----------------

#### OpenEmbedded-Core
OpenEmbedded-Core is a layer containing the core metadata for current versions of OpenEmbedded. It is distro-less (can build a functional image with DISTRO = "nodistro") and contains only emulated machine support.

For information about OpenEmbedded, see the OpenEmbedded website:
    https://www.openembedded.org/

The Yocto Project has extensive documentation about OE including a reference manual
which can be found at:
    https://docs.yoctoproject.org/

#### QEMU Emulation Targets
To simplify development, the build system supports building images to
work with the QEMU emulator in system emulation mode. Several architectures
are currently supported in 32 and 64 bit variants:

  * ARM (qemuarm + qemuarm64)
  * x86 (qemux86 + qemux86-64)
  * PowerPC (qemuppc only)
  * MIPS (qemumips + qemumips64)

Use of the QEMU images is covered in the Yocto Project Reference Manual.
The appropriate MACHINE variable value corresponding to the target is given
in brackets.

#### Board support packages 
Support for additional devices is normally added by adding BSP layers to your 
configuration. For more information please see the Yocto Board Support Package 
(BSP) Developer's Guide - documentation source is in documentation/bspguide or 
download the PDF from:

   https://docs.yoctoproject.org/

Note that these reference BSPs use the linux-yocto kernel and in general don't
pull in binary module support for the platforms. This means some device functionality
may be limited compared to a 'full' BSP which may be available.

Currently the only supported Board is the RaspberryPi 4B.