# LinuxCNC Ethercat specialities
The Ethercat Setup with LinuxCNC consists consist of the same kind of **HAL** and **INI** files, as per the normal setup.
Whats new is the **ethercat-conf.xml**, which is then used in the **HAL** to connect the "digital pins" of the Servo Drives-

## Ethercat-Conf

In the ethercat-conf.xml you define your connected ethercat devices and their signals.

Taken that you already done the [Initial Linux Ethercat Setup](https://github.com/Luc1luc/LinuxCNC_Ethercat_Guide/tree/main?tab=readme-ov-file#ethercat-installation-from-repositories--step-by-step-guide), as also all your devices are connected and powered
