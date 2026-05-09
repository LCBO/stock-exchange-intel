---
name: bvb-stock-analysis
description: Analiza completa a actiunilor listate la Bursa de Valori Bucuresti (BVB) - fundamentala (P/E, EPS, randament dividend, ROE, datorie), tehnica (medii mobile, RSI, MACD, suport/rezistenta), comparatii peer si rapoarte de investitie. Folosit cand utilizatorul cere analiza ticker BVB (ex "analizeaza TLV", "compara SNG vs TGN", "raport pe Hidroelectrica", "ce parere ai de SNP", "H2O dividend"). Acopera BET top 20 (TLV, SNP, H2O, BRD, FP, SNG, TGN, EL, M, DIGI, TEL, ATB, SNN, COTE, TRP, AQ, BVB, WINE, SFG, ONE) plus restul listei BET. Surse: bvb.ro, brokeri RO (Tradeville, BT Capital, BRK), presa (ZF, Profit, Bursa.ro). Mod incepator-friendly cu glosar inline si avertismente de risc obligatorii. NU este consultanta financiara.
---

# Analiza Actiuni BVB

## Trigger

Utilizator cere analiza ticker BVB (TLV, SNP, SNG, TGN, etc.), comparatie, raport, sau evaluare emitent listat la Bucuresti.

## Disclaimer obligatoriu

Incepe FIECARE raport cu:

> ⚠️ **Atentie**: Acest material este pentru informare si educatie. NU este recomandare de investitie, NU este consultanta financiara, NU garanteaza rezultate. Piata BVB este de tip frontier/emergenta - lichiditate redusa, volatilitate mare, spread-uri largi. Consulta un consilier autorizat ASF inainte de a investi. Trecutul nu garanteaza viitorul.

## Workflow

### Pas 0 - Clarificare cu utilizatorul (OBLIGATORIU daca request vag)

Daca user cere doar "analizeaza TLV" fara detalii, intreaba (foloseste AskUserQuestion daca disponibil):

1. **Tip analiza**: rapida (5 min) / fundamentala / tehnica / completa?
2. **Indicatori specifici doriti**: P/E, dividend yield, ROE, datorie, EPS growth, RSI, MACD, MA50/200, Bollinger, volum, support/rezistenta, beta, P/B?
3. **Orizont**: short-term trade / swing (saptamani-luni) / long-term investitie (ani) / dividend hold?
4. **Cu ce compara?**: peer sector (banci: TLV vs BRD; energie: SNP vs SNG; utilitati: TGN vs TEL vs EL) sau standalone?
5. **Nivel cunostinte**: incepator (explicatii inline) / experimentat (raport tehnic compact)?

Default daca user spune "oricum": completa + P/E + EPS + dividend yield + ROE + RSI + MA50/200 + comparatie peer + nivel incepator.

### Pas 1 - Identificare ticker

Normalizeaza simbol. Schema completa: vezi `references/tickere-bet.md`.

Daca ticker necunoscut sau ambiguu, cere clarificare. Atentie: simboluri RO se suprapun cu US (M = Macy's pe NYSE, M = MedLife pe BVB - foloseste mereu sufixul .RO sau context BVB).

### Pas 2 - Colectare date (WebSearch + WebFetch)

Lista surse autorizate (in ordine de prioritate): vezi `references/surse.md`.

Query-uri tip:
- `site:bvb.ro TLV cotatie` -> pret curent, volum, valoare tranzactionata
- `TLV raport anual 2025 site:bvb.ro` -> rezultate financiare
- `Banca Transilvania dividend 2025` -> politica dividend
- `TLV analiza Tradeville` / `TLV BT Capital target` -> rapoarte broker RO
- `Banca Transilvania stiri site:zf.ro OR site:profit.ro` -> stiri recente
- `BNR dobanda referinta` -> macro context

Date minime obligatorii:
1. Pret curent, variatie zi, variatie YTD, max/min 52 saptamani
2. Capitalizare bursiera, free float, lichiditate medie zilnica (RON)
3. P/E, P/B, EPS, ROE, randament dividend (yield)
4. Date financiare ultimul T si ultimul an (venit, profit net, marja)
5. Calendar evenimente (ex-dividend, raport trimestrial)
6. 3-5 stiri recente relevante

Daca date lipsa, NU inventa. Spune explicit "date indisponibile pentru X".

### Pas 3 - Aplicare framework

Citeste:
- `references/indicatori.md` - definitii si benchmark-uri pentru piata RO
- `references/glosar.md` - explicatii termeni pentru incepatori
- `references/raport-template.md` - structura output
- `references/risc-warnings.md` - red flags obligatorii

### Pas 4 - Generare raport

Urmeaza `references/raport-template.md`. Pentru utilizator incepator, fiecare metric primeste o linie de explicatie inline ("P/E = 8 inseamna ca pretul actiunii e 8x profitul anual pe actiune; mai mic = mai ieftin, dar verifica de ce").

### Pas 5 - Avertismente specifice RO

Verifica si include daca aplicabil:
- **Lichiditate redusa**: daca volum mediu < 500k RON/zi -> WARNING explicit, ordine limit obligatorii, slippage risc
- **Concentrare actionariat**: daca free float < 30% -> WARNING manipulare pret
- **Statul actionar majoritar**: SNG, TGN, TEL, SNN, EL, H2O - risc politic, dividend policy schimbabila
- **Dependenta sector unic**: SNP, SNG (gaz/petrol pretul commodity), banci (dobanda BNR)
- **Impozit dividend RO**: cota retinuta la sursa pentru rezidenti RO (verifica regula curenta - schimbata legislativ ultimii ani)
- **Curs RON/EUR**: emitent cu venituri EUR (ex DIGI) - expunere FX

## Tipuri de analiza

### A. Info rapid ("cat e TLV?")
- Pret + zi + YTD + capitalizare + P/E + dividend yield
- 1 paragraf context
- Disclaimer

### B. Fundamentala
- Business: ce face, sector, cota piata RO
- Financiare 3-5 ani: venit, profit, marje, ROE, datorie
- Evaluare: P/E vs istoric, vs peer RO, vs peer regional (CEE)
- Calitate management, dividend track record
- Riscuri specifice

### C. Tehnica
- Trend (MA50, MA200) - golden cross / death cross
- Momentum (RSI 14, MACD)
- Volatilitate (ATR, banzi Bollinger)
- Volum confirmare
- Niveluri suport/rezistenta din ultimele 6-12 luni
- ATENTIE: pe BVB volumul e adesea prea mic pentru indicatori tehnici fiabili. Mentioneaza explicit cand e cazul.

### D. Completa
A + B + C + comparatie peer + scenarii (bull/base/bear) + lista riscuri + concluzie nuantata (NU "cumpara"/"vinde")

## Comparatii peer tipice

- **Banci**: TLV vs BRD vs BVB (operator bursa)
- **Energie/Utilitati**: SNP vs SNG vs H2O vs SNN vs EL vs TEL vs TGN
- **Telecom/Media**: DIGI standalone (peer regional: Magyar Telekom, OTE)
- **Healthcare**: M (MedLife) vs ATB (Antibiotice)
- **Real estate/holding**: FP vs ONE vs IMP

## Limite

- NU recomanda explicit "cumpara" / "vinde". Foloseste "argumente pro / contra".
- NU prezice preturi tinta cu certitudine. Prezinta range si ipoteze.
- NU oferi consultanta fiscala. Trimite la consultant ASF/ANAF.
- Daca user cere "sigur cresc TLV" - refuza si explica de ce nimeni nu poate sti.

## Skill-uri inrudite din pack-ul BVB

- `bvb-market-news` - agregare stiri si calendar evenimente
- `bvb-screener` - filtre pe BET dupa criterii
- `bvb-dividend` - focus randament dividend RO
- `bvb-portfolio` - review portofoliu si concentrare
- `bvb-macro-ro` - context BNR, INS, curs


---

*Produs de [LawChat.ro](https://lawchat.ro) © 2026*
