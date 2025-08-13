# Summit

<img width="1140" height="800" alt="download" src="https://github.com/user-attachments/assets/ef7d4dd6-8f68-446b-a58c-a5a57f84f2e1" />

##  Objective

After participating in one too many incident response activities, PicoSecure has decided to conduct a threat simulation and detection engineering engagement to bolster its malware detection capabilities. You have been assigned to work with an external penetration tester in an iterative purple-team scenario. The tester will be attempting to execute malware samples on a simulated internal user workstation. At the same time, you will need to configure PicoSecure's security tools to detect and prevent the malware from executing.

Following the Pyramid of Pain's ascending priority of indicators, your objective is to increase the simulated adversaries' cost of operations and chase them away for good. Each level of the pyramid allows you to detect and prevent various indicators of attack.

Room Prerequisites

Completing the preceding rooms in the Cyber Defence Frameworks module will be beneficial before venturing into this challenge. Specifically, the following:

The Pyramid of Pain
MITRE
Connection Details

Please click Start Machine to deploy the application, and navigate to https://10-201-120-97.reverse-proxy-us-east-1.tryhackme.com once the URL has been populated.

Note: It may take a few minutes to deploy the machine entirely. If you receive a "Bad Gateway" response, wait a few minutes and refresh the page.
___
* What is the first flag you receive after successfully detecting sample1.exe?


<img width="487" height="372" alt="center" align="left" src="https://github.com/user-attachments/assets/30174114-7551-4cad-8643-add2ae5c0506" />

<img width="689" height="235" alt="image" src="https://github.com/user-attachments/assets/9cc82dd4-b4e9-47fe-b522-06dc74d091ee" />

<img width="869" height="762" alt="image" src="https://github.com/user-attachments/assets/d888956e-b74c-49a0-a0e1-736a43cdd4e5" />

After reading the e-mail I sent, I went to the malware sandbox to analyze the sample1.exe file that was sent to me. After studying it, I saw the behavior analysis Report about this malicious file. I then copied the hash of this file and brought it to the manage hashes section, where I entered the hash value to be blocked to ensure that it is stopped the next time this file is transmitted through e-mail.

<img width="914" height="552" alt="image" src="https://github.com/user-attachments/assets/e985a19b-5a0e-4ad4-9f68-342d97a32006" />

<img width="871" height="92" alt="image" src="https://github.com/user-attachments/assets/d97cf191-4715-430a-92e3-2353698b6cc8" />

___

* What is the second flag you receive after successfully detecting sample2.exe?

<img width="901" height="644" alt="image" src="https://github.com/user-attachments/assets/d5b4bdd7-653d-4785-bbbb-5b015fcc9afd" />

We got new mail. Now we must find a way to detect and block this slightly modified version.

<img width="587" height="818" alt="image" src="https://github.com/user-attachments/assets/e9c28106-fb64-4249-8058-203aeecd1f92" />

I looked closely at the network activities for this malware and made an HTTP request to an IP address. The firewall rules are the best way to block any network traffic in this situation. In the firewall rule manager, I created a rule for denying any outbound traffic to that specific IP address.

<img width="373" height="255" alt="image" src="https://github.com/user-attachments/assets/efb3d1c2-7907-4ef6-b26a-6248da6b09a5" />
<img width="508" height="68" alt="image" src="https://github.com/user-attachments/assets/e7422e7e-03cf-4c23-887e-6c903e70d28c" />


---

* What is the third flag you receive after successfully detecting sample3.exe?

<img width="914" height="656" alt="image" src="https://github.com/user-attachments/assets/2fa74e92-fd32-4d65-8707-f488dd21f4f6" />

<img width="1046" height="682" alt="image" src="https://github.com/user-attachments/assets/96e8e9d9-c020-4b70-9660-6f31b6f1078b" />

<img width="765" height="424" alt="image" src="https://github.com/user-attachments/assets/d1839c33-4025-4ae5-958e-5da242412bf7" />



---

* What is the fourth flag you receive after successfully detecting sample4.exe?

<img width="596" height="606" alt="image" src="https://github.com/user-attachments/assets/5b532f38-e1e1-4caf-8985-0bcbd09d032b" />

<img width="886" height="436" alt="image" src="https://github.com/user-attachments/assets/5e4b5926-d881-4f6b-9f46-a356462c4a29" />

<img width="1009" height="143" alt="image" src="https://github.com/user-attachments/assets/69c1db43-f16f-48cd-b7ab-c7b9742ea4d3" />

<img width="1009" height="118" alt="image" src="https://github.com/user-attachments/assets/df03947a-5bbe-4152-a1e5-488c9dbf76da" />

<img width="613" height="371" alt="image" src="https://github.com/user-attachments/assets/3df21bd4-08ab-498f-b915-152a091834cb" />

---

* What is the fifth flag you receive after successfully detecting sample5.exe?

<img width="584" height="762" alt="image" src="https://github.com/user-attachments/assets/d340d5fd-e089-4dd8-8c50-cace5c6de22c" />

<img width="725" height="727" alt="image" src="https://github.com/user-attachments/assets/cdb7e6e1-b9d9-4f02-9555-14c8b932f0d7" />

<img width="812" height="826" alt="image" src="https://github.com/user-attachments/assets/0433479a-bf64-43dd-92ec-2c4e80a8b616" />

<img width="896" height="177" alt="image" src="https://github.com/user-attachments/assets/d07450d4-1bc3-42d4-ac0b-5307a77c66e0" />

<img width="899" height="345" alt="image" src="https://github.com/user-attachments/assets/6b883003-a0fd-4f26-b0c3-3e9325162bb0" />

<img width="638" height="453" alt="image" src="https://github.com/user-attachments/assets/b57cac4c-2cc3-46eb-9472-c81e23e0521e" />


---

* What is the final flag you receive from Sphinx?

<img width="600" height="734" alt="image" src="https://github.com/user-attachments/assets/5f81a531-1c26-4614-867d-883a2c0a1980" />

<img width="435" height="302" alt="image" src="https://github.com/user-attachments/assets/5530d924-d67b-441d-a144-4a6d7d5f3346" />

<img width="898" height="234" alt="image" src="https://github.com/user-attachments/assets/48a79e3a-a37a-4a85-b200-95f3448d933b" />

<img width="883" height="150" alt="image" src="https://github.com/user-attachments/assets/5e563562-5c48-4379-9ca7-ae2fb0bcc104" />

<img width="786" height="439" alt="image" src="https://github.com/user-attachments/assets/420fe22d-1fcf-4a6d-b304-e50f5eb42406" />


