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
odds och EV anges för varje rekommenderat spel — utan undantag (I1, I2, I3).

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

## 3. Match för match

```markdown
## 🔍 Match för match

### N. Hemma – Borta (tid)

**Läge.** Form i både liga och Europa, tabellposition, vem som måste jaga och om
de kan (**F10** — vilken turnering kommer formen från?).

**Truppnytt (bekräftat <datum>).** Skador, avstängningar, avstängningens
turneringsomfång (**E6**), hela tillgängliga truppen (**E1**). Aldrig antaget.

**Läsning.** Tesen i två till fyra rader, med regelhänvisningar där en regel
faktiskt styr slutsatsen.

**Marknader.**
- **<Marknad>** — p **X%**, rimligt odds **Y**. Marknad Z (indikativt, källa). EV +N%. 🟢 8/10
- **<Marknad som avstås>** — kräver p X%, skattning Y%. Negativt EV. Avstå.
```

En matchrubrik per match, numrerad. Inga emoji i matchrubrikerna — trafikljuset
i marknadsraderna bär signalen istället, och emoji per lag blev slumpmässigt i
marsfilerna.

Avstådda marknader hör hit, inte bara i sektion 5: det är i matchen resonemanget
finns. Sektion 5 samlar bara de beslut som gäller hela kvällen.

## 4. Kuponger

```markdown
## 🎯 Kuponger — <budget> kr

| # | Typ | Spel | Konfidens | Odds | p | Rimligt | EV | Insats |
|---|---|---|---|---|---|---|---|---|
| 1 | Ankare | PSG vinst & ö2,5 | 🟢 8/10 | 1,22 | 85% | 1,18 | +4% | 100 kr |
| 2 | Huvudspel | Barça ö2,5 + Sporting ö2,5 | 🟡 7/10 | 2,04 | 51% | 1,96 | +4% | 80 kr |
| 3 | Hedge | Napoli–Arsenal u2,5 | 🟡 6,5/10 | 1,91 | 55% | 1,82 | +5% | 70 kr |
| 4 | Uppsida | Stuttgart ö2,5 + Liverpool ö2,5 | 🔴 5/10 | 2,27 | 45% | 2,20 | +3% | 50 kr |

**C1 — Ankare.** Tes: ... · Regel: **H10** (säkraste marknaden, inte bästa oddset)
**C2 — Huvudspel.** Tes: ... · Regel: **H1** (max 2–3 skänklar)
**C3 — Hedge.** Tes: ... · Regel: **H6** (motsatt tes mot C1/C2), **H3** (defensiv)
**C4 — Uppsida.** Tes: ... · Regel: **H7** (<vilken skänkel som är den trygga>)

**Matcher per kupong:** C1 PSG · C2 Barça, Sporting · C3 Napoli · C4 Stuttgart,
Liverpool — inga delade matcher (**H5**).
```

Tabellen först, sedan en rad per kupong: tes plus den regel som styr just den
kupongens roll. En rad, inte ett stycke — motiveringen finns i sektion 3.

Raden `Matcher per kupong` är obligatorisk. **H5** går inte att kontrollera i
efterhand utan den, och den 8 september kostade en oflaggad matchkoncentration
180 av 300 kr.

Förkortningar i tabellen: `ö2,5` över 2,5 mål · `u2,5` under 2,5 · `BTTS` ·
`BTTS-N` båda lagen gör mål: nej.

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
gick vidare till en kupong är urvalet inte gjort. **1H-marknader utan verifierad
måltidsfördelning skrivs alltid in här** — det är den enda platsen där **D2**
faktiskt syns.

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
```

## 8. Checklista

```markdown
## ✅ Checklista

**Verifiering** — tränare/skador/avstängningar ✅ · full trupp ✅ · turneringsomfång ✅ · domarstatistik ⚠️ 3/6
**Kalibrering** — inget resultatspel över 8 ✅ · 8+ datapunkter ⚠️ (7 för Arsenal-under) · A4 ✅ · A5 ✅
**Målmarknader** — C1/C2/C3 ✅ · C4 ✅ · C6 ✅ · C9 ✅ · D2 ✅ uteslutna
**Kuponger** — H2 ✅ · H3 ✅ · H5 ✅ · H6 ✅ · H7 ✅ · H8 ✅
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

<Vad som ändrades mot antagandet i sektion 3.>

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

### Kortspel (singlar, utanför kupongerna — G4)
| Spel | Konfidens | Linje | Odds | Insats | Utfall | Resultat |
|---|---|---|---|---|---|---|

### Totalt: X/Y kuponger | Vinst/förlust: +/- X kr

*P/L-underlag: <vilka priser summan bygger på — faktiska, indikativa eller
filens egna rimliga odds — och spannet mellan dem.>*

### 🧠 Självutvärdering
- **Kalibrering:** ...
- **Kvällens bästa läsning:** ...
- **Kvällens sämsta läsning:** ...
- **Lärdom:** ...
```

**90-minutersraden står direkt under rubriken**, inte i en tabell och inte i
löptext längre ner. Mål verifieras på **90 minuter** — förlängning räknas aldrig
(**C10**). Skriv ut vilka sena mål som räknats in och vilka som inte gjort det.

**Kortspelstabellen kräver konfidens och linje.** Konfidensen är det man
kalibrerar mot i efterhand; utan den blir tabellen en resultatlista utan
lärdom. Och utan bookmakerns **linje** går utfallet inte att bedöma alls —
den 8 september redovisades ett lagkortsspel som obedömbart av precis det
skälet (2 kort, men över 1,5 landade och över 2,5 inte). Står linjen inte i
förhandsanalysen ska cellen säga `ej angiven`, inte lämnas tom.

**P/L-underlaget är obligatoriskt när priserna inte är verkliga.** Totalraden
kräver en kronsiffra, men **I7** betyder att faktiska bookmakerpriser ofta inte
går att få. Skriv då vilka priser summan bygger på och spannet mellan dem —
den 8 september låg utfallet mellan -40 och -95 kr beroende på om man räknade
med indikativa marknadspriser eller filens egna rimliga odds, och -90 kr valdes
som konservativ post. En exakt siffra utan underlag är falsk precision.

En fil kan innehålla flera kupongset (ett per avsparkstid). Redovisa då varje
set separat plus en dagstotal.

Efter efteranalysen: uppdatera `results.md` med ny rad, löpande totaler och
kumulativ P/L. Skillförslag går via pull request, aldrig direkt i `SKILL.md`,
och bara med 8+ datapunkter (**A2**) eller som bekräftelse av en befintlig regel.
