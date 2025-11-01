# **DC Creation**

## **Introduction**
Following the completion of Independent Project 1, I now have two VMs: one running Windows Server 2025, and one running Windows 11. My current interests and career goals are related to endpoint engineering and system administration. With these VMs, I will be promoting my Windows Server VM (henceforth named vm-WinSer2025) to a domain controller, then joining my Windows 11 (henceforth named vm-Win11) to it.

<sub>Note: The screenshots in this file may appear strange due to the snipping tool not adjusting correctly for my HDR monitor.</sub>

## **Configuring the Server**
First, I made a DHCP reservation for vm-WinSer to give it a static IP, then set that same static IP on the network adapter to avoid any warnings. I matched the last octet of the address to the ID of the VM when I created it in Proxmox -- not sure if that's "best practice", but it made sense to me.
Next, I installed all available Windows Updates, then Active Directory Domain Services from the Server Manager app. After AD DS was installed, I ran through the AD DS Configuration Wizard to create my lab.local domain on my network.

<img width="1138" height="707" alt="image" src="https://github.com/user-attachments/assets/bfdcf98d-8782-4267-8c79-ff2897c94fd4" />

DNS test passed! I should be good to join clients at this point.

<img width="628" height="508" alt="image" src="https://github.com/user-attachments/assets/f08ab58e-5a70-4c75-bc46-2243dc885efd" />

## **Joining a PC to the DC**
First, I set the preferred DNS server on vm-Win11 to the DC's IP Address so I don't run into any service or policy connection issues. Next, I join the client to the domain through Advanced System Settings and restart the PC.

<img width="577" height="415" alt="image" src="https://github.com/user-attachments/assets/aec3692f-e53f-4cd8-9e93-5a51fbad8b27" />

To make sure this worked, I created a LabTestUser account on the domain within Active Directory Users and Computers (ADUC) and was able to successfully log in to vm-Win11 as that user.

<img width="527" height="190" alt="image" src="https://github.com/user-attachments/assets/c634061c-6efd-4425-b8a2-c413c0d1840d" />

<img width="906" height="500" alt="image" src="https://github.com/user-attachments/assets/8a168947-44b9-4858-b24b-041b50ac5e0b" />
