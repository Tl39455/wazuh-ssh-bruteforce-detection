# Wazuh SSH Brute-Force Detection

## Objective
Simulate an SSH brute-force attack using Kali Linux and detect authentication failures using Wazuh SIEM.

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

First a ping to the IP address being attacked to confirm there is a connection:
![image alt](https://github.com/Tl39455/wazuh-ssh-bruteforce-detection/blob/c3a802b4674cad6bf3c6d014fce42fdacd3a1352/Ping%20Agent%20IP.png)

Command used:
hydra -l root -P /usr/share/wordlists/rockyou.txt ssh://192.168.56.102

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
