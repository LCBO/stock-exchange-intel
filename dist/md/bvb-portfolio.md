---
name: bvb-portfolio
description: Review si optimizare portofoliu de actiuni BVB. Analizeaza concentrare pe ticker/sector, expunere risc politic (companii de stat), corelatii intra-portofoliu, randament dividend agregat, marime pozitii, lichiditate combinata, evaluare overlap cu indicele BET. Folosit cand utilizatorul listeaza actiunile detinute si cere "review portofoliul meu", "sunt prea concentrat", "diversificat?", "cat risc politic am", "ce sa adaug pentru echilibru".
---

# Review portofoliu BVB

## Trigger

User furnizeaza lista pozitii (ticker + cantitate sau ticker + valoare/procent) si cere review.

## Disclaimer obligatoriu

> ⚠️ Acest review nu este consultanta de portofoliu. Pentru aliniere obiective personale (orizont, toleranta risc, situatie fiscala) consulta consilier financiar autorizat ASF. Nu cunosc situatia ta completa - alte active, datorii, venit, varsta, dependenti.

## Workflow

### Pas 1 - Adunare date portofoliu

Daca user nu a furnizat tot, intreaba:
- Lista completa pozitii (ticker + cantitate SAU procent din total)
- Valoare totala (pentru calcul absolut riscuri)
- Orizont investitie (1-3 ani / 3-10 ani / > 10 ani)
- Obiectiv: crestere capital / venit dividend / mixed
- Alte active (cont depozit, titluri stat, fonduri, imobiliare) - context expunere globala
- Toleranta drawdown (cat e ok sa scada in criza?)

### Pas 2 - Calcule de baza

Pentru fiecare pozitie: ticker, % portofoliu, sector, capitalizare emitent, beta vs BET, dividend yield, lichiditate.

La nivel portofoliu:
- Top 3 si top 5 ponderi - daca > 60% si respectiv > 80% = concentrare mare
- Distributie pe sector (target uzual: nici un sector > 35-40%)
- % expunere companii de stat (SNG, TGN, TEL, EL, SNN, H2O, COTE)
- % expunere financiar (TLV, BRD, BVB)
- % expunere energie/commodity (SNP, SNG)
- Yield mediu ponderat
- Beta portofoliu vs BET (suma ponderata)
- Lichiditate ponderata zilnic - cat poti vinde fara impact pret

### Pas 3 - Evaluare diversificare

Reguli generale (NU absolute):

- O singura pozitie nu ar trebui sa depaseasca 15-20% portofoliu RO
- Top 5 sub 70% (altfel = concentrare extrema)
- Min 8-10 emitenti pentru diversificare rezonabila pe BVB (universul e mic)
- Max 35-40% un singur sector
- Max 50% companii de stat (risc politic concentrat)
- Pondere small cap (cap < 200M EUR) max 15-20%

### Pas 4 - Risc concentrare specific RO

Verifica:
- **Risc tara**: 100% BVB = 100% RO. Recomanda diversificare cu actiuni internationale (S&P500 ETF, MSCI World ETF prin broker RO sau european).
- **Risc politic**: % stat majoritar in portofoliu
- **Risc commodity**: SNP+SNG combinate - expunere pret gaz/petrol
- **Risc dobanda**: TLV+BRD - expuse decizii BNR si recesiune
- **Risc curs**: dividende toate in RON; daca cheltuiesti in EUR, expunere FX
- **Lichiditate combinata**: cat poti lichida in 1-3 zile fara > 5% impact pret

### Pas 5 - Comparatie cu indicele BET

Calculeaza overlap: cat % din portofoliu coincide cu ponderile BET. Daca > 80% similar BET, intreaba user daca nu ar fi mai eficient ETFBET (ETF pe BET) - costuri management mici, diversificare automata.

### Pas 6 - Output

```
# Review portofoliu BVB
## Data: [YYYY-MM-DD] | Valoare estimata: X RON

## Compozitie
| Ticker | Sector | Pondere | Yield | Lichiditate | Note |
|--------|--------|---------|-------|-------------|------|

## Indicatori agregati
- Numar pozitii: X
- Top pozitie: TICKER (X%)
- Top 3 pondere: X%
- Sectorul cel mai expus: X (X%)
- % companii de stat: X%
- Yield ponderat: X%
- Beta vs BET (estimat): X
- Lichiditate combinata 5%: X RON in Y zile

## Analiza diversificare
- Concentrare ticker: [ok / mediu / ridicat] - [comentariu]
- Concentrare sector: [...]
- Risc politic stat: [...]
- Diversificare RO vs international: [...]

## Puncte forte
- ...

## Puncte de atentie
- ...

## Sugestii pentru echilibru (NU recomandari)
- Daca > 40% banci -> reduce TLV/BRD sau adauga sector diferit
- Daca > 50% stat -> ia in considerare emitenti privati (TLV, M, DIGI, AQ, WINE, SFG, ATB, ONE)
- Daca lipseste expunere consumer/retail -> AQ, WINE, SFG, M
- Daca 100% RO -> ETF international via broker european / RO (atentie cost custodie + impozit)
- Daca ai > 12 pozitii mici -> simplifica, costurile broker erodeaza randament

## Comparatie cu BET
- Overlap cu BET: X%
- Daca > 80%: considera ETFBET pentru simplificare
```

## Avertismente

- NU rebalansa frecvent - costurile broker (0.3-0.65%/ordin) si fiscal (impozit castig) erodeaza
- Rebalansare anuala / la praguri (ex pondere > 1.5x target) e suficient
- NU vinde la panica - daca portofoliul e construit pe fundamente, drawdown 20-30% e normal in cicluri


---

*Produs de [LawChat.ro](https://lawchat.ro) © 2026*
