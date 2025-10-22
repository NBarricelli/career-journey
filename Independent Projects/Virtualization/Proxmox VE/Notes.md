# **Proxmox VE**

## **Introduction**
I had an extra desktop laying around and wanted to use it for something productive. It's an MFF desktop with an Intel i5-13600T, 16GB RAM, and 512GB local storage. It isn't a lot, but I can always upgrade later on if needed. I did some research on projects to do that complement the skills I am trying to develop, and a local hypervisor / virtualization host was at the top. This allows me to create a solid foundation for future projects since I'll be able to quickly spin up VMs for whatever I need. This file is documentation of everything I've done to set up and use Proxmox VE on my spare desktop.

## **Setting up Proxmox VE**

### **Installation**
I used BalenaEtcher to flash the Proxmox VE 9.0 ISO to my USB flashdrive, then I booted to the flashdrive from my desktop. Since I only have the one local drive, I installed Proxmox to it with ext4 filesystem. If this were a much larger computer with several more drives, I would consider using RAID 1 instead for redundancy purposes.
For the network setup, I used my home network's gateway and DNS server. I only have my ISP's modem and my TPLINK AXE5400 router, so the network setup is simple. I made my hostname and chose a good IP address. At the same time, I made a DHCP reservation from my router's web interface to make sure that IP address isn't leased to any other device on my network.
After the network configuration was complete, Proxmox VE began installing. Once it was finished, it booted to the "welcome" CLI screen and I was ready to go. I used my laptop to connect and log in using the IP address and login credentials I set, and it worked!

<img width="3820" height="2020" alt="image" src="https://github.com/user-attachments/assets/938a0fbc-f1a4-40b0-b8b1-f32c209c1871" />

### **Updating & Introduction to Proxmox VE Helper Scripts**
To introduce myself to Proxmox VE Helper Scripts and make sure my Proxmox is up to date, I ran the [PVE Post Install](https://community-scripts.github.io/ProxmoxVE/scripts?id=post-pve-install) script. 

<img width="2202" height="777" alt="image" src="https://github.com/user-attachments/assets/55e90f8b-a6b1-4d17-a486-04ba56b344cc" />

I also ran the [File Browser](https://community-scripts.github.io/ProxmoxVE/scripts?id=filebrowser&category=Files+%26+Downloads) addon installer to make navigating through my file directories easier.

<img width="724" height="400" alt="image" src="https://github.com/user-attachments/assets/d69bbcc3-2168-478c-9081-528e91325d95" />
