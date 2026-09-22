# LeoNet Pro v1.2.0 â€” Third-party notices / ÃœÃ§Ã¼ncÃ¼ taraf bildirimleri

## PySide6, Shiboken6 and Qt 6

LeoNet Pro uses PySide6 with QtCore, QtGui and QtWidgets. The source review environment used PySide6 6.11.2. The application remains proprietary; LGPL rights in covered libraries are not restricted by its EULA. The GNU LGPL v3 is the selected license for the LGPL-covered components; this is not a claim that all Qt modules have that license.

LeoNet Pro, QtCore, QtGui ve QtWidgets ile PySide6 kullanÄ±r. Kaynak inceleme ortamÄ± PySide6 6.11.2 kullanmÄ±ÅŸtÄ±r. Uygulama kapalÄ± kaynaklÄ± kalÄ±r; kapsanan kÃ¼tÃ¼phanelerin LGPL haklarÄ± EULA ile kÄ±sÄ±tlanmaz. LGPL kapsamÄ±ndaki bileÅŸenler iÃ§in GNU LGPL v3 seÃ§ilmiÅŸtir; tÃ¼m Qt modÃ¼llerinin bu lisansa sahip olduÄŸu iddia edilmez.

The final distribution must retain copyright notices, GNU GPL v3 and LGPL v3 texts, and the notices for its actual Qt plugins and dependencies. Recipients must be able to use compatible modified LGPL libraries as required by the license. Source and any required installation/relinking information must be provided through the applicable license's distribution mechanism. An upstream homepage link alone is not a complete source-distribution mechanism.

Final daÄŸÄ±tÄ±m telif bildirimlerini, GNU GPL v3 ve LGPL v3 metinlerini, kullanÄ±lan Qt eklentilerinin ve baÄŸÄ±mlÄ±lÄ±klarÄ±n bildirimlerini korumalÄ±dÄ±r. AlÄ±cÄ±larÄ±n lisansÄ±n gerektirdiÄŸi ÅŸekilde uyumlu deÄŸiÅŸtirilmiÅŸ LGPL kÃ¼tÃ¼phanelerini kullanabilmesi gerekir. Kaynak ve gerekli kurulum/yeniden baÄŸlama bilgileri lisansÄ±n daÄŸÄ±tÄ±m yÃ¶ntemine uygun saÄŸlanmalÄ±dÄ±r. Tek baÅŸÄ±na proje ana sayfasÄ± baÄŸlantÄ±sÄ± kaynak daÄŸÄ±tÄ±mÄ±nÄ± tamamlamaz.

References: [Qt for Python](https://doc.qt.io/qtforpython-6/), [Qt licensing](https://doc.qt.io/qt-6/licensing.html), [LGPL v3](https://www.gnu.org/licenses/lgpl-3.0.html).

## Other components / DiÄŸer bileÅŸenler

See LICENSE.txt for Python, iPerf3, Cygwin-related distribution notes, OCR libraries and external services. The existing Cygwin source archive covers Cygwin 3.6.7-1 only; it does not cover Qt or PySide6. iPerf3's actual distribution license must be retained; it is not replaced with an Apache license.

Python, iPerf3, OCR kÃ¼tÃ¼phaneleri ve harici hizmetler iÃ§in LICENSE.txt dosyasÄ±na bakÄ±n. Mevcut Cygwin kaynak arÅŸivi yalnÄ±zca Cygwin 3.6.7-1 iÃ§indir; Qt veya PySide6 kaynaklarÄ±nÄ± kapsamaz. iPerf3 daÄŸÄ±tÄ±mÄ±nÄ±n gerÃ§ek lisansÄ± korunmalÄ±dÄ±r; Apache lisansÄ± ile deÄŸiÅŸtirilmez.

## Included distribution material / Paketteki dağıtım malzemesi

This package provides source archives in `sources/`: PySide6/Shiboken6 6.11.2, qtbase 6.11.2, qtsvg 6.11.2, qtimageformats 6.11.2 and Cygwin 3.6.7-1. Source URLs and locally computed SHA256 values for Qt downloads are in `sources/PROVENANCE.json`. Upstream build scripts remain in the original archives. Unmodified upstream libraries are used.

`licenses/` contains GPL v3/LGPL v3 texts, Qt source copyright/license materials and Python-package notices. `LIBRARY-REPLACEMENT.txt` explains how to run with compatible modified shared libraries. Qt VirtualKeyboard, Qt PDF, QML and Quick are excluded from the application package; they are not needed by this Widgets UI.

Bu pakette `sources/` altında PySide6/Shiboken6 6.11.2, qtbase/qtsvg/qtimageformats 6.11.2 ve Cygwin 3.6.7-1 kaynakları bulunur. Qt indirme adresleri ve yerelde hesaplanan SHA256 değerleri `sources/PROVENANCE.json` içindedir. Kaynakların özgün derleme betikleri arşivlerde korunmuştur. Değiştirilmemiş upstream kütüphaneler kullanılır.

`licenses/` GPL v3/LGPL v3 metinleri, Qt lisans/telif malzemeleri ve Python paket bildirimlerini içerir. Uyumlu değiştirilmiş kütüphanelerle çalıştırma `LIBRARY-REPLACEMENT.txt` içinde açıklanır. Kullanılmayan Qt VirtualKeyboard, Qt PDF, QML ve Quick uygulama paketine dahil edilmez.

The optional Tesseract installer is bundled and opens as a separate installation step. Ookla Speedtest CLI is obtained separately from its vendor. EasyOCR/Torch are optional source-mode fallbacks and are not included in this build; OCR in this package uses separately installed Tesseract.

İsteğe bağlı Tesseract yükleyicisi pakete dahildir ve ayrı kurulum adımı olarak açılır. Ookla Speedtest CLI kendi sağlayıcısından ayrıca alınır. EasyOCR/Torch bu derlemeye dahil değildir; paketteki OCR ayrı kurulan Tesseract'ı kullanır.

