# 🛡️ My SOC Home Lab: End-to-End Threat Detection

Welcome to my Security Operations Center (SOC) Home Lab repository. This project demonstrates my practical experience in building a SIEM environment, simulating cyber attacks, and engineering detection rules to catch them.

## 🏗️ Lab Architecture

The lab is built using virtual machines, isolating the attack environment from the logging and detection environment.

```text
+------------------+          +-------------------+          +-------------------+
|  Attacker Node   |          |  Victim Endpoint  |          |    SIEM Server    |
|                  |          |                   |          |                   |
|  [ Kali Linux ]  | =======> |   [ Windows ]     | =======> |    [ Ubuntu ]     |
|                  | Network  |                   | Forward  |    (Splunk)       |
|  - Nmap, Hydra   | Attack   |  - Sysmon, ESET   |  Logs    |                   |
|  - Metasploit    |          |  - Winlogbeat     |          |  - Dashboards     |
+------------------+          +-------------------+          +-------------------+
