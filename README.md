# Türkiye Vegan / Vejetaryen Mekan Haritası

Vegan, vejetaryen ve vegan dostu mekanları il bazında listeleyen,
renk kodlu ve aranabilir interaktif harita.

## Yapı

```
index.html               -> Harita sayfası (Leaflet)
data/vegan_mekanlar.json -> Düz JSON (ad, il, ilce, tur, lat, lng, adres, telefon, not)
data/vegan_mekanlar.geojson -> Aynı veri, GeoJSON FeatureCollection formatında
```

## GitHub Pages ile yayınlama

1. Bu klasörün içeriğini bir GitHub reposuna push edin (repo kökü bu klasör olacak şekilde).
2. Repo > Settings > Pages > "Deploy from a branch" seçin, branch olarak `main` ve klasör
   olarak `/ (root)` işaretleyip kaydedin.
3. Birkaç dakika sonra `https://<kullanici-adi>.github.io/<repo-adi>/` adresinden erişilebilir olur.

## Yeni il/mekan eklemek

`data/vegan_mekanlar.json` dosyasına aynı alan yapısıyla (id, ad, il, ilce, tur, lat, lng,
adres, telefon, not, kaynak, eklenme) yeni kayıtlar ekleyip push etmek yeterli — `index.html`
dosyasına dokunmaya gerek yok, sayfa veriyi her yüklendiğinde bu dosyadan fetch eder.

`tur` alanı şu üç değerden birini almalı: `vegan`, `vejetaryen`, `vegan dostu`.

## Yerelde önizleme

Tarayıcılar `file://` üzerinden açılan sayfalarda `fetch()` isteklerini engelleyebildiği için
dosyaya çift tıklamak yerine basit bir yerel sunucu ile açın:

```bash
python3 -m http.server 8000
# sonra tarayıcıda http://localhost:8000 adresini açın
```
