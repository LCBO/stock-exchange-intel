---
name: bvb-dividend
description: Analiza si planificare strategie dividend pe BVB. Calculeaza randament, sustenabilitate (payout, cash flow, datorie), istoric distribuiri, calendar ex-dividend, impozit dividend RO, comparatie cu peer si cu randament titluri stat RO. Folosit cand utilizatorul cere "actiunile RO cu dividend mare", "e sustenabil dividendul TLV", "calendar dividende BET 2025", "cat dividend net iau dupa impozit", "strategie dividend bursa Bucuresti", "DRIP RO".
---

# Strategie dividend BVB

## Trigger

User intreaba despre dividende, randament, distribuiri, sau strategie venit pasiv din actiuni RO.

## Particularitati BVB pentru dividend

- Multe blue chips RO platesc dividend mare (yield 5-10%) - efect distributie statului ca actionar pentru SNG, TGN, EL, SNN, H2O
- Distribuire tipic ANUALA (nu trimestriala ca US) - exista si exceptii (TGN distribuiri intermediare)
- Plata in RON
- **Impozit pe dividend pentru rezident RO**: verifica regula curenta - din 2025 cota a fost ajustata. Confirma cu sursa fiscala curenta inainte de calcule nete.
- Nerezidenti: tratat in functie de conventie evitare dubla impunere
- Companiile NU au DRIP automat ca pe US - trebuie sa cumperi manual din dividendul incasat

## Disclaimer

> ⚠️ Material informativ. Politica dividend e decisa anual de AGA si poate fi schimbata. Pentru emitenti de stat, OUG poate modifica payout. Impozitarea poate fi schimbata legislativ. Consulta consilier fiscal pentru situatie personala.

## Workflow

### Pas 1 - Tip cerere

1. **Top emitenti dividend** - lista BET dupa yield
2. **Analiza sustenabilitate per ticker** - poate sustine dividendul?
3. **Calendar evenimente dividend** - ex-div, record, plata urmatoarele luni
4. **Calcul net dupa impozit** - randament real
5. **Strategie portofoliu dividend** - structura recomandata pentru venit

### Pas 2 - Date necesare per ticker

- Dividend brut pe actiune (DPS) ultimii 5 ani
- Pret curent -> yield gross curent
- Profit net si payout ratio (DPS / EPS)
- Cash flow operational vs DPS x nr actiuni - acopera distributia?
- Free cash flow vs dividend platit
- Datorie/EBITDA - presiune financiara?
- Track record: a redus vreodata dividend? Cand?

Surse: bvb.ro (rapoarte AGA), IR companie, Tradeville/BT Capital research.

### Pas 3 - Evaluare sustenabilitate

Semnale GREEN (probabil sustenabil):
- Payout < 80%
- FCF > dividend total platit (acoperire > 1.0x)
- Datorie/EBITDA < 2.5
- Profituri stabile/crescatoare 3-5 ani
- Track record fara taieri majore

Semnale RED (risc dividend cut):
- Payout > 100% an dupa an
- FCF < dividend platit (finantat din datorie)
- Datorie/EBITDA > 4 si in crestere
- Profituri in declin 2-3 ani
- Industrie ciclica in varf de ciclu
- Taxe extraordinare iminente (politic)

### Pas 4 - Calcul net

```
Dividend brut pe actiune: X RON
Impozit dividend RO rezident: [verifica cota curenta] %
Dividend net pe actiune: X * (1 - cota) RON

La pret curent P:
- Yield brut = X / P
- Yield net = X * (1 - cota) / P

La cumpararea de Y actiuni:
- Cost cumparare = Y * P + comision broker (~ 0.3-0.65%)
- Venit net dividend anual = Y * X * (1 - cota)
```

NU oferi consultanta fiscala individuala. Pentru calcul exact, consilier fiscal.

### Pas 5 - Comparatie cu alternative pasive RO

- Titluri de stat RO (Tezaur, Fidelis): randament curent X%
- Depozite bancare
- Obligatiuni corporative RO

Dividend bursier are RISC capital (pretul actiunii poate scadea) pe care titlurile de stat NU il au la maturitate. Yield mai mare la actiuni = compensatie risc.

### Pas 6 - Avertismente

- ⚠️ "Dividend trap" - yield 15-20% des inseamna pretul a cazut anticipand cut. Verifica intai sustenabilitate.
- ⚠️ Dividend special (one-off) NU = yield recurent. Separeaza in analiza.
- ⚠️ Concentrare sector la dividend RO: utilitati de stat domina lista. Diversifica.
- ⚠️ Risc politic: "taxa pe lacomie" sau OUG limitand dividend stat - precedente exista.
- ⚠️ Pretul scade in ziua ex-dividend cu valoarea dividendului - asta NU e pierdere, e ajustare contabila.

## Output recomandat

### Top emitenti BET dividend (sustenabili)
```
| Ticker | Yield brut | Yield net | Payout | FCF cover | Datorie/EBITDA | Verdict |
|--------|-----------|-----------|--------|-----------|----------------|---------|
| H2O | 9% | X% | 75% | 1.2x | 0.5 | Sustenabil |
| ... | | | | | | |
```

### Sablon strategie venit dividend (ilustrativ - NU recomandare)
- 30-40% portofoliu in 4-6 emitenti BET cu dividend sustenabil, sectoare diferite
- Restul in titluri stat / depozite / actiuni internationale
- Reinvestire manuala dividend daca scop = capitalizare
- Impozit anual de declarat la ANAF (dividende interne retinute la sursa, dar declarare anuala obligatorie pentru sume cumulative)


---

*Produs de [LawChat.ro](https://lawchat.ro) © 2026*
