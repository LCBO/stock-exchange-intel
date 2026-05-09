# Indicatori - benchmark-uri pentru piata RO

Piata BVB e frontier/emergenta. Benchmark-urile difera de US/EU developed.

## Multiplii fundamentali (mediana BET 2020-2025 aprox)

| Metric | Tipic BET | "Ieftin" | "Scump" |
|--------|-----------|----------|---------|
| P/E | 7-12 | < 6 | > 15 |
| P/B | 0.8-1.5 | < 0.7 | > 2.0 |
| Dividend yield | 5-9% | < 3% (low) | > 12% (verifica sustenabilitatea) |
| ROE banci (TLV, BRD) | 12-20% | < 10% | > 22% |
| ROE utilitati (SNG, TGN, TEL, EL) | 8-15% | < 6% | > 18% |
| Datorie/EBITDA | 0.5-2.5 | < 0.5 | > 3.5 |

P/E mic NU inseamna automat "cumpara". Verifica de ce: scadere profituri viitoare, risc politic, sector decline?

## Tehnici - particularitati BVB

- **Volum mic** distorsioneaza indicatorii. Pe actiuni cu < 200k RON/zi, RSI/MACD sunt zgomot.
- **Gap-uri frecvente** la deschidere - actiunile nu au pre-market lichid.
- **Fixing-uri** la deschidere/inchidere - preturile pot fi atipice in primele si ultimele minute.
- **Cicluri ex-dividend** - pretul scade artificial cu valoarea dividendului. Nu confunda cu trend bearish.

## Indicatori specifici recomandati per request user

Utilizator zice "vreau analiza pe SNG cu indicatorii X, Y, Z". Mapeaza:

| User cere | Calculezi |
|-----------|-----------|
| "randament" | Dividend yield TTM si forward |
| "valoare" | P/E, P/B, EV/EBITDA, P/S |
| "crestere" | EPS growth 3y, revenue CAGR, ROE |
| "siguranta" | Datorie net/EBITDA, current ratio, cash/cap |
| "momentum" | RSI 14, MACD, % vs MA50, perf 3M/6M/1Y |
| "trend" | MA20/50/200, ADX |
| "volatilitate" | ATR, Bollinger, beta vs BET |
| "lichiditate" | Volum mediu RON/zi, spread mediu, free float |

## Comparatie corecta

- Compara TLV cu BRD (ambele banci RO), NU cu JPM (banca US scara diferita).
- Compara SNP cu peers regionali: MOL (HU), PKN Orlen (PL), OMV (AT) - dar atentie la diferente fiscalitate/dividend policy.
- Pentru utilitati de stat, comparatia interna BVB (SNG vs TGN) e mai relevanta.

## Beta

- Beta vs BET (NU vs SP500). Beta > 1 = mai volatil decat indicele; < 1 = mai putin.
- TLV, SNP au beta ~1; utilitati ~0.5-0.8; small caps > 1.2.
