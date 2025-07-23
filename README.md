# **Work in Progress**

This guide is based on the knowledge and findings of many other users, whom I will credit where possible. My intention is simply to collect all relevant information in one place to give new Users an easier start. 
If you think something important is missing, please feel free to let me know.

# LinuxCNC Ethercat Base Guide
Basierend auf [LinuxCNC](https://linuxcnc.org) – lizenziert unter der [GPLv2](https://www.gnu.org/licenses/old-licenses/gpl-2.0.html).

## EtherCAT Installation from Repositories – Step-by-Step Guide
**Source:** [LinuxCNC Forum – rodw - EtherCAT Installation Guide](https://forum.linuxcnc.org/ethercat/45336-ethercat-installation-from-repositories-how-to-step-by-step)

### 📦 1. Update Your System

```bash
sudo apt update
sudo apt upgrade
```


---

### 🔧 2. Install EtherCAT and LinuxCNC

```bash
sudo apt install ethercat-master
sudo apt install linuxcnc-uspace linuxcnc-uspace-dev
```

---


### ⚙️ 3. Configure the EtherCAT Master

Search for the MAC-Address of the Port your Ethercat Master is connected to:
```bash
ip a
```

Now edit the following:
```bash
sudo geany /etc/ethercat.conf
```

Search for these settings:
```bash
MASTER0_DEVICE="xx:aa:yy:zz:bb:cc" (replace with your MAC)
DEVICE_MODULES="generic"
```

---


### 🔌 4. Enable and Start the EtherCAT Service

```bash
sudo systemctl enable ethercat
sudo systemctl start ethercat
```

---


### ✅ 5. Check EtherCAT Status

```bash
ethercat slaves
```

You should see a list of your EtherCAT devices if everything is connected properly.

---
