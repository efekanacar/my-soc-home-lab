# Web Dizini ve Dosya Kaba Kuvvet Taraması (Active Scanning - T1595.003)

Saldırganlar, web sunucusu üzerinde gizli dizinleri, yönetici panellerini veya unutulmuş yedek dosyalarını bulmak için otomatik tarama araçları (örn. Gobuster, Dirb) kullanırlar. Bu işlem sonucunda sunucuya saniyeler içinde binlerce istek gelir ve loglarda çok sayıda 404 (Bulunamadı) hata kodu görülür.

## Uygulama
Terminal üzerinden sırasıyla şu komutlar çalıştırılarak süreç simüle edilir:

# 1. Gobuster aracı ile yaygın dizinleri hedef web sunucusunda tara.
```cmd
gobuster dir -u http://localhost -w /usr/share/wordlists/dirb/common.txt
```
# 2. Alternatif olarak Dirb ile tarama başlat.
```cmd
dirb http://localhost /usr/share/wordlists/dirb/common.txt
```