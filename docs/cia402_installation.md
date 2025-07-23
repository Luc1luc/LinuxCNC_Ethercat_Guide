# **Work in Progress**

# Ethercat "Universal" CIA402 Driver Installation
**Source:** [GitHub – dbraun1981 - hal-cia402](https://github.com/dbraun1981/hal-cia402/tree/main)

This is an driver for cia402 compatible drives, which is widely used and supported for different Servos.\
You should still check if it works for your setup before.

## Installing the Universal Driver
```bash
cd ~/dev
git clone https://github.com/dbraun1981/hal-cia402
cd hal-cia402
sudo halcompile --install cia402.comp
```
This allows you to use the basic functions and communication of your Servos.

---
## Custom CIA402 Drivers additions
Nowadays theres many modified CIA402 drivers, which often require some additional Files which are not usually installed with LinuxCNC Installations via premade images.
But from what i found for most of them, theres an easy fix.

### Problem:
You wanted to install some custom made drivers to be able to use additional features, which might be product specific.
Taken this one from [Collin Bardini for Internal Homing of A6 Servos](https://github.com/CollinBardini/linuxcnc-a6-servo/tree/main), but many others are made like this too.

They have an include for files which normally just came with LinuxCNC Setups which were build from SourceCode.
´´´bash
#define HOMING_BASE /home/myname/linuxcnc-dev/src/emc/motion/homing.c
´´´
So when trying to install it will result in errors.

### Fix:
The missing base files can be found [here](https://github.com/LinuxCNC/linuxcnc/tree/master/src/emc/motion) at the LinuxCNC GitHub.
```bash
wget https://raw.githubusercontent.com/LinuxCNC/linuxcnc/master/src/emc/motion/homing.c -P ~/linuxcnc-dev/src/emc/motion/
wget https://raw.githubusercontent.com/LinuxCNC/linuxcnc/master/src/emc/motion/homing.h -P ~/linuxcnc-dev/src/emc/motion/
wget https://raw.githubusercontent.com/LinuxCNC/linuxcnc/master/src/emc/motion/motion.h -P ~/linuxcnc-dev/src/emc/motion/
```

If your drivers need different files and its available in the folder above, just modify the filename in the command.
```bash
wget https://raw.githubusercontent.com/LinuxCNC/linuxcnc/master/src/emc/motion/{filename} -P ~/linuxcnc-dev/src/emc/motion/
```

Modify the "#define HOMING_BASE ..." line to:
```bash
#define HOMING_BASE /home/$USER/linuxcnc-dev/src/emc/motion/homing.c
```
For other files:
```bash
#define HOMING_BASE /home/$USER/linuxcnc-dev/src/emc/motion/{]filename}
```

Thanks to **eduard** for bringing up the ["Idea" at the Forum](https://forum.linuxcnc.org/ethercat/51830-marco-reps-video-on-youtube-about-ethercat?start=10)

---

