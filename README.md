#  Node-RED Kripto Sinyal Botu

Bu proje, Node-RED üzerinde çalışan, Binance borsasından canlı veri çekerek belirlenen stratejiye göre görsel sinyaller üreten basit bir **Kripto Sinyal Takip Botu**dur.

##  Özellikler

* **Canlı Veri:** Binance API üzerinden her 10 saniyede bir gerçek zamanlı BTC/USDT fiyatı çekilir.
* **Otomatik Karar Mekanizması:** Belirlenen eşik değerine (Threshold) göre otomatik "AL" veya "SAT" sinyali üretir.
* **Görsel Dashboard:** Fiyat değişimlerini canlı grafik (Chart) üzerinden takip etme imkanı sunar.
* **Debug Modu:** Ham verileri Node-RED yan panelinde izleme seçeneği.

## Kurulum

1. Bilgisayarınızda veya sunucunuzda **Node-RED** kurulu olduğundan emin olun.
2. Dashboard arayüzü için `node-red-dashboard` eklentisini yükleyin:
```bash
cd ~/.node-red
npm install node-red-dashboard

```


3. Node-RED'i başlatın.
4. Sağ üstteki menüden **Import** seçeneğine tıklayın.
5. GitHub'daki JSON kodunu kutucuğa yapıştırın ve **Import** butonuna basın.
6. Sağ üstteki **Deploy** butonuna basarak akışı yayına alın.

## Akış Şeması

Bot aşağıdaki düğüm (node) yapısını kullanır:

1. **Inject (Her 10 Saniye):** Döngüyü tetikler.
2. **HTTP Request:** Binance API'sine GET isteği atar.
3. **Function (Karar Mekanizması):** Fiyatı kontrol eder ve sinyal üretir.
4. **UI Text & Chart:** Kararı ve fiyat grafiğini Dashboard'a yansıtır.

## 📉 Sinyal Mantığı

Mevcut akışta kullanılan örnek mantık şöyledir:

* Eğer Fiyat **< 95.000 USD** ise ➡️ **AL 🟢**
* Eğer Fiyat **> 95.000 USD** ise ➡️ **SAT 🔴**

> **Not:** `Sinyal Karar Mekanizması` düğümüne çift tıklayarak kendi stratejinizi ve eşik değerlerinizi kolayca düzenleyebilirsiniz.

## Dashboard Erişimi

Kurulum tamamlandıktan sonra arayüze şu adresten ulaşabilirsiniz:
`http://localhost:1880/ui`

### Sorumluluk Reddi

Bu proje sadece eğitim amaçlıdır. Herhangi bir yatırım tavsiyesi içermez. Kripto paralar yüksek risk içerir; gerçek para ile işlem yapmadan önce stratejinizi iyice test edin.
