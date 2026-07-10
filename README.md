# 🛡️ SOC Laboratuvarım: Uçtan Uca Tehdit Tespiti

SOC Laboratuvarıma hoş geldiniz. Bu proje, bir SIEM ortamı, siber saldırıları simüle etme ve bunları yakalamak için mühendislik tespit kuralları oluşturma konusundaki pratik deneyimimi gösteriyor.
##  Lab Mimarisi

Laboratuvar, saldırı ortamını günlük kaydı ve tespit ortamından izole eden sanal makineler kullanılarak oluşturulmuştur.

```text
+------------------+          +-------------------+          +-------------------+
| Saldırı Makinesi |          |   Kurban Makine   |          |    SIEM Sunucu    |
|                  |          |                   |          |                   |
|  [ Kali Linux ]  | =======> |   [ Windows ]     | =======> |    [ Ubuntu ]     |
|                  | Network  |                   | Forward  |    (Splunk)       |
|  - Nmap, Hydra   | Attack   |  - Sysmon, ESET   |  Logs    |                   |
|  - Metasploit    |          |  - Winlogbeat     |          |  - Dashboards     |
+------------------+          +-------------------+          +-------------------+
