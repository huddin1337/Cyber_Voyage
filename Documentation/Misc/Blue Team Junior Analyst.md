# Blue Team Junior Analyst Pathway Bundle
* [Introduction to Digital Forensics](#introduction-to-digital-forensics)
  * [Digital Evidence](#Digital-Evidence)
  * [Linux CLI](#Linux-CLI)
  * [Steganography](#Steganography)
  * [Cracking ZIP Files](#Cracking-ZIP-Files)
  * [Course Capstone](#Course-Capstone)
* [Introduction to OSINT](#Introduction-to-OSINT)
  * [Introduction](#Introduction)
  * [Intelligence](#Intelligence)
  * [Securing Yourself Online](#Securing-Yourself-Online)
  * [Tools and Services](#Tools-and-Services)
  * [Course Capstone](#Course-Capstone)
* [Introduction to Vulnerability Management](#Introduction-to-Vulnerability-Management)
* [Introduction to Threat Hunting](#Introduction-to-Threat-Hunting)
* [Introduction to Network Analysis](#Introduction-to-Network-Analysis)
* [Introduction to Dark Web Operations](#Introduction-to-Dark-Web-Operations)





# Introduction to Digital Forensics

> [!TIP]
>* Computer Forensics – Identifying, collecting, and preserving evidence taken from desktops, laptops, and other computer systems and storage media to aid investigations or legal proceedings.
>* Network Forensics – The monitoring, collection, and analysis of network activities such as visited websites and connected IPs, usually associated with incident response and intrusion detection.
>* Memory Forensics – The process of recovering evidence from the RAM of a running system (also known as live acquisition or live response).
>* Mobile Forensics – The process of recovering evidence from mobile phones, SIM cards, PDAs, tablets, and other mobile devices.


| Incident Response Capabilities | Legal Prosecution and Chain of Custody | Monitoring Employees |
| :--- | :--- | :--- |
| To improve **incident response capabilities**, it's important to have a team with strong technical backgrounds. When dealing with an incident, it is crucial to **correctly gather and preserve evidence**. **Digital Forensics analysts** are a great asset for investigating malicious activities like malware infections or insider threats. | A key procedure for submitting digital evidence in court is the **Chain of Custody**. If evidence is not kept secure and unmodified, it will be invalid and hold no weight in court. Forensics experts know how to handle and secure evidence to maintain its integrity. | Sometimes it's necessary to **closely monitor employees** due to suspicious or malicious behavior, such as inappropriate internet browsing or downloading malicious files. Forensics analysts can monitor for insider threats and covertly collect evidence for Human Resources or law enforcement. |


| Role | Responsibilities |
| :--- | :--- |
| **Tier 1 SOC Analyst** | Conducts initial investigations and first-line incident response. Collects evidence like IPs, domains, and emails to justify defensive actions. |
| **Tier 2/3 SOC Analyst** | Handles escalated and more critical investigations requiring greater technical expertise and access to specialized tools. Evidence collection is under stricter conditions. |
| **Malware Analyst** | Uses digital forensics to analyze malware samples, discover their purpose, and gather Indicators of Compromise (IOCs) for future detection. |
| **Digital Forensics Analyst** | Works on high-profile investigations, escalated cases, and employee monitoring. Collaborates with the Security Incident Response Team (SIRT) on tasks requiring trusted, highly-technical individuals. |
| **Insider Threat Analyst** | Utilizes extensive digital forensics skills to detect and monitor insider threats, ensuring all evidence against an individual is collected appropriately. |
| **Threat Hunter** | Expert technical defender with a deep understanding of offensive and defensive practices. Hunts for threats by understanding computer/network workings and identifying key artifacts. |
| **Incident Responder** | Top-tier security analyst with skills across blue-team disciplines, including forensics. Conducts deep, in-depth investigations to understand how a system was compromised and the behavior of the device. Often works with Forensic Examiners to retrieve and analyze data from physical media. |

---

### Evidence Collection

| Tool | Description |
| :--- | :--- |
| **KAPE** | **K**roll **A**rtifact **P**arser and **E**xtractor is a free, open-source tool for automating the collection and parsing of forensic artifacts from a computer's file system and memory. It can be used locally or remotely to quickly gather key data. |
| **FTK Imager** | A tool for creating hard drive and memory images for analysis. It can also import disk images, allowing users to navigate the file system as if on a live device. |
| **EnCase** | A suite of tools for digital forensics and e-Discovery. It can take forensic images of computers, mobile phones, and IoT devices for evidence collection and analysis. |
| **Cellebrite** | A suite of tools designed for mobile forensics, enabling the acquisition and processing of data from mobile devices. |

### Evidence Analysis

| Tool | Description |
| :--- | :--- |
| **Autopsy** | An open-source digital forensics tool with a user-friendly interface. It analyzes forensic images from hard drives and mobile devices to extract key information like recently used programs, deleted files, emails, and visited websites. |
| **Volatility** | A Python-based memory forensics framework that analyzes memory dumps to uncover a computer's past activities and potential malicious actions. It works across Windows, Linux, and Mac OS, and can even recover deleted files. |

---


## Digital Forensics
> [!NOTE]
> 
>### 1. Evidence via Computers
>Most evidence will be **files and other data on electronic storage media**, such as hard drives in desktops, laptops, and mobile devices. For example, a folder of inappropriate images on a work laptop is considered evidence and must be properly preserved for disciplinary action or prosecution.
>Other types of evidence found on computers can include:
>* Saved emails or chat logs
>* Images, videos, and audio files
>* Text files
>Criminals often use tactics to hide data from immediate view. Files and data can be hidden in **slack space** on hard drives or concealed within legitimate files using **steganography**.
>
>### 2. Evidence via Network
>When moving beyond physical storage, there are many types of evidence we can collect from networks.
>**Browser history** is a major source of evidence, acting as a record of visited sites and access times. This is useful for investigating breaches of a company’s **Acceptable Use Policy**, such as inappropriate browsing during work hours.
>We don't need to rely solely on the browser, as **network devices** like web proxies and routers also log information about online requests.
>In recent years, **social media posts**, as well as posts on forums and blogs, have been used as digital evidence in court, provided there is a reasonable belief they were made by the intended account owner. **Instant messaging conversations** from applications like Facebook Messenger and WhatsApp can also be used as evidence.
>To learn more about network forensics and tools, you can refer to the provided link.
>
>### 3. Evidence via Mobiles
>Due to their constant use, mobile phones contain a wealth of information that can be very useful to investigators. Evidence that can be retrieved from a mobile device includes:
>* Call history
>* Text messages
>* Contacts
>* Web history
>* Images and videos
>* Apps
>* GPS location
>* Notes
>With the use of specialized mobile forensics tools, even **deleted files** and old app data can be recovered.
>For more information on mobile forensics and the tools used, you can refer to the provided link.

---
> [!CAUTION]
> **Chain of Custody** is the crucial process of tracking the handling of evidence to ensure it hasn't been tampered with, making it admissible in court. The process requires tracking who received the evidence, who it was received by, and the date and time of the transfer. To maintain the chain of custody, analysts should never work on the original evidence. Instead, they should create a full-bit copy, verify its integrity using a hash, and then work on the copy. Before storing evidence, the storage media should be completely sanitized to avoid contamination.

---
### Digital Evidence Quiz

| Question | Correct Answer | Explanation |
| :--- | :--- | :--- |
| **Question 1: Persistent Data refers to;** | Data stored on storage media | Persistent data is data that is stored physically on a medium such as a hard drive or USB. |
| **Question 2: Volatile Data refers to;** | Data that can be lost if a system is powered off | Volatility data is data that can be lost under certain circumstances, such as a system being powered off, or the memory space being reallocated. |
| **Question 3: What should occur to ensure that the original evidence and any copies are completely identical?** | File hashing | Even the smallest change to the input file will result in a change to the resulting hash value, making it easy to prove (or disprove) the authenticity of digital evidence. |
| **Question 4: Can digital evidence be collected without authorization or a warrant?** | No | In 99% of cases, a warrant must be provided to collect digital evidence from a person of interest's devices. |
| **Question 5: Recently, the following evidence categories have been used in court; internet browsing history, ATM transactions, instant messaging conversations, and GPS tracking, true or false?** | True | The answer is true! This goes to show how important digital forensics is concerning law enforcement. |

---

## Linux CLI

### Linux File System and Command Summary

| Command/Concept | Description | Example Usage |
| :--- | :--- | :--- |
| **Linux File Structure** | A hierarchical, tree-like organization of all files and directories on the system, beginning at the root directory (`/`). | `/home/Bruce`, `/etc`, `/var/log` |
| **`cd`** | **C**hange **D**irectory. Used to navigate to a new directory. | `cd /var/www/html` |
| **`ls`** | **L**i**s**t. Lists the files and directories in the current directory. | `ls` |
| **`ls -a`** | **L**i**s**t **A**ll. Lists all files, including hidden ones (those with a `.` at the beginning of their name). | `ls -a` |
| **`cat`** | Concatenates files and prints their content to the standard output. Commonly used to display the entire content of a file. | `cat /etc/passwd` |
| **`strings`** | Extracts and prints human-readable strings from binary files. | `strings /bin/bash` |
| **`head`** | Displays the first few lines of a file (default is 10). | `head my_log_file.txt` |
| **`find`** | A powerful and flexible command used to search for files in a directory hierarchy based on various criteria. | `find /home/Bruce -name "report.txt"` |
| **`locate`** | A fast way to find files by searching a pre-built database. | `locate financial_statement.csv` |
| **`file`** | Determines the file type. | `file my_document.pdf` |

---

## Steganography
> [!IMPORTANT]
> ```
> sudo apt-get install steghide
> ```

### Steganography with Steghide: A Step-by-Step Guide
> [!NOTE]
> ### **1. Prepare the Secret File**
> 
> First, you need to compress the file or folder you want to hide. This ensures all the data is in one file ready for embedding.
> 
> - **Command:** `zip -r secret.zip secret`
> - **Note:** The `-r` flag tells the `zip` command to compress recursively, including all files and subdirectories.
> 
> ### **2. Embed the Secret File in a Cover File**
> 
> Next, use the `steghide` tool to hide your compressed file inside a cover file, like an image.
> 
> - **Command:** `steghide embed -cf [cover_file] -ef [secret_file]`
> - **Example:** `steghide embed -cf laptop.jpg -ef secret.zip`
> - **Flags:**
>     - `-cf`: Specifies the **c**over **f**ile.
>     - `-ef`: Specifies the file you want to **e**mbed.
> - **Optional:** You can use the `-sf` flag to save the output to a new file instead of overwriting the cover file.
> - **Example:** `steghide embed -cf laptop.jpg -ef secret.zip -sf laptop2.jpg`
> 
> ### **3. Extract the Hidden File**
> 
> To retrieve the hidden data, use the `steghide extract` command. You will be prompted to enter the passphrase you set during the embedding process.
> 
> - **Command:** `steghide extract -sf [stego_file]`
> - **Example:** `steghide extract -sf laptop2.jpg`
> - **Flags:**
>     - `-sf`: Specifies the **s**tego **f**ile from which to extract data.
> 
### Steganography Activity and Quiz

```
sudo apt install stegseek
## I create a password list containg words given to me for this quiz
stegseel cars.jpeg password.txt
## Brute forces passwords on steghide phrases
## all files in directory
for f in *; do stegseek $f  pass.txt;  done

## At the end of the quiz they metioned using "StegDetect"

```
      
---

## Cracking ZIP Files
> [!TIP]
> ### Creating a Password-Protected ZIP File
> 
> #### **Step 1: Install the `zip` tool**
> 
> Ensure you have the `zip` tool installed on your system.
> 
> - **Command:** `sudo apt-get install zip`
> - **Note:** This command is for Debian/Ubuntu-based operating systems.
> 
> #### **Step 2: Create the Encrypted ZIP Archive**
> 
> Use the `zip` command with the `--encrypt` flag to create a password-protected ZIP file.
> 
> - **Command:** `zip --encrypt [output_file_name] [input_file]`
> - **Example:** `zip --encrypt Protected.zip text.txt`
> - **Note:** You will be prompted to enter a password, which will be required to access the file's contents later.
> 
> #### **Step 3: Verify Encryption**
> - Attempt to unzip the file to confirm it is password-protected. The system will ask for the password before extracting the files.

---
> [!NOTE]
> ### ZIP Password Cracking with `fcrackzip`
> 
> #### **1. Install `fcrackzip`**
> 
> First, ensure you have the `fcrackzip` tool installed on your system.
> 
> - **Command:** `sudo apt-get install fcrackzip`
> - **Note:** This command is for Debian/Ubuntu-based operating systems.
> 
> #### **2. Understand Brute-Force Attacks**
> 
> A brute-force attack tries every possible password combination to find the correct one.
> 
> - **Pros:** Guarantees finding the password eventually. Can be faster if you know the password's length or character set.
> - **Cons:** Extremely time-consuming, especially for longer passwords.
> 
> #### **3. Launch the Brute-Force Attack**
> 
> Use the `fcrackzip` command with specific flags to launch a brute-force attack on a password-protected ZIP file.
> 
> - **Command:** `fcrackzip -b -u -c [char_set] -l [length] [target_file]`
> - **Example:** `fcrackzip -b -u -c a1 -l 4 BruteForceAttack.zip`
> - **Notes on Flags:**
>     - `-b`: Specifies a brute-force attack.
>     - `-u`: Unzips the file if the password is found.
>     - `-c`: Defines the character set to use for the attack (e.g., `a1` for lowercase letters and numbers).
>     - `-l`: Sets the password length to check.
 
      
---
> [!NOTE]
> ### ZIP Password Cracking with a Dictionary Attack
> 
> #### **1. Understand the Method**
> 
> A dictionary attack uses a wordlist (a file containing common passwords) to guess the password.
> 
> - **Pros:** Can be very fast if the password is in the wordlist.
> - **Cons:** Will fail completely if the password is not in the wordlist.
> 
> #### **2. Find a Wordlist**
> 
> Locate a wordlist on your system. A popular one is `rockyou.txt`.
> 
> - **To locate:** `locate rockyou.txt`
> - **To decompress (if needed):** `gunzip /path/to/rockyou.txt.gz`
> 
> #### **3. Launch the Dictionary Attack**
> 
> Use the `fcrackzip` command with the `-D` flag to perform the attack.
> 
> - **Command:** `fcrackzip -D -u -p [wordlist_path] [target_file]`
> - **Example:** `fcrackzip -D -u -p /usr/share/wordlists/rockyou.txt DictionaryAttack.zip`
> - **Notes on Flags:**
>     - `-D`: Specifies a dictionary attack.
>     - `-u`: Unzips the file if the password is found.
>     - `-p`: Points to the wordlist file.
 
      
---

## Course Capstone
> [!IMPORTANT]
> ### Digital Forensics Challenge: Finding Hidden Evidence
> 
> #### **Step 1: Environment Setup**
> 
> * **Install:** VirtualBox and the Kali Linux VM.
> * **Download:** The challenge disk image to your Kali VM and unzip it.
> 
> #### **Step 2: Begin Investigation**
> 
> * Start in the "Saved Emails" directory as your starting point.
> * **Commands:** Use `cd` to navigate and `ls` to list files.
> 
> #### **Step 3: Apply Forensic Techniques**
> 
> Use the following commands to find 4 pieces of evidence (look for strings like `{1 of 4}`).
> 
> | Technique | Commands | Notes |
> | :--- | :--- | :--- |
> | **Hidden Files/Folders** | `ls -a` | Look for files starting with a `.` |
> | **Incorrect File Extensions** | `file` | Use this to determine a file's true type. |
> | **Reading Files** | `cat`, `head`, `strings` | Read contents of text files or extract strings from binary files. |
> | **Steganography** | `steghide` | Use the `info` and `extract` commands. |
> | **Password Cracking** | `fcrackzip` | Use with the `rockyou.txt` wordlist for `.zip` files. |
> 
> #### **Step 4: Comprehensive Search**
> 
> * Examine all files and folders in both the GUI and CLI.
> * Remember to look in unexpected places, as some evidence is subtly hidden.
> * **Tip:** Use `man <command>` for help with any tool.
  

---































 






---
# Introduction to OSINT

---
## Introduction
> [!IMPORTANT]
> ### What is OSINT?
> 
> **OSINT**, or **Open-Source Intelligence**, is data collected from publicly available sources. It is widely used in various fields, from law > enforcement and business to cybercrime, for both offensive and defensive purposes.
> 
> #### Examples of OSINT Data:
> 
> * **Publicly-available employee information:** Websites with a "meet the team!" section can be used by attackers to find targets for social engineering.
> * **Job descriptions:** These can reveal a company's internal systems and technologies, which attackers can use to plan their attacks.
> * **Social media metadata:** Geotagged photos on social media can reveal a user's location and the type of device they used.
> * **User profiles:** Public social media information (date of birth, location, interests) can be used to build a profile of an individual.
> * **Exposing cyber criminals:** OSINT can be used to identify cyber criminals and pass their details to law enforcement.
> 
> OSINT is a powerful tool that helps attackers understand their targets without direct engagement and allows defenders to reduce their public > information footprint and improve security.

> [!NOTE]
> ### Why OSINT is Useful
> 
> OSINT is a valuable tool with applications across multiple fields.
> 
> | Group | How They Use OSINT |
> | :--- | :--- |
> | **Defenders** | Use it to perform public exposure assessments, reducing the attack surface by identifying and mitigating publicly available information about employees and the company. |
> | **Law Enforcement** | Utilizes it for profiling and tracking persons of interest. It is also used to uncover the real identities of cybercriminals and find missing persons. |
> | **Businesses** | Monitors market activity and competitors. It helps them improve business operations and customer engagement, and it also serves as a security measure to watch for leaked data and planned attacks. |
> | **Attackers** | Use it for passive information gathering to plan attacks. By collecting information on a target's systems and employees, they can prepare more effective social-engineering and spear-phishing campaigns. |

> [!TIP]
> ### Associated Roles
> 
> | Role | How They Use OSINT |
> | :--- | :--- |
> | **Tactical Threat Analyst** | Gathers information on adversaries, collects IOCs from public sources, and conducts internal threat exposure > checks. |
> | **Strategic Threat Analyst** | Identifies and mitigates publicly available information about the organization, such as details on internal systems and employee data. |
> | **Security Analyst** | Checks the reputation of IOCs (like IP addresses and file hashes) using OSINT sources such as VirusTotal, and investigates malicious social media accounts. |
> | **Vulnerability Analyst** | Stays up-to-date with publicly announced vulnerabilities using sources like the National Vulnerability Database (NVD) and social media. |
> | **Penetration Tester/Red Teamer** | Gathers intelligence on target systems and employees to craft more effective and discreet attacks, leading to a faster and more successful penetration test. |



---
## Intelligence

### The Intelligence Cycle: A Step-by-Step Guide

The intelligence cycle is a 5-step process used to convert raw data into actionable intelligence.

| Step | Purpose | Notes |
| :--- | :--- | :--- |
| **1. Planning and Direction** | Define the purpose and scope of your investigation. | This is the crucial first step where you determine what problem you are solving and what information you need. |
| **2. Collection** | Gather raw data and information. | Use various techniques to obtain data that will help with your intelligence operation. |
| **3. Processing** | Organize and filter the collected data. | This involves decoding, decrypting, and validating information to identify only what is useful for your research. |
| **4. Analysis** | Convert processed information into a meaningful intelligence product. | Compile your filtered information to find solutions and create a coherent report or presentation. |
| **5. Dissemination** | Deliver the final intelligence product to clients. | This step helps stakeholders make informed decisions based on your findings. |

---
## Securing Yourself Online
> [!TIP]
> ### Securing Yourself Online: Online Tracking
> 
> | Type of Tracking | Description |
> | :--- | :--- |
> | **Fingerprinting** | The general term for the "traces" you leave behind while browsing, which are used to follow you across websites and build a profile of your interests. |
> | **IP Addresses** | Your public IP address is a fundamental piece of information that is transmitted to every website you visit, revealing your location and identity. |
> | **Cookies** | Small files stored on your computer. **Tracking cookies** are a type of third-party cookie used to monitor your online activity and provide data for targeted advertising and user profiling. |
> | **Browser Fingerprinting** | The most dangerous form of tracking, where a unique identifier is created using data from your browser and computer settings, such as browser version, operating system, and screen resolution. This makes it very difficult to browse privately. |
> 
> ### Securing Yourself Online: Anonymization
> 
> | Method | Description |
> | :--- | :--- |
> | **Add Extra Layers** | Use a Virtual Machine (VM) or a Live USB to perform research. By reverting the system to a clean state after use, you can erase all traces of your activity. |
> | **Hide Your Public IP** | Use a VPN or the Tor browser to change your public IP address. This helps you to remain private and makes it harder for websites to identify and track you. |
> | **Browser Extensions** | Install extensions like Privacy Badger, No Script, and Ublock Origin to block trackers, prevent unwanted scripts from running, and automatically delete cookies. |
> | **Sock Puppetry** | Create alter-ego accounts to conduct research. This keeps your real identity separate from your OSINT activities and helps you avoid direct connections to your social networks. |





---
## Tools and Services

### $$\color{red}{\text{1. The Harvester}}$$   

The Harvester is a command-line tool for **Open-Source Intelligence (OSINT)** that gathers information on a target domain from publicly available sources.

| Command Flag | Purpose | Example |
| :--- | :--- | :--- |
| `-d` | Specifies the **d**omain to investigate. | `-d google.com` |
| `-b` | Selects the **b**ackend data source. | `-b linkedin` |
| `-l` | Limits the number of results to **l**ist. | `-l 100` |

**Example Usage:**
* **To find IPs and hostnames from Google:** `theharvester -d google.com -l 100 -b google`
* **To find employee names from LinkedIn:** `theharvester -d google.com -l 100 -b linkedin`


### $$\color{orange}{\text{2. Maltego}}$$   

### Maltego

Maltego is a powerful OSINT tool that graphically represents real-time data and connections between different entities.

#### **1. Launch and Set Up**
* **Launch Maltego:** Type `maltego` in the terminal.
* **Select Version:** Choose the free **Community Edition**.
* **Create an Account:** You will need to create an account and get an API key to use the tool.

#### **2. Install Transforms**
* Go to the **Transform Hub** to install tools that gather data from different sources.
* **Example Transforms:** "CaseFile Entities," "HaveIBeenPwned?", "Social Links CE," and "Shodan."

#### **3. Create a New Graph**
* Open a blank graph.
* From the "Entity Palette," drag a target entity (e.g., "Domain") onto the graph.

#### **4. Run a Scan**
* Right-click the entity and run "All transforms."
* **Result:** Maltego will generate a visual graph displaying all the discovered information and connections.


### $$\color{yellow}{\text{3. Tweetdeck}}$$   

### TweetDeck Summary

| Feature | Description |
| :--- | :--- |
| **Purpose** | A tool for security professionals to monitor Twitter in real-time, tracking vulnerabilities, attacks, and threat actors. |
| **Columns** | Allows users to create custom columns based on specific search queries. |
| **Search Queries** | Users can build complex queries using keywords, hashtags (`#`), and logical operators (`AND`/`OR`) to filter a massive volume of tweets. |
| **Advanced Search** | Twitter's Advanced Search tool can be used to build and refine complex search strings before pasting them into TweetDeck. |



### $$\color{green}{\text{4. Google Docks}}$$   

### Google Dorks

| Operator | Purpose | Example |
| :--- | :--- | :--- |
| **`filetype:`** | Searches for a specific file type. | `cyber security filetype:pdf` |
| **`site:`** | Restricts the search to a specific domain. Can be used with `-` to exclude sites for subdomain enumeration. | `site:facebook.com -site:www.facebook.com` |
| **`inurl:`** | Finds a keyword within the URL of a webpage. | `inurl:admin` |


### $$\color{cyan}{\text{5. Defending Against Google Dorks}}$$   

### Defending Against Google Dorks

| Method | Description |
| :--- | :--- |
| **Geofencing** | Blocks access to web content based on a user's IP address and geographic location. |
| **IP Whitelisting** | A more secure method that only allows specified IP addresses to access a resource, blocking all others. |
| **Crawler Restrictions** | Prevents search engine crawlers from indexing parts of your website using a `robots.txt` file. |
| **Requesting Content Removal** | You can request that Google temporarily or permanently remove sensitive content from its search index if you can prove ownership of the site. |


### $$\color{blue}{\text{6. OSINT Framework}}$$   

### OSINT Framework

The [OSINT Framework](https://www.osintframework.com/) is a web-based hub that categorizes hundreds of OSINT tools and resources.

| Use Case | How to Access | Description |
| :--- | :--- | :--- |
| **Persona Creation** | Navigate to `OpSec` > `Persona Creation`. | Find tools to create authentic-looking fake personas for social engineering. |
| **Email Breach Checks** | Navigate to `Email Address` > `Data Breach`. | Find services to check if an email address has been compromised in a data breach. |
| **Skill Development** | Navigate to the `Training` branch. | Provides resources and links to further your OSINT knowledge. |


### $$\color{purple}{\text{7. TinyEye}}$$   

[TinyEye](https://tineye.com/)

| Tool | Purpose | How to Use | Use Case |
| :--- | :--- | :--- | :--- |
| **TinEye** | A reverse image search engine that identifies where an image appears online. It can also be used to find altered or resized versions of an image. | Go to the website, then upload an image or paste a URL into the search bar. | **Identifying Social-Media Fakes**: Upload a profile photo to see if it's a stock image or widely used online, which suggests a fake account. |


### $$\color{fuchsia}{\text{8. Google Image Search}}$$   

| Tool | Purpose | How to Use | Key Features |
| :--- | :--- | :--- | :--- |
| **Google Image Search** | Performs reverse image searches to find where an image exists online. | Upload an image file or paste an image URL into the search bar. | Finds exact matches on indexed pages, provides a generated description of the image, and returns a massive number of results. |


---
## Course Capstone
> [!IMPORTANT]
> ### OSINT Challenge Brief
> 
> #### **1. Challenge Objectives**
> * Identify social media accounts and websites.
> * Build a profile of the person-of-interest.
> * Find evidence of malicious activity.
> 
> #### **2. Starting Information**
> * **Twitter Handle:** `@sp1ritfyre`
> * **Report Template:** `SBT-OSINT-Challenge-Report.txt`
> 
> #### **3. Key Techniques and Tips**
> * **Follow the Report Template:** Use the provided `.txt` file to focus your information gathering.
> * **Do Not Perform Unauthorized Access:** Do not attempt to brute force passwords. Instead, look for publicly available credentials.
> * **Check DNS TXT Records:** These records can sometimes contain hidden text strings or comments.
> * **Decode Encoded Data:** Look for strings in **Base64** or **Hexadecimal** and use a decoder to read them.
> * **Use Tools:** Apply OSINT tools like The Harvester, Maltego, the OSINT Framework, and Google Dorks.
> * **Collaborate:** Discuss the challenge with other students in the specified Discord channel, but do not share spoilers.
---
































---

# Introduction to Vulnerability Management
































---
# Introduction to Threat Hunting
































---
# Introduction to Network Analysis
































---
# Introduction to Dark Web Operations






























---
