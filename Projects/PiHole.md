I will be installing Pi-hole on a Raspberry Pi Zero 2 W to act as a network-wide ad blocker and DNS sinkhole. I’ll walk through the setup process step by step, starting with preparing the Pi (flashing Raspberry Pi OS, connecting it to the network, and updating packages), then moving on to installing Pi-hole using the automated installer. After that, I’ll configure the Pi-hole admin interface, set the Pi as my network’s DNS server, and test it to make sure it’s blocking ads properly. This summary will outline the exact steps I took to get Pi-hole up and running on my Pi Zero 2 W.
# Flashing OS

1. So to begin you're going to need to use the Raspberry Pi imager to install a new light OS which I will be using a 32 bit. The process is simple as you choose your Raspberry device and then the operating system as well as the storage device you were using. Before you begin to process the install you need to edit some settings such as the host name create a username and password to log into the Raspberry Pi as well as entering your network credentials. In the service section you want to enable SSH so we can access the reserve Pi through putty.
<img width="681" height="479" alt="image" src="https://github.com/user-attachments/assets/37e92ac0-1ce0-4386-a84c-f68f4e52ff93" />


<img width="550" height="171" alt="image" src="https://github.com/user-attachments/assets/204cb47b-2ebb-427f-bcca-e253002e28cc" />


<img width="680" height="476" alt="image" src="https://github.com/user-attachments/assets/50a34f88-d0fd-4ae5-a6c9-6e49641f96e0" />




<img width="550" height="173" alt="image" src="https://github.com/user-attachments/assets/b8513afd-367b-46f1-ae1f-613182c55bce" />


# Installing Pi Hole

1. For me installing the pie hole was really simple prior to that I made sure to update my apps and repositories using the update and upgrade command. After which I ran the command that that is posted on the π hole repository on GitHub. After the successfully installs it's going to ensure that you did set the IP address for the Raspberry Pi to be static so it doesn't change the designated IP address needed to keep it working properly. After going through the process you should be prompted with the password for the login into the π hole as well as the URL.

* http://github.com/pi-hole/pi-hole/#one-step-automated-install

* Sudo apt upgdate && sudo apt upgrade -y

* curl -sSL https://install.pi-hole.net | bash

<img width="573" height="392" alt="image" src="https://github.com/user-attachments/assets/a29b4d98-5b43-442e-b9aa-1c45cc8f8dc4" />


<img width="1257" height="916" alt="image" src="https://github.com/user-attachments/assets/ea1592c4-7462-45e3-a2c6-9306a42d822b" />







