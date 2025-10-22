# **DC Configuration**

## **Introduction**
Following the completion of Independent Project 1, I now have two VMs: one running Windows Server 2025, and one running Windows 11. My current interests and career goals are related to endpoint engineering and system administration. With these VMs, I will be promoting my Windows Server VM (henceforth named vm-WinSer) to a domain controller, then joining my Windows 11 (henceforth named vm-Win11) to it.

## **Configuring the Server**
First, I made a DHCP reservation for vm-WinSer to give it a static IP. I matched the last octet of the address to the ID of the VM when I created it in Proxmox -- not sure if that's "best practice", but it made sense to me.
Next, I installed all available Windows Updates, then Active Directory Domain Services from the Server Manager app.
