# **Home Assistant Setup**

## **Introduction**
I currently have a Proxmox VE server with some extra resources, and I would love to use Home Assistant in the future for all my smart devices. I also have an old iPad Mini 2, which is unable to install nearly any app on the App Store due to the iOS limitations; however, it could be a fanastic "hub" to view and control my Home Assistant environment via the web interface once it's up and running. In this project, I try to set up a Home Assistant VM on my server.

## **Setup**
The Home Assistant image for Proxmox can be found [here](https://www.home-assistant.io/installation/alternative). I copy the link on that page to the KVM/Proxmox image, then use `winget *link*` to download the file and `unxz haos_ova-16.2.qcow2.xz` to unzip it.

Now I can create the VM. I'm going to go with Home Assistant's recommended minimum CPU and Memory specs for now: 2 cores, 4GB RAM. I make sure "start at boot" is selected and I give the VM and ID. For OS, I select "don't use any media." For System, I set "machine" to *q35*, set BIOS to *OVMF (UEFI)*, make local-lvm the EFI storage, and make sure "Pre-Enroll keys" is unchecked. I clear out the Disks list, set the minimum CPU and Memory specs I previously mentioned, and leave the network settings default.

Next, I add the image to the VM by moving it from the host to the VM's storage using `qm importdisk 200 haos_ova-16.2.qcow2 local-lvm` in the console. I go back into the VM in Proxmox and go to the Hardware tab. I'll edit the Unused Disk and check the "Discard" option, then edit Options > Boot Order and make sure only the new drive (scsi0) is checked.

I can now start the VM!

<img width="1087" height="700" alt="image" src="https://github.com/user-attachments/assets/22aaead4-3283-4b82-9353-5338cf260531" />

<img width="821" height="700" alt="image" src="https://github.com/user-attachments/assets/b86856c5-552c-461f-919f-0622322e120b" />

<img width="1335" height="700" alt="image" src="https://github.com/user-attachments/assets/3f358b6e-f293-4443-bde2-4ac499799786" />
