# LeoNet Pro v1.1.0 — Kullanım Kılavuzu / User Guide

> 🇹🇷 **Türkçe** — aşağıda Türkçe rehber yer alıyor.
> 🇬🇧 **English** — scroll down to the English section.

---

## 📑 İçindekiler / Table of Contents

**Türkçe**
- [Hızlı Başlangıç](#hızlı-başlangıç)
- [Ana Ekran](#ana-ekran)
- [iPerf3 / LibreSpeed](#iperf3--librespeed)
- [Geçmiş](#geçmiş)
- [Tanılama](#tanılama)
- [Wi-Fi](#wi-fi)
- [Ayarlar](#ayarlar)
- [Klavye Kısayolları](#klavye-kısayolları)
- [Sorun Giderme](#sorun-giderme)
- [SSS](#sıkça-sorulan-sorular)

**English**
- [Quick Start](#quick-start)
- [Home](#home)
- [iPerf3 / LibreSpeed (EN)](#iperf3--librespeed-en)
- [History](#history)
- [Diagnostics](#diagnostics)
- [Wi-Fi (EN)](#wi-fi-en)
- [Settings](#settings)
- [Keyboard Shortcuts](#keyboard-shortcuts)
- [Troubleshooting](#troubleshooting)
- [FAQ](#faq)

---

# 🇹🇷 TÜRKÇE

---

## Hızlı Başlangıç

### İlk Kurulum (5 dakika)

1. **LeoNet Pro'yu yükle** — `LeoNetPro_Setup_v1.1.0.exe` dosyasını çalıştır
2. Kurulum sırasında dil olarak **Türkçe** seç
3. iPerf3 ve Tesseract OCR bileşenlerini **işaretli bırak** (önerilir)
4. Kurulum bitince **masaüstü kısayolundan** uygulamayı başlat
5. İlk açılışta tema ve dil otomatik Windows ayarlarına göre seçilir — istersen **Ayarlar** sekmesinden değiştirebilirsin

### Speedtest CLI Kurulumu (ZORUNLU)

İnternet hız testi için Ookla'nın resmi aracı gerekli (yasal sebeplerle uygulamaya gömülmedi):

1. https://www.speedtest.net/apps/cli adresine git
2. **Windows** sürümünü indir (zip dosyası)
3. Zip'i aç, `speedtest.exe` dosyasını **`C:\Windows`** veya **`C:\Program Files\Speedtest`** klasörüne kopyala
4. LeoNet Pro'yu yeniden başlat — otomatik bulur

**Alternatif:** Speedtest CLI yoksa **Cloudflare** üzerinden manuel test yapabilirsin (saatte birkaç kez sınırlı).

### İlk Test

1. **Ana Ekran** sekmesine git
2. **Hız Testini Başlat** butonuna tıkla (veya `Ctrl+T`)
3. 30 saniye bekle — DL/UL/Ping gauge'ları dolar
4. Sonuç otomatik olarak **Geçmiş** sekmesine kaydedilir

✅ Tebrikler, ilk testin tamamlandı.

---

## Ana Ekran

Uygulamanın açıldığında gördüğün ilk sekme. Üç ana fonksiyon: hız testi, TR-143 hesabı, OCR.

### 🚀 İnternet Hız Testi

**Nasıl çalışır:**
1. **Hız Testini Başlat** butonuna tıkla (veya `Ctrl+T`)
2. Uygulama arka planda **Speedtest CLI** çağırır
3. Üç canlı gösterge gerçek zamanlı dolmaya başlar:
   - **🔽 İndirme** (Download) — Mbps cinsinden
   - **🔼 Yükleme** (Upload) — Mbps cinsinden
   - **📶 Ping** — milisaniye cinsinden gecikme
4. Test bitince sonuç **otomatik kaydedilir** (Geçmiş sekmesinde görürsün)

**İpuçları:**
- En doğru sonuç için diğer uygulamaları kapat (Netflix, YouTube vs.)
- Wi-Fi yerine kablolu bağlantı tercih et (etkili karşılaştırma için)
- Aynı saatte tekrarlı test yap — günün saatine göre değişir

**Beklenmedik düşük sonuç çıkarsa:**
- Modem/router'ı yeniden başlat (10 saniye fişi çek)
- Aynı testi 5 dakika sonra tekrarla
- Wi-Fi'da -65 dBm'den zayıf sinyalle test yapma

### 📐 TR-143 Hesaplayıcı

ACS / TR-069 raporlarındaki BOM/EOM zaman damgalarından **gerçek hızı hesaplar**.

**Kullanım:**
1. **Bayt** kutusuna ölçülen bayt sayısını gir
   - Örnek: `1234567` (ham sayı)
   - Veya birimle: `12 MB`, `0.5 GiB`, `2.5 GB`
2. **Süre** kutusuna ölçüm süresini saniye olarak gir
   - Örnek: `12.345`
3. **Hesapla** (veya `Ctrl+Enter`)
4. Sonuç 5 farklı birimde gösterilir: bps, Kbps, Mbps, Mbits/sec, Mbytes/sec

**Neden bu hesap?**
ACS sistemleri bazen sadece bayt+süre verir, hızı sen hesaplaman gerekir. CPE Test mühendisleri için bu temel iş.

### 📷 OCR Ekran Görüntü Analizi

ACS arayüzünden alınan ekran görüntüsünden **otomatik** BOM/EOM zaman damgalarını çıkarır.

**Kullanım:**
1. ACS arayüzünden ekran görüntüsü al (Win+Shift+S veya Snipping Tool)
2. Görüntüyü **OCR alanına sürükle-bırak**
3. Tesseract OCR otomatik olarak zaman damgalarını çıkarır
4. Çıkan değerler hesaplayıcıya **otomatik doldurulur**

**Desteklenen formatlar:** PNG, JPG, BMP, WebP, TIFF

**Çoklu dosya:** Aynı anda birden fazla görüntü sürükleyebilirsin — sırayla işler.

**OCR çalışmıyorsa:**
- Tesseract OCR'ın yüklü olduğundan emin ol (kurulum sırasında işaretliydi)
- Ekran görüntüsünün **çözünürlüğü** yüksek olsun (en az 100 DPI)
- Zaman damgalarının üzerinde **yazı olmasın** (örn watermark)

---

## iPerf3 / LibreSpeed

İkinci sekme. **Throughput testi** — yani gerçek ağ kapasitesini ölçmek için.

### 📊 iPerf3 İstemci Modu

iPerf3 bant genişliği test aracıdır. Public server'lara veya kendi server'ına test yapabilirsin.

**Adım adım kullanım:**

1. **Sunucu** kutusuna server adresi gir:
   - Public: `iperf.he.net`, `bouygues.iperf.fr`, `speedtest.hetzner.de`
   - Yerel: `192.168.1.50` gibi LAN IP'si
2. **Port** kutusu (default `5201`)
3. **Süre** (default `10` saniye)
4. **Paralel Stream** sayısı (default `1`, gerçekçi için `4` kullan)
5. **Test Başlat** butonuna tıkla
6. **Canlı grafik** açılır — bant genişliği saniyelik çizilir

**Canlı grafik neden önemli?**
- Dalgalanmaları görürsün (steady mi, dalgalı mı?)
- Drop'lar net belli olur (paket kaybı varsa düşüş anlık görünür)
- Modem CPU'sunun ısınma efektini izleyebilirsin (uzun testte düşüş başlarsa)

### 💻 Gelişmiş Komut Kutusu

İleri kullanıcılar için — iPerf3'ün tüm parametrelerini yazabilirsin:

```
-c iperf.he.net -p 5201 -t 30 -P 4 --reverse
```

**Yaygın komutlar:**

| Komut | Anlamı |
|---|---|
| `-c <ip>` | Server'a bağlan (client modu) |
| `-t <saniye>` | Test süresi |
| `-P <sayı>` | Paralel stream sayısı |
| `-R` veya `--reverse` | Ters yön (server → sen = download) |
| `--bidir` | Çift yönlü (DL + UL aynı anda) |
| `-u` | UDP modu (jitter/loss için) |
| `-b 100M` | Bant genişliği sınırı (100 Mbps cap) |

**Senaryo örnekleri:**

```
# Download testi (server senin yönüne basıyor)
-c iperf.he.net -t 30 -P 4 --reverse

# Çift yönlü stres testi (bufferbloat için)
-c iperf.he.net -t 30 --bidir

# UDP — packet loss / jitter
-c iperf.he.net -t 10 -u -b 50M

# Yerel LAN testi (modem ↔ PC)
-c 192.168.1.50 -t 10
```

### 🖥️ iPerf3 Sunucu Modu

PC'ni bir test sunucusu yapar. Başka bir cihazdan bağlanıp test yapabilirsin (örn telefondan, başka PC'den, modem testi).

**Kullanım:**
1. **Sunucuyu Başlat** butonuna tıkla
2. Port 5201'de dinlemeye başlar
3. **Canlı log paneli** gelen bağlantıları gösterir
4. Test cihazından `iperf3 -c <PC_IP_adresin> -t 10` çalıştır
5. Sunucu modu kapatınca port otomatik temizlenir

**CPE Saha Senaryosu:**
Müşteri evinde modem test ediyorsun, internet kesik. Telefonunu PC'ne hotspot yap, telefonu PC1, iPerf3 server PC1'de, modem alın PC2'den client testi → modem WAN'sız bile LAN performansını ölçersin.

### 🌐 LibreSpeed

Tarayıcı tabanlı hız testi. Speedtest CLI olmasa bile çalışır.

**Kullanım:**
1. **LibreSpeed Aç** butonuna tıkla
2. Tarayıcıda yeni sekme açılır
3. Otomatik test başlar — sonuç tarayıcıda görünür

**Avantajı:** Speedtest CLI gerektirmez. Dezavantajı: sonuç otomatik geçmişe kaydolmaz.

### 🛠 Ağ Araçları

iPerf3'ün alt kısmında pratik araçlar var:

| Araç | Açıklama | Örnek |
|---|---|---|
| **Ping** | 4 paket ping, ortalama RTT | Hedef: `8.8.8.8` |
| **TCP Port** | Port açık mı kontrol | `google.com:443` |
| **UDP Port** | UDP probe | `8.8.8.8:53` |
| **DNS Lookup** | Domain → IP, ters arama | `microsoft.com` |
| **Traceroute** | Hop hop hedefe yol | Hedef: `8.8.8.8` |

---

## Geçmiş

Tüm hız testleri otomatik kaydolur. Üçüncü sekmede analiz et.

### 📋 Tablo

Sıralanabilir kolonlar:
- **Zaman** — testin tarihi/saati
- **Sunucu** — Speedtest CLI'nin seçtiği sunucu
- **Ping** — milisaniye
- **DL/UL** — Mbps
- **Durum** — Geçti / Uyarı / Başarısız (ayarladığın eşiklere göre)

**Sıralama:** Kolonun başlığına tıkla → o kolona göre sırala. Tekrar tıkla → ters çevir.

### 📈 Grafikler

Zaman serisi grafikler:
- **Download** zaman içinde
- **Upload** zaman içinde
- **Ping** zaman içinde

Tema rengine uyumlu renkler. Sağ tık → ölçek değiştir, dışa aktar.

### 💾 Dışa Aktarma

**4 farklı dışa aktarma:**

| Format | Ne için? |
|---|---|
| **CSV** | Excel'de açmak için |
| **DB** | Tüm SQLite veritabanını yedeklemek için |
| **PDF Rapor** | TR-143 uyumlu profesyonel rapor (müşteriye sunmak için) |
| **Özet Rapor** | İstatistiksel özet (ortalama/min/maks, başarı oranı) |

---

## Tanılama

Dördüncü sekme. Ağın derinlemesine analizi.

### 📡 Canlı Ping Monitörü

Bir hedefe sürekli ping atar, grafik çizer.

**Kullanım:**
1. **Hedef** alanına IP veya domain gir (`8.8.8.8`, `google.com`)
2. **Başlat** butonuna tıkla
3. Grafik gerçek zamanlı çizilir
4. **Eşik** ayarla (örn 100 ms) — aşıldığında uyarı verir

**Outage History:**
Bağlantı kesintileri otomatik kaydedilir:
- **Başlangıç** — kesintinin saati
- **Bitiş** — bağlantının döndüğü saat
- **Süre** — kesintinin süresi

CPE testlerinde "bu modem bir saatte 3 kez bağlantı kesmiş" tarzı tespit için ideal.

### 🔬 Tanılama Testleri

**Tam Tanılama Yap** butonuyla **13 ayrı test** aynı anda çalışır:

| Test | Yöntem | Ne Söyler |
|---|---|---|
| **Paket Kaybı** | 20× ICMP ping | Bağlantı güvenilirliği (%) |
| **Jitter** | RFC 3550 | Pingler arası dalgalanma (VoIP/IPTV kalitesi) |
| **Ortalama Ping** | 20× ICMP | Gidiş-dönüş süresi |
| **MTU Discovery** | DF bit ile ikili arama | Yolun maks paket boyutu (576-1500), VPN/PPPoE tespiti |
| **Bufferbloat** | Çift yönlü yük + ping | A-F notu (yük altında gecikme) |
| **DNS Latency** | UDP × 3 | 5 DNS sağlayıcının medyan gecikmesi |
| **DNSSEC** | Cloudflare DoH AD flag | ISP DNS güvenlik doğrulaması yapıyor mu |
| **DoH** | HTTPS probe | DNS over HTTPS çalışıyor mu |
| **DoT** | TLS port 853 | DNS over TLS çalışıyor mu |
| **DNS Leak** | whoami.akamai.net | Asıl DNS sunucun kim (VPN leak tespiti) |
| **Gateway** | Otomatik + 5× ping | Modem yerel IP'si ve gecikmesi |
| **TTL/Hops** | ICMP TTL | Karşı tarafın OS tahmini + hop sayısı |
| **Adaptörler** | `ipconfig /all` | Tüm ağ adaptörleri |

### 🏆 Ağ Kalite Skoru

Tüm testlerin sonuçlarından hesaplanan **0-100 sağlık skoru**:
- **90-100:** Mükemmel ✅
- **70-89:** İyi
- **50-69:** Orta — bazı sorunlar var
- **<50:** Kötü ❌

Tek bakışta ağ durumunu anlamak için.

### 💡 Pratik Senaryo

Müşteri "internetim yavaş" diyor. Ne yapayım?

1. **Tam Tanılama** çalıştır
2. **Kalite Skoru** 65 çıktı
3. Detaylara bak:
   - Ping: 12 ms ✅
   - Jitter: 35 ms ❌ (10 ms üstü kötü)
   - Bufferbloat: D ❌
   - Packet Loss: 2.3% ❌
4. **Yorum:** "Hız iyi ama jitter/bufferbloat kötü → modem QoS sorunu"
5. **Çözüm:** Modem ayarlarında QoS aktifleştir, yeniden test et

---

## Wi-Fi

Beşinci sekme. **Çevredeki kablosuz ağların derin analizi** — profesyonel araç seviyesinde.

### 🔍 Tarama

**Kullanım:**
1. **Tara** butonuna tıkla (veya otomatik tarama bekle)
2. Windows `WlanScan` API tetiklenir — **gerçek tarama** (cache değil)
3. ~3.5 saniye bekle
4. Tablo dolar

**Otomatik tarama:**
- Default: AÇIK, 15 saniye aralıkla
- Aralık 5-300 saniye arasında ayarlanabilir
- Uygulama açıldıktan 1 saniye sonra otomatik başlar

### 🎚 Filtre Toggle'ları

Üst barda 3 checkbox:

**👁 Gizli Ağları Göster** (default: KAPALI)
- Açıkken: SSID broadcast etmeyen `<Hidden>` ağlar tabloya gelir
- Her gizli BSSID kendi satırında
- **Kafayı karıştırıyorsa kapalı bırak**

**🔍 Tüm Ağları Göster** (default: KAPALI)
- Açıkken: Sinyal değeri okunamayan BSSID'ler de görünür
- **Forensik analiz** için faydalı (zayıf radyolar)

**🔗 Grupla** (default: AÇIK)
- Açıkken: Aynı SSID'liler **alt alta**, en güçlü sinyal en üstte
- Kapalıyken: Tüm BSSID'ler **saf sinyal sıralaması** (karışabilir)

### 📊 BSSID Bazlı Tablo

Her BSSID kendi satırında. Mesh sistemleri için **çok değerli**:

| SSID | Sinyal | Kanal | Band | BSSID |
|---|---|---|---|---|
| ⭐ MyHomeWiFi | -52 dBm | 36 | 5 GHz | aa:bb:cc:11:22:34 |
| MyHomeWiFi | -54 dBm | 6 | 2.4 GHz | aa:bb:cc:11:22:33 |
| MyHomeWiFi | -68 dBm | 44 | 5 GHz | dd:ee:ff:55:66:78 |
| MyHomeWiFi | -70 dBm | 11 | 2.4 GHz | dd:ee:ff:55:66:77 |

**⭐ Yıldız** = şu an bağlı olduğun BSSID. Mesh sisteminde hangi cihaza bağlısın hemen görürsün.

### 🔬 Detail Panel

Tabloda bir satıra tıkla → sağdaki panel 5 bölümle dolar:

#### 1. Varlık (Entity)
- **SSID** — Ağ adı
- **Access Point** — Bağlandığın BSSID
- **MAC Address** — BSSID alternatif gösterim
- **Üretici** — MAC OUI'den çıkarılan vendor (289 entry: TP-Link, Cisco, Apple, Huawei vs.)
- **Model** — N/A (modem rapor etmiyor)

#### 2. İstatistikler (Stats)
- **Sinyal** — dBm + rating:
  - 🟢 ≥-50 dBm → **Mükemmel**
  - 🔵 -50 ila -65 dBm → **İyi**
  - 🟠 -65 ila -75 dBm → **Orta**
  - 🔴 <-75 dBm → **Zayıf**

#### 3. Yapılandırma (Configuration)
- **Kanal** — 1, 6, 11, 36, 44, 100, 149 vs.
- **Genişlik** — 20/40/80/160 MHz
- **Güvenlik** — WPA2-Personal / WPA3 / OWE
- **Basic Rates** — Temel hızlar (1, 2, 5.5, 11 Mbps vs.)
- **Country** — Ülke kodu (genelde N/A)

#### 4. Yetenekler (Capabilities)
- **WiFi Mode** — Wi-Fi 4 (n), Wi-Fi 5 (ac), Wi-Fi 6 (ax), Wi-Fi 6E, Wi-Fi 7 (be)
- **Max Data Rate** — Teorik tepe hız (örn 1200.9 Mbps)
- **Spatial Streams** — Anten sayısı (1, 2, 4...)
- **Max MCS Index** — Modülasyon endex (0-11)
- **Additional** — MU-MIMO, OFDMA, BSS Coloring

#### 5. Sinyal Zamanı (Signal History)
- **Üstte büyük dBm gösterge** — 18pt, renk kodlu
- **Altında canlı grafik** — saniyelik sinyal değişimi
- Sürekli güncellenir (otomatik tarama açıksa)

### 🗺 Kanal Haritası

Tablonun altında 3 ayrı grafik:
- **2.4 GHz** — Kanal 1-13 (TR/EU bölgesi)
- **5 GHz** — Kanal 36-177
- **6 GHz** — Kanal 1-233 (Wi-Fi 6E/7)

Her ağ **üçgen** olarak çizilir:
- **Taban** = kanal genişliği (20/40/80/160 MHz)
- **Yükseklik** = sinyal gücü

**Çakışma analizi:** 2.4 GHz'de kanal 1, 6, 11 birbirini örtmez. Diğer kanallar (2, 3, 4...) çakışır → kötü performans.

### 📤 CSV Export

**CSV** butonuyla mevcut tabloyu Excel uyumlu dosyaya aktar. Saha raporları için ideal.

### 💡 Pratik Senaryo: Mesh Kapsama Analizi

Müşteri "evimin bir köşesinde Wi-Fi zayıf" diyor.

1. **Otomatik tarama** AÇIK bırak
2. Telefonu kapı kapı dolaştır (Wi-Fi uçtaki noktalara git)
3. **Sinyal Zamanı grafiğine** bak — hangi BSSID güçlü, hangisi zayıf?
4. **Detail panel**'den vendor'a bak (modem mi mesh node mu?)
5. **Channel Map**'te 2.4 GHz çakışması var mı kontrol et
6. **CSV export** → müşteriye rapor

---

## Ayarlar

Altıncı sekme. Tüm tercihler burada.

### 🌐 Dil

Türkçe / İngilizce. **Anlık** değişir — uygulamayı yeniden başlatmana gerek yok.

### 🎨 Tema

6 seçenek:
- **Light** — Beyaz temalı
- **Dark Navy** — Koyu lacivert
- **Forest Green** — Orman yeşili
- **Sunset Orange** — Gün batımı turuncu
- **Cherry Blossom** — Sakura pembesi
- **Midnight Black** — Tam koyu

Tema isimleri aktif UI diline göre çevrilir.

`F11` tuşuyla **temalar arasında geçiş**.

### 🔔 Uyarılar (Alerts)

**E-posta Uyarısı:**
- SMTP sunucu (örn `smtp.gmail.com`)
- Port (587 TLS veya 465 SSL)
- Kullanıcı adı / Şifre (Gmail için "uygulama şifresi" oluştur)
- Alıcı e-posta
- **Eşikler** — hangi durumda mail gelsin (örn DL < 50 Mbps)

**Webhook Uyarısı:**
- Slack, Teams, Discord, özel sunucu — JSON POST destekleyen her sistem
- Webhook URL'sini yapıştır
- Aynı eşikler geçerli

### 🔊 Ses

- **Tıklama sesi** açık/kapalı
- **Uyarı sesi** açık/kapalı

### 🔄 Hakkında → Güncellemeleri Kontrol Et

**Manuel güncelleme kontrolü:**
1. Butona tıkla
2. GitHub Releases API'sine sorgu yapılır
3. 3 olası sonuç:
   - **Güncel** — En son sürümdesin
   - **Yeni sürüm var** — İndirme sayfası açılır
   - **Hata** — İnternet yok veya GitHub erişilemiyor

**Otomatik kontrol:** Günde 1 kez, uygulama açılışında otomatik kontrol edilir (sessiz).

---

## Klavye Kısayolları

| Tuş | İşlev |
|---|---|
| `Ctrl+Enter` | TR-143 hesapla |
| `Ctrl+T` | Hız testi başlat/durdur |
| `F5` | Logları yenile |
| `Ctrl+K` | Sonucu panoya kopyala |
| `Ctrl+O` | OCR ekran görüntü analizi |
| `Ctrl+P` | PDF rapor oluştur |
| `Ctrl+W` | Formu temizle |
| `Ctrl+M` | Mini widget aç/kapat |
| `Ctrl+D` | Tanılama sekmesine git |
| `Ctrl+H` | Geçmiş sekmesine git |
| `Ctrl+,` | Ayarlar sekmesine git |
| `F11` | Tema değiştir (6 tema) |
| `Ctrl+Q` | Uygulamadan çık |

---

## Sorun Giderme

### ❌ "Speedtest CLI bulunamadı" hatası

**Sebep:** Ookla'nın resmi CLI aracı yüklü değil veya PATH'te değil.

**Çözüm:**
1. https://www.speedtest.net/apps/cli indir
2. `speedtest.exe`'yi `C:\Windows` veya `C:\Program Files\Speedtest` içine kopyala
3. Uygulamayı yeniden başlat

**Alternatif:** Ayarlar → Cloudflare fallback'i kullan (manuel, sınırlı)

### ❌ Wi-Fi taraması boş çıkıyor

**Sebep 1:** WiFi adaptörü kapalı
- Windows + R → `ncpa.cpl` → WiFi adaptörünü aç

**Sebep 2:** Bilgisayar Ethernet'e bağlı, WiFi kullanmıyor
- WiFi'yi açık tut, Ethernet'i çıkarmana gerek yok

**Sebep 3:** Wi-Fi sürücüsü eski
- Üreticinin sitesinden en güncel sürücüyü yükle

### ❌ iPerf3 "unable to connect to server"

**Sebep 1:** Sunucu kapalı
- Farklı sunucu dene: `bouygues.iperf.fr`, `speedtest.hetzner.de`

**Sebep 2:** Güvenlik duvarı engelliyor
- Windows Defender → Gelen kurallar → 5201 portu açık mı kontrol et

**Sebep 3:** ISP bazı portları engelliyor
- Farklı port dene: `-p 5202`, `-p 5203`

### ❌ OCR çalışmıyor

**Sebep:** Tesseract OCR yüklü değil

**Çözüm:**
1. Kurulum sırasında **Tesseract OCR** seçeneği işaretliydi mi?
2. Yüklenmediyse: https://github.com/UB-Mannheim/tesseract/wiki indir
3. Standart yere yükle (`C:\Program Files\Tesseract-OCR\`)
4. Uygulamayı yeniden başlat

### ❌ Drag-drop çalışmıyor

**Sebep:** Uygulama yönetici (admin) yetkisinde çalıştırılmış

**Çözüm:**
1. Uygulamayı kapat
2. Masaüstündeki kısayola **sağ tık** → Özellikler
3. Uyumluluk → **"Yönetici olarak çalıştır" işaretini KALDIR**
4. Tekrar aç → drag-drop çalışacak

(Sebebi: Windows UIPI politikası — admin program, normal user'dan drop kabul etmez.)

### ❌ Uygulama açılır açılmaz kapanıyor

**Sebep:** Eksik DLL veya bozuk kurulum

**Çözüm:**
1. Denetim Masası → Uygulamayı kaldır
2. `%APPDATA%/LeoNetPro` klasörünü sil (ayarlar sıfırlanır)
3. En son setup'ı yeniden yükle

---

## Sıkça Sorulan Sorular

### Bu uygulama veri topluyor mu?

**Hayır.** Tüm test sonuçları yerel SQLite veritabanında saklanır (`%APPDATA%/LeoNetPro/history.db`). Hiçbir veri sunucuya gönderilmez.

Sadece şu kullanıcı-başlattığı bağlantılar yapılır:
- Speedtest CLI sunucuları (hız testi sırasında)
- Cloudflare CDN (fallback hız testi)
- GitHub Releases API (güncelleme kontrolü, opsiyonel)

### Verilerim nerede saklanıyor?

- **Veritabanı:** `%APPDATA%/LeoNetPro/history.db`
- **Ayarlar:** Windows Registry — `HKCU\Software\Burak Aslan\LeoNet Pro`
- Bilgisayarını silmediğin sürece tüm geçmiş kayıt durur.

### Bu uygulamayı şirketimde kullanabilir miyim?

EULA'ya göre **ticari kullanım yasak**. Kişisel ve eğitim amaçlı kullanım serbest. Şirket içi diagnostics için kullanmak istersen yazarla iletişime geç (LinkedIn).

### Bir sürüm sonra ayarlarım gidiyor mu?

**Hayır.** Installer otomatik upgrade yapar — geçmiş, ayarlar, tema seçimi korunur.

### Wi-Fi taraması bilgisayara zarar verir mi?

**Hayır.** WlanScan API Windows'un yerleşik özelliği. Tamamen pasif okuma yapar.

### Birden fazla bilgisayara kurabilir miyim?

Evet — kişisel kullanım için herhangi bir sınır yok.

---

# 🇬🇧 ENGLISH

---

## Quick Start

### First Setup (5 minutes)

1. **Install LeoNet Pro** — run `LeoNetPro_Setup_v1.1.0.exe`
2. Select **English** as the installation language
3. Keep **iPerf3** and **Tesseract OCR** components checked (recommended)
4. After installation, launch from the **desktop shortcut**
5. On first launch, theme and language follow Windows settings — change them in **Settings** if needed

### Speedtest CLI Setup (REQUIRED)

For internet speed testing, Ookla's official CLI is needed (not bundled for legal reasons):

1. Go to https://www.speedtest.net/apps/cli
2. Download the **Windows** version (zip)
3. Extract `speedtest.exe` to `C:\Windows` or `C:\Program Files\Speedtest`
4. Restart LeoNet Pro — it will auto-detect

**Alternative:** If Speedtest CLI is missing, use **Cloudflare** fallback (manual, rate-limited).

### First Test

1. Go to **Home** tab
2. Click **Start Speed Test** (or `Ctrl+T`)
3. Wait ~30 seconds — DL/UL/Ping gauges fill
4. Result is auto-saved to **History** tab

✅ Congrats, your first test is complete.

---

## Home

The default tab — three main functions: speed test, TR-143 calculator, OCR.

### 🚀 Internet Speed Test

**How it works:**
1. Click **Start Speed Test** (or `Ctrl+T`)
2. App invokes **Speedtest CLI** in background
3. Three live gauges fill in real-time:
   - **🔽 Download** (Mbps)
   - **🔼 Upload** (Mbps)
   - **📶 Ping** (ms)
4. Result is **auto-saved** to History

**Tips:**
- Close other apps for best accuracy (Netflix, YouTube, etc.)
- Prefer wired connection over Wi-Fi
- Run multiple tests at the same time of day for comparison

**If you get unexpectedly low results:**
- Reboot modem/router (unplug 10 seconds)
- Retry after 5 minutes
- Don't test on Wi-Fi weaker than -65 dBm

### 📐 TR-143 Calculator

Calculates throughput from BOM/EOM timestamps in ACS/TR-069 reports.

**Usage:**
1. Enter **bytes** measured: `1234567` or with units like `12 MB`, `0.5 GiB`
2. Enter **time** in seconds: `12.345`
3. Click **Calculate** (or `Ctrl+Enter`)
4. Result shown in 5 units: bps, Kbps, Mbps, Mbits/sec, Mbytes/sec

**Why this calc?**
ACS systems sometimes only give bytes+time; you compute the throughput. Standard task for CPE Test Engineers.

### 📷 OCR Screenshot Analysis

Extracts BOM/EOM timestamps automatically from ACS interface screenshots.

**Usage:**
1. Take screenshot of ACS interface (Win+Shift+S or Snipping Tool)
2. **Drag-drop** image onto OCR area
3. Tesseract OCR extracts timestamps automatically
4. Values auto-fill into calculator

**Supported formats:** PNG, JPG, BMP, WebP, TIFF

**Multi-file:** drag multiple images at once — processed in sequence.

**If OCR fails:**
- Ensure Tesseract OCR is installed (was checked during setup)
- Screenshot should be high resolution (min 100 DPI)
- No overlays/watermarks over timestamps

---

## iPerf3 / LibreSpeed (EN)

Second tab. **Throughput testing** — measure real network capacity.

### 📊 iPerf3 Client Mode

iPerf3 is a bandwidth test tool. Test against public servers or your own.

**Step by step:**

1. **Server** field: enter server address
   - Public: `iperf.he.net`, `bouygues.iperf.fr`, `speedtest.hetzner.de`
   - Local: LAN IP like `192.168.1.50`
2. **Port** (default `5201`)
3. **Duration** (default `10` seconds)
4. **Parallel Streams** (default `1`, use `4` for realistic testing)
5. Click **Start Test**
6. **Live chart** — bandwidth plotted second-by-second

**Why the live chart matters:**
- See variations (steady vs fluctuating)
- Drops are visible as instant dips
- Watch modem CPU heat-up effect on long tests

### 💻 Advanced Command Box

For power users — type any iPerf3 argument string:

```
-c iperf.he.net -p 5201 -t 30 -P 4 --reverse
```

**Common commands:**

| Command | Meaning |
|---|---|
| `-c <ip>` | Connect to server (client mode) |
| `-t <sec>` | Test duration |
| `-P <num>` | Parallel streams |
| `-R` / `--reverse` | Reverse direction (server → you = download) |
| `--bidir` | Bidirectional (DL + UL simultaneously) |
| `-u` | UDP mode (for jitter/loss) |
| `-b 100M` | Bandwidth cap (100 Mbps) |

**Example scenarios:**

```
# Download test
-c iperf.he.net -t 30 -P 4 --reverse

# Bidirectional stress (for bufferbloat)
-c iperf.he.net -t 30 --bidir

# UDP — packet loss / jitter
-c iperf.he.net -t 10 -u -b 50M

# Local LAN test
-c 192.168.1.50 -t 10
```

### 🖥️ iPerf3 Server Mode

Makes your PC a test server. Test from another device.

**Usage:**
1. Click **Start Server**
2. Listens on port 5201
3. **Live log panel** shows incoming connections
4. From test device: `iperf3 -c <your_PC_IP> -t 10`
5. Stop server → port auto-released

**Field Scenario:**
Testing customer modem, no WAN. Make phone hotspot for PC1, run iPerf3 server on PC1, test from PC2 (modem-only client) → measure LAN even without internet.

### 🌐 LibreSpeed

Browser-based speed test. Works without Speedtest CLI.

**Usage:**
1. Click **Open LibreSpeed**
2. New browser tab opens
3. Auto-test starts in browser

**Advantage:** No CLI needed. **Disadvantage:** Result not auto-saved to history.

### 🛠 Network Tools

Below iPerf3 — practical tools:

| Tool | Description |
|---|---|
| **Ping** | 4-ping with average RTT |
| **TCP Port** | Connection test (open/closed/filtered) |
| **UDP Port** | UDP probe |
| **DNS Lookup** | Forward + reverse |
| **Traceroute** | Live hop-by-hop |

---

## History

All speed tests auto-saved. Third tab for analysis.

### 📋 Table

Sortable columns:
- **Timestamp** — test date/time
- **Server** — Speedtest CLI's chosen server
- **Ping** — milliseconds
- **DL/UL** — Mbps
- **Status** — Pass / Warn / Fail (based on configured thresholds)

**Sort:** Click column header. Click again to reverse.

### 📈 Charts

Time-series graphs for Download, Upload, Ping. Theme-aware colors.

### 💾 Export

**4 export formats:**

| Format | Used For |
|---|---|
| **CSV** | Excel-compatible |
| **DB** | Full SQLite backup |
| **PDF Report** | TR-143 compliant professional report |
| **Summary Report** | Statistical overview (avg/min/max, pass rate) |

---

## Diagnostics

Fourth tab. Deep network analysis.

### 📡 Live Ping Monitor

Continuous ping to a target with graph.

**Usage:**
1. Enter **Target** (IP or domain): `8.8.8.8`, `google.com`
2. Click **Start**
3. Real-time graph
4. Set **Threshold** (e.g., 100 ms) — alerts when exceeded

**Outage History:**
Auto-logs disconnections:
- **Start** — time of outage
- **End** — when connection returned
- **Duration** — outage length

Ideal for CPE testing: "modem dropped 3 times in an hour" type detection.

### 🔬 Diagnostic Tests

**Run Full Diagnostics** button runs **13 tests** simultaneously:

| Test | Method | What It Tells |
|---|---|---|
| **Packet Loss** | 20× ICMP | Reliability (%) |
| **Jitter** | RFC 3550 | Inter-packet variation (VoIP/IPTV quality) |
| **Avg. Ping** | 20× ICMP | Round-trip average |
| **MTU Discovery** | Binary search with DF bit | Path MTU (576-1500), VPN/PPPoE detection |
| **Bufferbloat** | Bidirectional load + ping | A-F grade |
| **DNS Latency** | UDP × 3 | Median latency for 5 providers |
| **DNSSEC** | Cloudflare DoH AD flag | DNSSEC validation by ISP |
| **DoH** | HTTPS probe | DNS over HTTPS availability |
| **DoT** | TLS port 853 | DNS over TLS availability |
| **DNS Leak** | whoami.akamai.net | Real DNS resolver (VPN leak check) |
| **Gateway** | Auto + 5× ping | Modem local IP + latency |
| **TTL/Hops** | ICMP TTL | Remote OS guess + hop count |
| **Interfaces** | `ipconfig /all` | All network adapters |

### 🏆 Network Quality Score

A single 0-100 health score:
- **90-100:** Excellent ✅
- **70-89:** Good
- **50-69:** Fair — some issues
- **<50:** Poor ❌

At-a-glance status.

### 💡 Practical Scenario

Customer says "internet is slow". What do I do?

1. Run **Full Diagnostics**
2. **Quality Score**: 65
3. Look at details:
   - Ping: 12 ms ✅
   - Jitter: 35 ms ❌ (>10 ms is bad)
   - Bufferbloat: D ❌
   - Packet Loss: 2.3% ❌
4. **Interpretation:** "Speed OK but jitter/bufferbloat bad → router QoS issue"
5. **Solution:** Enable QoS in router settings, retest

---

## Wi-Fi (EN)

Fifth tab. **Deep Wi-Fi network analysis** — professional grade.

### 🔍 Scanning

**Usage:**
1. Click **Scan** (or wait for auto-scan)
2. Windows `WlanScan` API triggers — **real scan** (not cached)
3. Wait ~3.5 seconds
4. Table populates

**Auto-Scan:**
- Default: ON, 15-second interval
- Configurable 5-300 seconds
- Auto-starts 1 second after UI ready

### 🎚 Filter Toggles

Top bar has 3 checkboxes:

**👁 Show Hidden Networks** (default: OFF)
- When on, `<Hidden>` SSID rows appear
- Each hidden BSSID gets its own row
- **Keep off if confusing**

**🔍 Show All Networks** (default: OFF)
- When on, BSSIDs without measurable signal also shown
- Useful for **forensic analysis** (weak radios)

**🔗 Group SSIDs** (default: ON)
- When on, same-SSID rows kept adjacent, strongest signal on top
- When off, all BSSIDs in **pure signal order**

### 📊 BSSID-Based Table

Each BSSID gets its own row. Very valuable for mesh systems:

| SSID | Signal | Channel | Band | BSSID |
|---|---|---|---|---|
| ⭐ MyHomeWiFi | -52 dBm | 36 | 5 GHz | aa:bb:cc:11:22:34 |
| MyHomeWiFi | -54 dBm | 6 | 2.4 GHz | aa:bb:cc:11:22:33 |
| MyHomeWiFi | -68 dBm | 44 | 5 GHz | dd:ee:ff:55:66:78 |
| MyHomeWiFi | -70 dBm | 11 | 2.4 GHz | dd:ee:ff:55:66:77 |

**⭐ Star** = BSSID you're currently connected to. Instantly see which mesh node you're on.

### 🔬 Detail Panel

Click any row → right panel fills with 5 sections:

#### 1. Entity
- **SSID** — Network name
- **Access Point** — BSSID you're connected to
- **MAC Address** — BSSID alternative display
- **Vendor** — From MAC OUI lookup (289 entries: TP-Link, Cisco, Apple, Huawei, etc.)
- **Model** — N/A (modem doesn't report)

#### 2. Stats
- **Signal** — dBm with rating:
  - 🟢 ≥-50 dBm → **Excellent**
  - 🔵 -50 to -65 dBm → **Good**
  - 🟠 -65 to -75 dBm → **Fair**
  - 🔴 <-75 dBm → **Weak**

#### 3. Configuration
- **Channel** — 1, 6, 11, 36, 44, 100, 149, etc.
- **Width** — 20/40/80/160 MHz
- **Security** — WPA2-Personal / WPA3 / OWE
- **Basic Rates** — Base rates (1, 2, 5.5, 11 Mbps, etc.)
- **Country** — Country code (usually N/A)

#### 4. Capabilities
- **WiFi Mode** — Wi-Fi 4 (n), Wi-Fi 5 (ac), Wi-Fi 6 (ax), Wi-Fi 6E, Wi-Fi 7 (be)
- **Max Data Rate** — Theoretical PHY peak (e.g., 1200.9 Mbps)
- **Spatial Streams** — Antenna count (1, 2, 4...)
- **Max MCS Index** — Modulation index (0-11)
- **Additional** — MU-MIMO, OFDMA, BSS Coloring

#### 5. Signal History
- **Large dBm display** on top — 18 pt, color-coded
- **Live graph** below — second-by-second
- Continuously updates (if auto-scan is on)

### 🗺 Channel Map

3 separate plots below the table:
- **2.4 GHz** — Channels 1-13 (TR/EU)
- **5 GHz** — Channels 36-177
- **6 GHz** — Channels 1-233 (Wi-Fi 6E/7)

Each network as a **triangle**:
- **Base** = channel width (20/40/80/160 MHz)
- **Height** = signal strength

**Overlap analysis:** 2.4 GHz channels 1, 6, 11 don't overlap. Others (2, 3, 4...) overlap → bad performance.

### 📤 CSV Export

**CSV** button exports current table to Excel-compatible file. Great for field reports.

### 💡 Practical Scenario: Mesh Coverage Analysis

Customer says "Wi-Fi is weak in one corner of my house."

1. Keep **Auto-scan** ON
2. Walk around with the phone (go to far corners)
3. Watch **Signal History graph** — which BSSID strong, which weak?
4. Check **Detail Panel** vendor (is it modem or mesh node?)
5. Check **Channel Map** for 2.4 GHz overlap
6. **CSV export** → report to customer

---

## Settings

Sixth tab. All preferences here.

### 🌐 Language

Turkish / English. **Instant** switch — no restart needed.

### 🎨 Theme

6 options: Light, Dark Navy, Forest Green, Sunset Orange, Cherry Blossom, Midnight Black.

Theme names translate to active UI language.

`F11` to **cycle themes**.

### 🔔 Alerts

**Email Alert:**
- SMTP server (e.g., `smtp.gmail.com`)
- Port (587 TLS or 465 SSL)
- Username/Password (for Gmail, create an "app password")
- Recipient email
- **Thresholds** — when to email (e.g., DL < 50 Mbps)

**Webhook Alert:**
- Slack, Teams, Discord, custom server — any JSON POST endpoint
- Paste webhook URL
- Same thresholds apply

### 🔊 Sound

- **Click sound** on/off
- **Alert sound** on/off

### 🔄 About → Check for Updates

**Manual update check:**
1. Click button
2. GitHub Releases API query
3. 3 possible outcomes:
   - **Up to date** — Latest version
   - **New version available** — Download page opens
   - **Error** — No internet or GitHub unreachable

**Auto-check:** Once daily on launch (silent).

---

## Keyboard Shortcuts

| Key | Action |
|---|---|
| `Ctrl+Enter` | Calculate TR-143 |
| `Ctrl+T` | Start/Stop Speed Test |
| `F5` | Reload Logs |
| `Ctrl+K` | Copy result to clipboard |
| `Ctrl+O` | OCR Screenshot Analysis |
| `Ctrl+P` | Generate PDF Report |
| `Ctrl+W` | Clear form |
| `Ctrl+M` | Toggle Mini Widget |
| `Ctrl+D` | Go to Diagnostics tab |
| `Ctrl+H` | Go to History tab |
| `Ctrl+,` | Go to Settings tab |
| `F11` | Cycle themes (6 themes) |
| `Ctrl+Q` | Quit application |

---

## Troubleshooting

### ❌ "Speedtest CLI not found" error

**Cause:** Ookla's official CLI is not installed or not in PATH.

**Solution:**
1. Download from https://www.speedtest.net/apps/cli
2. Copy `speedtest.exe` to `C:\Windows` or `C:\Program Files\Speedtest`
3. Restart the application

**Alternative:** Use Cloudflare fallback in Settings (manual, rate-limited)

### ❌ Wi-Fi scan returns empty

**Cause 1:** Wi-Fi adapter is off
- Windows + R → `ncpa.cpl` → enable Wi-Fi adapter

**Cause 2:** PC is on Ethernet, not using Wi-Fi
- Keep Wi-Fi on; you don't need to unplug Ethernet

**Cause 3:** Outdated Wi-Fi driver
- Install latest driver from manufacturer's website

### ❌ iPerf3 "unable to connect to server"

**Cause 1:** Server is down
- Try different server: `bouygues.iperf.fr`, `speedtest.hetzner.de`

**Cause 2:** Firewall blocking
- Windows Defender → Inbound rules → check port 5201

**Cause 3:** ISP blocking some ports
- Try different port: `-p 5202`, `-p 5203`

### ❌ OCR not working

**Cause:** Tesseract OCR not installed

**Solution:**
1. Was **Tesseract OCR** checked during installation?
2. If not: download from https://github.com/UB-Mannheim/tesseract/wiki
3. Install to standard location (`C:\Program Files\Tesseract-OCR\`)
4. Restart application

### ❌ Drag-drop not working

**Cause:** App is running with administrator (admin) privileges

**Solution:**
1. Close the application
2. Right-click desktop shortcut → Properties
3. Compatibility → **UNCHECK "Run as administrator"**
4. Reopen → drag-drop will work

(Reason: Windows UIPI policy — admin apps can't receive drops from normal user.)

### ❌ App closes immediately after opening

**Cause:** Missing DLL or corrupted installation

**Solution:**
1. Control Panel → Uninstall application
2. Delete `%APPDATA%/LeoNetPro` folder (settings reset)
3. Reinstall latest setup

---

## FAQ

### Does this app collect data?

**No.** All test results are stored in a local SQLite database (`%APPDATA%/LeoNetPro/history.db`). No data is sent to any server.

Only these user-initiated connections happen:
- Speedtest CLI servers (during speed test)
- Cloudflare CDN (fallback speed test)
- GitHub Releases API (update check, optional)

### Where is my data stored?

- **Database:** `%APPDATA%/LeoNetPro/history.db`
- **Settings:** Windows Registry — `HKCU\Software\Burak Aslan\LeoNet Pro`
- All history persists unless you delete your computer.

### Can I use this in my company?

According to EULA, **commercial use is prohibited**. Personal and educational use is free. For internal corporate diagnostics, contact the author (LinkedIn).

### Do I lose settings on version upgrade?

**No.** Installer handles upgrades automatically — history, settings, theme selection preserved.

### Does Wi-Fi scanning harm my computer?

**No.** WlanScan API is a built-in Windows feature. Completely passive — only reads data.

### Can I install on multiple computers?

Yes — no limit for personal use.

---

## Author & Contact

**Author:** Burak Aslan
**LinkedIn:** [Burak ASLAN](https://www.linkedin.com/in/burak-aslan-/)
**GitHub:** [github.com/burakaslann/LeoNetPro](https://github.com/burakaslann/LeoNetPro)
**Version:** 1.1.0

For bug reports or feature suggestions:
[github.com/burakaslann/LeoNetPro/issues](https://github.com/burakaslann/LeoNetPro/issues)
