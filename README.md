# Horský deník – blog o turistice

Školní projekt: statický frontend (HTML5 + CSS), téma **tematický blog** o turistice po českých horách. Vizuální styl: Flat design.

**Autor:** Adam Rosenberger

## Struktura projektu

```
index.html      – domovská stránka
detail.html     – detail článku (Výstup na Sněžku)
kontakt.html    – o nás a kontakty
css/style.css   – styly
img/            – obrázky (logo.svg + obrázky ve WEBP ve 3 velikostech)
```

## Checklist splněných požadavků

### Struktura webu
| Požadavek | Kde je splněno |
|---|---|
| 3 navigovatelné stránky | index.html, detail.html, kontakt.html |
| Představení projektu na domovské stránce | index.html, ř. 32–39 (`section.uvod`) |
| Náhledy nejnovějších článků v mřížce | index.html, ř. 42–94 |
| První náhled vede na detail, ostatní placeholder | index.html, ř. 48–55 (odkaz na detail.html), ř. 58–91 placeholdery |
| Dlouhý text rozdělený do sekcí | detail.html, ř. 53–167 (6× `<section>`) |
| `<aside>` s glosářem a parametry trasy | detail.html, ř. 174–200 |
| Zdroj textu uveden na konci článku | detail.html, ř. 169 |
| Stránka Info / Kontakty | kontakt.html, ř. 30–59 |
| Hlavní navigace na každé stránce | index.html ř. 20–26, detail.html ř. 19–25, kontakt.html ř. 19–25 |
| Patička se jménem, IČO a mapou webu | index.html ř. 99–108, detail.html ř. 205–214, kontakt.html ř. 63–72 |

### Sémantické HTML
| Tag | Kde je použit |
|---|---|
| `<header>` | ř. 11–12 na všech stránkách |
| `<nav>` | ř. 19–20 na všech stránkách |
| `<main>` | index.html ř. 29, detail.html ř. 28, kontakt.html ř. 28 |
| `<footer>` | index.html ř. 99, detail.html ř. 205, kontakt.html ř. 63 |
| `<section>` | index.html ř. 32, 42; detail.html ř. 53, 69, 94, 112, 136, 160; kontakt.html ř. 30, 39, 51 |
| `<article>` | index.html ř. 48–86 (karty článků); detail.html ř. 32 (celý článek) |
| `<aside>` | detail.html ř. 174 |

### Mikrosémantika
| Tag | Kde je použit |
|---|---|
| `<time>` | index.html ř. 53, 61, 68, 75, 82, 89; detail.html ř. 40; kontakt.html ř. 33 |
| `<hgroup>` | v hlavičce všech stránek (ř. 14–15); detail.html ř. 34 (nadpis + podtitulek článku) |
| `<address>` | kontakt.html ř. 41 |
| `<abbr>` | patička všech stránek (IČO); detail.html ř. 140 (HS), ř. 189 (KRNAP) |
| `<mark>` | detail.html ř. 57 |
| `<figure>`, `<figcaption>`, `<dl>` | detail.html ř. 45, 79, 103, 127, 146; `<dl>` ř. 176 |

### Multimédia a obrázky
| Požadavek | Kde je splněno |
|---|---|
| `<iframe>` | kontakt.html ř. 54–58 (mapa z OpenStreetMap) |
| SVG obrázek | img/logo.svg, vloženo ř. 13–14 na všech stránkách |
| Rastrové obrázky jen WEBP/AVIF | všechny obrázky ve složce img/ jsou `.webp` |
| 5 obrázků se `srcset` na detailu | detail.html ř. 47, 81, 105, 129, 148 (každý ve 3 velikostech 400w/800w/1200w) |

## Zdroje fotografií

Fotografie jsou převzaté z internetu a převedené do formátu WEBP ve třech velikostech: 

## Wireframe

Wireframe domovské stránky je nakreslený ručně na papíře: `wireframe.jpg` 

## Použití AI

Při tvorbě projektu jsem používal AI (Claude) jako konzultanta a mentora pro pokročilejší techniky. 

**S čím vším mi AI pomáhala:**
1. **Responzivní obrázky a `srcset`:** Pomohla mi správně sestavit syntaxi atributu `srcset` a `sizes` pro 5 obrázků na detailu článku ve třech různých velikostech (`400w`, `800w`, `1200w`)
2. **Mikrosémantika a struktura tagů:** Konzultoval jsem s ní správné vnoření tagů jako `<hgroup>`, `<aside>` a mikrosémantických prvků (`<abbr>`, `<mark>`, `<time datetime="...">`)
3. **CSS layout (Grid & Flexbox):** Pomohla mi navrhnout responzivní mřížku pro karty článků na domovské stránce pomocí `display: grid` s funkcí `minmax()`

**Proč:** Chtěl jsem mít jistotu, že HTML struktura bude plně sémantická a bez chyb.

**Vysvětlení kódu:**

- **Hlavička (`<header>`)** obsahuje logo (SVG) a `<hgroup>`, který spojuje hlavní nadpis `<h1>` s podtitulkem `<p>`. Tím je jasné, že podtitulek patří k nadpisu a není to samostatný odstavec.
- **`<nav>`** obsahuje seznam `<ul>` s odkazy na všechny stránky. Navigace je seznam, protože jde o výčet položek.
- **`<main>`** obaluje hlavní obsah, který je na každé stránce jiný. Na stránce smí být jen jeden.
- **`<section>`** dělí obsah na tematické části. Každá sekce má vlastní nadpis.
- **`<article>`** je samostatný obsah, který dává smysl i vytržený ze stránky. Proto je článkem každá karta na úvodní stránce i celý článek na detailu.
- **`<aside>`** je doplňkový obsah vedle článku. Glosář a parametry trasy s článkem souvisí, ale nejsou jeho hlavní částí.
- **`<time datetime="...">`** zobrazí datum lidsky („2. listopadu 2026“), ale v atributu `datetime` je ve strojovém formátu, kterému rozumí prohlížeč a vyhledávače.
- **`<address>`** označuje kontaktní údaje. **`<abbr title="...">`** vysvětluje zkratku, při najetí myší se ukáže celý název. **`<mark>`** zvýrazňuje důležitý text.
- **`<figure>` a `<figcaption>`** spojují obrázek s jeho popiskem.
- **`<dl>`, `<dt>`, `<dd>`** je seznam definic, hodí se na glosář (pojem a vysvětlení).
- **`srcset` a `sizes`**: `srcset` nabízí prohlížeči tři velikosti obrázku (400, 800 a 1200 px). `sizes` říká, jak široký bude obrázek na stránce (na mobilu celá šířka, jinak 700 px). Prohlížeč si podle toho stáhne nejmenší obrázek, který stačí, a šetří data.
- **WEBP** je moderní formát, který má menší velikost souboru než JPG při stejné kvalitě.
- **`<iframe>`** vkládá cizí stránku, tady mapu z OpenStreetMap. `loading="lazy"` znamená, že se načte až když k ní uživatel doscrolluje, a `title` je kvůli čtečkám obrazovky.
- **CSS**: mřížka článků je `display: grid` s `repeat(auto-fill, minmax(250px, 1fr))`, takže se sloupce samy přizpůsobí šířce obrazovky. Článek a aside jsou vedle sebe přes `display: flex` a pomocí `@media (max-width: 700px)` se na mobilu dají pod sebe.
