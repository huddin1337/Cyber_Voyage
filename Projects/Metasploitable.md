Metasploitable 2 is a deliberately vulnerable Linux virtual machine created by Rapid7 for security testing and training. It comes preloaded with outdated services, weak configurations, and exploitable software, making it an ideal target for practicing penetration testing techniques.

You can use it to learn by:

* Practicing scanning and enumeration with tools like Nmap or Nikto.

* Exploiting vulnerabilities using frameworks like Metasploit.

* Learning manual exploitation (e.g., weak passwords, misconfigurations, SQL injection).

* Understanding post-exploitation techniques (privilege escalation, persistence, pivoting).

* Building attack-defense skills in a safe, isolated lab environment.


# Installing Metasploitable
<img width="453" height="120" alt="image" src="https://github.com/user-attachments/assets/db75d0b9-0aef-48e3-9354-4f0ce3568535" />

To install Metasploitable you're going to need to click on new in your VirtualBox this is where you're going to enter your name for your virtual machine you're going to create a folder where all this is going to be stored. Do not select any ISO image as we'll be pulling Metasploitable from an existing save. Personally I chose Linux and my subtype as Debian but I've heard other people have used Ubuntu as an alternative. Once you click next it's going to ask you to allocate CPU and ram you can choose which you would like but I kept it simple and small. The most important step is utilizing the existing VM hardware disks file, as you would need the saved VMDK that is given to us by rapid 7. Once you've selected that file you're then able to run the virtual machine possessing Metasploitable.

<img width="975" height="405" alt="image" src="https://github.com/user-attachments/assets/88b25e98-c844-4112-8123-d0776261af38" />
<img width="897" height="122" alt="image" src="https://github.com/user-attachments/assets/d36ed4f6-eab7-4697-b44c-71add91c8166" />

# Create Virtual Network

How to safely run Metasploitable on a network that won't affect other devices on your personal network we're going to create a virtual network. To do so you're just going to head over to the tools section hitting the tab to list a bunch of useful tools and head over to network. From there you're going to create a network name it whatever you want then configure the IPV 4 address followed by a sider notation while enabling DHCP. This custom network is going to be utilized by my Kali Linux and Metasploitable VM.

<img width="347" height="450" alt="image" src="https://github.com/user-attachments/assets/c4c3a03b-4401-4130-9da5-d4cd97fbeb55" />


<img width="453" height="227" alt="image" src="https://github.com/user-attachments/assets/7124361a-d247-4496-b5ca-15baed06667c" />

Now all that is left to do is to head over to your Kali VM end your Metasploitable VM and change the network But you have to type to Nat network then you're virtual network name should be selected.

<img width="866" height="303" alt="image" src="https://github.com/user-attachments/assets/feb34ff4-e3dd-45ac-bea8-1df2dddb62ff" />


# Metasploitable

| **VM**             | **Username** | **Password** |
|---------------------|--------------|--------------|
| Metasploitable 2    | msfadmin     | msfadmin     |

