# Windows Loglarının Silinmesi (Defense Evasion - T1070.001)

Saldırgan, SOC ekibinin faaliyetlerini analiz etmesini engellemek için Windows Güvenlik ve Sistem olay günlüklerini silerek izlerini kaybettirmeye çalışır.

## Uygulama (Windows Komut Satırı)
Yerleşik `wevtutil` aracını kullanarak, komut satırından logları sildim.

# Security loglarını sil
```cmd
wevtutil cl Security
```
# System loglarını sil
```cmd
wevtutil cl System
```