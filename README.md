# Türkiye Yarış Takvimi Veri Seti

Türkiye'deki koşu, patika koşusu, bisiklet, yüzme ve triatlon yarışlarının açık
takvimi: yarışın adı, tarihi, mesafeleri ve kendi sayfasının adresi. Kaynak:
[Yarış Radarı](https://yarisradari.com). Her gün otomatik güncellenir.

Open race calendar for running, trail, cycling, swimming and triathlon events in
Türkiye: race name, date, distances and the address of its page. Source:
[Yarış Radarı](https://yarisradari.com), refreshed daily.

## Dosyalar

| Dosya | İçerik |
| --- | --- |
| `races.json` | Yarış başına `slug`, `name`, `start_date`, `end_date`, `page_url`, `distances_km` |
| `races.csv` | Aynı veri düz tablo hâlinde; mesafeler noktalı virgülle ayrılır |

## Kapsam

Bu set yalnızca yarışın adını, tarihini, mesafelerini ve bizdeki sayfasının
adresini verir. Tek günlük yarışlarda `end_date` başlangıçla aynıdır. Şehir,
branş, koordinat, mevki, start saati, açıklama metni, ücret, son kayıt tarihi,
kayıt ve organizatör bağlantıları, GPX dosyaları ve geçmiş sezon sonuçları
burada **yoktur**; hepsi [yarisradari.com](https://yarisradari.com)
üzerinde ve [yarış API'sinde](https://yarisradari.com/yaris-api) durur. Her
yarışın `page_url` alanı kendi sayfasına gider.

Kişisel veri yoktur.

## Lisans

CC BY 4.0. Kullanabilirsin, ama kaynak olarak
[yarisradari.com](https://yarisradari.com) adresini göstermen gerekir.
