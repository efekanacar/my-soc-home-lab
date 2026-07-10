# Hızlı Sistem ve Ağ Keşfi (Discovery - T1087)

Sisteme ilk erişim sağlandığında, saldırgan ele geçirilen makine, yetkileri ve ağ topolojisi hakkında bilgi toplamak için hızla birden fazla komut çalıştırır.

## Uygulama (Windows Komut Satırı)
Birbiri ardına hızlı bir şekilde bir dizi standart keşif komutu çalıştırdım.

# Mevcut kullanıcı yetkilerini keşfet
```cmd
whoami /priv
```
# Sistem mimarisi ve OS detaylarını getir
```cmd
systeminfo
```
# Ağ yapılandırmalarını keşfet
```cmd
ipconfig /all
```
# Aktif ağ bağlantılarını görüntüle
```cmd
netstat -ano
```