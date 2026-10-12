# Fırsat Platform — Ürün ve Teknik Plan (v0.1, taslak)

> Tarih: 12 Ekim 2026
> Hazırlayan: Claude (plan aşaması, kod yazılmadı)
> Hedef: JelMap (jelmap.com + iOS uygulaması) ile aynı işi yapan, ama daha iyi ve daha gelişmiş bir
> "iş ortaklığı / pro hizmet / bayilik ilan platformu" kurmak. İsim şimdilik **Fırsat Platform**
> (isim sonradan değişebilir; kodda marka adı tek bir config'den okunacak).

## Bu klasördeki dosyalar

| Dosya | İçerik |
|---|---|
| `00-README.md` | Bu dosya. Özet, kapsam, nasıl kullanılacağı |
| `01-jelmap-analizi.md` | JelMap'in ekran ekran, buton buton analizi + iş mantığı + eksikleri |
| `02-urun-tanimi-ve-ozellikler.md` | Fırsat Platform'un tüm özellikleri (JelMap'in aynısı + daha iyisi), kullanıcı rolleri, iş kuralları |
| `03-tasarim-sistemi.md` | Turuncu tema, Dijital Asistan arka planının uyarlaması, gece/gündüz, tipografi, bileşenler |
| `04-veritabani-semasi.md` | Tüm tablolar, alanlar, ilişkiler, index'ler, enum'lar |
| `05-api-tasarimi.md` | `firsat.sosyalplatform.com/api/v1` tüm endpoint'ler, auth, hata formatı, sürümleme |
| `06-mobil-uygulama.md` | iOS + Android uygulamasının her ekranı, akışları, state yönetimi, push, in-app purchase |
| `07-web-sitesi.md` | firsat.sosyalplatform.com sitesinin her sayfası, SEO, pSEO |
| `08-admin-paneli.md` | Mevcut admin panelinin (masaüstü "admin çalış") nasıl uyarlanacağı, tüm modüller |
| `09-altyapi-ve-deploy.md` | AlmaLinux 8 + PHP 8.3 + Laravel kurulumu, sunucu, queue, cron, yedek, güvenlik, KVKK |
| `10-yol-haritasi-ve-kodlama-sirasi.md` | Faz faz, dosya dosya kodlama sırası; düşük maliyetli ajan için talimatlar |
| `11-acik-sorular.md` | Karar vermeniz gereken sorular (kodlamaya başlamadan önce cevaplanmalı) |
| `12-ajan-brief-CLAUDE.md` | Kod yazacak ajanın proje köküne koyacağı CLAUDE.md taslağı (token tasarrufu için) |

## Tek cümlelik ürün tanımı

Fırsat Platform; ortak arayan, yatırımcı arayan, işletmesini/markasını devretmek isteyen, bayilik veren
ve profesyonel hizmet sunan kişi ve firmaların ilan verdiği, diğer kullanıcıların bu ilanları keşfedip
uygulama içi mesajlaşma ile iletişime geçtiği; gelirini **doping (öne çıkarma)**, **premium üyelik** ve
**iletişim hakkı (kontör)** satışlarından elde eden; iOS, Android ve web üzerinde çalışan bir ilan platformudur.

## Kapsam (ne yapılacak)

1. **Backend + API**: Laravel 12 (PHP 8.3), MySQL 8, Redis. Tek kod tabanı; web sitesi, API ve admin aynı projede.
2. **Web sitesi**: firsat.sosyalplatform.com (SEO uyumlu, ilan listeleme, ilan verme, mesajlaşma, üyelik, ödeme).
3. **Admin paneli**: firsat.sosyalplatform.com/admin — masaüstündeki hazır admin panelinin uyarlanması.
4. **Mobil uygulama**: iOS + Android, tek kod tabanı (öneri: Flutter — bkz. açık sorular), gece/gündüz modu.
5. **Ödeme**: Web'de iyzico (veya PayTR), uygulamada App Store / Google Play uygulama içi satın alma.
6. **Bildirim**: Firebase Cloud Messaging (push), e-posta, uygulama içi bildirim merkezi.

## Kapsam dışı (ilk sürümde yok)

- Çoklu dil (altyapı hazır olacak, sadece Türkçe yayınlanacak)
- Canlı görüntülü görüşme
- Kendi ödeme altyapısı / cüzdandan para çekme
- Web'de harita üzerinde gezinme dışında karmaşık coğrafi analiz

## Bu planın durumu ve önemli uyarılar

- Plan, **web araştırması + sizin gönderdiğiniz JelMap ana sayfa ekran görüntüsü + Dijital Asistan ekran
  görüntüsü** üzerinden hazırlandı. Bu oturum bulutta çalıştığı için Mac'inizdeki JelMap uygulamasına
  tıklayamadım, masaüstündeki "admin çalış" ve "Dijital Asistan" klasörlerini göremedim.
- Bu yüzden `01-jelmap-analizi.md` içinde **"Doğrulanmalı"** etiketli maddeler var. Bunlar uygulamada
  kendiniz kontrol edip (veya bilgisayar kullanımı açıkken bana gezdirip) netleştireceğiniz noktalar.
- `11-acik-sorular.md` cevaplanmadan kodlamaya geçilmemeli. Özellikle: mobil framework, admin panelinin
  teknolojisi, ödeme sağlayıcı ve gelir modeli kararları planın geri kalanını etkiler.

## Planı nasıl kullanacaksınız

1. Bu klasörü Mac'teki `Masaüstü/Fırsat Platform/` içine kopyalayın.
2. `11-acik-sorular.md` dosyasındaki soruları cevaplayın (dosyanın içine yazabilirsiniz).
3. Masaüstündeki `admin çalış` klasörünü ve Dijital Asistan kaynak kodunu bu repoya (veya yeni bir repoya) push edin.
   Böylece plan v0.2'de admin panel uyarlaması ve tasarım sistemi gerçek koda göre netleşir.
4. Kodlama aşamasında daha ucuz bir ajana `12-ajan-brief-CLAUDE.md` + ilgili faz dosyasını verin.
