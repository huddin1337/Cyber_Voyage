For today's project, we'll be installing Openvas On my Kali Linux machine. After installation, will begin to proceed with conducting A vulnerability scan on my home network. OpenVAS (Open Vulnerability Assessment Scanner) is an open-source tool used for vulnerability scanning. It scans systems, services, and applications for known security issues and misconfigurations, helping security teams identify and fix weaknesses before attackers can exploit them. 

## Initial install
To get this started, I'm going to run the apt update and upgrade command. After it's successfully updated and upgraded. After updating our packages, we're going to install Openvas using the command: 
 
**sudo apt install openvas** 
 
After a successful install, I will have to change to the root user and run these commands: 
 
**Sudo –i** 
 
**Gvm-setup** 
 
  After running the setup command you're able to see your password towards the bottom under “user created with password”. By default the username will be admin and that long string will be your password to log in.
The setup was a success, So the next step would be to run a check to ensure that it is installed correctly: 
 
**Gvm-check-setup** 
 
<img width="975" height="81" alt="image" src="https://github.com/user-attachments/assets/b5631457-d1c6-450f-b2d0-7546ec85364b" />

## Postgresql Error
After running the check I received an error message stating im using an outdate version of postgresql.   To fix this issue we're going to have to purge open boss and all remains of postgresql.  The commands will be run as followed:

**Sudo apt purge openvas**
**Sudo apt autoremove**
**Sudo apt clean**

After removing openvas we're going to use grep to identify traces of postgresql on kali to remove them.
**dpkg -l | grep postgres**
** sudo apt-get  --purge remove (all postgres listed above)


now i will redo the whole process of installing openvas on my VM, as well as conducing another check. 

<img width="667" height="66" alt="image" src="https://github.com/user-attachments/assets/50a3f754-91b5-40d9-b909-bf6687e6953e" />

## Starting GVM  
We have the greenlight. All we have to do now is to start GVM. Was already running Ohh so I ran the command to stop GVM, then I proceeded to run the command to start GVM which ended up loading the web browser for me

**sudo gvm-stop**

**sudo gvm-start**


Unfortunately I forgot my password that originally came with the previous install of GVM as I already had an admin account associated with this program. In order for me to change it I ran the following command:

**sudo -E -u _gvm gvmd –user=admin –new-password=’new password’**


