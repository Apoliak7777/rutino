# rutino.online

Predajná stránka služby **Rutino**: malý program na mieru pre jeden opakovaný firemný proces
(cenové ponuky, faktúry do tabuľky, evidencia namiesto Excelu). Pevná cena, ukážka na dátach
klienta zadarmo, hotové do desiatich dní.

Statický web bez buildu a bez závislostí. Beží na GitHub Pages, doména `rutino.online`
(súbor `CNAME`).

## Čo tu je

| Cesta | Čo to je |
|---|---|
| `index.html` | hlavná stránka, CSS aj skript sú v súbore (kalkulačka návratnosti, objavovanie sekcií, lepiaci pás na mobile) |
| `ukazky/ponukovac/` | ukážková toolka 1: cenová ponuka z vlastného cenníka, PDF cez tlač prehliadača, mail zákazníkovi |
| `ukazky/papiere/` | ukážková toolka 2: PDF faktúry do tabuľky (pdf.js v `pdfjs/`, Apache 2.0), vzorové faktúry vo `vzory/` |
| `ukazky/evidencia/` | ukážková toolka 3: evidencia zákaziek, tabuľka a nástenka, strop 12 zákaziek |
| `obrazky/` | náhľady ukážok pre hlavnú stránku (1280 × 800 JPEG) |
| `fonts/` | Newsreader 500 a Manrope, hostované tu, aby stránka nevolala Google Fonts |
| `og-image.png` | obrázok pre zdieľanie (1200 × 630) |
| `ochrana-udajov.html`, `404.html`, `robots.txt`, `sitemap.xml` | podporné stránky |

## Pravidlá stránky

- **Žiadny cudzí skript, písmo ani cookie.** Stránka to o sebe tvrdí v pätičke, preto sem nepatrí
  analytika ani widgety.
- **Ukážky predvádzajú, nenahrádzajú toolku.** Nič neukladajú, Ponukovač má pevnú vymyslenú firmu a PDF
  s vodoznakom UKÁŽKA, Papiere nemajú export a berú 2 vlastné PDF, Evidencia nemá tlač ani export a má strop 12 zákaziek.
- **Žiadny kontaktný formulár.** Kontakt je adresa veľkým písmom a `mailto:` s predvyplneným
  predmetom. Formulár cez `mailto:` nefunguje ľuďom s poštou v prehliadači.
- **Referencie sa nevymýšľajú.** Namiesto nich sú tri funkčné ukážky.
- Ukážky majú `noindex` a sú v `robots.txt` zakázané, aby Google neindexoval vymyslené firmy.

## Kontaktná adresa

Všetky `mailto:` odkazy vedú na `info@rutino.online` (schránka na Hostingeri od 14.09.2026).

## Lokálny náhľad

```
python -m http.server 8097 --bind 127.0.0.1 --directory .
```

a otvoriť `http://127.0.0.1:8097/`. Ukážka „Papiere do tabuľky“ potrebuje server (pdf.js sa načítava
ako modul), z `file://` nejde.

## Generátory (mimo repozitára, v `..\_PRACA\`)

- `faktury_ukazka.py` vyrobí tri vzorové faktúry do `ukazky/papiere/vzory/`
- `og_obrazok.py` vyrobí `og-image.png`
- `nahlady.js` vyrobí náhľady ukážok do `obrazky/`, s parametrom `kontrola` aj screenshoty stránky
- `sekcie.js` vyrobí screenshoty jednotlivých sekcií vo veľkosti okna

## Nasadenie

Push do `main` mení živý web do dvoch minút. DNS u Hostingera: A záznamy apexu na GitHub Pages
(185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153), `www` ako CNAME na
`apoliak7777.github.io`, v Settings → Pages custom domain `rutino.online` a vynútené HTTPS.
