# Machine Setup

To add a machine GPU or CPU you need to install Ubuntu 22.04 on the machine and prepare a range of open ports, choose a standard installation of Ubuntu 22.04 desktop or server version. currently we do not support any other version of ubuntu. Windows and ubuntu 23.04 support will be added later. To install quickpod software on your machine and connect it to your account switch to root account with command sudo su - and run the following command.

Copy

{% code overflow="wrap" %}
```
wget -O install.bin https://data.quickpod.io/install.bin && chmod 755 ./install.bin && ./install.bin YOUR_API_KEY
```
{% endcode %}

The installer will ask for your open port range, if you made a mistake you can manually edit the following file to update your port range /var/lib/quickpod/machine\_open\_port\_range. After a successful installation please visit the machine page GPU Machines if machine has GPUs or CPU Machines to list your machine and set prices for GPU, CPU, storage and duration etc. If you face difficulties please use live chat or [quickpod discord](https://discord.gg/CwgSdWVCHC).
