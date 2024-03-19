# PacketDetective

Wireshark is used for this challenge

## 1. What is the amount of bandwidth being used by the SMB protocol in bytes?

Statistics > Protocol Hierarchy

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/32d5aff1-ec2d-4745-ad0e-aac4bb8d0459)

Flag 1: `4406`

## 2. Which username was utilized for authentication via SMB?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/fc84c243-127e-448f-969e-ea62cba59123)

Flag 2: `Administrator`

## 3. What is the name of the file that was opened?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/6db03088-ecf1-4af9-891b-a4907ab6fa5c)

Flag 3: `eventlog`

## 4. What is the timestamp of the attempt to clear the event log? (24H-UTC)

Convert to UTC 24hr format

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/be020a45-59fc-4ca2-9c16-e5d053b512e6)

Flag 4: `2020-09-23 16:50:16`

## 5. An attacker used a named pipe for communication to blend in and evade detection. What is the name of the service that utilized this pipe for communication?

Filter: ip.src == 172.16.66.1 and dcerpc 

Follow TCP stream

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/1e4fa968-4e3c-405d-92ee-4ec44443f1ef)

Flag 5: `atsvc`

## 6. What was the duration of communication between 172.16.66.1 and 172.16.66.36?

Statistics > Conversations

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/b800f5cb-cca0-4646-95b9-4c1890fadc1e)

Flag 6: `11.7247`

## 7. Which username is used to set up requests that may be considered suspicious?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/93e4002d-3539-40fa-a550-afcf9cd8ce92)

Flag 7: `backdoor`

## 8. What is the name of the executable file utilized to execute processes remotely?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/629f8fa5-44d9-46f0-af8c-e197fa59e3f4)

Flag 8: `PSEXESVC.exe`














