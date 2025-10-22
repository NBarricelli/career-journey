# **Proxmox VE**

## **Introduction**
I had an extra desktop laying around and wanted to use it for something productive. It's an MFF desktop with an Intel i5-13600T, 16GB RAM, and 512GB local storage. It isn't a lot, but I can always upgrade later on if needed. I did some research on projects to do that complement the skills I am trying to develop, and a local hypervisor / virtualization host was at the top. This allows me to create a solid foundation for future projects since I'll be able to quickly spin up VMs for whatever I need. This file is documentation of everything I've done to set up and use Proxmox VE on my spare desktop.

## **Setting up Proxmox VE and VMs**

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

...and then ran the [FileBrowser Quantum](https://community-scripts.github.io/ProxmoxVE/scripts?id=filebrowser-quantum&category=Files+%26+Downloads) addon installer instead.

<img width="724" height="400" alt="image" src="https://github.com/user-attachments/assets/21adbff7-7dd5-4cf7-9d1b-9c96099180d2" />

### **Adding Another Drive**
I had an unused M.2 SSD to USB 3.2 enclosure laying around, so I decided to use that and add another 512GB to my available storage. I realize this is sub-optimal due to limitations with running VMs off of a USB device, but unfortunately I only have one onboard SSD slot on this computer.

I plugged the enclosure into the desktop and ran `lsblk` in the shell to get a list of drives connected to the desktop. After identifying the new drive, I saw it had a 4 existing partitions. I used gdisk to remove those by running `gdisk /dev/sda`, then using `d` to delete the partitions and `w` to write the changes. I now have an unpartitioned drive, and I ran `pvcreate /dev/sda` to initialize it as a physical volume.

It is worth mentioning that I am far from fluent in Linux. At this point, I was stuck because I couldn't figure out what else I needed to run, and Proxmox was not able to create an LVM on the new drive yet. I decided to take a step back and run `cfdisk /dev/sda` to clear the drive, then `mkfs.ext4 /dev/sda1` to create the filesystem. Now I could use `mkdir /mnt/SSD01` to create a folder, then `mount /dev/sda1 /mnt/SSD01` to mount the drive to said folder. At this point, I was able to create a new Directory using that SSD01 folder successfully.

### **Adding a Backup Schedule**
I figure it's good practice to create a backup schedule, even if I might not be storing important or persistent data on my VMs right now. This was simple: navigating to the Backup section of the "datacenter", and hitting Add. I set the rule to backup all VMs every week at Sunday 23:00, store it on the local drive, and only keep the previous 1 backup. This should be sufficient for now.

<img width="1078" height="163" alt="image" src="https://github.com/user-attachments/assets/c851470b-b4ed-4238-9ee6-283ca10c7eb6" />

### **Uploading and Spinning Up VMs**
I am going to run two VMs: one Windows Server 2025 VM to use as a Domain Controller (foundation for identity/hybrid labs), and one Windows 11 25H2 VM to use with endpoint management testing. I grabbed the ISOs from Microsoft and was able to upload them to Proxmox easily. Since Windows 11 requires TPM, I also needed to grab the [VirtIO Drivers](https://pve.proxmox.com/wiki/Windows_VirtIO_Drivers) ISO.

I first started with the Windows 11 VM. I'm running this one on my local drive and gave it 100GB of storage, 4 cores, and 4GB RAM to work with. After creating it, I added the VirtIO drive using the Add > CD/DVD button on the VM page. I then did the exact same thing for the Windows Server 2025 VM, but I gave this one 150GB of storage. I spun both of these VMs up and installed the respective OSes without any problems.

<img width="1312" height="825" alt="image" src="https://github.com/user-attachments/assets/ae00c62b-fe4b-4d00-8bd8-da803d1f6ad5" />

<img width="1277" height="678" alt="image" src="https://github.com/user-attachments/assets/2188af09-d1b9-4776-91a2-fc492c113ae6" />
