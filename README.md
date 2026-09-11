# Türkiye Yarış Takvimi Veri Seti

Türkiye'deki koşu, patika koşusu, bisiklet, yüzme ve triatlon yarışlarının açık veri seti. Kaynak: [Yarış Radarı](https://yarisradari.com). Veriler her gün otomatik güncellenir.

Open dataset of running, trail, cycling, swimming and triathlon races in Türkiye. Source: [Yarış Radarı](https://yarisradari.com), refreshed daily.

## Dosyalar

| Dosya | İçerik |
| --- | --- |
| `races.json` | Yarışların tamamı; parkurlar, kayıt dönemleri, açıklamalar ve koordinatlar dahil |
| `races.csv` | Yarış başına tek satır özet (tarih, şehir, branş, en kısa ve en uzun parkur) |
| `distances.csv` | Parkur başına tek satır (mesafe, yükseklik kazancı, ITRA puanı, ücret, GPX bağlantısı) |
| `results.json` | Geçmiş sezonların toplu sonuçları; parkur başına bitiren, bırakan ve derece yüzdelikleri, kontrol noktası geçişleri |
| `results.csv` | Sonuçların düz tablo hali |

Kişisel veri yoktur: sonuç dosyaları yalnızca toplu sayılar ve süre yüzdelikleri içerir, katılımcı adı veya derecesi barındırmaz.

## Alanlar

`races.json` içindeki her yarış:

- `slug`, `name`, `sport`, `status`, `city`, `venue`, `country_code`
- `start_date`, `end_date`, `start_time`, `latitude`, `longitude`
- `website_url`, `instagram_url`, `results_url`, `photos_url`, `page_url`
- `description_tr`, `description_en`, `updated_at`
- `distances[]`: `label`, `distance_km`, `elevation_gain_m`, `itra_points`, `price`, `currency`, `swim_km`, `bike_km`, `run_km`, `start_time`, `surface_note`, `gpx_url`
- `registration[]`: `kind`, `opens_at`, `closes_at`, `price`, `currency`, `url`

`results.json` içindeki her parkur sezonu:

- `race_slug`, `edition_year`, `course_label`, `distance_km`, `event_date`
- `registered`, `starters`, `finishers`, `dnf`
- `fastest_seconds`, `slowest_seconds`, `p10_seconds`, `p25_seconds`, `p50_seconds`, `p75_seconds`, `p90_seconds`
- `checkpoints[]`: `position`, `name`, `km`, `passed`, `dropouts`, `median_seconds`
- `source_url`: sonuçların alındığı zamanlama sayfası

Süreler saniye cinsindendir. `sport` değerleri: `road_run`, `trail_run`, `cycling`, `swimming`, `triathlon`, `duathlon`, `hyrox`, `orienteering`.

## Veri nereden geliyor

Türkiye Atletizm Federasyonu ve Türkiye Triatlon Federasyonu takvimleri, PassTiming ve Plustimer zamanlama sayfaları, HYROX ve UTMB World Series listeleri, G-Live sonuç dosyaları ve yarışların resmi siteleri. Her kayıt yayından önce kaynağıyla eşleştirilir; elle doğrulanan kayıtlar otomatik güncellemeye kapatılır.

Bilgiler değişebilir. Kayıt yapmadan önce yarışın resmi kaynağından teyit edin.

## Kullanım

```python
import json, urllib.request

url = "https://raw.githubusercontent.com/alparslandev/turkiye-yaris-takvimi/main/races.json"
races = json.load(urllib.request.urlopen(url))["races"]
trail = [race for race in races if race["sport"] == "trail_run"]
print(len(trail), "patika koşusu")
```

## Lisans

[CC BY 4.0](LICENSE). Kullanabilir, dağıtabilir ve ticari işlerde kullanabilirsiniz; tek şart kaynak göstermek:

> Kaynak: [Yarış Radarı](https://yarisradari.com)
