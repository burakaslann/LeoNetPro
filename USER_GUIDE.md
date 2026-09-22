# LeoNet Pro v1.2.0 — Kullanım Kılavuzu / User Guide

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

## v1.2.0: NIC seçimi, sağ tık ve güncelleme

**Ping kaynak IP seçimi:** Tanılama sekmesindeki Çıkış NIC listesinden etkin kartın IPv4 adresini seç. Otomatik, kaynak IP zorlamasını kaldırır. Kart takıp çıkardıysan yenile düğmesini kullan; seçimi test başlamadan yap. Destekleyen ping komutları Windows'ta `-S` kaynak IP parametresini kullanır. Windows yönlendirmesi ve hedefin erişilebilirliği geçerlidir. Bu seçenek Ookla, DNS, HTTP veya iPerf trafiğinin tamamını seçilen karta bağlamaz; fiziksel çıkış yolunu kesinleştirmek için ayrıca doğrulama gerekir.

**Sağ tık menüsü:** Uygulama alanında sağ tıkla; hesaplama, hız testi, OCR, PDF, sekme geçişi ve çıkış gibi işlemlere eriş. Bazı metin/tablo alanları kendi yerel menülerini gösterebilir. Etiketler etkin dil ve temaya göre oluşturulur.

### PySide6 ve testlerin birlikte kullanımı

- **PySide6 / Qt 6 geçişi:** Arayüz PyQt5 yerine PySide6 kullanıyor.
- **Thread yaşam döngüsü:** Çalışan işçilerin referansları korunuyor; çıkışta işçilerin bitmesi bekleniyor.
- **Ping Monitor:** Start/Stop sırasında buton durumu güncelleniyor; işçi sonlanana kadar yeniden başlatma kısa süre devre dışı kalabilir.
- **Testlerin birlikte kullanımı:** Speedtest + Ping ve iPerf3 + Ping kullanılabilir. Özel iPerf dahil ağır hız testlerinin eşzamanlı başlatılması engellenir. Bufferbloat içeren tanılama paketi de ağır test olarak değerlendirilir.

Ookla CLI indirme/yükleme fazlarının süresini kendi belirler; yaklaşık 5 saniyelik bir faz tek başına hata değildir. iPerf3 süresi ayrı ayarlanır. PySide6 geçişi bir mobil sürüm değildir; bu kılavuz Windows uygulaması içindir.

**Dil:** Ayarlar'dan İngilizce seçildiğinde ping eşiği etiketi Alert, Türkçede Uyarı olur. Bu düzeltme tüm dinamik mesajların veya geçmiş kayıtların eksiksiz çevrildiği garantisi değildir.

**Güncelleme:** GitHub HTTPS isteği certifi CA paketiyle doğrulanır. Hata ayrıntıları `%TEMP%\LeoNetPro-update-UpdateFix4.log` dosyasına yazılabilir; günlük yerel kullanıcı/dosya yolları içerebilir. Paylaşmadan önce incele. Güncelleme kontrolü yeni sürümü otomatik kurmaz. 1.2.0 yayımlanmadan GitHub'da 1.1.1 görülmesi beklenebilir.

## Hızlı Başlangıç

### İlk Kurulum (5 dakika)

1. **LeoNet Pro'yu yükle** — `LeoNetPro_Setup_v1.2.0.exe` dosyasını çalıştır
2. Kurulum sırasında dil olarak **Türkçe** seç
3. Gereken bileşenleri seç. Tesseract seçeneği yalnızca yükleyicisi pakette varsa görünür; kurulum sonunda ayrı yükleyiciyi çalıştırıp tamamla.
4. Kurulum bitince **masaüstü kısayolundan** uygulamayı başlat
5. Dil ve temayı **Ayarlar** sekmesinden seç; seçimler sonraki açılışlar için saklanır.

### Speedtest CLI Kurulumu (Ookla ve zamanlanmış testler için)

İnternet hız testi için Ookla'nın resmi aracı gerekli (yasal sebeplerle uygulamaya gömülmedi):

1. https://www.speedtest.net/apps/cli adresine git
2. **Windows** sürümünü indir (zip dosyası)
3. Zip'i aç, `speedtest.exe` dosyasını **LeoNet Pro EXE'sinin bulunduğu klasöre** kopyala
4. LeoNet Pro'yu yeniden başlat — otomatik bulur

**Alternatif:** Speedtest CLI yoksa **Cloudflare** üzerinden manuel test yapabilirsin (manuel; testler arasında en az 30 saniye bekleme).

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
   - Public: kullanım izni olan ve o anda erişilebilir bir iPerf3 sunucusu
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
-c 192.168.1.50 -p 5201 -t 30 -P 4 --reverse
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
-c 192.168.1.50 -t 30 -P 4 --reverse

# Çift yönlü stres testi (bufferbloat için)
-c 192.168.1.50 -t 30 --bidir

# UDP — packet loss / jitter
-c 192.168.1.50 -t 10 -u -b 50M

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
İki Windows bilgisayarı aynı yerel ağa bağla. Birinde iPerf3 sunucusu başlat; diğerinden o bilgisayarın LAN IP adresine istemci testi yap. Bu test internet hızını değil iki cihaz arasındaki yolu ölçer.

### 🌐 LibreSpeed

Tarayıcı tabanlı hız testi. Speedtest CLI olmasa bile çalışır.

**Kullanım:**
1. **LibreSpeed Aç** butonuna tıkla
2. Tarayıcıda yeni sekme açılır
3. Açılan test arayüzünde testi başlat; sonuçların gösterildiği yeri kontrol et

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

Grafikler tema renklerini kullanır. Dışa aktarma için uygulamadaki ilgili düğmeleri kullan.

### 💾 Dışa Aktarma

**4 farklı dışa aktarma:**

| Format | Ne için? |
|---|---|
| **CSV** | Excel'de açmak için |
| **DB** | Tüm SQLite veritabanını yedeklemek için |
| **PDF Rapor** | TR-143 test verilerinden oluşturulan PDF raporu |
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

**Tam Tanılama Yap** butonuyla tanılama adımları sırayla yürütülür:

| Test | Yöntem | Ne Söyler |
|---|---|---|
| **Paket Kaybı** | 20× ICMP ping | Bağlantı güvenilirliği (%) |
| **Jitter** | Ardışık ping RTT farkları | Ortalama mutlak gidiş-dönüş süresi değişkenliği |
| **Ortalama Ping** | 20× ICMP | Gidiş-dönüş süresi |
| **MTU Discovery** | DF bit ile ikili arama | Yanıtlara bağlı MTU tahmini; VPN/PPPoE yorumu kesin tespit değildir |
| **Bufferbloat** | Çift yönlü yük + ping | A-F notu (yük altında gecikme) |
| **DNS Latency** | UDP × 3 | 5 DNS sağlayıcının medyan gecikmesi |
| **DNSSEC** | Cloudflare DoH AD flag | Cloudflare yanıtında AD bayrağı; ISP doğrulaması değildir |
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
   - Packet Loss: 5% ❌
4. **Yorum:** Yük altında gecikme var; bunun nedeni tek başına bu sonuçtan belirlenemez.
5. Kablolu bağlantıyla ve aynı hedefle karşılaştır; ağ yükünü kontrol et. QoS değişikliğini kendi cihazının belgelerine göre değerlendir.

---

## Wi-Fi

Beşinci sekme. **Çevredeki kablosuz ağların derin analizi** — profesyonel araç seviyesinde.

### 🔍 Tarama

**Kullanım:**
1. **Tara** butonuna tıkla (veya otomatik tarama bekle)
2. Windows `WlanScan` API tetiklenir — tarama isteği; sonuçlar gecikmeli veya önbellekten olabilir
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

### 🔎 SSID Arama (v1.1.1 ile eklendi)

Üst bardaki **🔎 SSID ara...** kutusuna yazarak tabloyu anlık filtreleyebilirsin:
- Yazdıkça eşleşmeyen satırlar gizlenir (silinmez)
- Arama kutusunu temizleyince hepsi geri gelir (yeniden tarama gerekmez)
- Sayaç güncellenir (örn "5 / 61")
- Tarama devam ederken bile filtre korunur

Kalabalık ortamlarda (50+ ağ) belirli bir SSID'yi hızlıca bulmak için ideal.

### ↔️ Sütun Genişletme (v1.1.1 ile eklendi)

Tablo sütunlarını **kenarından sürükleyerek** genişletebilirsin. Özellikle uzun SSID veya BSSID değerleri için faydalı.

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
- **Spatial Streams** — Uzamsal akış sayısı tahmini; fiziksel anten sayısını doğrulamaz
- **Max MCS Index** — Modülasyon endex (0-11)
- **Additional** — MU-MIMO, OFDMA, BSS Coloring

#### 5. Sinyal Zamanı (Signal History)
- **Üstte büyük dBm gösterge** — 18pt, renk kodlu
- **Altında canlı grafik** — son alınan sinyal değerlerinin gösterimi
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
2. Windows uygulamasının çalıştığı dizüstü bilgisayarla farklı odalara git; her noktada yeni tarama sonucunu bekle
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
   - **Yeni sürüm var** — Sürüm bilgisi ve indirme seçeneği gösterilir
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
2. `speedtest.exe`'yi LeoNet Pro EXE'sinin bulunduğu klasörün içine kopyala
3. Uygulamayı yeniden başlat

**Alternatif:** CLI bulunmadığında sunulan manuel Cloudflare yedek testini kullan.

### ❌ Wi-Fi taraması boş çıkıyor

**Sebep 1:** WiFi adaptörü kapalı
- Windows + R → `ncpa.cpl` → WiFi adaptörünü aç

**Sebep 2:** Bilgisayar Ethernet'e bağlı, WiFi kullanmıyor
- WiFi'yi açık tut, Ethernet'i çıkarmana gerek yok

**Sebep 3:** Wi-Fi sürücüsü eski
- Üreticinin sitesinden en güncel sürücüyü yükle

### ❌ iPerf3 "unable to connect to server"

**Sebep 1:** Sunucu kapalı
- Farklı sunucu dene: `192.168.1.50` (örnek/example; kendi sunucunuzu kullanın/use your own server)

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
2. Silme işlemi yapmadan önce DB/CSV dışa aktarımıyla geçmişi yedekle; hata mesajını ve sürümü kaydet
3. En son setup'ı yeniden yükle

---

## Sıkça Sorulan Sorular

### Bu uygulama hangi verileri saklar ve hangi bağlantıları kurar?

Test geçmişi yerel bilgisayarda tutulur. Ağ işlemleri harici hizmetlere bağlanır; bu hizmetler genel IP adresiniz gibi bağlantı bilgilerini ve işlem için gereken istekleri alır. Etkinleştirilen e-posta/webhook bildirimleri, bildirim içeriğini yapılandırdığınız hedeflere gönderir.

Ağ etkinlikleri şunları kapsar:
- Testlerde Speedtest CLI (Ookla), LibreSpeed ve iPerf3 bağlantıları; etkinleştirildiğinde zamanlanmış Speedtest CLI testleri.
- Manuel yedek hız testi ve bufferbloat tanılamasında Cloudflare indirme/yükleme istekleri; tanılama sırasında DNS sağlayıcıları ve Akamai çözücü kontrolleri.
- Tanılama hedeflerine ICMP, DNS, TCP ve UDP sorguları. Kesinti izleyicisi uygulamayla birlikte otomatik başlar.
- Açılışta otomatik (başarılı kontrolden sonra günde en fazla bir kez) ve elle başlatılan GitHub güncelleme kontrolleri.
- Varsayılan olarak otomatik başlayan, Windows ve sürücü davranışına bağlı yerel Wi-Fi taraması.
- Yapılandırılıp etkinleştirilen e-posta/webhook bildirimleri.

Zamanlanmış hız testi özelliği Cloudflare yedek hız testini kullanmaz. Üçüncü taraf hizmetlerin kendi gizlilik politikaları ve kullanım koşulları geçerlidir. Arka planda hiçbir harici bağlantı kurulmadığı iddia edilmez.

### Verilerim nerede saklanıyor?

- **Veritabanı:** `%TEMP%\hiz_testleri.db` (bu sürümün kullandığı konum). Uygulamadaki DB dışa aktarımıyla yedekleyin.
- **Ayarlar:** Windows Registry üzerinden QSettings; ana anahtar `HKCU\Software\BurakAslan\LeoNetPro`. iPerf özel komut ayarları ayrıca `HKCU\Software\LeoNetPro\iperf_custom` altında tutulur. Rastgele Registry anahtarı silmeyin.
- Windows geçici klasör temizliği geçmişi silebilir. Güncelleme veya yeniden kurulumdan önce yedek alın.

### Ölçüm sınırlamaları

Bu sonuçlar tanılama tahminleridir; sertifikasyon sonucu değildir. Wi-Fi dBm değeri Windows sinyal yüzdesinden hesaplanır: `floor(sinyal_yüzdesi / 2) - 100`. Windows bildirmediğinde kanal genişliği, azami veri hızı ve radyo yetenekleri tahmin edilebilir. Bazı tahminler yıldızla işaretlenir; yıldız bulunmaması doğrudan donanım ölçümü yapıldığını kanıtlamaz. Tarama verisi gecikmeli veya önbellekten olabilir; grafiğin yenilenmesi yeni radyo örneği alındığı anlamına gelmez.

Jitter, ardışık ping gidiş-dönüş sürelerindeki değişkenliktir; RFC 3550'deki RTP hesabı değildir. DNSSEC kontrolü Cloudflare DoH yanıtının AD bayrağını okur; ISP çözücünüzün DNSSEC davranışını doğrulamaz. Çözücü IP gözlemi tek başına VPN DNS sızıntısını kanıtlamaz. MTU, bufferbloat ve kalite skoru yanıt alınmasına ve yük üretiminin başarısına bağlıdır. Eksik yanıt veya başarısız yük yanıltıcı sonuç verebilir; önemli ölçümleri tekrarlayın veya başka yöntemle karşılaştırın. PDF raporu TR-143 uygunluğunu belgelemez.

### Bu uygulamayı şirketimde kullanabilir miyim?

EULA'ya göre **ticari kullanım yasak**. Kişisel ve eğitim amaçlı kullanım serbest. Şirket içi diagnostics için kullanmak istersen yazarla iletişime geç (LinkedIn).

### Bir sürüm sonra ayarlarım gidiyor mu?

Geçmiş ve ayarların korunması kurulum/sürüm davranışına bağlıdır. Güncellemeden önce DB/CSV yedeği alın; geçici klasördeki geçmiş için kalıcılık garantisi yoktur.

### Wi-Fi taraması bilgisayara zarar verir mi?

Uygulama Windows'un yerleşik WlanScan API'siyle tarama ister. Bu işlem yalnızca pasif bir dosya okuması değildir; zamanlama ve radyo davranışı sürücüye bağlıdır.

### Birden fazla bilgisayara kurabilir miyim?

Evet — kişisel kullanım için herhangi bir sınır yok.

---

# 🇬🇧 ENGLISH

---

## v1.2.0: Adapter selection, context menu and updates

**Ping source IP:** Choose an active adapter's IPv4 address in Diagnostics → Source NIC. Automatic removes the source-IP override. Refresh after adapter changes and choose before starting a test. Supported Windows ping commands use `-S`; Windows routing and target reachability still apply. This does not bind Ookla, DNS, HTTP or iPerf traffic to that adapter. Verify the actual egress path separately when it matters.

**Context menu:** Right-click the application area for common actions, navigation and exit. Some input/table widgets may display their own native menus. The application menu uses the current language and theme.

**Language:** The ping threshold label refreshes to Alert in English and Uyarı in Turkish. This fix does not guarantee complete translation of every dynamic message or historical record.

### PySide6 and concurrent tests

- **PySide6 / Qt 6 migration:** The interface now uses PySide6 instead of PyQt5.
- **Thread lifecycle:** Running workers retain their references; application exit waits for them to finish.
- **Ping Monitor:** Start/Stop updates the button state; restarting may be briefly disabled while the worker finishes.
- **Concurrent tests:** Speedtest + Ping and iPerf3 + Ping can run together. Concurrent heavy speed tests, including custom iPerf, are blocked. The diagnostics suite includes bufferbloat and is also treated as a heavy test.

Ookla CLI controls its download/upload phase durations; a phase lasting around 5 seconds is not itself an error. iPerf3 duration is configured separately. The PySide6 migration is not a mobile release; this guide covers the Windows application.

**Updates:** GitHub HTTPS requests validate against the certifi CA bundle. Errors may be logged to `%TEMP%\LeoNetPro-update-UpdateFix4.log`; this log can contain local usernames and file paths. Review before sharing. Checking for updates does not install a release. GitHub may still report 1.1.1 before 1.2.0 is published.

## Quick Start

### First Setup (5 minutes)

1. **Install LeoNet Pro** — run `LeoNetPro_Setup_v1.2.0.exe`
2. Select **English** as the installation language
3. Select the required components. Tesseract is offered only if its installer is bundled; complete its separate installation at the end.
4. After installation, launch from the **desktop shortcut**
5. Choose language and theme in **Settings**; preferences are saved for later launches.

### Speedtest CLI Setup (for Ookla and scheduled tests)

For internet speed testing, Ookla's official CLI is needed (not bundled for legal reasons):

1. Go to https://www.speedtest.net/apps/cli
2. Download the **Windows** version (zip)
3. Extract `speedtest.exe` to the folder containing the LeoNet Pro executable
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
   - Public: an available iPerf3 server you are permitted to use
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
-c 192.168.1.50 -p 5201 -t 30 -P 4 --reverse
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
-c 192.168.1.50 -t 30 -P 4 --reverse

# Bidirectional stress (for bufferbloat)
-c 192.168.1.50 -t 30 --bidir

# UDP — packet loss / jitter
-c 192.168.1.50 -t 10 -u -b 50M

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
Connect two computers to the same LAN. Start an iPerf3 server on one and test its LAN IP from the other. This measures the path between those devices, not internet speed.

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
| **PDF Report** | PDF report generated from TR-143 test data |
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

**Run Full Diagnostics** button runs diagnostic steps sequentially:

| Test | Method | What It Tells |
|---|---|---|
| **Packet Loss** | 20× ICMP | Reliability (%) |
| **Jitter** | Consecutive ping RTT differences | Mean absolute round-trip-time variation |
| **Avg. Ping** | 20× ICMP | Round-trip average |
| **MTU Discovery** | Binary search with DF bit | Reply-dependent MTU estimate; VPN/PPPoE interpretation is heuristic |
| **Bufferbloat** | Bidirectional load + ping | A-F grade |
| **DNS Latency** | UDP × 3 | Median latency for 5 providers |
| **DNSSEC** | Cloudflare DoH AD flag | AD flag in the Cloudflare response; not ISP validation |
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
   - Packet Loss: 5% ❌
4. **Interpretation:** Latency rises under load; this result alone does not establish the cause.
5. Compare over Ethernet with the same target and inspect network load; consult device documentation before changing QoS.

---

## Wi-Fi (EN)

Fifth tab. **Deep Wi-Fi network analysis** — professional grade.

### 🔍 Scanning

**Usage:**
1. Click **Scan** (or wait for auto-scan)
2. Windows `WlanScan` API triggers — scan request; returned results may be delayed or cached
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

### 🔎 SSID Search (introduced in v1.1.1)

Type in the **🔎 Search SSID...** box in the top bar to filter the table instantly:
- Non-matching rows are hidden as you type (not deleted)
- Clearing the box restores all rows (no rescan needed)
- The counter updates (e.g. "5 / 61")
- The filter persists across scans

Ideal for quickly finding a specific SSID in crowded environments (50+ networks).

### ↔️ Column Resizing (introduced in v1.1.1)

Resize table columns by **dragging the column borders**. Useful for long SSID or BSSID values.

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
- **Spatial Streams** — Estimated spatial streams; not a verified physical antenna count
- **Max MCS Index** — Modulation index (0-11)
- **Additional** — MU-MIMO, OFDMA, BSS Coloring

#### 5. Signal History
- **Large dBm display** on top — 18 pt, color-coded
- **Live graph** below — displays the latest available signal values
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
2. Carry the Windows laptop running the app between rooms; wait for a new scan result at each location
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
   - **New version available** — Version details and download option are shown
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
2. Copy `speedtest.exe` to the folder containing the LeoNet Pro executable
3. Restart the application

**Alternative:** Use the manual Cloudflare fallback offered when the CLI is unavailable.

### ❌ Wi-Fi scan returns empty

**Cause 1:** Wi-Fi adapter is off
- Windows + R → `ncpa.cpl` → enable Wi-Fi adapter

**Cause 2:** PC is on Ethernet, not using Wi-Fi
- Keep Wi-Fi on; you don't need to unplug Ethernet

**Cause 3:** Outdated Wi-Fi driver
- Install latest driver from manufacturer's website

### ❌ iPerf3 "unable to connect to server"

**Cause 1:** Server is down
- Try different server: `192.168.1.50` (örnek/example; kendi sunucunuzu kullanın/use your own server)

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
2. Back up history with DB/CSV export before deleting anything; record the error and version
3. Reinstall latest setup

---

## FAQ

### What data is stored and which connections are made?

Test history is stored locally. Network operations contact external services, which receive connection information such as your public IP address and the requests needed to perform the operation. Enabled email and webhook alerts send notification content to the configured destinations.

Network activity includes:
- Speedtest CLI (Ookla), LibreSpeed and iPerf3 connections during tests, including scheduled Speedtest CLI tests when enabled.
- Cloudflare download/upload requests for manual fallback tests and bufferbloat diagnostics; DNS providers and Akamai resolver checks during diagnostics.
- ICMP, DNS, TCP and UDP probes to diagnostic targets. The connection outage monitor starts automatically with the application.
- GitHub Releases API requests for automatic update checks on launch (at most once daily after a successful check) and manual checks.
- Local Wi-Fi scanning, enabled automatically by default and subject to Windows/driver behavior.
- Email/webhook notifications when configured and enabled.

Cloudflare fallback speed tests are not used by the scheduled speed-test feature. Third-party services have their own privacy policies and terms. This application does not claim that no external connections occur in the background.

### Where is my data stored?

- **Database:** `%TEMP%\hiz_testleri.db`, used by this version. Use DB export to back it up.
- **Settings:** QSettings: main key `HKCU\Software\BurakAslan\LeoNetPro`; iPerf custom command settings use `HKCU\Software\LeoNetPro\iperf_custom`. Do not delete unrelated keys.
- Windows temporary-file cleanup can remove history. Back up before upgrading or reinstalling.

### Measurement limitations

These are diagnostic estimates, not certification results. Displayed Wi-Fi dBm is estimated from Windows signal quality: `floor(quality_percent / 2) - 100`. Width, maximum data rate and radio capabilities may be inferred when Windows does not report them. An asterisk marks some estimated values; its absence is not proof of a direct hardware measurement. Scan data can be delayed or cached, and chart refresh does not guarantee a new radio sample.

Jitter here is variation between consecutive ping round-trip times, not the RTP interarrival-jitter calculation in RFC 3550. The DNSSEC check reads the AD flag in a Cloudflare DoH response; it does not verify your ISP resolver's DNSSEC behavior. Resolver-IP observations alone do not prove a VPN DNS leak. MTU, bufferbloat and the quality score depend on probe replies and successful load generation. Missing replies or failed load can make results misleading; repeat or cross-check important measurements. A PDF report does not certify TR-143 compliance.

### Can I use this in my company?

According to EULA, **commercial use is prohibited**. Personal and educational use is free. For internal corporate diagnostics, contact the author (LinkedIn).

### Do I lose settings on version upgrade?

Retention depends on the installer and version. Export a DB/CSV backup before upgrading; history in the temporary folder is not guaranteed to persist.

### Does Wi-Fi scanning harm my computer?

The app requests scanning through the Windows WlanScan API. It is not merely passive file reading; timing and radio behavior depend on the driver.

### Can I install on multiple computers?

Yes — no limit for personal use.

---

## Author & Contact

**Author:** Burak Aslan
**LinkedIn:** [Burak ASLAN](https://www.linkedin.com/in/burak-aslan-/)
**GitHub:** [github.com/burakaslann/LeoNetPro](https://github.com/burakaslann/LeoNetPro)
**Version:** 1.2.0

For bug reports or feature suggestions:
[github.com/burakaslann/LeoNetPro/issues](https://github.com/burakaslann/LeoNetPro/issues)


### Bu derlemenin OCR bileşenleri / OCR components in this build

Tesseract motoru ayrıca kurulur; EasyOCR/Torch bu EXE paketinde bulunmaz. / Install Tesseract separately; EasyOCR/Torch are not included in this executable package.


### PDF ve çıkış düzeltmeleri / PDF and exit fixes

PDF raporlarında Türkçe karakterleri destekleyen gömülü DejaVu Sans kullanılır. Başlık satır aralıkları düzeltildi. Hız testi sırasında Ctrl+Q ile çıkış, çalışan Speedtest işlemini iptal eder. Tepsiye küçültme etkinse X düğmesi uygulamayı arka plana alabilir.

PDF reports embed DejaVu Sans for Turkish characters and use corrected heading spacing. Ctrl+Q cancels the active Speedtest process when exiting. With minimize-to-tray enabled, the X button may keep the application running in the tray.

