# Stock Exchange Intel — BVB Skills Pack

> **Produs de [LawChat.ro](https://lawchat.ro) © 2026**

Suita de skill-uri pentru **Claude Code** dedicata investitorilor pe **Bursa de Valori Bucuresti (BVB)**.

Pachet dedicat mediului romanesc: tickere BET (TLV, SNP, SNG, TGN, H2O, BRD, FP, EL, M, DIGI etc.), surse oficiale RO (bvb.ro, BNR, INS, ASF), brokeri locali (Tradeville, BT Capital, BRK), presa financiara (ZF, Profit, Bursa.ro) si reguli specifice — risc politic stat, lichiditate redusa, impozit dividend RO.

## ⚠️ Disclaimer

Acest material este **informativ si educational**. **NU** este consultanta financiara, **NU** este recomandare de investitie ASF, **NU** este oferta. Investitiile la bursa implica **risc de pierdere a capitalului**. Performanta trecuta nu garanteaza viitorul. Consulta un consilier autorizat ASF inainte de orice decizie. Autorul si Claude nu isi asuma responsabilitate pentru decizii bazate pe acest material.

## Skill-uri incluse

| Skill | Cand se activeaza | Output |
|-------|-------------------|--------|
| **`bvb-stock-analysis`** | "analizeaza TLV", "raport SNG", "compara TGN vs TEL" | Raport complet ticker BVB cu fundamental, tehnic, peer, riscuri. **Intreaba ce indicatori vrei.** |
| **`bvb-market-news`** | "stiri BVB azi", "ce a anuntat Hidroelectrica", "calendar dividende" | Sumar piata, stiri pe ticker, calendar evenimente |
| **`bvb-screener`** | "actiuni RO sub P/E 8", "BET cu dividend > 7%", "supravandute BVB" | Tabel filtrat candidati pe criterii |
| **`bvb-dividend`** | "dividend H2O sustenabil?", "top yield RO", "calcul net dupa impozit" | Analiza sustenabilitate, calcul net, comparatie titluri stat |
| **`bvb-portfolio`** | "review portofoliul meu RO", "sunt prea concentrat?" | Analiza concentrare, sector, risc politic, sugestii echilibru |
| **`bvb-macro-ro`** | "context BNR 2025", "impact dobanda pe banci RO" | Snapshot macro RO + impact pe sectoare BVB |

## Caracteristici cheie

- **Mod incepator-friendly**: glosar inline, fiecare metric explicat, avertismente clare.
- **Risc-aware**: lichiditate redusa BVB, risc politic stat, spread larg, impozit dividend, free float — mereu mentionate.
- **Sursa primara intai**: bvb.ro si IR emitent inainte de presa, presa inainte de sociale.
- **Disclaimer obligatoriu**: la inceput si sfarsit raport.
- **Intreaba inainte sa execute**: cand request e vag (ex "analizeaza TLV"), skill-ul cere clarificari pe tip analiza, indicatori doriti, orizont, peer, nivel cunostinte.
- **Tickere acoperite**: BET top 20 (TLV, SNP, H2O, BRD, FP, SNG, TGN, EL, M, DIGI, TEL, ATB, SNN, COTE, TRP, AQ, BVB, WINE, SFG, ONE) + restul BET-XT + AeRO la cerere.

## Surse de date utilizate

**Oficial**: bvb.ro, asfromania.ro, bnr.ro, insse.ro, mfinante.gov.ro
**IR emitenti**: tlv.ro, omvpetrom.com, hidroelectrica.ro, etc.
**Brokeri RO**: Tradeville, BT Capital Partners, BRK Financial, Wood & Co
**Presa**: zf.ro, profit.ro, bursa.ro, economica.net, economedia.ro
**Macro CEE**: Eurostat, FMI, banci centrale regionale

## Instalare

### Cerinte
- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) instalat (`claude` in PATH)
- `git`

### Pentru Claude.ai web/Online (upload skills UI)

Fisiere gata-de-upload in folder-ul [`dist/`](dist/):
- **`dist/zip/<skill>.zip`** — bundle complet (SKILL.md + references). **Recomandat.**
- **`dist/md/<skill>.md`** — single file (YAML frontmatter cu name+description). Doar SKILL.md, fara references.

Conform cerintei Claude.ai:
> `.md` file must contain skill name and description formatted in YAML
> `.zip` or `.skill` file must include a SKILL.md file

Upload pe claude.ai → Settings → Capabilities → Skills → Upload. Vezi [`dist/README.md`](dist/README.md).

### Optiunea 0 — Claude Code Marketplace (CLI, cea mai simpla)

Repo-ul e un **Claude Code marketplace**. Instaleaza tot pachetul cu o singura comanda:

```
/plugin marketplace add LCBO/stock-exchange-intel
/plugin install bvb@stock-exchange-intel
```

Verifica:
```
/plugin
```
Ar trebui sa apara `bvb` ca instalat. Skills `bvb-*` devin disponibile imediat fara restart.

Update mai tarziu:
```
/plugin marketplace update stock-exchange-intel
/plugin install bvb@stock-exchange-intel
```

Dezinstalare:
```
/plugin uninstall bvb@stock-exchange-intel
```

### Optiunea 1 — User-level skills (manual)

Instaleaza skill-urile la nivel de utilizator. Disponibile in toate proiectele.

```bash
# clone repo
git clone https://github.com/LCBO/stock-exchange-intel.git
cd stock-exchange-intel

# copiaza in directorul user-level skills al Claude Code
mkdir -p ~/.claude/skills
cp -r skills/bvb-* ~/.claude/skills/

# verifica
ls ~/.claude/skills/ | grep bvb
```

Restart Claude Code (sau deschide o sesiune noua). Skill-urile sunt detectate automat din numele si descrierea din `SKILL.md`.

### Optiunea 2 — Project-level skills

Doar pentru proiectul curent.

```bash
cd /path/to/your/project
mkdir -p .claude/skills
cp -r /path/to/stock-exchange-intel/skills/bvb-* .claude/skills/
```

### Optiunea 3 — Symlink (dezvoltare)

Daca vrei sa contribui sau sa modifici local cu hot-reload:

```bash
git clone https://github.com/LCBO/stock-exchange-intel.git ~/repos/stock-exchange-intel
mkdir -p ~/.claude/skills
for dir in ~/repos/stock-exchange-intel/skills/bvb-*; do
  ln -sf "$dir" ~/.claude/skills/$(basename "$dir")
done
```

### Verificare instalare

In Claude Code:

```
analizeaza TLV
```

Skill-ul `bvb-stock-analysis` ar trebui sa porneasca si sa intrebe ce indicatori vrei. Daca nu, listeaza skill-urile cu `/help` si verifica ca apar `bvb-*`.

## Structura repo

```
stock-exchange-intel/
├── README.md                         # acest fisier
├── CLAUDE-ONLINE.md                  # versiune single-file pentru claude.ai/code
├── LICENSE                           # MIT
├── .claude-plugin/
│   ├── marketplace.json              # marketplace manifest
│   └── plugin.json                   # plugin manifest
├── skills/
│   ├── bvb-stock-analysis/
│   │   ├── SKILL.md
│   │   └── references/
│   │       ├── tickere-bet.md        # lista BET + simboluri
│   │       ├── glosar.md             # termeni explicati incepatori
│   │       ├── indicatori.md         # benchmark-uri RO
│   │       ├── surse.md              # ierarhie surse de date
│   │       ├── risc-warnings.md      # red flags obligatorii
│   │       └── raport-template.md    # structura output
│   ├── bvb-market-news/SKILL.md
│   ├── bvb-screener/SKILL.md
│   ├── bvb-dividend/SKILL.md
│   ├── bvb-portfolio/SKILL.md
│   └── bvb-macro-ro/SKILL.md
```

`references/` din `bvb-stock-analysis` sunt **partajate**: celelalte skill-uri trimit catre `../bvb-stock-analysis/references/...`. Daca instalezi doar un singur skill, copiaza si `bvb-stock-analysis/references/`.

## Exemple de utilizare

### Analiza ticker
```
analizeaza Hidroelectrica pentru un investitor pe termen lung pe dividend
```
Skill-ul intreaba: tip analiza? indicatori? peer? -> raport structurat cu disclaimer, sumar, financiare 5 ani, evaluare vs peer (SNG, SNN), tehnic, riscuri, concluzie.

### Comparatie peer
```
compara TLV vs BRD - care e mai atractiv?
```

### Screener
```
gaseste actiunile BET cu dividend yield peste 6% si payout sub 80%
```

### Stiri zi
```
sumar piata BVB azi
```

### Review portofoliu
```
am: 30% TLV, 20% SNP, 15% H2O, 15% SNG, 10% BRD, 10% FP. review?
```

### Macro
```
cum afecteaza dobanda BNR sectoarele BVB?
```

### Dividend
```
top 5 emitenti BVB cu dividend sustenabil. calcul net dupa impozit RO.
```

## Personalizare

### Schimbare lista tickere default
Editeaza `skills/bvb-stock-analysis/references/tickere-bet.md` sa reflecte componenta BET curenta (lista se actualizeaza periodic la BVB).

### Adauga surse proprii
Editeaza `skills/bvb-stock-analysis/references/surse.md` cu broker-ul tau, newsletter-uri preferate, etc.

### Schimbare cota impozit dividend
Skill-urile cer verificare cota curenta (s-a schimbat in 2023, 2025). Actualizeaza in `bvb-dividend/SKILL.md` daca vrei o cota fixa fara verificare.

### Mod expert (fara explicatii inline)
La intrebarea "nivel cunostinte" raspunde "experimentat". Skill-ul produce raport tehnic compact fara glosar inline.

## Ce NU face

- ❌ NU recomanda explicit "cumpara" / "vinde"
- ❌ NU prezice preturi tinta cu certitudine
- ❌ NU ofera consultanta fiscala individuala
- ❌ NU executa ordine la broker
- ❌ NU acceseaza conturi reale
- ❌ NU foloseste API-uri platite (totul prin WebSearch / WebFetch public)

## Limite cunoscute

- Nu exista API public consolidat gratuit pentru BVB → skill-urile depind de WebSearch/WebFetch (variabila ca calitate)
- Date intra-day pe bvb.ro **delayed 15 min** pentru public
- Lista BET se actualizeaza periodic — verifica componenta curenta inainte de raport extensiv
- Impozitarea dividend RO e schimbata legislativ → skill-ul cere verificare cota curenta inainte de calcul
- Pentru screener larg (>10 tickere), durata mare din cauza cautari individuale per ticker

## Pozitionare

| Caracteristica | stock-exchange-intel |
|----------------|----------------------|
| Piata | BVB (Bursa de Valori Bucuresti) |
| Numar skill-uri | 6 (focus pe esential RO) |
| Limba | RO |
| Surse | bvb.ro, ZF, Profit, Tradeville, BT Capital, BRK, BNR, INS |
| Audienta | Investitori RO **inclusiv non-experti** (glosar inline) |
| Risc politic stat | **Factor central** (SNG, TGN, H2O, EL etc.) |
| Lichiditate | **Avertizat constant** (volum mic BVB) |
| Focus | Analiza si decizie informata, NU sisteme automate de tranzactionare |

Serveste investitorul roman care vrea sa inteleaga ce cumpara intr-o piata mai mica si mai riscanta decat US/EU developed.

## Roadmap

- [ ] `bvb-ipo-calendar` — IPO-uri si listari noi BVB
- [ ] `bvb-aero` — focus piata SMEs (AeRO) cu reguli specifice
- [ ] `bvb-bonds` — obligatiuni corporative listate BVB
- [ ] `bvb-titluri-stat` — Tezaur/Fidelis ca alternativa
- [ ] Integrare opționala API tradeville/eToro (daca user are credentiale proprii)
- [ ] Suport indicii BET-NG (energie), BET-FI (financiar), BET-TR (total return)

## Contributii

PR-uri binevenite. Ghid:
- Pastreaza tonul prudent (nu "cumpara/vinde", ci "argumente pro/contra")
- Nu adauga skill-uri care promit randament garantat
- Disclaimer obligatoriu in fiecare skill nou
- Actualizeaza `tickere-bet.md` cand componenta BET se schimba
- Test manual: skill-ul porneste pe trigger asteptat, intreaba inainte de a executa pe request vag

## Licenta

MIT — vezi [`LICENSE`](LICENSE).

---

**Produs de [LawChat.ro](https://lawchat.ro) © 2026** — platforma AI pentru profesionisti din domeniul juridic si financiar din Romania.

## Credit

- Format skill: [Claude Code Skills documentation](https://docs.anthropic.com/en/docs/claude-code)
- Date piata: Bursa de Valori Bucuresti (bvb.ro)

## Resurse externe

- [BVB — site oficial](https://bvb.ro)
- [ASF — Autoritatea de Supraveghere Financiara](https://asfromania.ro)
- [BNR — date macro](https://bnr.ro)
- [INS — statistici economice](https://insse.ro)
- [Ziarul Financiar](https://zf.ro)
- [Profit.ro](https://profit.ro)
- [Bursa.ro](https://bursa.ro)
