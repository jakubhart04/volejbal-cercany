# Volejbal Čerčany – statická HTML prezentace (školní projekt VŠE)

Statická, ručně psaná HTML5 + CSS prezentace volejbalového oddílu **TJ Slavoj Čerčany, z.s.** (reálná entita, IČO 147 98 034). Bez CMS, bez šablon, bez JavaScriptu, bez Bootstrapu.

Obsah vychází z veřejně dostupných zdrojů (stav listopad 2026):
- oficiální web oddílu [volejbal-cercany.cz](https://volejbal-cercany.cz) (rozpis zápasů, aktuality)
- [zscercany.cz](https://www.zscercany.cz/cs/zajmove-krouzky-skolni-rok-20252026) (volejbalový kroužek, 10–12 let)
- [cvf.cz / iscus.cz](https://iscus.cz/web/sportovni-subjekty/3201009) (IČO, členství v ČUS, oddíly TJ)

Obrázky jsou **AI-generované ilustrační fotografie** (ne fotografie skutečného oddílu); logo a favicon jsou vlastní SVG grafika.

## Struktura

```
volejbal-cercany/
├── index.html          Domů (hero, zápasy, aktuality)
├── o-oddilu.html       O oddíle + vícesloupcový layout + sidebar
├── tymy.html           Naše týmy (6 karet kategorií)
├── treninky.html       Tréninky a nábor (+ FAQ)
├── zapasy.html         Zápasy – jediná tabulka (k čemu tabulka je)
├── aktuality.html      Aktuality (<time>)
├── kontakt.html        Kontakt (<address>, odkazy na mapy)
├── css/
│   ├── style.css       veškerý styl obrazovky (žádný inline CSS)
│   └── print.css       tisková verze (media="print")
└── img/                optimalizované JPEG (≤ ~220 KB) + favicon
```

## Zadání → jak je splněno

| Požadavek | Řešení |
|---|---|
| Reálná entita, smysluplný obsah | volejbalový oddíl TJ Slavoj Čerčany (data z veřejných zdrojů) |
| Min. 5 stránek, provázaná navigace | 7 stránek, stejná navigace, `aria-current="page"` u aktivní položky |
| Platná HTML5 + sémantika | validováno oficiálním W3C validátorem (validator.w3.org) – **0 chyb** na všech 7 stránkách |
| HTML5 sémantické značky | `header`, `nav`, `main`, `section`, `article`, `aside`, `footer`, `address`, `figure/figcaption`, `time` |
| CSS/JS odděleny od obsahu | externí `css/style.css` + `css/print.css`; žádný JS, žádný inline `style` |
| Vícesloupcový beztabulkový layout | CSS Grid 2 sloupce (o-oddilu, treninky, kontakt) + responzivní mřížky |
| Tisková verze | `print.css` – tiskne obsah + identifikaci webu + odkazy s adresami; skryje navigaci/dekorace |
| Identifikace webu na všech stránkách (i v tisku, i bez obrázků) | logo + název v hlavičce, patička, v tisku `.no-print-identity` |
| Bez duplikování URL | každá stránka jediný soubor, relativní odkazy |
| Podtržené, odlišitelné odkazy | odkazy vždy podtržené (`text-underline-offset`), hover zesílení |
| Zvýraznění aktivní položky v menu | bílý text + oranžový podtržník + `aria-current="page"` |
| Vlastní `<h1>` a `<title>` (vč. názvu webu) | každá stránka má unikátní h1 i title („… – Volejbal Čerčany“) |
| Meta informace + favicon | `description`, `viewport`, `theme-color`, favicon SVG + PNG (32/180/192/512) |
| Významové obrázky s `alt`, optimalizace | 2 obsahové fotografie s českým `alt` (CTA pás je CSS pozadí – dekorace), JPEG ≤ 220 KB, rozměry atributy |
| Rozlišení 800×600, bez horizontálního scrollu | ověřeno v Chromiu (`scrollWidth = 800`, 0) |
| Kontrast písma a pozadí | všechny kombinace ≥ 4.5:1 (ověřeno výpočtem WCAG) |
| Bez CMS/šablon | ručně psané HTML/CSS |

## Co upravit před odevzdáním

1. ~~Své jméno~~ – hotovo (v patičce je uvedeno **Jakub Hart · student VŠE**).
2. **(Volitelné) údaje o zápasech a aktualitách** – rozpis vychází z listopadu 2026; před odevzdáním ověř aktuální termíny na [volejbal-cercany.cz](https://volejbal-cercany.cz) a případně je uprav v `zapasy.html` a `index.html`.
3. V patičce je poznámka „školní projekt“ – prezentace neposkytuje oficiální web oddílu; to je záměr (respekt k reálné entitě). Chceš-li, můžeš nahradit vlastní formulací.

## Zveřejnění na internetu (vyber jednu možnost)

### A) eso.vse.cz (doporučeno pro toto zadání)
1. Přihlaš se na `eso.vse.cz` svým účtem VŠE (SSH/SFTP, např. přes klienta WinSCP/FileZilla).
2. Nahraj **obsah** složky `volejbal-cercany/` (ne složku samotnou) do své webové složky (typicky `~/public_html/`).
3. Práva: složky `755`, soubory `644` (WinSCP/FileZilla nastaví automaticky; přes SSH: `chmod -R u=rwX,go=rX ~/public_html`).
4. Web bude dostupný na adrese typu `https://eso.vse.cz/~<tvé-učo>/` (konkrétní adresu a přesné nasazení ověř u cvičícího nebo v nápovědě IT VŠE – fakulty se mohou lišit).

### B) GitHub Pages (nejjednodušší, zdarma, HTTPS)
1. Založ si účet/repozitář na GitHubu, např. `volejbal-cercany`.
2. Nahraj soubory do větve `main` (root) a v **Settings → Pages** zvol nasazení z větve `main` / složka `/ (root)`.
3. URL bude `https://<uživatel>.github.io/volejbal-cercany/`.

### C) Jakýkoliv hosting (Wedos, Forpsi, …)
Nahraj přes FTP obsah složky do kořene webu (`www/` resp. `public_html/`).

Pak odevzdej do ISIS jednorádkový soubor s URL (přesně dle pokynů v odevzdávárně).

## Ověření před odevzdáním
- W3C validátor: https://validator.w3.org → „Validate by Direct Input“ → zkopíruj obsah každého `.html` souboru (všech 7!). Očekávaný výsledek: 0 chyb.
- Tisk: Ctrl+P v prohlížeči – zobrazí se čistá textová verze s kontaktem.
- Vypnout CSS v nástrojích vývojáře – obsah zůstane čitelný a odkazy funkční.

## Poznámky k pravdivosti obsahu
- Web je **neoficiální školní prezentace** reálného oddílu – nekopíruje obsah oficiálního webu, texty jsou napsané vlastní.
- AI-generované ilustrační fotografie nejsou skutečné fotografie oddílu (v posudcích to uváděj pravdivě, pokud se na to zeptají).
- Data (IČO, členství v ČUS, kontakt, rozpis) jsou veřejná; i tak je před odevzdáním rychle překontroluj.
