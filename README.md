# Wazuh SSH Brute-Force Detection

## Objective
Simulate an SSH brute-force attack using Kali Linux in my home lab environment and detect authentication failures using Wazuh SIEM.

## Lab Environment
- Attacker: Kali Linux
- Target: Ubuntu Agent
- SIEM: Wazuh Manager
- Virtualization: VirtualBox

## Tools Used
- Kali Linux
- Wazuh
- Hydra
- Ubuntu

## Attack Simulation
The attack was executed from Kali Linux using Hydra against the SSH service on the Ubuntu agent.

First, a ping to the IP address being attacked to confirm there is a connection using "ping 192.168.56.102".

If rockyou.txt.gz is still compressed, extract it with:

sudo gzip -d /usr/share/wordlists/rockyou.txt.gz

If you get no such file or directory, verify whether the wordlist is already extracted:

ls /usr/share/wordlists

If rockyou.txt is present, proceed with Hydra using that file.

The brute force attack was intitated using the command:

hydra -l root -P /usr/share/wordlists/rockyou.txt ssh://192.168.56.102:

![image alt](https://github.com/Tl39455/wazuh-ssh-bruteforce-detection/blob/c36b22789bb0eabfb61b02816e408b054edadbe4/Hydra%20Attack.png)
![image alt](https://github.com/Tl39455/wazuh-ssh-bruteforce-detection/blob/c3a802b4674cad6bf3c6d014fce42fdacd3a1352/Ping%20Agent%20IP.png)

The agent VM was logged in real-time using this command: 

![image alt](https://github.com/Tl39455/wazuh-ssh-bruteforce-detection/blob/43f5fe4a5fe13f78403d154d6c8d33db4513fde5/Agent%20real-time%20logs%20of%20attack.png)

The attack was monitored from the Wazuh VM dashboard in real-time:

![image alt](https://github.com/Tl39455/wazuh-ssh-bruteforce-detection/blob/5e1c5acdab92b8f0c144ce35bda8966ec4e9304e/Security%20events%20of%20attack.png)

## Detection Results
Wazuh detected:
- Multiple failed SSH login attempts
- sshd: authentication failed
- Rule ID: 5760
- MITRE ATT&CK: T1110.001 (Brute Force)

## Skills Demonstrated
- Threat simulation
- SIEM monitoring
- Log analysis
- Attack detection
- Security event correlation

## Outcome
Successfully validated real-time detection of brute-force attacks using Wazuh SIEM.
