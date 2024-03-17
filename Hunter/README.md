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

Flag 4: `S-1-5-21-2489440558-2754304563-710705792 (last 3 or 4 digits is RID which is a unique user ID)`

## 5. What is the Operating System(OS) version?

Path: SOFTWARE\Microsoft\Windows NT\CurrentVersion

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/953d6577-7821-4e19-8dd5-ff1a6776a57d)

Flag 5: `Windows 8.1`

## 6. What was the computer timezone?

Path: SYSTEM\ControlSet001\Control\TimeZoneInformation

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/2a2bd44f-dd2a-4f1b-baed-00bd902965d6)

Flag 6: `UTC-07:00 (Daylight saving time)`

## 7. How many times did this user log on to the computer?

Use Regripper and load SAM hive

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/d9fb2b31-95df-44e9-8be5-e9b5ab5da77d)

Flag 7: `3`

## 8. When was the last login time for the discovered account? Format: one-space between date and time

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/37329ad3-50d8-42c6-962b-fe679bd5f570)

Flag 8: `2016-06-21 01:42:40`

## 9. There was a “Network Scanner” running on this computer, what was it? And when was the last time the suspect used it? Format: program.exe, YYYY-MM-DD HH:MM:SS UTC

Use FTK Imager

Path: User/Windows/Prefetch 

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/3d2b9935-a41a-47cc-b532-97fb9f34cea5)

Parse it with PECmd.exe 

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/3b3b32a0-07d9-4924-8edb-8d0901ea80a1)

Open it with Timeline Explorer

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/dbb1234c-82cf-46d0-8fe9-0390c46973a8)

Flag 9: `zenmap.exe,2016-06-21 12:08:13 UTC`

## 10. When did the port scan end? (Example: Sat Jan 23 hh:mm:ss 2016)

Path: Users/Hunter/.zenmap/recent_scans.txt 

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/b7a34af8-3007-4ced-80f3-5ba5196078e2)

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/f6f1234e-bd2b-4065-8337-f737eb7cc3e0)

Flag 10: `Tue Jun 21 05:12:09 2016`

## 11. How many ports were scanned?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/1535eece-7149-4133-8774-47d500d802fa)

Flag 11: `1000`

## 12.  What ports were found "open"?(comma-separated, ascending)

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/c72e0284-b3b8-4054-9025-cbd9370a352b)

Flag 12: `22, 80, 9929, 31337`

































