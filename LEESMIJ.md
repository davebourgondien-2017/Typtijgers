# Typtijgers - de site online zetten

## Wat zit er in deze map

| Bestand | Wat het is |
|---|---|
| `index.html` | De startpagina: wat is het, voor wie, en het algemene feedbackformulier |
| `Typtijgers.html` | **De cursus zelf.** Werkt ook los, zonder internet (dubbelklikken) |
| `privacy.html` | Privacyverklaring |
| `bedankt.html` | Pagina na het versturen van feedback |
| `site.css` | Opmaak van de site (de cursus heeft zijn eigen opmaak ingebouwd) |
| `favicon.svg` | Het tijgertje in het browsertabblad |
| `netlify.toml` | Instellingen voor Netlify (geen bouwstap, nette adressen, beveiligingsheaders) |
| `robots.txt` | Vertelt zoekmachines en AI-bots dat alles welkom is |
| `sitemap.xml` | Lijst met de drie pagina's, voor Google |
| `llms.txt` | Samenvatting van de site voor AI-tools |
| `og-typtijgers.png` | De afbeelding die verschijnt bij delen in WhatsApp, Facebook, LinkedIn |

---

## Vindbaarheid (Google en AI-tools)

Het domein staat vast op **https://www.typtijgers.nl** (mét www). Dat adres staat in:
`index.html`, `Typtijgers.html`, `privacy.html` (canonical + og:url), `sitemap.xml`,
`robots.txt` en `llms.txt`. Ga je ooit naar een ander domein of naar de vorm zónder
www, vervang het dan in al die bestanden tegelijk - een canonical die naar het
verkeerde adres wijst zorgt ervoor dat Google je pagina's juist níét opneemt.

Wat er is ingebouwd:

- **Canonical-adressen**: `/` , `/cursus` en `/privacy`. De nette adressen werken via
  `netlify.toml` (status 200, dus geen omleiding).
- **Social previews** (Open Graph + Twitter card) met `og-typtijgers.png`, 1200x630.
- **Structured data** in `index.html`: `WebSite`, `Course` en `FAQPage`. De acht vragen
  daarin staan letterlijk hetzelfde op de pagina zelf - dat eist Google, anders vervalt
  de rich result. Pas je een vraag of antwoord aan, pas het dan op beide plekken aan.
- **robots.txt** staat GPTBot, ClaudeBot, PerplexityBot, Google-Extended en
  Applebot-Extended expliciet toe, zodat de cursus in AI-antwoorden mag opduiken.
- **llms.txt** is een korte samenvatting van de site, speciaal voor AI-tools.

### Na het publiceren: 3 dingen doen

1. **Google Search Console** ([search.google.com/search-console](https://search.google.com/search-console)):
   voeg `https://www.typtijgers.nl` toe, bevestig eigendom (via Netlify DNS of een
   HTML-bestand), en dien `https://www.typtijgers.nl/sitemap.xml` in onder *Sitemaps*.
2. **Bing Webmaster Tools**: zelfde verhaal. Bing voedt ook ChatGPT-zoekresultaten,
   dus dit telt dubbel.
3. **Controleer de rich results** via de Rich Results Test van Google en plak je URL
   in de Facebook Sharing Debugger om de preview-afbeelding te testen.

Reken op enkele weken voordat je in Google verschijnt. Een nieuw domein zonder links
heeft tijd nodig; dat is normaal en niets kapot.

---

## Naam en contactgegevens (ingevuld)

De site staat op naam van **Dave Bourgondiën**, met **dave.bourgondien@gmail.com**
als contactadres. Dat staat op twee plekken:

- `index.html` — onderaan in de voettekst
- `privacy.html` — onderaan bij "Vragen of iets laten verwijderen?"

Wil je dit wijzigen, pas het dan op beide plekken aan. Een privacyverklaring moet
vermelden wie de site beheert en hoe mensen contact kunnen opnemen.

---

## Online zetten (ongeveer 10 minuten)

### Stap 0 - OneDrive eerst lokaal zetten
Deze map staat in OneDrive. Staan de bestanden alleen "in de cloud" (wolkje in
plaats van een groen vinkje in Verkenner), dan sleep je lege plaatshouders naar
Netlify en werkt de site niet.

> Rechtsklik op de map `Typcursus` → **Altijd behouden op dit apparaat**.
> Wacht tot alle bestanden een groen vinkje hebben.

### Stap 1 - Account
Ga naar [app.netlify.com](https://app.netlify.com) en maak een gratis account
(kan met een e-mailadres, GitHub is niet nodig).

### Stap 2 - Map erin slepen
Klik op **Add new project** (bij oudere accounts: *Add new site*) →
**Deploy manually**. Sleep de hele map `Typcursus` in het vak op het scherm.
Na ongeveer een halve minuut staat de site online op een adres als
`https://willekeurige-naam-123.netlify.app`.

### Stap 3 - Een nette naam
**Project configuration → Site information → Change site name** →
bijvoorbeeld `typtijgers`. Het adres wordt dan `https://typtijgers.netlify.app`.

### Stap 4 - Formulieren aanzetten en testen
Zie het kopje *De feedback ophalen* hieronder. Doe dit meteen, anders merk je
pas later dat er geen reacties binnenkomen.

### Stap 5 - Controleren
- `https://<jouwnaam>.netlify.app` → startpagina
- `https://<jouwnaam>.netlify.app/cursus` → de cursus
- Doe één les en kijk of de voortgang blijft staan na verversen (F5)

Een eigen domein (bijvoorbeeld `typtijgers.nl`) kan later onder
**Domain management → Add a domain**. Netlify regelt het https-certificaat zelf.

### Een nieuwe versie online zetten
Zelfde weg: open het project → tabblad **Deploys** → sleep de bijgewerkte map in
het vak onderaan. De oude versies blijven bewaard, dus je kunt altijd terug met
**Published deploy → Publish deploy** bij een oudere regel.

---

## De feedback ophalen

De site heeft twee formulieren:

- **`feedback-site`** - het formulier op de startpagina (algemene feedback)
- **`feedback-cursus`** - het venster in de cursus, dat vanzelf verschijnt zodra
  iemand een module afrondt, en verder via "geef feedback" bovenaan

Beide komen binnen in Netlify onder **Forms**. Daar staat per formulier de lijst
met inzendingen, met een knop **Download as CSV**.

> **Controleer na de eerste keer publiceren** of formulierdetectie aanstaat:
> Project configuration → Forms. Netlify zet dit meestal vanzelf aan zodra het een
> formulier in de HTML vindt, maar niet altijd. Staat het uit, zet het aan en
> publiceer nog een keer. Test daarna zelf één keer het formulier op de startpagina;
> je zou dan op de bedankpagina moeten uitkomen en de inzending bij Forms zien staan.

> **Zet e-mailmeldingen aan:** Forms → Settings → Form notifications →
> *Email notification*, en vul je eigen adres in. Dan krijg je bericht bij elke
> reactie in plaats van dat je moet gaan kijken.

Het gratis pakket doet **100 inzendingen per maand**. Loopt dat vol, dan is dat
goed nieuws en kun je overstappen op een betaald pakket.

### Wat er in een inzending staat
`module` (1 t/m 5 of "algemeen"), `niveau` (Aapje/Panter/Tijger), `leuk` (1-5),
`moeilijk`, `wie`, `opmerking`, `voortgang` (hoeveel lessen en sterren) en
`versie` van de cursus. Bewust géén naam, e-mailadres of leeftijd.

### De feedback laten verwerken
Download het CSV-bestand en geef het aan Claude met bijvoorbeeld:
*"Hier is de feedback van de eerste maand, verwerk dit in de cursus."*
Dan kunnen lessen aangepast, toegevoegd of makkelijker gemaakt worden.

---

## Voortgang van gebruikers

De voortgang staat in **localStorage** op het apparaat van de gebruiker, niet op
een server. Er is dus niets in te zien of te beheren, en er zijn geen accounts.

Wie op een andere computer verder wil, klikt op het profielscherm op
*"Voortgang meenemen naar een ander apparaat"*, kopieert de code en plakt die
op het andere apparaat. Een volledige voortgang is ongeveer 420 tekens.

---

## Waar je op moet letten bij wijzigingen

- **De cursus moet los blijven werken.** `Typtijgers.html` heeft geen enkel
  ander bestand nodig. Houd dat zo: geen externe CSS, geen lettertypen van
  internet, geen plaatjes van een CDN.
- **Het verborgen formulier onderin `Typtijgers.html` niet weghalen.** Netlify
  leest bij het publiceren de HTML om te weten welke formuliervelden er zijn.
  Zonder dat formulier komt feedback uit de cursus niet aan.
- **Nieuwe velden in het feedbackvenster?** Voeg ze dan ook toe aan dat
  verborgen formulier, anders gooit Netlify ze weg.
- **Versienummer.** Bovenin de cursus staat `var APPVERSIE="2.0";`. Hoog dat op
  bij een nieuwe versie, dan zie je in de feedback over welke versie het gaat.

---

## De opbouw van de cursus (versie 2.0)

49 stappen op één route: **45 lessen in 5 modules**, met tussen elke module een
Letterregen-station.

| # | Module | Stappen | Waar het over gaat |
|---|---|---|---|
| 1 | Beginner 🌱 | 13 | Vingernamen, thuisrij, alle letters, hoofdletters, cijfers |
| — | Letterregen 🎮 | 1 | Station: haal het doel voor drie sterren |
| 2 | Inslijten 🐊 | 10 | Zelfde toetsen, nu vlot: zwakke vingers, dubbele letters, gekke woorden |
| — | Letterregen 🎮 | 1 | Station |
| 3 | Sneller ⚡ | 10 | Veelgebruikte woorden, sch/ch/ng, tempo, tongbrekers |
| — | Letterregen 🎮 | 1 | Station |
| 4 | Meester 🏔️ | 10 | Leestekens, getallen in tekst, verhalen, een briefje |
| — | Letterregen 🎮 | 1 | Station |
| 5 | Examen 🏆 | 2 | Proefexamen en eindexamen met diploma |

**Tijgerpunten** verdien je per stap (sterren + netjes typen + combobonus, die
laatste zit op 15 dicht). Daarmee koop je kleding in de winkel en klim je door de
rangen Welp → Speurneus → Klimmer → Jager → Tijger → Grootmeester.

**De examennorm** staat in `EXAMEN_NORM` en verschilt per leeftijdscategorie:
Aapje 10 wpm / 90% goed, Panter 18 wpm / 93%, Tijger 24 wpm / 96%. Wie haalt,
krijgt een printbaar diploma. Onder **Rapport** staat een printbaar overzicht per
stap - handig voor ouders of de juf.

### Voortgang van oude versies
De opslag heet nu `typtijgers_v3`. Bestaande voortgang uit `v1` of `v2` wordt bij
het eerste openen automatisch omgezet (de lesnummers schuiven op omdat er stations
tussen zijn gekomen). Oude voortgangscodes (`TT1`) worden ook nog gelezen.
