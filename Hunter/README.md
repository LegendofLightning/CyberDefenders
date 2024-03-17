# Hunter

Tools used for this challenge:
- Registry Explorer
- RegRipper
- FTK Imager
- PECmd
- SQLite
- PST viewer
- Shellbags Explorer
- Jumplist Explorer

## 1. What is the computer name of the suspect machine?

Load SYSTEM hive in Registry Explorer

Path: SYSTEM\ControlSet001\Control\ComputerName\ComputerName

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/33b84b64-823b-4d5e-af3c-b42e11771c4f)

Flag 1: `4ORENSICS`

## 2. What is the computer IP?

Path:  SYSTEM\ControlSet001\Services\Tcpip\Parameters\Interfaces

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/9c80c354-194d-42e0-bbf7-e79051c480a6)

Flag 2: `10.0.2.15`

## 3. What was the DHCP LeaseObtainedTime?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/db6fb772-3a1b-486a-af51-05ba24852a9e)

Convert timestamp to human-readable date

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/84ed2b0b-7b27-4250-817a-63b307ec83f0)

Flag 3: `21/06/2016 02:24:12 UTC`

## 4. What is the computer SID?

Load SOFTWARE hive in Registry Explorer

Path: SOFTWARE\Microsoft\Windows NT\CurrentVersion\ProfileList

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/6844fc51-2224-49bd-a3fa-b86d6018fe92)

Flag 4: `S-1-5-21-2489440558-2754304563-710705792` (last 3 or 4 digits is RID which is a unique user ID)

## 5. What is the Operating System(OS) version?

Path: SOFTWARE\Microsoft\Windows NT\CurrentVersion

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/953d6577-7821-4e19-8dd5-ff1a6776a57d)

Flag 5: `Windows 8.1`

## 6. What was the computer timezone?

Path: SYSTEM\ControlSet001\Control\TimeZoneInformation

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/2a2bd44f-dd2a-4f1b-baed-00bd902965d6)

Flag 6: `UTC-07:00` (Daylight saving time)

## 7. How many times did this user log on to the computer?

Use Regripper and load SAM hive

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/d9fb2b31-95df-44e9-8be5-e9b5ab5da77d)

Flag 7: `3`

## 8. When was the last login time for the discovered account? Format: one-space between date and time

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/37329ad3-50d8-42c6-962b-fe679bd5f570)

Flag 8: `2016-06-21 01:42:40`

## 9. There was a “Network Scanner” running on this computer, what was it? And when was the last time the suspect used it? Format: program.exe, YYYY-MM-DD HH:MM:SS UTC

Use FTK Imager

Path: C:/User/Windows/Prefetch 

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/3d2b9935-a41a-47cc-b532-97fb9f34cea5)

Parse it with PECmd.exe 

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/3b3b32a0-07d9-4924-8edb-8d0901ea80a1)

Open it with Timeline Explorer

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/dbb1234c-82cf-46d0-8fe9-0390c46973a8)

Flag 9: `zenmap.exe,2016-06-21 12:08:13 UTC`

## 10. When did the port scan end? (Example: Sat Jan 23 hh:mm:ss 2016)

Path: C:/Users/Hunter/.zenmap/recent_scans.txt 

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/b7a34af8-3007-4ced-80f3-5ba5196078e2)
![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/f6f1234e-bd2b-4065-8337-f737eb7cc3e0)

Flag 10: `Tue Jun 21 05:12:09 2016`

## 11. How many ports were scanned?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/1535eece-7149-4133-8774-47d500d802fa)

Flag 11: `1000`

## 12.  What ports were found "open"?(comma-separated, ascending)

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/c72e0284-b3b8-4054-9025-cbd9370a352b)

Flag 12: `22, 80, 9929, 31337`

## 13. What was the version of the network scanner running on this computer?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/af1d2341-97bf-4d94-aa0b-a08628fb0c23)

Flag 13: `7.12`

## 14. The employee engaged in a Skype conversation with someone. What is the skype username of the other party?

Path: C:/Users/Hunter/AppData/Roaming/Skype/hunterehpt/main.db

Use SQLite

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/32eaaeb1-9b71-4a74-bb90-20a7131a0049)
![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/c19d0ecc-3bfe-4139-98ab-264e660a59d5)

Flag 14: `linux-rul3z`

## 15. What is the name of the application both parties agreed to use to exfiltrate data and provide remote access for the external attacker in their Skype conversation?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/8e45f212-4f63-4007-bd57-7baef3e00181)

Flag 15: `teamviewer`

## 16. What is the Gmail email address of the suspect employee?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/0b1d7a7a-b255-4df5-ae87-57f407b2efc8)

Flag 16: `sgs@gmail.com`

## 17. It looks like the suspect user deleted an important diagram after his conversation with the external attacker. What is the file name of the deleted diagram?

Path: Users/Hunter/Documents/Outlook Files/backup.pst

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/58df0614-6d61-4050-866c-673d76cb0d1c)
![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/d8393c83-e268-4259-9858-9efd30db393e)

Flag 17: `home-network-design-networking-for-asingle-family-home-case-house-arkko-1433-x-792.jpg`

## 18. The user Documents' directory contained a PDF file discussing data exfiltration techniques. What is the name of the file?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/70f5a8f3-87ce-4e24-9f5a-6b05cc65d840)

Flag 18: `Ryan_VanAntwerp_thesis.pdf`

## 19. What was the name of the Disk Encryption application Installed on the victim system? (two words space separated)

Path: Program Files (x86)/Jetico/BCWipe/UnInstall.log

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/8b11aba0-2d5d-4b19-88e5-dd43dc2ce78b)

Flag 19: `Crypto Swap`

## 20. What are the serial numbers of the two identified USB storage?

Path: SYSTEM\ControlSet001\Enum\USB

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/ca0faec6-0ff6-4066-9dc5-43bb4be3cca9)

Flag 20: `07B20C03C80830A9,AAI6UXDKZDV8E9OU`

## 21. One of the installed applications is a file shredder. What is the name of the application? (two words space separated)

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/35b7574e-7321-4a0a-a3a5-9e227e0f3728)

Flag 21: `Jetico BCWipe`

## 22. How many prefetch files were discovered on the system?

Extract all files from prefetch and move all .pf files to a different folder except the ones with 0 bytes

Flag 22: `174`

## 23. How many times was the file shredder application executed?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/a2b00597-432e-4ce1-ba0e-caad6ac64705)

Flag 23: `5`

## 24. Using prefetch, determine when was the last time ZENMAP.EXE-56B17C4C.pf was executed?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/30a71511-2d66-4177-b7dd-0f83fab57918)

Flag 24: `06/21/2016 12:08:13 PM`

## 25. A JAR file for an offensive traffic manipulation tool was executed. What is the absolute path of the file?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/a9080871-837d-40f9-a54c-3ca8bc06e967)

Flag 25: `C:\USERS\HUNTER\DOWNLOADS\BURPSUITE_FREE_V1.7.03.JAR`

## 26. The suspect employee tried to exfiltrate data by sending it as an email attachment. What is the name of the suspected attachment?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/755968c2-b0d1-415f-99e4-bfe2290e4e15)

Flag 26: `Pictures.7z`

## 27. Shellbags shows that the employee created a folder to include all the data he will exfiltrate. What is the full path of that folder?

Path: C:/Users/Hunter/AppData/Local/Microsoft/Windows/UsrClass.dat

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/1c89cbd7-6ec0-4aa2-92cc-3f8911f4e701)

Flag 27: `C:\Users\Hunter\Pictures\Exfil`

## 28. The user deleted two JPG files from the system and moved them to $Recycle-Bin. What is the file name that has the resolution of 1920x1200?

Path: Users/Hunter/Pictures/Private
![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/33bd8b5e-3613-465c-8c01-ef57f3f0262c)
![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/443d7015-e9b2-47fe-97d6-a152eaaead88)

Flag 28: `ws_Small_cute_kitty_1920x1200.jpg`

## 29. Provide the name of the directory where information about jump lists items (created automatically by the system) is stored?

Flag 29: `AutomaticDestinations`

## 30. Using JUMP LIST analysis, provide the full path of the application with the AppID of "aa28770954eaeaaa" used to bypass network security monitoring controls.

Path: C:/Users/Hunter/AppData/Roaming/Microsoft/Windows/Recent/CustomDestinations

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/bec65608-a677-462e-b4e2-0292e5232629)

Use JumpList Explorer

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/c41768c5-8e8b-454c-9583-8f29d409c233)

Flag 30: `C:\Users\Hunter\Desktop\Tor Browser\Browser\firefox.exe`


























































