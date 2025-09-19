# Windows Forensics 1

1. **Structure of the Registry:**
* HKEY_CURRENT_USER: Stores settings and configuration data specific to the user currently logged in.
* HKEY_USERS: Contains user-specific settings for all users on the computer, including the default profile.
* HKEY_LOCAL_MACHINE: Holds global settings and configuration for the entire computer and all users.
* HKEY_CLASSES_ROOT: Manages information about file extensions and the applications associated with them.
* HKEY_CURRENT_CONFIG: Links to the HKEY_LOCAL_MACHINE branch that contains the current hardware profile configuration.

[Microsofts Documentation](https://learn.microsoft.com/en-us/troubleshoot/windows-server/performance/windows-registry-advanced-users)

2. **Registry Hives Explained:**
Registry hives are essential files that store the Windows operating system's configuration data. Each one is loaded into the Windows Registry at startup, appearing as a tree-like structure you can see in Regedit.

* DEFAULT
The DEFAULT hive, located at HKEY_USERS\DEFAULT, is the template for new user profiles. When a new user logs into a computer for the first time, Windows uses this hive to create their personal settings.

* SAM & SECURITY
The SAM (Security Account Manager) hive at HKEY_LOCAL_MACHINE\SAM stores local user accounts and hashed passwords. The SECURITY hive at HKEY_LOCAL_MACHINE\Security stores system-wide security policies. Together, they manage security for the local machine.

* SOFTWARE & SYSTEM
The SOFTWARE hive at HKEY_LOCAL_MACHINE\Software holds configuration settings for applications and Windows components. The SYSTEM hive at HKEY_LOCAL_MACHINE\System contains critical boot-related information for device drivers and services, making it essential for the operating system to start and run.

Located in C:\Users\<username>\ is where is where the user profile directory is: 
* NTUSER.DAT (mounted on HKEY_CURRENT_USER when a user logs in)
* USRCLASS.DAT (mounted on HKEY_CURRENT_USER\Software\CLASSES)
  
Windows creates this hive to save information on programs that were recently run on the system. This hive is located in C:\Windows\AppCompat\Programs\Amcache.hve 

3. Think of transaction logs and backups as two different ways Windows keeps the registry reliable.
* Transaction logs are like a running diary of changes to the registry. When a change is made, it's first written to a .LOG file before being saved to the main registry hive. This means the log might contain the very latest changes that haven't been fully committed yet. For forensic analysis, these logs can reveal recent activity that's not present in the main registry files.
* Registry backups are snapshots of the registry hives. Windows automatically copies these hives to the RegBack directory every 10 days. These backups are useful if a registry key has been deleted or modified, as they can provide a record of its state at a previous point in time.


KAPE:
<img width="1920" height="1020" alt="image" src="https://github.com/user-attachments/assets/35fe0d0b-a3d6-4527-851a-44b10cc3e41b" />


Autopsy:
<img width="1710" height="922" alt="image" src="https://github.com/user-attachments/assets/c4f345a7-930f-4308-9078-431c96344f1a" />


FTK Imager:
<img width="1166" height="737" alt="image" src="https://github.com/user-attachments/assets/3da97c6f-289a-4392-a624-4833a706a758" />

Registry Viewer:
<img width="1424" height="736" alt="image" src="https://github.com/user-attachments/assets/532434c8-52d2-42de-aff4-b6d8e1eec558" />

Zimmerman's Registry Explorer:
<img width="1202" height="714" alt="image" src="https://github.com/user-attachments/assets/62e74713-801e-42d9-9fb8-cf45a0cc8ba9" />

RegRipper:
<img width="611" height="525" alt="image" src="https://github.com/user-attachments/assets/c251ae48-d9cf-41ee-ba60-9736d038a288" />



