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



















