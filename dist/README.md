# Distributie pentru Claude.ai online

Fisiere conforme cu cerintele Claude.ai pentru upload skill via web UI:

> **File requirements**
> - `.md` file must contain skill name and description formatted in YAML
> - `.zip` or `.skill` file must include a SKILL.md file

## `md/` — fisiere `.md` standalone

Fiecare skill ca single file cu YAML frontmatter (`name`, `description`). Se uploadeaza individual la claude.ai → Skills → Upload.

| File | Skill |
|------|-------|
| `bvb-stock-analysis.md` | Analiza ticker BVB (DOAR SKILL.md, fara references — pentru references full vezi `.zip` corespunzator) |
| `bvb-market-news.md` | Stiri si calendar |
| `bvb-screener.md` | Screener BET |
| `bvb-dividend.md` | Strategie dividend |
| `bvb-portfolio.md` | Review portofoliu |
| `bvb-macro-ro.md` | Macro RO |

**ATENTIE**: `.md` standalone nu include `references/`. Pentru `bvb-stock-analysis` recomandat `.zip` (contine glosar, indicatori, surse, risc-warnings, sablon).

## `zip/` — bundle complet (RECOMANDAT)

Include `SKILL.md` la root + `references/` cand exista. Conform cerintei `.zip must include a SKILL.md`.

| File | Continut |
|------|----------|
| `bvb-stock-analysis.zip` | SKILL.md + references/{tickere-bet, glosar, indicatori, surse, risc-warnings, raport-template}.md |
| `bvb-market-news.zip` | SKILL.md |
| `bvb-screener.zip` | SKILL.md |
| `bvb-dividend.zip` | SKILL.md |
| `bvb-portfolio.zip` | SKILL.md |
| `bvb-macro-ro.zip` | SKILL.md |

## Cum se uploadeaza pe Claude.ai

1. Mergi la **claude.ai** → Settings → **Capabilities** → **Skills** (sau Project → Skills)
2. Click **Upload skill**
3. Alege fisierul `.md` sau `.zip` din `dist/`
4. Repeta pentru fiecare din cele 6 skills
5. Activeaza skill-urile in Project sau global

## Ordine recomandata upload

1. `bvb-stock-analysis.zip` (core, contine references partajate)
2. `bvb-market-news.md` sau `.zip`
3. `bvb-screener.md`
4. `bvb-dividend.md`
5. `bvb-portfolio.md`
6. `bvb-macro-ro.md`

## Regenerare bundle-uri

Dupa modificari in `skills/`:

```bash
cd /root/stock-exchange-intel
rm -rf dist/md dist/zip
mkdir -p dist/md dist/zip
for skill in skills/bvb-*; do
  name=$(basename "$skill")
  cp "$skill/SKILL.md" "dist/md/$name.md"
done
python3 -c "
import os, zipfile
for n in sorted(os.listdir('skills')):
  if not n.startswith('bvb-'): continue
  src=f'skills/{n}'
  with zipfile.ZipFile(f'dist/zip/{n}.zip','w',zipfile.ZIP_DEFLATED) as z:
    for dp,_,files in os.walk(src):
      for f in files:
        full=os.path.join(dp,f)
        z.write(full, os.path.relpath(full, src))
"
```

---

*Produs de [LawChat.ro](https://lawchat.ro) © 2026*
