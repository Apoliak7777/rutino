# rutino.online

Predajná stránka služby **Rutino**: program na mieru pre jednu prácu, ktorú malá firma robí stále dookola
(cenové ponuky, faktúry z PDF do tabuľky, zákazky namiesto Excelu, prípadne niečo iné). Pevná cena od 490 €,
hotové do 10 dní od zálohy.

Statický web bez buildu a bez závislostí. Beží na GitHub Pages, doména `rutino.online` (súbor `CNAME`).

## Vzhľad: farba (od 27.10.2026)

Každý program má svoju farbu a tá znamená vždy to isté: v páse na prvej obrazovke, v kalkulačke, v cenníku,
v skladačke mailu aj v hlavičke ukážky. Pozadie stránky je čisto biele, zvyšok nesie typografia a skutočné
snímky programov. Zadanie, podľa ktorého vzhľad vznikol, je v `..\_PRACA\navrhy2\STAVBA.md`.

**Farby** (premenné v `:root` hlavnej stránky; kontrast textu na ploche podľa WCAG):

| Čo | Plocha | Text na ploche | Jemný tón | Kontrast |
|---|---|---|---|---|
| Rutino, Alex, kontakt | zelená `#0B6A3D` (hover `#08552F`) | biela `#FFFFFF` | `#E3F0E8` | 6,7 : 1 |
| Ponukovač | staroružová `#D9A3AE` | vínová `#4E0F2C` | `#F8E1E8` | 6,9 : 1 |
| Papiere do tabuľky | nebeská `#93CDEE` | tmavomodrá `#0A2E50` | `#E2F2FB` | 8,0 : 1 |
| Evidencia | marhuľová `#F2B98C` | hnedá `#4A2108` | `#FCE8D8` | 8,0 : 1 |
| niečo iné, textové časti | biela `#FFFFFF` | `#12251A` (menej dôležitý text `#4E5B53`) | linky `#D5DBD7` | 16 : 1 |

Plné farby sú na pásoch, v cenníku a pri vybranej voľbe v mailu, jemné tóny na ploche kalkulačky a v ukážkach.
Zaoblenie je všade rovnaké, 3 px (`--r`). Žiadne tiene, prechody farieb, sklo, šum, ikony ani emoji.

**Písma:** Funnel Display (nadpisy, slová v pásoch, ceny, veľké časy v postupe; malými písmenami ako veta,
váha 500) a Funnel Sans (text, tlačidlá, polia, čísla v tabuľkách). Obe SIL OFL 1.1, lokálne vo `fonts/`,
rozdelené na latin a latin-ext cez `unicode-range`, štyri súbory sa prednačítavajú. Čísla v cenách a výpočtoch
majú `tabular-nums`. Žiadne mono písmo, verzálky ani úzke rezy, ani v ukážkach a PDF.

Stránka zhora nadol:

- **Hlavička:** značka „rutino“ zelenou, navigácia (Ukážky, Návratnosť, Postup, Cenník, Otázky; pod 1000 px
  skrytá) a tlačidlo Napíšte mi.
- **Prvá obrazovka je voľba, nie delený hero.** Nadpis cez celú šírku „Napíšem vám program na prácu, ktorú robíte
  stále dookola.“, pod ním jedna veta od Alexa (od 490 €, do 10 dní) a hneď štyri farebné pásy: cenové ponuky
  (490 €), faktúry z PDF (690 €), zákazky v Exceli (990 €), niečo iné (490 až 990 €, biely pás s linkami).
  Každý pás má veľké slovo malými písmenami, cenu a vetu v reči zákazníka („Píšete ich ručne vo Worde alebo
  v Exceli.“). Od 1000 px má zatvorený pás vpravo okno do programu (`*-nahlad.webp`, výrez skutočnej ukážky
  takmer v skutočnej veľkosti), ktoré sedí na spodnej hrane pásu. Pod 1000 px je pod pásmi horná časť PDF
  ponuky (`ponukovac-pdf-hore.webp`), aby aj ten, kto neklikne, videl skutočný výstup programu.
- **Klik pás otvorí na mieste**, priamo pod jeho hlavičkou, a naraz je otvorený najviac jeden. V otvorenom páse
  je snímka dokladu a programu (odkaz na bežiacu ukážku), dve vety o tom, čo program robí, rozpis platby
  (polovica pri objednávke, polovica pri odovzdaní, pri Evidencii aj server na prvý rok), termín s dátumom
  „keby ste zálohu poslali dnes“ a tlačidlá Vyskúšať ukážku a Napíšte mi o Ponukovači / o Papieroch do tabuľky /
  o Evidencii / o svojej práci. Pás „niečo iné“ má namiesto snímok príklady prác, klik na príklad ho vloží do mailu.
  Klik na pás zároveň nastaví cenu v kalkulačke a program v maile. Bez JavaScriptu sú všetky pásy otvorené.
  Adresa `?co=ponuky|faktury|zakazky|ine` otvorí príslušný pás, posunie stránku naň (okrem prvého pásu a návratu
  na `#kontakt`) a predvyplní mail. Pod pásmi je jedna veta o troch vymyslených firmách z ukážok.
- **Kalkulačka návratnosti je veta.** Nadpis „Spočítajte si, kedy sa vám program zaplatí“, vstupy sú polia priamo
  vo vete („Jedna ponuka nám zaberie 40 minút a týždenne ich je 15. Hodina práce nás stojí 18 € a program 490 €.“),
  pod ňou rýchla voľba cien (490, 690, 990, ďalší 390). Výsledok sú dve vety („Mesačne ušetríte asi 39 hodín,
  teda 701 €. Program za 490 € sa vám zaplatí za 4 týždne.“), vzorec je drobným písmom pod nimi. Plocha sa
  zafarbí jemným tónom programu, ktorého cenu počítate; pri inej cene a pri „Niečo iné“ je zelená. Vzorec:
  hodiny mesačne = min × počet × 4,33 / 60 × 0,9; eurá = hodiny × sadzba; týždne = cena / (eurá / 4,33).
  Tlačidlo Poslať mi tieto čísla vloží čísla do mailu a pri každej zmene kalkulačky sa v mailu prepíšu.
- **Postup:** veľké zelené časy „dnes / do 24 hodín / do 10 dní / pri odovzdaní“ a vedľa nich veta, bez čísiel
  krokov. Pod tým **Čo máte istené** (cena v zmluve sa nemení, druhá polovica až pri odovzdaní, program
  aj zdrojový kód sú vaše).
- **Cenník:** riadky vo farbách programov s rozpisom platby a sumou, pod nimi biele riadky: server pre Evidenciu
  (5 € mesačne, 60 € ročne), iná vec (490 až 990 €), ďalší program (390 €), úprava alebo nová funkcia (od 90 €).
- **Kto to robí** na zelenej ploche: pár viet od Alexa v prvej osobe a podpis s adresou; vedľa krátko a samostatne
  **Čo nerobím** (weby, e-shopy, appky do obchodov, účtovníctvo, veľké systémy, chatboty, jednorazové veci).
- **Otázky** ako obyčajný text, otázka a pod ňou odpoveď, bez akordeónu. Tie isté otázky sú v JSON-LD `FAQPage`.
- **Kontakt je skladačka mailu** na zelenej ploche (podrobne v pravidlách nižšie). Voľby sú riadky, nie mriežka
  rámčekov; vybraný riadok „O čo ide“ sa zafarbí farbou programu, ostatné vybrané riadky sú biele. Náhľad mailu
  je biela karta, riadok, ktorý v ňom pribudol, sa na chvíľu podsvieti. Na konci podpis „Odpíšem vám do 24 hodín.
  Alex“.
- **Lepiaci pás na mobile** (do 899 px): zelený pás dole s textom „Program od 490 €“ (po výbere programu napríklad
  „Ponukovač za 490 €“) a tlačidlom Napíšte mi. Na prvej obrazovke a v kontakte je skrytý.
- **Pätička** biela: značka, odkazy, adresa, ochrana údajov a veta, že stránka nenačítava cudzie skripty, písma
  ani cookies.
- **Pohyb** je len tam, kde niečo vysvetľuje: otvorenie pásu, zmena farby kalkulačky, nový riadok v maile,
  lepiaci pás. Pri `prefers-reduced-motion` sa vypne.

Ukážky majú rovnakú hlavičku na ploche svojho programu (značka, Späť na rutino.online, názov, veta o vymyslenej
firme, Napíšte mi) a na konci pás „Program na vaše …“ v tej istej farbe s tlačidlami Napíšte mi a Späť na
rutino.online, ktoré vedie na otvorený pás programu na hlavnej stránke. Ikona stránky (favicon) je štvorec
vo farbe programu s písmenom.

## Čo tu je

| Cesta | Čo to je |
|---|---|
| `index.html` | hlavná stránka, CSS aj skript sú v súbore; v `<head>` title, description, canonical, og, twitter, JSON-LD `Service` (tri ponuky) a `FAQPage`, favicon ako SVG a preload štyroch písiem |
| `ukazky/ponukovac/` | ukážka 1: veľkoobchod s obalmi Krabica a Páska s. r. o. robí cenovú ponuku pre e-shop Lúčka s. r. o. (kontakt novak@example.com); cenník obalov, súčet s DPH, PDF cez tlač prehliadača s vodoznakom UKÁŽKA, mail zákazníkovi |
| `ukazky/papiere/` | ukážka 2: e-shop s čajom a kávou Lúčka s. r. o. načíta faktúry od dodávateľov Krabica a Páska s. r. o., Kuriér Rýchlik s. r. o. a Pražiareň Zrnko s. r. o. do tabuľky (pdf.js v `pdfjs/`, Apache 2.0), vzorové faktúry vo `vzory/faktura-1.pdf` až `faktura-3.pdf` |
| `ukazky/evidencia/` | ukážka 3: zákazky Tlačiarne Bodka s. r. o. (letáky, vizitky, katalóg, roll-up, kalendáre…), tabuľka a nástenka, strop 12 zákaziek |
| `obrazky/` | 13 skutočných snímok ukážok a PDF Ponukovača vo WebP, každý súbor do 120 kB, vyrába ich `_PRACA/obrazky.js` (s `obrazky.py`). Okná do zatvorených pásov `ponukovac-nahlad`, `papiere-nahlad`, `evidencia-nahlad` (všetky 1040 × 328); Ponukovač `ponukovac-pdf` (celé PDF ponuky), `ponukovac-pdf-hore` (horná časť PDF pod pásmi na mobile), `ponukovac-program`, `ponukovac-mobil`, `ponukovac-ponuka-m` (koniec ponuky v mobile); Papiere `papiere-faktura` (faktúra Pražiarne Zrnko), `papiere-tabulka`, `papiere-mobil`; Evidencia `evidencia-nastenka`, `evidencia-mobil`. Na hlavnej stránke je PDF bez veľkého vodoznaku UKÁŽKA, v samotnej ukážke ostáva. Snímky predošlých verzií sú v `_PRACA/obrazky_navyse/` |
| `fonts/` | `funnel-display-latin.woff2`, `funnel-display-latin-ext.woff2`, `funnel-sans-latin.woff2`, `funnel-sans-latin-ext.woff2` a licencia `OFL-funnel.txt`; hostované tu, aby stránka nevolala Google Fonts. Písma predošlých verzií (Archivo, Martian Mono, Manrope, Newsreader) sú v `_PRACA/nepouzivane_pisma/` |
| `og-image.png` | obrázok pre zdieľanie (1200 × 630): hore zelená plocha s adresou, nadpisom z prvej obrazovky a vetou o cene a termíne, pod ňou štyri pásy vo farbách programov s cenami; vyrába ho `_PRACA/og_obrazok.py` z tých istých písiem |
| `ochrana-udajov.html` | ochrana údajov v tom istom vzhľade; jediné miesto s celým menom prevádzkovateľa, právne vety sa menia len na Alexov pokyn |
| `404.html` | stránka pre neexistujúcu adresu („Na tejto adrese nič nie je.“, tlačidlá Na úvodnú stránku a Napíšte mi); odkazy aj písma sú od koreňa webu (`/fonts/`, `/#kontakt`), lebo sa zobrazuje na ľubovoľnej adrese |
| `robots.txt`, `sitemap.xml` | podporné súbory |

## Pravidlá stránky

- **Žiadny cudzí skript, písmo ani cookie.** Stránka to o sebe tvrdí v pätičke, preto sem nepatrí analytika
  ani widgety. Za behu nesmie ísť ani jeden dopyt mimo vlastnej domény (Gmail je len odkaz).
- **Ukážky predvádzajú, nenahrádzajú program.** Nič neukladajú (po obnovení stránky sú ako na začiatku), Ponukovač
  má pevnú vymyslenú firmu a PDF s vodoznakom UKÁŽKA, Papiere nemajú export a berú dve vlastné PDF, Evidencia
  nemá tlač ani export a má strop 12 zákaziek.
- **Zo stránky sa nič neodosiela, kontakt je skladačka mailu.** Návštevník klikne, o čo ide, koľko ich je vo firme
  (1 až 2, 3 až 9, 10 až 24) a ako často to robia, prípadne dopíše vetu. Stránka z toho poskladá predmet aj text
  s náhľadom. Odoslať ho dá cez `mailto:` (Otvoriť v e-maile), cez Gmail (`mail.google.com/mail/?view=cm`, len odkaz
  s `target=_blank`, žiadny skript) alebo si text skopíruje (Kopírovať text), lebo `mailto:` ľuďom s poštou
  v prehliadači nič neotvorí. Pod tým je adresa info@rutino.online s tlačidlom Kopírovať adresu. Tlačidlá
  „Napíšte mi o …“ pri programoch, klik na pás aj odkazy z ukážok (`?co=ponuky`, `?co=faktury`, `?co=zakazky`)
  predvyplnia program; „Poslať mi tieto čísla“ vloží do mailu čísla z kalkulačky. Keby bol odkaz `mailto:` dlhší
  ako asi 1 900 znakov, ostanú z kalkulačky v mailu len výsledky. Bez JavaScriptu sú voľby skryté a ostane hotový
  mail s tlačidlami. Žiadny `<form>` s odoslaním.
- **Nič zadarmo.** Slová zadarmo, bezplatne, free ani nezáväzná konzultácia na stránke nie sú. Všetko sa platí.
- **Na webe sa nepíše „toolka“.** Zákazník kupuje program.
- **Kto to robí:** na stránke je krstné meno Alex (ako podpis v mailoch); celé meno prevádzkovateľa je len v ochrane
  údajov. Žiadny telefón (ani vo vymyslených dátach ukážok) a žiadne odkazy na iné weby.
- **Nič vymyslené.** Žiadne referencie, recenzie, logá klientov ani štatistiky; čísla len z cenníka a postupu.
  Namiesto referencií sú tri funkčné ukážky pre vymyslené firmy z rôznych odborov (všetky e-maily v nich sú
  `@example.com`, IČO, DIČ a IBAN sú zjavne vymyslené). Na hlavnej stránke sú tieto firmy spomenuté raz.
- **Písanie:** vykanie s malým „vy, vás, váš“, žiadne dlhé ani stredné pomlčky v texte (U+2014, U+2013) (rozsahy „490 až 990 €“),
  medzi číslom a € nezalomiteľná medzera. Jednopísmenové predložky a spojky skript pripojí k ďalšiemu slovu,
  aby neostali na konci riadku. Počty: „do 24 hodín“ najviac 3×, „10 dní“ najviac 4×, „sám“ najviac 2×.
- Ukážky, ochrana údajov aj 404 majú `noindex`. V `robots.txt` zakázané nie sú, lebo Google by potom `noindex`
  neprečítal a adresu by mohol ukázať bez popisu.

## Kontaktná adresa

Všetky `mailto:` odkazy stránky vedú na `info@rutino.online` (schránka na Hostingeri od 14.09.2026). Tlačidlá
„Napíšte mi“ v ukážkach vedú na `../../?co=…#kontakt`, na 404 na `/#kontakt`. Výnimkou je tlačidlo Otvoriť mail
zákazníkovi v ukážke Ponukovača, ktoré ide na adresu zákazníka vyplnenú v ukážke (predvolená novak@example.com).

## Lokálny náhľad

```
python -m http.server 8097 --bind 127.0.0.1 --directory .
```

a otvoriť `http://127.0.0.1:8097/` (alebo preview server „rutino“ z `Claude_Robota\.claude\launch.json`).
Ukážka Papiere do tabuľky potrebuje server (pdf.js sa načítava ako modul až pri prvom súbore), z `file://` nejde.
Stránka 404 berie písma od koreňa (`/fonts/`), lokálne ich nájde, keď server beží nad týmto priečinkom.

## Generátory a kontrola (mimo repozitára, v `..\_PRACA\`)

Spúšťajú sa z priečinka `Rutino`. Playwright je `playwright-core` z `%APPDATA%\npm\node_modules`, Chromium
z `%LOCALAPPDATA%\ms-playwright`; server si skripty pustia samy.

- `obrazky.js` (s `obrazky.py`) odfotí bežiace ukážky v 2× rozlíšení a PDF Ponukovača a spraví z nich
  `obrazky/*.webp` (PyMuPDF, Pillow); výrezy ráta z DOM ukážok
- `faktury_ukazka.py` vyrobí tri vzorové faktúry s textovou vrstvou do `ukazky/papiere/vzory/` (reportlab)
- `og_obrazok.py` vyrobí `og-image.png` priamo z písiem vo `fonts/` (Pillow, fontTools, brotli)
- `snimky.js` urobí snímky stránky na 1440, 390 a 360 px (`d01…`, `m01…`, `n01`) a `sprava.json` s chybami
  konzoly, cudzími doménami a pretekaním
- `test_uvodnej.js` overí hlavnú stránku: sieť a cookies, `<head>` a JSON-LD, pásy a `?co=`, kalkulačku, skladačku
  mailu, lepiaci pás, 320 a 360 px, stránku bez JavaScriptu, klávesnicu, kontrast farieb, výkon, texty a počty,
  písma, 404 a ochranu údajov
- `test_ukazky.js` preklikne tri ukážky (sieť, nič sa neukladá, písma, texty, mobil, klávesnica, bez JavaScriptu,
  kontrast, výkon, návrat cez Späť)
- staršie a pre tento vzhľad sa nepoužívajú: `nahlady.js` (JPEG náhľady prvej verzie), `sekcie.js` (snímky sekcií
  prvej verzie), `pisma_zmensit.py` (zmenšenie písiem Archivo a Martian Mono); skripty verzie „dielňa“ sú
  v `nepouzivane_skripty\`

Snímky z kontrol sú v `..\_PRACA\kontrola\`.

## Nasadenie

Push do `main` mení živý web do dvoch minút. DNS: A záznamy apexu na GitHub Pages
(185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153), `www` ako CNAME na adresu
GitHub Pages účtu, v Settings → Pages custom domain `rutino.online` a vynútené HTTPS.
