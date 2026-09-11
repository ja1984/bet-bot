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

# Strukturen

Sektion 1–10 finns i varje fil, i den här ordningen. Sektion 11 bara när
startelvorna bekräftas efter publicering. Sektion 12 läggs till efter matcherna.

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

## 3. Match för match

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

| Marknad | Sannolikhet | Band | Odds | Brytpunkt | Värde | Tesmatchning |
|---|---|---|---|---|---|---|
| Över 2,5 | 68% | 62–72% | 1,65 | 60,6% | Stark | Stark |
| BTTS | 59% | 52–64% | 1,70 | 58,8% | Svag | Medel |
| Hemmalaget över 1,5 | 61% | 55–66% | 1,75 | 57,1% | Medel | Stark |
| Hemmalaget över 2,5 | 38% | — | `PRIS EJ TILLGÄNGLIGT` | — | — | Stark |
| Bästa 1X2 | 72% | 67–76% | 1,30 | 76,9% | Svag | Medel |

<En rad: varför den valda marknaden uttrycker matchbilden bättre än de närmaste
alternativen — och om BTTS var kandidat, varför den *inte* vann jämförelsen (**K2b**).>

**Motargument (L4).** <Det starkaste argumentet *mot* spelet, plus den enskilt
viktigaste motsägande datapunkten — och hur mycket den flyttade sannolikheten.>

**Marknader.**
- **<Marknad>** — p **X% (band A–B%)**, rimligt odds **Y**. Marknad Z (indikativt, källa). EV +N%. Utfallskonfidens **7/10** · spelkvalitet 🟢 **7,5/10**
- **<Marknad som avstås>** — kräver p X%, skattning Y%. Negativt EV. Avstå.
**Beslut (N1).** Tre frågor, besvarade var för sig:

| | |
|---|---|
| **Bästa fotbollsprognos** | <vad som mest sannolikt händer — utan marknad> |
| **Bästa marknad** | <marknad> |
| **Sannolikhet** | <X% (band A–B%)> |
| **Odds** | <faktiskt hämtat pris, källa> |
| **Brytpunkt** | <1/odds> |
| **Värde** | Stark / Medel / Svag |
| **Spelkonfidens** | Hög / Medel / Låg |
| **Starkaste motargument** | <mest sannolika förlustscenariot — och om någon annan marknad överlever det bättre (**N4**)> |
| **Beslut** | 🟢 **SPELA** / 🟡 **LITET SPEL** / 🔴 **PASS** |
| **Varför denna marknad i stället för BTTS / över-under / 1X2** | <en mening> |

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

Avstådda marknader hör hit, inte bara i sektion 6: det är i matchen resonemanget
finns. Sektion 6 samlar bara de beslut som gäller hela kvällen.

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
också utanför budgeten i sektion 4 och redovisas i sektion 5, på egen liten peng. Odds saknas normalt i alla källor
(**I8**) — därför bär tabellen sannolikhet och rimligt odds istället för en oddskolumn.

## 4. Kuponger

```markdown
## 🎯 Kuponger — <budget> kr

| # | Typ | Spel | Spelkvalitet | Utfallskonf. | Odds | Sannolikhet | Band | Rimligt odds | EV | Insats |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | Ankare | PSG vinst & ö2,5 | 🟢 7,5/10 | 8/10 | 1,22 | 85% | 80–88% | 1,18 | +4% | 100 kr |
| 2 | Huvudspel | Barça ö2,5 + Sporting ö2,5 | 🟡 7/10 | 2,04 | 51% | 1,96 | +4% | 80 kr |
| 3 | Hedge | Napoli–Arsenal u2,5 | 🟡 6,5/10 | 1,91 | 55% | 1,82 | +5% | 70 kr |
| 4 | Uppsida | Stuttgart ö2,5 + Liverpool ö2,5 | 🔴 5/10 | 2,27 | 45% | 2,20 | +3% | 50 kr |

- **C1 — Ankare.** Tes: ... · Regel: **H10** (säkraste marknaden, inte bästa oddset)
- **C2 — Huvudspel.** Tes: ... · Regel: **H1** (max 2–3 skänklar)
- **C3 — Hedge.** Tes: ... · Regel: **H6** (motsatt tes mot C1/C2), **H3** (defensiv)
- **C4 — Uppsida.** Tes: ... · Regel: **H7** (<vilken skänkel som är den trygga>)

**Matcher per kupong:** C1 PSG · C2 Barça, Sporting · C3 Napoli · C4 Stuttgart,
Liverpool — inga delade matcher (**H5**).
```

Tabellen först, sedan **en punktlista** med en post per kupong: tes plus den
regel som styr just den kupongens roll. En rad, inte ett stycke — motiveringen
finns i sektion 3. Listan måste vara punkter med tom rad före; fyra rader
`**C1 …**` efter varandra utan tom rad kollapsar till ett enda ihopklumpat
stycke när markdown renderas.

Raden `Matcher per kupong` är obligatorisk. **H5** går inte att kontrollera i
efterhand utan den, och den 8 september kostade en oflaggad matchkoncentration
180 av 300 kr.

Förkortningar i tabellen: `ö2,5` över 2,5 mål · `u2,5` under 2,5 · `BTTS` ·
`BTTS-N` båda lagen gör mål: nej.

## 5. Dagens singelspel

```markdown
## 🎲 Dagens singelspel

| Tid | Match | Spel | Typ | Odds | Sannolikhet | Band | Rimligt odds | EV | Spelkvalitet | Insats |
|---|---|---|---|---|---|---|---|---|---|---|
| 18:45 | Fenerbahçe – Roma | Över 2,5 mål | Mål | 1,68 | 62% | 56–66% | 1,61 | +4% | 🟡 6,5/10 | 40 kr |
| 18:45 | Fenerbahçe – Roma | Malen 2+ skott på mål | Skott | — | 51% | 45–56% | 1,96 | `pris ej belagt` | 🟡 6/10 | 20 kr |
| 21:00 | Slavia – Lens | BTTS | Mål | 1,55 | 68% | 62–72% | 1,47 | +5% | 🟡 7/10 | 50 kr |
| 21:00 | Slavia – Lens | Hermoso bokad | Kort | 3,00 | 36% | 30–40% | 2,78 | +8% | 🟡 6/10 | 25 kr |
| 21:00 | Como – Leipzig | Como över 1,5 | Lagtotal | 1,90 | 58% | 52–63% | 1,72 | +10% | 🟡 6,5/10 | 40 kr |

**Summa singelspel:** X kr — utanför kupongbudgeten i sektion 4.
**Delad exponering (L6):** <hur många av raderna som hänger på samma match, samma lag
och samma tes — och hur mycket i kronor.>
```

Det här är kvällens **översikt över alla enskilda spel**, i en enda tabell: mål,
BTTS, lagtotal, skott på mål, kort, resultat och 1H om något av dem
rekommenderas. Tabellen finns för att gå att skanna under kvällen — därför står
avsparkstiden först, medan sorteringen är **spelkvalitet, därefter sannolikhet**.

Krav som gäller varje gång:

- **Sektionen är en sammanställning, inte en ny analys.** Varje rad ska gå att hitta
  i sin matchsektion (sektion 3) eller i kortsektionen (sektion 7) med samma
  sannolikhet, samma band och samma pris. Står en rad bara här är den inte analyserad.
- **Inget här är en skänkel.** Raderna är singlar och byggs aldrig ihop till en
  kupong eller kombination (**G4**, **J6**) — kupongerna är sektion 4 och bär sin
  egen budget.
- **`Typ`-kolumnen är obligatorisk.** Den är det som gör översikten läsbar: fem
  rader som alla säger "Mål" är en tes i fem förklädnader, och det ska synas direkt
  (**L6**).
- **Insatserna ligger utanför de 300 kronorna** och summeras på egen rad. Kvarts-Kelly
  gäller per rad (**I6**), och kort- och spelarmarknader hålls små oavsett vad
  formeln säger (**G4**).
- **Pris som inte går att belägga skrivs `pris ej belagt`** med sannolikhet och
  rimligt odds kvar (**I8**) — läsaren jämför mot sitt eget spelbolag.
- **Tom tabell är ett giltigt utfall.** Finns inga singelspel värda pengar skrivs
  `inga singelspel ikväll` plus skälet — en rad som läggs in för att fylla tabellen
  är exakt det **L5** finns för att stoppa.

## 6. Medvetet undvikna spel

```markdown
## ⚠️ Medvetet undvikna spel

| Marknad | Varför |
|---|---|
| Alla 1H-marknader | Måltidsfördelning inte dragen för något lag (**D2**) |
| Arsenal vinst 1,78 | Läsningen rätt, priset fel — kräver 56%, skattning 52% (**I4**) |
| BTTS PSG–Slovan 2,75 | Bussparkering identifierad (**C9**) |
```

Sektionen är obligatorisk och får inte vara tom. Om varje marknad som övervägdes
gick vidare till en kupong är urvalet inte gjort. **1H-marknader utan verifierad
måltidsfördelning skrivs alltid in här** — det är den enda platsen där **D2**
faktiskt syns.

## 7. Kort

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

## 8. Felmarginal & insatser

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

## 9. Checklista

```markdown
## ✅ Checklista

**Verifiering** — tränare/skador/avstängningar ✅ · full trupp ✅ · turneringsomfång ✅ · domarstatistik ⚠️ 3/6
**Kalibrering** — inget resultatspel över 8 ✅ · 8+ datapunkter ⚠️ (7 för Arsenal-under) · A4 ✅ · A5 ✅
**Målmarknader** — C1/C2/C3 ✅ · C4 ✅ · C6 ✅ · C9 ✅ · D2 ✅ uteslutna
**Marknadsval** — K1 ✅ matchbild före marknad · K2 ✅ stegen gången · K4 ✅ lagtotal prissatt · K5 ✅ jämförelsetabell · K6 ✅ (1X2)
**Osäkerhet** — L1 ✅ band på varje p · L2 ✅ drivare namngivna · L3 ✅ motståndarjusterad form · L4 ✅ motargument med effekt · L5 ✅ PASS övervägt · M1 ✅ två konfidenssiffror
**Singelspel** — varje rad återfinns i sektion 3 eller 7 ✅ · inga skänklar ✅ (G4, J6) · Typ-kolumn ifylld ✅ · insatser utanför kupongbudgeten ✅
**Kuponger** — H2 ✅ · H3 ✅ · H5 ✅ · H6 ✅ · H7 ✅ · H8 ✅ · L6 ✅ delad exponering i kronor
```

En rad per block ur SKILL.md:s Pre-Bet Checklist, med ✅ / ⚠️ / ❌ per punkt.
**⚠️ kräver en parentes som säger vad som saknas.** En checklista där allt är
grönt varje kväll är inte en checklista.

## 10. Källor

```markdown
## 📚 Källor

<Länkar med källnamn.>

*Alla odds är indikativa och hämtade ur previewartiklar (**I7** — bookmakersajter
går inte att läsa). De kan ha rört sig; använd ditt eget pris.*
```

Kursiveringen är obligatorisk och ordagrann. Utan den läses odds i filen som
priser som gick att få.

## 11. Uppdatering (frivillig)

```markdown
## 🔄 Uppdatering <tid> — bekräftade startelvor

<Vad som ändrades mot antagandet i sektion 3.>

### Vad detta gör med kupongerna
<Vilken insats som faktiskt flyttas — eller uttryckligen: ingen.>

### 📚 Källor — uppdateringen
```

Bara när startelvorna bekräftas efter publicering. Underrubriken *Vad detta gör
med kupongerna* är obligatorisk i sektionen: en ändrad förutsättning som inte
flyttar en insats ska stå som ett aktivt beslut, inte som ett utelämnande.

## 12. Efteranalys

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

### Singelspelsutfall — samma rader som sektion 5
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

**Singelspelsutfallet är sektion 5 med två kolumner till.** Samma rader, samma
ordning, samma sannolikheter — bara `Utfall` och `Resultat` tillagda. Skiljer sig
raderna från sektion 5 är antingen förhandsanalysen eller efteranalysen fel, och
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
