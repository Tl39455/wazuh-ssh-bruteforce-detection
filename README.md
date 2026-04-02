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
