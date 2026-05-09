---
name: bvb-macro-ro
description: Context macro Romania pentru investitori BVB. Dobanda referinta BNR, ROBOR, curs RON/EUR/USD, inflatie (IPC) INS, PIB, somaj, deficit bugetar, datorie publica, rating tara (Fitch/S&P/Moody's), spread CDS RO, sentiment investitori straini. Coreleaza cu impactul asupra sectoarelor BVB banci sensibile dobanda, utilitati sensibile politic, exportatori sensibili curs. Folosit cand user cere "impact dobanda BNR pe TLV", "context macro RO 2025", "cum afecteaza inflatia bursa", "rating Romania", "curs RON".
---

# Context macro RO pentru BVB

## Trigger

User cere context economic Romania, impact dobanzi/inflatie/curs asupra bursei sau emitentilor specifici.

## Disclaimer

> ⚠️ Datele macro sunt revizuite frecvent. Verifica pe BNR/INS pentru cele mai recente cifre. Corelatiile macro-bursa sunt tendinte, nu legi - excursii pe termen scurt sunt normale.

## Workflow

### Pas 1 - Tip cerere

1. **Snapshot macro** - sumar curent indicatori cheie
2. **Impact pe sector/ticker** - cum afecteaza X actiuni Y emitenti
3. **Trend / istoric** - evolutie pe N luni/ani
4. **Comparatie regionala** - RO vs PL, HU, CZ

### Pas 2 - Date de colectat

Prioritate, vezi `../bvb-stock-analysis/references/surse.md`:

**Politica monetara (BNR)** - bnr.ro:
- Dobanda referinta (rata politica monetara)
- Lombard, depo facility
- ROBOR 3M, 6M, 12M
- Comunicat ultim board BNR
- Prognoza inflatie BNR

**Inflatie (INS)** - insse.ro:
- IPC anual (yoy), lunar
- Inflatie de baza (core)
- Asteptari inflatie

**Activitate economica (INS / Eurostat)**:
- PIB trimestrial yoy
- Productie industriala
- Vanzari retail
- Somaj
- Cont curent

**Curs valutar (BNR)**:
- RON/EUR, RON/USD curent si tendinta 12 luni
- Interventii BNR

**Fiscal-bugetar (MF)**:
- Deficit bugetar % PIB
- Datorie publica % PIB
- Eurobonduri RO randament 5y, 10y

**Rating tara**:
- Fitch, S&P, Moody's - ultim rating si outlook
- Spread CDS Romania 5y vs Germania

**Politic / regulator**:
- Bugetul anual
- OUG-uri cu impact bursier (taxe sectoriale, plafonari)
- Legi pensii, salariale

### Pas 3 - Mapare impact pe BVB

| Macro shock | Impact BVB |
|-------------|------------|
| BNR creste dobanda | Banci (TLV, BRD): pe termen scurt + (marja); pe termen lung - (cerere credit). Imobiliare (ONE, IMP): -. Companii indatorate: -. |
| BNR scade dobanda | Banci: marje sub presiune. Imobiliare: +. Indatorate: +. Dividend stocks (utilitati): + (pe yield comparat). |
| Inflatie sus | Companii cu putere pricing (utilitati reglementate cu pass-through, banci variable rate): +. Companii cost-bound (industriale): -. |
| RON slab | Exportatori / venituri EUR (DIGI partial, SNP partial): +. Importatori / cost EUR: -. Datorie EUR: -. |
| Rating taiat | Toata bursa -, banci si stat in special. |
| Risc politic (alegeri, OUG) | Companii de stat: volatilitate +. |
| Recesiune | Ciclic (banci, real estate, consumer): -. Defensiv (utilitati, pharma): mai bine relativ. |

### Pas 4 - Output

#### Snapshot macro
```
# Macro RO - [data]

## Politica monetara
- Dobanda BNR: X%
- ROBOR 3M: X%
- Ultima decizie board: [data] [actiune]

## Inflatie
- IPC anual: X% (target BNR: 2.5% +/- 1pp)
- Trend: [crestere / stabil / dezinflatie]

## Activitate
- PIB yoy ultim T: X%
- Somaj: X%

## Curs
- RON/EUR: X (var 12L: +/-X%)
- RON/USD: X

## Fiscal
- Deficit buget: X% PIB
- Datorie publica: X% PIB
- Eurobond 10y RO: X%

## Rating
- Fitch / S&P / Moody's: ratings + outlook
- CDS 5y: X bp

## Implicatii BVB (sumar)
- Sectoare favorizate: [...]
- Sectoare presate: [...]
- Riscuri pe orizont 3-6 luni: [...]
```

### Pas 5 - Avertismente

- Macro -> bursa nu e direct si imediat. Decalaje 3-12 luni tipice.
- Surprize > nivel absolut. Piata reactioneaza la diferenta vs asteptari.
- RO e small-open economy: ECB, Fed, sentimentul global emerging markets domina pe termen scurt mai mult decat factori interni.
- Risc politic specific RO greu de modelat - tine cont in scenarii bear.

## Comparatie regionala (CEE)

Utila pentru context. Surse: Eurostat, FMI, banci centrale (NBP, MNB, CNB).

| Indicator | RO | PL | HU | CZ |
|-----------|----|----|----|-----|
| Dobanda BC | | | | |
| Inflatie | | | | |
| PIB yoy | | | | |
| Rating | | | | |

Investitori straini compara CEE-4. RO underperform vs peers daca rating sau politica fiscala derapeaza.


---

*Produs de [LawChat.ro](https://lawchat.ro) © 2026*
