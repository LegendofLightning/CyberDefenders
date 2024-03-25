# MITRE-T1110.003

I used Event Log Explorer for this challenge.

## 1. Who was the last logged-in user?

The first thing that came to my mind was to open the security log using Event Log Explorer and filter in event ID 4624. Here you can see all the login sessions created. 

![1](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/19895263-3abb-4f95-b324-5644d152a472)

Flag 1: `Administrator`

## 2. What is the logon type of the failed logons?

The failed logon attempts are associated with the event ID 4625. I clicked on one of the events and saw the logon type. 

![2](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/9019cae7-45e7-4eb7-86cc-5bd2417f1e33)

Flag 2: `3`

## 3. What is the protocol the attacker tried to brute force?

Flag 3: `RDP`

## 4. How many users did the attacker succeed in getting their accounts?

From Microsoft-Windows-TerminalServices-RemoteConnectionManager%4Operational.evtx

I went to the remote connection manager operational event log and filtered in event ID 1149 and saw 7 total events. 2 of them were successfully authenticated using Administrator accounts. 

![4](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/e5df6a7b-b20f-42ec-bd75-6227bd4d4696)

Flag 4: `6`

## 5. According to Microsoft. What is the description of the "Sub Status" code for event id 4625?

Go to the security log and filter in event ID 4625

![5 1](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/29525523-b85e-4b21-b5d3-8f769ecb2182)

From Microsoft website
![5](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/f4741a48-5f15-4cff-9279-8b0ecfaaef58)

Flag 5: `User logon with misspelled or bad password`

## 6. How long did the brute force last? MM:SS

To detect brute force attacks, I needed to filter in event ID 4625 and analyze if there were any multiple login attempts within a few seconds. 

![6](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/00e83a0d-f009-490c-b380-a000718cf000)

![6 1](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/95bb200e-4642-449e-8cf1-06b1576dc99e)

The brute force attacks started from 4:29:10 to 4:34:57. Initially, I input 5:47 but the flag did not take it. Then, I tried 5:48. 

Flag 6: `5:48`

## 7.  After How long did the attacker login to the machine again? MM:SS

Since the attacker logon to the machine remotely, I went to the remote desktop service operational log.

![7](https://github.com/LegendofLightning/CyberDefenders/assets/66300601/bfde9eaa-2dd0-4693-8de3-40de918b0ac6)

Again, I put in 11:11 at first but the flag did not take that as an answer. Then I put in 11:12. 

Flag 7: `11:12`

## 8 What is the name of the policy used to lock the account after a certain number of failed login attempts?

I found the answer on the Microsoft website

Flag 8: `lockout Policy`



















