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

## Google Analytics

Site, GA4 Ölçüm Kimliği `G-E11YLKMDJE` ile Google Analytics'e bağlıdır (`index.html`
`<head>` içindeki `gtag.js` kodu). Ziyaretçi verilerini
[analytics.google.com](https://analytics.google.com) üzerinden görebilirsiniz.
ID'yi değiştirmek isterseniz `index.html` içindeki iki `G-E11YLKMDJE` geçen yeri güncelleyin.

## SEO (Arama motorlarında görünürlük)

- `index.html` içine meta description, Open Graph, Twitter Card ve WebSite JSON-LD
  yapısal verisi eklendi. Hepsi `https://ipapila.github.io/vegan-harita/` canonical
  adresini kullanıyor — repo adı veya domain değişirse bu adresi `index.html`,
  `robots.txt` ve `sitemap.xml` içinde güncelleyin.
- `robots.txt` ve `sitemap.xml` site kökünde yer alır, GitHub Pages'te otomatik
  erişilebilir olurlar (`/robots.txt`, `/sitemap.xml`).
- Yayınladıktan sonra [Google Search Console](https://search.google.com/search-console)'a
  girip mülk olarak `https://ipapila.github.io/vegan-harita/` adresini ekleyin, sahipliği
  doğrulayın (HTML dosyası ya da DNS ile) ve **Sitemaps** bölümünden `sitemap.xml`'i
  gönderin. Bu, Google'ın siteyi taramasını hızlandırır.
- Aramalarda öne çıkmak için düzenli olarak yeni mekan eklemek (taze içerik),
  sayfanın hızlı yüklenmesi (zaten statik/hafif) ve başka vegan/vejetaryen
  sitelerden bağlantı almak (backlink) en etkili yöntemlerdir.

## Yerelde önizleme

Tarayıcılar `file://` üzerinden açılan sayfalarda `fetch()` isteklerini engelleyebildiği için
dosyaya çift tıklamak yerine basit bir yerel sunucu ile açın:

```bash
python3 -m http.server 8000
# sonra tarayıcıda http://localhost:8000 adresini açın
```
