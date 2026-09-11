# Mall för dagens analysfil

Den här filen är normerande för allt under `predictions/`. Varje ny analys kopierar
strukturen nedan i **exakt den ordningen**. Filer från mars 2026 följer den inte —
de skrivs inte om retroaktivt, men ingen ny fil får avvika.

**Filnamn:** `YYYY-MM-DD-TURNERING.md`, turneringar i VERSALER med bindestreck,
flera turneringar sammanfogade med `-`:
`2026-03-03-PREMIER-LEAGUE-COPA-DEL-REY.md`

**Språk:** svenska genomgående — rubriker, tabellhuvuden, brödtext och efteranalys.
Research görs fortfarande på engelska (SKILL.md, Core Principles), men ingenting av
det syns i filen.

**Siffror:** svenskt decimalkomma (`1,91` inte `1.91`). Odds, sannolikhet, rimligt
odds och EV anges för varje rekommenderat spel — utan undantag (I1, I2, I3):

| Kolumn | Betyder |
|---|---|
| **Odds** | priset som faktiskt går att få, alltid märkt indikativt med källa (**I7**) |
| **Sannolikhet** | den egna skattningen, `p` i regelverket — hur ofta spelet landar (**I1**) |
| **Rimligt odds** | `1 / sannolikhet`, alltså brytpunkten (**I2**) |
| **EV** | `sannolikhet × odds`, redovisat som procent över eller under noll (**I3**) |

Skriv rubrikerna i klartext. `p` och `Rimligt` som kolumnhuvuden säger ingenting
för den som läser filen ett halvår senare.

## Konfidensskala

Samma trafikljus i varje tabell i filen, härlett ur /10-siffran:

| Ljus | Intervall | Betydelse |
|---|---|---|
| 🟢 | 7,5–8 | Stark läsning. Taket är 8 på resultatmarknader (**A1**) och 8 totalt. |
| 🟡 | 6–7 | Håller, men bär en identifierad osäkerhet. |
| 🔴 | ≤ 5,5 | Tunn. Får bara ligga i en kupong om odds kompenserar (**I4**). |

Siffran står alltid kvar bredvid ljuset — trafikljuset är för skanning, siffran är
det som går att revidera i efteranalysen.

---

# Längd — filen ska gå att läsa på en minut

Analysen är ett spelunderlag, inte en rapport. Ordningen är **spelen först, skälen
sist**, och skälen ska vara korta nog att hoppa över.

Tak som gäller varje fil:

| Del | Tak |
|---|---|
| Dagens spel (sektion 3) | en rad per spel, inga motiveringar |
| Matchbild per match | **1–2 rader** |
| Marknadsjämförelse | **max 3 rader** — det valda spelet plus de två närmaste |
| Motargument | **en rad** |
| Läsning/resonemang per match | **max 3 rader** |
| Regelhänvisningar | bara taggen, t.ex. (**K3**) — aldrig en förklaring av regeln |

Det som INTE får kortas: sannolikhet, band, pris, EV, beslut, `Matcher per kupong`,
H8-fältet och delad exponering. De är kontrollsiffror, inte text — och efteranalysen
kan inte klassa en miss utan dem.

Skriv inte ut varför en regel finns, vad den heter i klartext eller vad den lärde sig
av en tidigare kväll. Den informationen står i `SKILL.md`.

---

# Strukturen

Sektion 1–9 finns i varje fil, i den här ordningen. Sektion 10 bara när
startelvorna bekräftas efter publicering. Sektion 11 läggs till efter matcherna.

---

## 1. Titel

```markdown
# ⚽ <Turnering> — <fas>, <veckodag> <D> <månad> <ÅÅÅÅ>
```

Exempel: `# ⚽ Champions League — ligafas omgång 1, onsdag 9 september 2026`

Direkt under titeln: en rad som slår fast om det är enkelmatcher eller ben i en
tvåmötesomgång, eftersom **B1/B2** står och faller med det.

## 2. Kvällens matcher & domare

```markdown
## 📋 Kvällens matcher & domare

| Tid | Match | Domare | Gula/match | Urval |
|---|---|---|---|---|
| 18:45 | Barcelona – Feyenoord | Jablonski (GER) | — | ej verifierad |
| 21:00 | Liverpool – Atlético | Massa (ITA) | 4,16–4,76 | 330–438 matcher, karriär |
```

Alla matcher, även de som inte analyseras. Domare med i samma tabell — då syns det
direkt vilka som är overifierade, och **G1** kan inte glömmas bort. Skriv `—` och
`ej verifierad` istället för att utelämna raden.

## 3. Dagens spel

Först i filen, före all analys. Två tabeller, inga motiveringar — motiveringen finns
per match längre ner för den som vill.

```markdown
## 🎯 Dagens spel

**Kuponger — <budget> kr**

| # | Typ | Spel | Odds | p | EV | Kvalitet | Insats |
|---|---|---|---|---|---|---|---|
| 1 | Ankare | PSG vinst & ö2,5 | 1,22 | 85% | +4% | 🟢 7,5 | 100 kr |

**Singelspel**

| Tid | Match | Spel | Typ | Odds | p | EV | Kvalitet | Insats |
|---|---|---|---|---|---|---|---|---|
| 21:00 | Lag A – Lag B | BTTS | Mål | 1,55 | 68% | +5% | 🟡 7 | 50 kr |

**Matcher per kupong:** C1 PSG · C2 … — inga delade matcher (**H5**)
**Exponering:** X kr på mål · Y kr på en match · Z kr utanför kupongbudgeten
**Pass:** <matcher utan spel, en rad>
```

**Inget tak på antalet singelspel** — varje rad som klarar värdetestet får vara med, och
en kväll kan ge noll eller tolv. Det som begränsar är priset och insatsen, inte antalet.
Blir tabellen längre än ungefär sex rader: sortera på kvalitet, så går den fortfarande
att skanna.

Fyra krav på singeltabellen:

- **Sammanställning, inte ny analys.** Varje rad ska finnas i sin matchsektion (4) eller
  kortsektionen (6) med samma sannolikhet, band och pris.
- **Inget här är en skänkel** — singlar byggs aldrig ihop till en kupong (**G4**, **J6**).
- **`Typ` är obligatorisk.** Fem rader som alla säger "Mål" är en tes i fem förklädnader,
  och det ska synas direkt (**L6**).
- **Tom tabell är ett giltigt utfall:** skriv `inga singelspel ikväll` plus skälet
  (**L5**). En rad som läggs in för att fylla tabellen är precis vad **L5b** förbjuder.

Skott på mål-listningen är något annat: den ligger kvar per match med sina sex rader
(top 3 per lag, **J1**) och är en *lista att välja ur*. Bara de rader du faktiskt
rekommenderar en insats på flyttas upp hit.

## 4. Match för match

```markdown
## 🔍 Match för match

### N. Hemma – Borta (tid)

**Läge.** Form i både liga och Europa, tabellposition, vem som måste jaga och om
de kan (**F10** — vilken turnering kommer formen från?).

**Truppnytt (bekräftat <datum>).** Skador, avstängningar, avstängningens
turneringsomfång (**E6**), hela tillgängliga truppen (**E1**). Aldrig antaget.

**Matchbild (K1).** Två till tre rader *utan att nämna en enda marknad*: förväntad
målmiljö, förväntad dominans, om **båda** lagen har en egen väg till mål eller om ett
lag sannolikt gör de flesta målen, förväntat matchläge, förväntad varians.

**Läsning.** Tesen i två till fyra rader, med regelhänvisningar där en regel
faktiskt styr slutsatsen.

**Marknadsjämförelse (K2, K5).**

| Marknad | Sannolikhet | Band | Odds | Brytpunkt | Värde |
|---|---|---|---|---|---|
| **Över 2,5** | 68% | 62–72% | 1,65 | 60,6% | Stark |
| BTTS | 59% | 52–64% | 1,70 | 58,8% | Svag |
| Hemmalaget över 1,5 | 61% | 55–66% | 1,75 | 57,1% | Medel |

<En rad: varför den valda marknaden uttrycker matchbilden bättre än de närmaste
alternativen — och om BTTS var kandidat, varför den *inte* vann jämförelsen (**K2b**).>

**Motargument (L4).** <Det starkaste argumentet *mot* spelet, plus den enskilt
viktigaste motsägande datapunkten — och hur mycket den flyttade sannolikheten.>

**Marknader.**
- **<Marknad>** — p **X% (band A–B%)**, rimligt odds **Y**. Marknad Z (indikativt, källa). EV +N%. Utfallskonfidens **7/10** · spelkvalitet 🟢 **7,5/10**
- **<Marknad som avstås>** — kräver p X%, skattning Y%. Negativt EV. Avstå.
**Beslut.** 🟢 SPELA / 🟡 LITET SPEL / 🔴 PASS — <marknad> @ <odds>, p <X% (A–B%)>,
brytpunkt <Y%>, EV <+N%>. Utfallskonfidens <n>/10.
**Motargument:** <en rad — och om en annan marknad överlever det bättre (**N4**)>
**Bästa marknad i matchen:** <marknad> · **spelad:** JA/NEJ <om NEJ: pris/värde/korrelation/insats/otillgänglig/riskbeslut (**H8**)>

**Skott på mål — sidospel (J6).** Top 3 skyttar i varje lag.

| Lag | Spelare | Skott på mål/match | Urval | Linje | Sannolikhet | Rimligt odds |
|---|---|---|---|---|---|---|
| Real Madrid | Vinícius Jr | 2,4 | 9 matcher, CL 25/26 | 2+ | 55% | 1,82 |
| Real Madrid | Mbappé | 1,9 | 9 matcher, CL 25/26 | 1+ | 78% | 1,28 |
| Real Madrid | Bellingham | 1,1 | 9 matcher, CL 25/26 | 1+ | 62% | 1,61 |
| Marseille | Aubameyang | 1,6 | 8 matcher, CL 25/26 | 1+ | 70% | 1,43 |
| Marseille | Greenwood | 1,4 | 8 matcher, CL 25/26 | 1+ | 66% | 1,52 |
| Marseille | Højbjerg | 0,7 | 8 matcher, CL 25/26 | 1+ | 45% | 2,22 |

<En rad: vem som sticker ut och varför — huvudalternativet, vilka hot som saknas,
straff- eller frisparksläggare — och minutrisken per namn som inte är självklar
startspelare (**J4**).>
```

En matchrubrik per match, numrerad. Inga emoji i matchrubrikerna — trafikljuset
i marknadsraderna bär signalen istället, och emoji per lag blev slumpmässigt i
marsfilerna.

Avstådda marknader hör hit, inte bara i sektion 5: det är i matchen resonemanget
finns. Sektion 5 samlar bara de beslut som gäller hela kvällen.

**Ordningen matchbild → jämförelse → marknad är inte kosmetisk.** Matchbilden skrivs
utan marknadsnamn just för att den inte ska skrivas baklänges från ett spel man redan
bestämt sig för (**K1**). Jämförelsetabellen måste innehålla de närmaste alternativen
på stegen — **över 1,5 · över 2,5 · över 3,5 · BTTS · lagtotal över 1,5 · vinst +
över** för en målmatch, **under 3,5 · under 2,5 · BTTS-Nej · lagtotal under 1,5** för
en stängd, och **1X2 · dubbelchans · DNB · asiatiskt handikapp** för en resultatmatch
(**K2**). **Minst en lagtotal ska vara prissatt varje gång** — det är ramverkets
dokumenterade blindfläck (**K4**).

Två mål-matchbilder är inte samma spel (**K3**): *många mål men ett lag gör dem* är
över 2,5 eller en lagtotal, inte BTTS; *båda lagen med egen väg till mål* är BTTS.

**Varje sannolikhet bär ett band** (**L1**), och bandet är ett robusthetsmått — EV
räknas fortfarande på centralskattningen. Ligger brytpunkten *inne* i bandet är spelet
marginellt eller PASS.

**Motargumentsraden är obligatorisk och får inte vara dekorativ.** Den ska säga hur
mycket den motsägande datapunkten flyttade sannolikheten. Att nämna motevidens och
sedan lämna skattningen orörd är exakt felet **L4** finns för att stoppa.

**Tre beslut, inte två** (**L5b**): 🟢 SPELA vid tydligt positivt riskjusterat värde,
🟡 LITET SPEL när kanten är positiv men mindre robust, 🔴 PASS bara när det inte finns
något tillräckligt pålitligt värde. **PASS får inte användas för att ett spel "bara"
är osäkert** — osäkerhet finns i varje fotbollsmatch, och ett ramverk som passar på
allt det inte kan bevisa är inte disciplinerat, det är overksamt. En kväll med två
spel och fyra pass är normal; en kväll med noll spel kräver en förklaring.

**Ett pris som inte gått att hämta skrivs `PRIS EJ TILLGÄNGLIGT`** (**K4c**) — aldrig
uppskattat, aldrig bakåtberäknat. Raden står kvar i tabellen med sannolikhet och
tesmatchning ifyllda, så att skillnaden mellan *bästa fotbollsmarknad* och *bästa
spelbara marknad* syns. Att utelämna raden är att låtsas att marknaden inte finns.

**Två konfidenssiffror, inte en** (**M1**): utfallskonfidens svarar på "hur säker är
jag på att det händer", spelkvalitet (trafikljuset) på "hur bra är priset givet
sannolikheten och bandet". Det är trafikljuset insatserna följer.

**BTTS:s utfallskonfidens är tillfälligt capad på 6,5/10** (**A7**) — mätt 14/29 (48%)
i mars mot Över 2,5:s 19/25. Capet gäller **bara** utfallskonfidensen: sannolikheten
skattas fritt, och en välprissatt BTTS kan fortfarande bli 🟢 **SPELA** om värdetestet
håller. Capet försvinner när `CALIBRATION.md` har tillräckligt med BTTS-rader för att
mäta bandet direkt.

**Skott på mål-blocket finns i varje analyserad match** och listar **top 3 skyttar i
varje lag** — sex rader, sorterade högst först per lag (**J1**). Varje rad namnger
**vem** och **hur många**: spelare, linje, sannolikhet. Blocket är en listning, inte ett
urval; läsaren väljer själv ur den.

Siffran är spelarens egen skott på mål/match över ett angivet urval i **samma turnering**
(**J2, F10**), inte lagets skottvolym och inte totala skott omräknade i huvudet
(**J3** — ungefär en tredjedel av skotten går på mål, och kvoten är spelarberoende).
Räcker inte underlaget till åtta matcher: skriv karriär- eller helsäsongssiffran och
vilken som används (**G3**). Går ett lags tredje namn inte att belägga skrivs raden ut
med `underlag saknas` — aldrig en tom cell och aldrig färre än tre rader utan förklaring.

**Detta är sidospel och ingenting byggs kring dem** (**J6**): de ligger utanför de fyra
kupongerna, är aldrig en skänkel, och ingen insats eller tes vilar på dem. De ligger
också utanför kupongbudgeten och redovisas i sektion 3, på egen liten peng. Odds saknas normalt i alla källor
(**I8**) — därför bär tabellen sannolikhet och rimligt odds istället för en oddskolumn.

## 5. Medvetet undvikna spel

```markdown
## ⚠️ Medvetet undvikna spel

| Marknad | Varför |
|---|---|
| Alla 1H-marknader | Måltidsfördelning inte dragen för något lag (**D2**) |
| Arsenal vinst 1,78 | Läsningen rätt, priset fel — kräver 56%, skattning 52% (**I4**) |
| BTTS PSG–Slovan 2,75 | Bussparkering identifierad (**C9**) |
```

Sektionen är obligatorisk och får inte vara tom. Om varje marknad som övervägdes
gick vidare till en kupong är urvalet inte gjort.

**1H-marknader hör inte automatiskt hit.** Tidigare krävde mallen att varje
1H-marknad utan verifierad måltidsfördelning skrevs in i den här sektionen. Det var en
veto-regel utan stöd: den strök 14 1H-ben i mars-granskningen, varav 13 landade, och
1H Över 0,5 gick 23/26 den månaden. **D2** är numera en konfidensmodifierare —
saknad måltidsdata *sänker* siffran och ska redovisas på marknadsraden, men avvisar
inte marknaden. Hit hör en 1H-marknad bara om den faller på värde, pris eller
korrelation som alla andra. Och åt andra hållet: 26 observationer räcker inte till en
regel *för* 1H-marknader heller (**A2b**).

## 6. Kort

```markdown
## 🟨 Kort

| Domare | Match | Gula/match | Urval |
|---|---|---|---|

<Slutsats: vem som är kvällens kortdomare, och om ett kortspel rekommenderas.>
```

Krav som gäller varje gång:
- Karriärsiffra när säsongsurvalet är under åtta matcher, och skriv vilken som
  används (**G3**).
- Kortspel är **singlar**, aldrig i de fyra kupongerna (**G4**).
- Utan bookmakerns linje och lagens egna kort per match: rekommendera inget, och
  skriv varför (**G5**, **G9**).

## 7. Felmarginal & insatser

```markdown
## 📐 Felmarginal & insatser

<Var edgen är tunn nog att försvinna inom den egna skattningen (**I5**).>
<Kvarts-Kelly för minst den mest utsatta kupongen (**I6**).>
<Kvällens svagaste punkt: korrelation, koncentration, eller att alla kuponger
lutar samma väg.>
<Delad exponering i kronor (**L6**): hur mycket som hänger på mål totalt, på en
enskild match, på ett lag och på en enda tes — inklusive spel du lagt utanför
kupongerna. Om allt lutar samma väg ska det stå, och totalen sizas ned; att tvinga in
en negativ-EV-Under för att se balanserad ut är sämre (**H3**, **L6**).>
```

## 8. Checklista

```markdown
## ✅ Checklista

**Verifiering** — tränare/skador/avstängningar ✅ · full trupp ✅ · turneringsomfång ✅ · domarstatistik ⚠️ 3/6
**Kalibrering** — inget resultatspel över 8 ✅ · 8+ datapunkter ⚠️ (7 för Arsenal-under) · A4 ✅ · A5 ✅
**Målmarknader** — C1/C2/C3 ✅ · C4 ✅ · C6 ✅ · C9 ✅ · D2 ✅ uteslutna
**Marknadsval** — K1 ✅ matchbild före marknad · K2 ✅ stegen gången · K4 ✅ lagtotal prissatt · K5 ✅ jämförelsetabell · K6 ✅ (1X2) · N9 ✅ sjustegsordningen följd
**Bevis och priors** — A2b ✅ marknadsprior har 30+ obs eller är märkt WEAK EVIDENCE · A7 ✅ BTTS-cap på utfallskonfidens · N8 ✅ priorn utfrågad på alla sju frågor · H8 ✅ bästa marknaden spelad eller förklarad
**Osäkerhet** — L1 ✅ band på varje p · L2 ✅ drivare namngivna · L3 ✅ motståndarjusterad form · L4 ✅ motargument med effekt · L5 ✅ PASS övervägt · M1 ✅ två konfidenssiffror
**Singelspel** — varje rad återfinns i sektion 4 eller 6 ✅ · inga skänklar ✅ (G4, J6) · Typ-kolumn ifylld ✅ · insatser utanför kupongbudgeten ✅
**Kuponger** — H2 ✅ · H3 ✅ · H5 ✅ · H6 ✅ · H7 ✅ · H8 ✅ · L6 ✅ delad exponering i kronor
```

En rad per block ur SKILL.md:s Pre-Bet Checklist, med ✅ / ⚠️ / ❌ per punkt.
**⚠️ kräver en parentes som säger vad som saknas.** En checklista där allt är
grönt varje kväll är inte en checklista.

## 9. Källor

```markdown
## 📚 Källor

<Länkar med källnamn.>

*Alla odds är indikativa och hämtade ur previewartiklar (**I7** — bookmakersajter
går inte att läsa). De kan ha rört sig; använd ditt eget pris.*
```

Kursiveringen är obligatorisk och ordagrann. Utan den läses odds i filen som
priser som gick att få.

## 10. Uppdatering (frivillig)

```markdown
## 🔄 Uppdatering <tid> — bekräftade startelvor

<Vad som ändrades mot antagandet i sektion 4.>

### Vad detta gör med kupongerna
<Vilken insats som faktiskt flyttas — eller uttryckligen: ingen.>

### 📚 Källor — uppdateringen
```

Bara när startelvorna bekräftas efter publicering. Underrubriken *Vad detta gör
med kupongerna* är obligatorisk i sektionen: en ändrad förutsättning som inte
flyttar en insats ska stå som ett aktivt beslut, inte som ett utelämnande.

## 11. Efteranalys

Läggs till efter matcherna, ordagrant den här strukturen:

```markdown
---

## 📊 Efteranalys

**90-minutersverifiering (C10):** <hur mål efter 90 hanterats — se regeln nedan.>

### Resultat
| Match | Resultat | Nyckelhändelser |
|---|---|---|
| Lag A – Lag B | X-X | Målskyttar, minuter |

### Marknadsutfall
| Match | Marknad | Prognos | Utfall | Resultat |
|---|---|---|---|---|
| Lag A – Lag B | Över 2,5 | ✅ väntat | 3 mål | ✅ |

### Kupongutfall
| Kupong | Resultat | Fallen skänkel |
|---|---|---|
| C1 — Ankare | ✅ / ❌ | — / vilken skänkel |

### Singelspelsutfall — samma rader som sektion 3
| Tid | Match | Spel | Typ | Odds | Sannolikhet | Insats | Utfall | Resultat |
|---|---|---|---|---|---|---|---|---|
| 21:00 | Lag A – Lag B | BTTS | Mål | 1,55 | 68% | 50 kr | 2-1 | ✅ |
| 21:00 | Lag A – Lag B | Hermoso bokad | Kort | 3,00 | 36% | 25 kr | inget kort, 78 min | ❌ |

*Kortrader kräver **linjen** i `Spel`-kolumnen när det är en lagtotal (`lag över 1,5
kort`), inte bara "kort" — den 8 september blev ett lagkortsspel obedömbart av precis
det skälet (2 kort, men över 1,5 landade och över 2,5 inte). Saknas linjen i
förhandsanalysen skrivs `linje ej angiven`.*

### Skott på mål (sidospel, utanför kupongerna — J6)
| Lag | Spelare | Linje | Sannolikhet | Spelade minuter | Skott på mål | Utfall |
|---|---|---|---|---|---|---|

### Totalt: X/Y kuponger | X/Y singelspel | Vinst/förlust: +/- X kr

*P/L-underlag: <vilka priser summan bygger på — faktiska, indikativa eller
filens egna rimliga odds — och spannet mellan dem.>*

### 🧠 Självutvärdering
- **Kalibrering:** ...
- **Kvällens bästa läsning:** ...
- **Kvällens sämsta läsning:** ...
- **Orsaksklassning per miss:** dåliga data · dålig tolkning · dålig sannolikhet ·
  **dåligt marknadsval** · dåligt pris · varians · recensbias (**L3**) · narrativbias
  (**L4**) · överkonfidens (**L1**) · korrelation (**L6**)
- **Lärdom:** ...
```

**90-minutersraden står direkt under rubriken**, inte i en tabell och inte i
löptext längre ner. Mål verifieras på **90 minuter** — förlängning räknas aldrig
(**C10**). Skriv ut vilka sena mål som räknats in och vilka som inte gjort det.

**Singelspelsutfallet är sektion 3:s singeltabell med två kolumner till.** Samma rader, samma
ordning, samma sannolikheter — bara `Utfall` och `Resultat` tillagda. Skiljer sig
raderna från sektion 3 är antingen förhandsanalysen eller efteranalysen fel, och
tabellen ska inte "städas" så att de stämmer. Den bär **sannolikheten**, inte bara
resultatet: utan den blir tabellen en resultatlista utan kalibreringsvärde, och det
är dessa rader som förs över till `CALIBRATION.md` (**M2**).

**Skott på mål-tabellen tar med alla sex raderna per match — även de som ingen skulle
ha spelat — och kräver spelade minuter.** Hela poängen med sex rader är kalibrering:
fyra matcher ger 24 skattningar mot 24 mätbara utfall, vilket klarar **A2**:s krav på
åtta datapunkter på en vecka istället för en säsong (**J7**). Plockar man bara ut de
spelade raderna försvinner det underlaget.

Minutkolumnen är obligatorisk eftersom en rad faller på två helt olika sätt — han sköt
inte, eller han var inte på planen — och bara minuterna skiljer dem åt. Utan den
kalibreras **J4** aldrig, och en bänkad spelare läses i efterhand som en felaktig
skottläsning. Byttes han in eller ut: skriv minuterna, inte `startade`.

**P/L-underlaget är obligatoriskt när priserna inte är verkliga.** Totalraden
kräver en kronsiffra, men **I7** betyder att faktiska bookmakerpriser ofta inte
går att få. Skriv då vilka priser summan bygger på och spannet mellan dem —
den 8 september låg utfallet mellan -40 och -95 kr beroende på om man räknade
med indikativa marknadspriser eller filens egna rimliga odds, och -90 kr valdes
som konservativ post. En exakt siffra utan underlag är falsk precision.

En fil kan innehålla flera kupongset (ett per avsparkstid). Redovisa då varje
set separat plus en dagstotal.

**Orsaksklassningen gäller även vinster.** Ett vunnet spel kan vara en dålig
prediktion och ett förlorat kan vara en bra — utan klassning går de två inte att
skilja, och då justeras modellen av utfall i stället för av fel.

Efter efteranalysen: uppdatera `results.md` med ny rad, löpande totaler och
kumulativ P/L, och lägg nattens rader i `CALIBRATION.md` i bet-bot-brain (**M2**) —
en rad per rekommenderad marknad med angivet sannolikhetsband och utfall. `results.md`
mäter pengar, `CALIBRATION.md` mäter om siffrorna var ärliga. Skillförslag går via pull request, aldrig direkt i `SKILL.md`,
och bara med 8+ datapunkter (**A2**) eller som bekräftelse av en befintlig regel.
