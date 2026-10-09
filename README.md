# Oficjalna strona Technix-Pro

Jednoplikowa, responsywna strona projektu Technix-Pro. Interfejs, style i skrypty znajdują się w `index.html`; projekt nie wymaga instalowania zależności, nie korzysta z cookies ani narzędzi analitycznych.

## Pliki

- `index.html` – strona główna, sekcje, style i skrypty.
- `404.html` – samodzielna strona błędu dla hostingu statycznego.
- `assets/technix-pro-logo.svg`, `assets/technix-pro-token.svg` – grafiki projektu.
- `assets/og-image.svg` – grafika podglądu udostępniania.
- `site.webmanifest` – metadane instalacji strony.
- `CHANGELOG.md` – zestawienie etapów zmian.

## Uruchomienie lokalne

W katalogu repozytorium uruchom:

```sh
python3 -m http.server 8000
```

Otwórz `http://localhost:8000`. Serwer statyczny nie jest wymagany do podglądu HTML, ale umożliwia sprawdzenie ścieżek zasobów.

## Konfiguracja treści

W skrypcie na końcu `index.html`:

- `MINI_APP_LAUNCH_DATE` pozostaw pusty, dopóki data premiery nie zostanie oficjalnie potwierdzona. Aby włączyć odliczanie, wpisz datę ISO 8601, np. `2026-12-01T18:00:00+01:00`.
- W obiekcie `LINKS` ustaw potwierdzone adresy kanałów. Każdy adres musi zaczynać się od `https://`. `tiktok` pozostaje pusty do czasu potwierdzenia linku; po jego uzupełnieniu karta TikTok stanie się aktywna.

Roadmapę aktualizuj w sekcji `#roadmapa`: klasę `done` stosuj dla ukończonych etapów, `now` dla aktualnie realizowanego, a elementom listy `.ck` przypisuj `ok` lub `wip` zgodnie ze stanem prac. Nie publikuj niepotwierdzonych dat ani obietnic.

Nowe pytanie FAQ dodaj w sekcji `#faq` jako kolejne `<details>` z nagłówkiem `<summary>` i odpowiedzią w `<p>`. Wyszukiwarka korzysta z tekstu tych elementów.

## Publikacja, SEO i zadania właściciela

Repozytorium nie zawiera obecnie potwierdzonego adresu witryny, `CNAME` ani konfiguracji GitHub Pages. Dlatego nie wpisano zgadywanego adresu canonical, `og:url`, absolutnego URL-a grafiki, `robots.txt` ani `sitemap.xml`. Po ustaleniu domeny:

1. Uzupełnij `link rel="canonical"`, `og:url` i absolutne adresy `og:image`/`twitter:image` w `<head>` pliku `index.html`.
2. Zastąp `assets/og-image.svg` obrazem PNG o wymiarach 1200×630, jeśli wymagają tego portale społecznościowe, i zaktualizuj metadane.
3. Utwórz `robots.txt` z `User-agent: *` oraz `Allow: /`; dodaj `Sitemap: https://POTWIERDZONA-DOMENA/sitemap.xml` dopiero po potwierdzeniu domeny.
4. Utwórz `sitemap.xml` z jedną pozycją dla potwierdzonego adresu strony głównej.

Przykładowa zawartość `robots.txt` po podmianie placeholdera:

```text
User-agent: *
Allow: /
Sitemap: https://POTWIERDZONA-DOMENA/sitemap.xml
```

Szablon `sitemap.xml` (zastąp adres potwierdzoną domeną):

```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url><loc>https://POTWIERDZONA-DOMENA/</loc></url>
</urlset>
```

Do uzupełnienia lub zatwierdzenia przez właściciela:

- adres publikacji i domena canonical;
- docelowy obraz OG PNG (jeśli portale nie obsłużą SVG);
- oficjalna data premiery mini-aplikacji;
- potwierdzony link TikTok;
- zweryfikowane szczegóły integracji i współpracy z EngineCore;
- ewentualne dane do wsparcia finansowego, wyłącznie po ich potwierdzeniu i publikacji oficjalnym kanałem.

Konfiguracji GitHub Actions ani Pages nie wykryto w repozytorium; publikacja powinna pozostać statyczna i nie wymaga procesu budowania.
