---
name: bvb-screener
description: Screener pentru actiunile listate la Bursa de Valori Bucuresti (BET, BET-XT, AeRO). Filtreaza dupa criterii dividend yield, P/E, P/B, ROE, capitalizare, volum, performanta YTD/1Y, sector, RSI, distanta fata de MA200. Folosit cand utilizatorul cere "actiunile RO cu cel mai mare dividend", "BVB sub P/E 8", "care emitenti BET sunt supravanduti", "top crestere YTD bursa Bucuresti", "actiuni RO ieftine". Genereaza tabele filtrate cu explicatii pentru incepatori.
---

# Screener BVB

## Trigger

User cere lista actiuni RO filtrate dupa unul/mai multe criterii.

## Disclaimer

> ⚠️ Screener-ul produce o lista de candidati pentru analiza, NU recomandari. Fiecare ticker rezultat trebuie analizat individual. Vezi `bvb-stock-analysis`.

## Workflow

### Pas 1 - Determina criteriile

Intreaba user (daca neclar) folosind AskUserQuestion. Criterii uzuale:

**Valoare:**
- P/E max (ex < 10)
- P/B max (ex < 1.5)
- EV/EBITDA max

**Randament:**
- Dividend yield min (ex > 6%)
- Payout ratio max (ex < 80%) - sustenabilitate

**Calitate:**
- ROE min (ex > 12%)
- Datorie net/EBITDA max (ex < 3)
- Marja neta min

**Crestere:**
- EPS growth 3y min
- Revenue CAGR min

**Tehnic:**
- RSI < 30 (supravandut) sau > 70 (supracumparat)
- Pret > MA200 (uptrend) sau < MA200
- Distanta de la max 52w

**Lichiditate (filtru obligatoriu pentru retail):**
- Volum mediu RON/zi min - DEFAULT > 100k RON/zi
- Capitalizare min - DEFAULT > 100M RON
- Free float min - DEFAULT > 25%

**Sector:**
- Banking / Energy / Utilities / Pharma / Telecom / Real estate / Consumer / Industrial

### Pas 2 - Universul

- **BET** (default) - top blue chips, lichiditate decenta
- **BET-XT** - extins, mai multe small caps
- **AeRO** - micro caps, atentie risc inalt
- **All BVB** - tot ce e listat

Lista tickere: vezi `../bvb-stock-analysis/references/tickere-bet.md`

### Pas 3 - Colectare date (web search per ticker)

NU exista API gratuit consolidat pentru BVB. Strategie:

1. Pleaca de la lista tickere universe ales
2. Pentru fiecare, WebSearch pe bvb.ro / Tradeville / TradingView pentru P/E, dividend yield, ROE, etc.
3. Pune intr-un tabel
4. Filtreaza in tabel

Pentru screener larg (>10 tickere), avertizeaza user ca dureaza si propune sa se concentreze pe BET (20 emitenti).

Alternativ: foloseste agregatori (TradingView screener cu filtru BVB, simplywall.st, stockanalysis.com cu .RO) - dar verifica datele.

### Pas 4 - Output

```
# Screener BVB - [criterii]
## Universe: [BET / BET-XT / All]
## Data: [YYYY-MM-DD]

| Ticker | Companie | Pret | P/E | Div Y | ROE | Vol/zi | [criteriu] | Status |
|--------|----------|------|-----|-------|-----|--------|------------|--------|
| ... | | | | | | | | ✓ |
| ... | | | | | | | | ✗ datorie |

N emitenti indeplinesc TOATE criteriile: [lista].

## Top 3 candidati pentru analiza aprofundata
1. [TICKER] - [de ce iese in evidenta]
2. ...
3. ...

## ⚠️ Atentie
- [TICKER X] are dividend yield 15% dar payout > 100% -> nesustenabil
- [TICKER Y] are P/E mic dar profit in declin 3 ani consecutivi
- [TICKER Z] sub volum prag - foarte ilichid

## Pasi urmatori
Foloseste skill-ul `bvb-stock-analysis` pe top candidati pentru raport complet.
```

### Pas 5 - Avertismente specifice

- P/E mic poate fi capcana valoare ("value trap")
- Dividend yield mare poate semnala risc dividend cut
- RSI < 30 nu = automat "buy" - poate continua scaderea
- Screener-ul foloseste date statice; piata se misca

## Preset-uri uzuale (sugestii daca user nu specifica)

### "Dividend solid"
Div yield > 6%, payout < 80%, ROE > 10%, datorie/EBITDA < 3, vol > 200k RON/zi

### "Value classic"
P/E < 10, P/B < 1.5, ROE > 10%, datorie/EBITDA < 3

### "Quality at reasonable price"
ROE > 15%, marja neta > 10%, P/E < 15, EPS growth 3y > 5%

### "Pullback in uptrend"
Pret < MA50 dar > MA200, RSI 30-45, pret 5-15% sub max 52w

### "Oversold rebound candidate"
RSI < 30, pret > MA200, fundamente OK (ROE > 10%, datorie/EBITDA < 3)


---

*Produs de [LawChat.ro](https://lawchat.ro) © 2026*
