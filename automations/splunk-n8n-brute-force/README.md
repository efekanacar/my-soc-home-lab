# Splunk & n8n ile Otomatik Brute Force Engelleme 

Bu projede, Windows bir makineden Kali Linux hedef sunucusuna yapılan SSH Brute Force saldırılarının **Splunk (SIEM)** ile tespit edilerek **n8n (SOAR)** üzerinden otomatik olarak engellenmesi (UFW Firewall) ve analiste **Telegram** üzerinden bildirim gönderilmesi senaryolaştırılmıştır.

## Kullanılan Teknolojiler & Bileşenler
* **SIEM:** Splunk Enterprise (Log Toplama ve Korelasyon)
* **SOAR:** n8n (İş Akışı Otomasyonu)
* **Hedef & Firewall:** Kali Linux & UFW (Uncomplicated Firewall)
* **Bildirim:** Telegram Bot API

---

## Senaryo Akışı

1. **Saldırı Simülasyonu:** Saldırgan makineden hedef Kali Linux SSH servisine arka arkaya hatalı giriş denemeleri yapılır.
2. **SIEM Tespiti:** Splunk, `/var/log/auth.log` üzerinden gelen `Failed password` loglarını izler. 1 dakika içinde 5'ten fazla hatalı giriş yapan IP adreslerini filtreler.
3. **SOAR Tetiklenmesi (Webhook):** Splunk Alert mekanizması tetiklenir ve yakalanan zararlı IP adresi POST metoduyla n8n Webhook düğümüne fırlatılır.
4. **Güvenlik Kontrolü (White-list):** n8n üzerinde bir `If` düğümü ile gelen IP'nin güvenilir ağda olup olmadığı doğrulanır (Self-ban önleme).
5. **Otomatik Yanıt :** n8n, SSH düğümü üzerinden hedef sunucuya bağlanarak `sudo ufw deny from <saldırgan_ip>` komutunu çalıştırır ve saldırganı banlar.
6. **Bildirim:** Operasyon başarılı olduğunda analistin Telegram hesabına anlık güvenlik uyarısı iletilir.

---

## Splunk Tespit Sorgusu (SPL)

Aşağıdaki sorgu ile son 24 saat içindeki hatalı denemeler gruplanarak eşik değerini aşanlar tespit edilir:

```spl
index=main "Failed password" 
| rex field=_raw "Failed password for .* from (?<src_ip>\d+\.\d+\.\d+\.\d+)" 
| stats count by src_ip 
| where count >= 5