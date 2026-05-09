# Surse de date pentru piata RO

Ierarhie de incredere (sus = mai oficial):

## 1. Oficial - reglator si bursa

- **bvb.ro** - cotatii live (delayed 15 min pentru public), rapoarte emitenti, calendar evenimente, comunicate. Sectiunea "Emitenti" -> ticker -> Rapoarte.
- **asfromania.ro** - reglementari, sanctiuni, decizii ASF
- **bnr.ro** - dobanda referinta, curs RON, rapoarte stabilitate financiara
- **insse.ro** - INS - inflatie (IPC), PIB, somaj
- **mfinante.gov.ro** - buget, datorie publica

## 2. Investor relations emitent

- Pagini IR oficiale (ex: tlv.ro/investitori, omvpetrom.com/investors, hidroelectrica.ro). Rapoarte anuale, prezentari investitori, transcripts conferinte.

## 3. Brokeri RO - rapoarte de cercetare

- **Tradeville** (tradeville.ro) - analize, target price, buletine
- **BT Capital Partners** (btcapitalpartners.ro) - research banci/utilitati
- **BRK Financial Group** (brk.ro) - rapoarte si comentarii zilnice
- **Banca Transilvania - BT Brokerage** - reports clienti
- **Wood & Company** (wood.cz) - acopera CEE inclusiv RO, mai institutional
- **Erste/BCR research** - reports CEE
- **Raiffeisen Centrobank** - CEE coverage

CAUTA: `"TLV target price [broker]"` sau `"[ticker] analiza [broker] 2025"`.

## 4. Presa financiara RO

- **zf.ro** (Ziarul Financiar) - principal, multe analize
- **profit.ro** - stiri rapide piata
- **bursa.ro** - ziar financiar dedicat
- **economica.net** - macro + companii
- **economedia.ro**, **republica.ro** (sectiunea economie)
- **mediafax.ro / digi24.ro / news.ro** - generaliste, sectiune economie

## 5. Internationale relevante

- **Reuters / Bloomberg** - quote in EUR, perspectiva globala
- **TradingView** - charting si comunitate (atentie la cherry-picking analize)
- **Stooq, Investing.com** - date istorice
- **Yahoo Finance** - cu sufix `.RO` sau `.BVB` pentru tickere

## 6. Sociale (folosit cu PRECAUTIE)

- Forumuri tradeville/forum.softpedia.com investitii - sentiment, NU date
- X/Twitter analisti RO - filtreaza foarte selectiv
- Reddit r/RomaniaInvest, r/Romania - sentiment retail

NU folosi sociale ca sursa primara de date. Doar pentru sentiment.

## Strategie cautare

```
WebSearch: "[TICKER] cotatie site:bvb.ro"
WebSearch: "[Companie] raport anual 2024 site:bvb.ro"
WebSearch: "[TICKER] analiza Tradeville OR BT Capital OR BRK"
WebSearch: "[Companie] stiri 2025 site:zf.ro OR site:profit.ro"
WebSearch: "BNR dobanda referinta 2025" (macro)
WebFetch: pagina specifica IR companie pentru rapoarte PDF
```

Mereu verifica data datelor. Date mai vechi de 1 an = mentioneaza explicit.
