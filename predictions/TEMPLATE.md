# Mall för dagens analysfil

Normerande för allt under `predictions/`. Varje ny fil följer strukturen nedan i exakt
den ordningen. Filer från mars och tidig september 2026 följer den inte — de skrivs
inte om, men ingen ny fil får avvika.

**Filnamn:** `ÅÅÅÅ-MM-DD-TURNERING.md`, turneringar i VERSALER med bindestreck, flera
sammanfogade med `-`: `2026-09-14-PREMIER-LEAGUE-LA-LIGA.md`. Dagens alla matcher
ligger i **en** fil — behåll filnamnet även om en ny turnering tillkommer senare på
dagen.

**Språk:** svenska genomgående. Research görs på engelska, men ingenting av det syns.

**Siffror:** svenskt decimalkomma (`1,91` inte `1.91`). Skriv **sannolikhet** i klartext
— aldrig `p` som kolumnrubrik eller i löptext.

---

# Skriv för läsaren, inte för regelverket

**Inga regelhänvisningar i filen.** Skriv aldrig `(**C4**)`, `(**K2b**)` eller
`enligt H5`. Läsaren har ingen nytta av att veta vilken regel som styrde ett beslut —
han vill veta *vad* beslutet är och *varför*, i klartext. Reglerna bor i `SKILL.md`
och gäller lika mycket för att de inte nämns.

Skriv alltså **"Valencia har gjort ett mål på fyra matcher"**, inte
**"målsnittet är lågt (**C6**)"**. Samma information, utan koden.

Två markörer är undantag, för de betyder något konkret:

- **`PRIS EJ TILLGÄNGLIGT`** — marknaden gick inte att prissätta. Aldrig en gissning.
- **`underlag saknas`** — statistiken gick inte att hämta för den raden.

## Längdtak

| Del | Tak |
|---|---|
| Dagens spel | en rad per spel, inga motiveringar |
| Matchbild | **1–2 meningar** |
| Jämförelsetabell | **max 4 rader** — det valda spelet plus de närmaste alternativen |
| Beslut, motargument, bästa marknad | **en rad var** |

Ett matchblock ska landa på **femton rader eller mindre**. Blir det dubbelt så långt är det
för att något sägs två gånger.

**Säg aldrig samma siffra två gånger.** Sannolikhet, band, odds, brytpunkt och EV står
i jämförelsetabellen. Beslutsraden pekar på tabellen — den upprepar den inte.

---

# Strukturen

Sektion 1–6 finns i varje fil. Sektion 7 bara när startelvorna bekräftas efter
publicering.

## 1. Titel

```markdown
# ⚽ <Turnering(ar)> — <dag> <D> <månad> <ÅÅÅÅ>

<En rad: vilka omgångar det gäller, och om det är enkelmatcher eller ben i en
tvåmötesomgång — det senare avgör hur formen ska läsas.>
```

Är filen skriven i flera omgångar under dagen får varje tillskott en egen rubrik:
`## Hela dagen (analyserad 13:00)`, `## Tillägg 20:00 — bekräftade elvor`.

## 2. Kvällens matcher & domare

```markdown
## 📋 Kvällens matcher & domare

| Tid | Match | Domare | Gula/match | Urval |
|---|---|---|---|---|
| 21:00 | Leeds – Newcastle | Salisbury (ENG) | 3,71 | 154 matcher, karriär |
```

Alla dagens matcher, även de som inte analyseras. Domaren i samma tabell, så det syns
direkt vilka som är overifierade: skriv `—` och `ej verifierad` i stället för att
utelämna raden.

## 3. Dagens spel

Först i filen, före all analys. Inga motiveringar — de finns per match längre ner.

```markdown
## 🎯 Dagens spel

**Kuponger — <budget> kr**

| # | Typ | Spel | Odds | Sannolikhet | EV | Kvalitet | Insats |
|---|---|---|---|---|---|---|---|
| 1 | Ankare | PSG vinst & ö2,5 | 1,22 | 85% | +4% | 🟢 7,5 | 100 kr |

**Singelspel**

| Tid | Match | Spel | Typ | Odds | Sannolikhet | EV | Kvalitet | Insats |
|---|---|---|---|---|---|---|---|---|
| 21:00 | Lag A – Lag B | BTTS | Mål | 1,55 | 68% | +5% | 🟡 7 | 50 kr |

**Exponering:** X kr på mål · Y kr på en match · Z kr utanför kupongbudgeten
**Pass:** <matcher utan spel, en rad med skälet>
```

Krav:

- **Fyra kuponger är inget krav.** Antalet följer vad som klarar värdetestet. En kväll
  med två kuponger och fyra pass är normal; noll spel kräver en förklaring.
- **Inget tak på antalet singelspel**, men över ungefär sex rader: sortera på kvalitet.
- **`Typ` är obligatorisk** — fem rader som alla säger "Mål" är en tes i fem
  förklädnader, och det ska synas.
- **Inget här är ett kupongben.** Singlar byggs aldrig ihop.
- **Tom tabell är giltigt:** `inga singelspel ikväll` plus skälet.
- **Exponeringsraden är obligatorisk** när mer än ett spel ligger på samma match eller
  samma tes.

## 4. Match för match

```markdown
### N. Hemma – Borta (tid)

**Matchbild.** <En till två meningar. Förväntad målmiljö, vem som dominerar, och om
båda lagen har en egen väg till mål eller om ett lag gör de flesta målen. Frånvaro och
formfakta tas med som bisats **bara när de flyttar skattningen** — "utan sina två
mittbackar", inte en skadelista.>

| Marknad | Sannolikhet | Band | Odds | Brytpunkt | Värde |
|---|---|---|---|---|---|
| **Under 2,5** | 50% | 44–55% | 2,06 | 48,5% | Medel |
| Över 2,5 | 50% | 45–56% | 1,80 | 55,6% | Svag |
| BTTS | 53% | 47–58% | 1,60 | 62,5% | Svag |
| Hemmalaget över 1,5 | 42% | 36–48% | `PRIS EJ TILLGÄNGLIGT` | — | — |

**Beslut.** 🟡 LITET SPEL — under 2,5. Utfallskonfidens 6/10.
**Motargument.** <Mest sannolika förlustscenariot, och om någon annan marknad
överlever det bättre.>
**Bästa marknad:** under 2,5 · **spelad:** JA
```

Krav:

- **Matchbilden skrivs utan att nämna en marknad.** Annars skrivs den baklänges från
  ett spel som redan är valt. Två meningar räcker; behöver den fyra är det för att den
  återger research i stället för en slutsats.
- **Inget eget truppnyttsblock.** Skador och avstängningar ska verifieras lika noga som
  förut, men de skrivs bara ut när de påverkar en skattning. Resten stannar i
  researchen.
- **Jämförelsetabellen ska innehålla de närmaste alternativen**, inte bara vinnaren.
  För en målmatch: över 1,5 / över 2,5 / BTTS / lagtotal. För en stängd: under 2,5 /
  under 3,5 / BTTS-Nej. För en resultatmatch: 1X2 / dubbelchans / DNB / handikapp.
  **Minst en lagtotal ska prissättas varje gång** — det är den marknad som oftast
  passar tesen och som oftast glöms.
- **Var BTTS en kandidat men förlorade?** Säg varför i en mening under tabellen.
- **Brytpunkten inne i bandet** betyder marginellt eller pass. Bandets bredd kommer
  från namngiven osäkerhet, aldrig från en schablon.
- **`Bästa marknad` får aldrig försvinna.** Är den inte spelad ska skälet stå:
  inget pris, för tunt värde, korrelerar med ett annat spel, insatsbegränsning, eller
  ett uttalat riskbeslut.
- **Beslutet är ett av tre:** 🟢 SPELA · 🟡 LITET SPEL · 🔴 PASS. Pass används inte för
  att något "bara" är osäkert — osäkerhet finns i varje match.

### Skott på mål

Läggs till per match när underlaget finns: top 3 skyttar i varje lag, sorterade högst
först.

```markdown
**Skott på mål — sidospel.**

| Lag | Spelare | Skott på mål/match | Urval | Linje | Sannolikhet |
|---|---|---|---|---|---|
| Leeds | Calvert-Lewin | 1,07 | 34 matcher, PL 25/26 | 1+ | 62% |
```

Siffran är spelarens egen, över ett angivet urval i samma tävling.

**Rader utan underlag skrivs inte ut.** Räkna dem i stället på en rad under tabellen:
*"Tre rader utan underlag (Okafor, Gudmundsson, Wissa)."* Namnen behövs för att
efteranalysen ska veta vad som saknades — utan dem mäts bara spelare med bra
statistiktäckning, och kalibreringen blir skev. Går ingen av de sex att belägga: skriv
bara den raden, ingen tabell.

## 5. Medvetet undvikna spel

```markdown
## ⚠️ Medvetet undvikna spel

| Marknad | Varför |
|---|---|
| Över 2,5 1,80 | Kräver 55,6%, skattning 50% |
| BTTS 1,60 | Kräver 62,5%, skattning 53% — fel marknad för en ensidig målbild |
```

Obligatorisk och får inte vara tom. Gick varje övervägd marknad vidare till ett spel
är urvalet inte gjort.

## 6. Kort

**En rad när inget kortspel läggs:**

```markdown
## 🟨 Kort

Salisbury ligger på 3,71 gula per match över 154 karriärmatcher. Inget kortspel —
lagens kort per match saknas och ingen linje går att få.
```

Fullt avsnitt med tabell bara när ett kortspel faktiskt rekommenderas. Kortspel är
alltid singlar utanför kupongerna, och redovisas i sektion 3.

## 7. Uppdatering (frivillig)

```markdown
## 🔄 Tillägg <tid> — bekräftade elvor

<Vad som ändrades mot antagandet, per match. Ändras en bedömning: ny sannolikhet,
nytt band, nytt rättvist odds.>

**Vad detta gör med spelen:** <vilken insats som faktiskt flyttas — eller
uttryckligen: ingen.>
```

Bara när informationen är **bekräftad** och **ändrar något**. Ändras ingenting: skriv
inget alls. Ett tillägg som bekräftar att allt är som förut är brus.

---

# Efteranalys

Läggs till efter matcherna, ordagrant den här strukturen:

```markdown
---

## 📊 Efteranalys

**90-minutersverifiering:** <hur mål efter 90 hanterats — förlängning räknas aldrig.>

### Resultat
| Match | Resultat | Nyckelhändelser |
|---|---|---|

### Marknadsutfall
| Match | Marknad | Sannolikhet | Utfall | Resultat |
|---|---|---|---|---|

### Singelspelsutfall — samma rader som sektion 3
| Tid | Match | Spel | Typ | Odds | Sannolikhet | Insats | Utfall | Resultat |
|---|---|---|---|---|---|---|---|---|

### Skott på mål — alla rader, även ospelade
| Lag | Spelare | Linje | Sannolikhet | Spelade minuter | Skott på mål | Utfall |
|---|---|---|---|---|---|---|

### Kupongutfall
| Kupong | Resultat | Fallet ben |
|---|---|---|

### Totalt: X/Y kuponger | X/Y singelspel | Vinst/förlust: +/- X kr

*P/L-underlag: <vilka priser summan bygger på — faktiska, indikativa eller filens egna
rimliga odds — och spannet mellan dem.>*

### 🧠 Självutvärdering
- **Kalibrering:** ...
- **Bästa läsning:** ...
- **Sämsta läsning:** ...
- **Orsak per miss och per vinst:** dåliga data · dålig tolkning · dålig sannolikhet ·
  dåligt marknadsval · dåligt pris · varians · recensbias · narrativbias ·
  överkonfidens · korrelation
- **Lärdom:** ...
```

**90-minutersraden står direkt under rubriken.** Skriv ut vilka sena mål som räknats
in och vilka som inte gjort det.

**Singelspelsutfallet speglar sektion 3 rad för rad**, i samma ordning och med samma
sannolikheter. Skiljer de sig är antingen förhandsanalysen eller efteranalysen fel —
städa inte tabellen så att de stämmer.

**Skottabellen kräver spelade minuter för varje rad**, även de ingen skulle ha spelat.
Ett skottspel faller på två olika sätt — han sköt inte, eller han var inte på planen —
och bara minutkolumnen skiljer dem åt. Går skottsiffran inte att hämta i efterhand:
skriv `ej bedömbar` men fyll ändå i minuterna.

**Orsaksklassningen gäller även vinster.** Ett vunnet spel kan vara en dålig prediktion
och ett förlorat kan vara en bra — utan klassning justeras modellen av utfall i stället
för av fel.

**P/L-underlaget är obligatoriskt när priserna inte är verkliga.** Totalraden kräver en
kronsiffra, men faktiska bookmakerpriser går ofta inte att få. Skriv då vilka priser
summan bygger på och spannet mellan dem. En exakt siffra utan underlag är falsk
precision.

En fil kan innehålla flera avsnitt med egna kupongset. Redovisa varje set separat plus
en dagstotal.

Efter efteranalysen: uppdatera `results.md` med ny rad, löpande totaler och kumulativ
P/L, och lägg nattens rader i `CALIBRATION.md`. Skillförslag går via pull request,
aldrig direkt i `SKILL.md`.
