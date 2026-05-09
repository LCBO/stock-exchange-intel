---
name: bvb-market-news
description: Agregare stiri si calendar evenimente pentru Bursa de Valori Bucuresti. Sumar zilnic/saptamanal piata RO, stiri pe ticker, calendar ex-dividend si rapoarte trimestriale, sentiment piata. Folosit cand utilizatorul cere "ce stiri TLV", "sumar piata RO azi", "ce e cu BVB saptamana asta", "calendar dividende BET", "de ce a scazut SNP", "ce a anuntat Hidroelectrica". Surse bvb.ro (comunicate), zf.ro, profit.ro, bursa.ro, economica.net, economedia.ro, plus IR pages emitenti.
---

# Stiri si calendar piata BVB

## Trigger

User cere stiri, sumar piata, calendar evenimente, sau context evenimente specifice pe ticker BVB.

## Disclaimer

Incepe cu:
> ⚠️ Material informativ. Stirile pot fi incomplete sau interpretate gresit. Verifica sursa primara (bvb.ro, raport oficial emitent) inainte de decizii.

## Workflow

### Pas 1 - Clarifica scop

- **Sumar zi/saptamana**: piata generala BET + top miscari + stiri majore
- **Stiri ticker**: focus pe 1 emitent
- **Calendar evenimente**: ex-dividend, AGA, raport T - urmatoarele 30/60/90 zile
- **Context eveniment**: "de ce a scazut/crescut X azi" - cauza specifica

### Pas 2 - Surse de cautare

Prioritate (vezi `../bvb-stock-analysis/references/surse.md`):

1. **bvb.ro** - sectiunea "Stiri" si "Comunicate emitenti" - sursa primara
2. **Brokeri**: Tradeville buletin, BT Capital, BRK comentariu zilnic
3. **Presa**: zf.ro (sectiunea Piete -> Bursa), profit.ro/bursa, bursa.ro, economica.net, economedia.ro
4. **IR emitent** pentru comunicate originale

Query-uri:
```
WebSearch: "[ticker] site:bvb.ro" -> comunicate oficiale
WebSearch: "BET indice azi site:zf.ro OR site:profit.ro"
WebSearch: "calendar dividende BVB 2025"
WebSearch: "[Companie] anunt site:profit.ro"
```

### Pas 3 - Filtrare semnal vs zgomot

PRIORITIZEAZA:
- Comunicate ASF / bvb.ro oficiale
- Rapoarte financiare publicate
- Anunturi dividend / split / buyback
- Schimbari conducere (CEO, CFO, presedinte CA)
- Tranzactii actionari mari (raportari ASF "persoane initiate")
- Tinte pret broker actualizate
- Decizii reglementare/legislative care afecteaza sectorul

DESPRIORITIZEAZA:
- Speculatii forum-uri
- "Influenceri" pe X/Tiktok
- Stiri repetate fara update

### Pas 4 - Format output

#### Sumar zilnic piata
```
# Piata BVB - [data]

## Indici
- BET: X puncte (+/-X%)
- BET-TR (total return): X%
- BET-XT, BET-NG, BET-FI: variatii

## Top crescatori (volum semnificativ)
1. [TICKER] +X% - [scurt motiv]
2. ...

## Top scazatori
1. [TICKER] -X% - [scurt motiv]
2. ...

## Stiri majore zi
- [bullet 1]
- [bullet 2]

## Calendar maine
- [emitent] raport T / ex-dividend / AGA

## Context macro RO
- BNR / curs RON / inflatie / decizii guvern relevante
```

#### Stiri pe ticker
```
# Stiri [TICKER] - [interval]

## Cele mai importante (cronologic, recente sus)
- [data] [titlu] - [sursa] - [1 linie context]

## Comunicate oficiale (bvb.ro)
- [data] [tip raport] - link

## Calendar urmator
- [event] [data]

## Interpretare (optional, cu mentiune "opinie")
Neutru / pozitiv / negativ pentru actiune, motive...
```

#### Calendar evenimente BET (next 30 zile)
Tabel: data | emitent | tip eveniment (ex-div / record / payment / raport T / AGA / split) | detalii (suma dividend, etc.)

### Pas 5 - Avertismente

- Stire pozitiva NU = trade buy. Pretul incorporeaza adesea anuntul rapid.
- "Buy on rumor, sell on news" e des aplicabil pe BVB
- Atentie la "pump" pe small caps via grup-uri Telegram/Discord - escrocherii

## Limite

- Date intra-day pe bvb.ro sunt delayed 15 min pentru public.
- Sambata/duminica - bursa inchisa, doar IR si presa active.
- Sarbatori legale RO - bursa inchisa, marcheaza in calendar.


---

*Produs de [LawChat.ro](https://lawchat.ro) © 2026*
