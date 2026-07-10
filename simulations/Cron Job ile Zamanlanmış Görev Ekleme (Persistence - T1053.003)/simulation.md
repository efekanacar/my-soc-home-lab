# Cron Job ile Zamanlanmış Görev Ekleme (Persistence - T1053.003)

Saldırganlar, hedef sistemde kalıcı olabilmek ve belirledikleri zararlı yazılımların/komutların arka planda düzenli aralıklarla otomatik olarak çalışmasını sağlamak için Linux'un zamanlanmış görev servisi olan Cron'a yeni girdiler eklerler. Bu sayede sistem yeniden başlatılsa dahi bağlantı kopmaz.

## Uygulama
Terminal üzerinden şu komut satırı çalıştırılarak her 5 dakikada bir çalışacak sahte bir görev simüle edilir:

# Mevcut kullanıcının crontab dosyasına her 5 dakikada bir çalışacak şüpheli bir script eklenir.
```cmd
(crontab -l 2>/dev/null; echo "*/5 * * * * /tmp/.hidden_script.sh") | crontab -
```