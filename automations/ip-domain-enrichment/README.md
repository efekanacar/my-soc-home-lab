# My SOC Lab: SIEM & SOAR Automation Hub

Bu repo, **Splunk (SIEM)** ve **n8n (SOAR)** teknolojilerini kullanarak siber güvenlik operasyon merkezlerinde (SOC) gerçekleşen "tespit, zenginleştirme ve engelleme" süreçlerini simüle ettiğim laboratuvar ortamımdır.



## Proje Amacı
Bu laboratuvarın temel hedefi, manuel olarak yapılan "log inceleme" ve "tehdit analizi" işlerini otomatize ederek, bir SOC analistinin operasyonel yükünü azaltacak otomasyon (playbook) senaryoları geliştirmektir.

## 🛠 Kullanılan Araçlar
* **SIEM:** Splunk Enterprise (Log toplama, korelasyon ve alarm)
* **SOAR:** n8n (Otomasyon iş akışları)
* **Firewall:** Kali Linux & UFW (Log kaynağı ve engelleme noktası)
* **Threat Intel:** VirusTotal API (İtibar kontrolü)
* **Notification:** Telegram Bot API (Analist bilgilendirme)

---

## Senaryolar

### 1. SSH Brute Force Otomasyonu
Hedef sunucuya yapılan başarısız SSH giriş denemelerinin Splunk tarafından tespit edilip, n8n üzerinden saldırgan IP'sinin UFW (Firewall) ile otomatik engellenmesi ve analiste bildirim gönderilmesi.


### 2. Otomatik Threat Intelligence (Enrichment)
Firewall loglarına düşen şüpheli dış bağlantıların, n8n üzerinden VirusTotal API'sine gönderilerek itibar puanlarının sorgulanması ve zararlı bulunan IP'lerin analiste "zenginleştirilmiş veri" olarak raporlanması.


---