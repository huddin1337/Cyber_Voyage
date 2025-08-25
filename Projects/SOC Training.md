This is going to be where I start off my journey trying to learn skills necessary to be a successful sock analyst. 

In this section I'll be using my windows VM as a sandbox to gain some experiences through trial and error.  

## Disabling Windows Defender
To get started I will be removing the Windows Defender from this VM,  and to test this i'll be using a test file “Eicar” before and after Disabling. To get started I'm going to head to the windows security settings > virus and threat protection > virus and threat protection settings (manage settings) > then I uncheck tamper protection turning it off. 
 <img width="784" height="245" alt="image" src="https://github.com/user-attachments/assets/fe3188eb-4695-43fa-bd0e-79d10ca83112" />

Next I will be heading to PowerShell as an administrator where I will run a couple of commands to turn off Windows Defender. 
1.	 Set-MpPreference -DisableRealtimeMonitoring $true
2.	 Set-MpPreference -DisableScanningNetworkFiles $true
3.	 Set-MpPreference -DisableBlockAtFirstSeen $true
4.	reg add "HKLM\SOFTWARE\Policies\Microsoft\Windows Defender" /v DisableAntiSpyware /t REG_DWORD /d 1 /f
 
<img width="694" height="267" alt="image" src="https://github.com/user-attachments/assets/a8b4fbe9-3aea-4b32-b039-619610d7b1f9" />


