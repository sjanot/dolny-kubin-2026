# Dolný Kubín 2026 — stav nasadenia

*Posledná aktualizácia: jún 2026*

## Živé adresy
- **Funguje teraz:** https://sjanot.github.io/dolny-kubin-2026/
- **Vlastná doména:** https://dk.it-dk.sk (nabieha — viď nižšie)

## Repozitár
- GitHub: `github.com/sjanot/dolny-kubin-2026` (verejný)
- Lokálne: `/home/stef/PersonalProjects/primator/`
- Branch: `main` · GitHub Pages zo `/` (root)

## Súbory
| Súbor | Obsah |
|---|---|
| `index.html` | Webstránka (responzívna, filtrovanie, „Viac ▾" detaily ku každej téme) |
| `dolny-kubin-analyza.md` | Plná analýza + detailné zistenia so zdrojmi |
| `dolny-kubin-analyza.pdf` | Tlačová verzia (1× A4 landscape, tabuľka 20 tém) |
| `fb-prispevok.md` | Neutrálny text na FB príspevok |
| `CNAME` | `dk.it-dk.sk` (custom doména pre GitHub Pages) |

## Stav vlastnej domény dk.it-dk.sk
- ✅ DNS na Wedose nastavené správne: `dk` CNAME → `sjanot.github.io` (overené na všetkých 3 Wedos NS).
- ✅ Cieľ správne smeruje na GitHub Pages (185.199.108–111.153).
- ⏳ **Verejné resolvery (Google/Cloudflare) držia staré „NXDOMAIN" v cache** (negatívny TTL 3600 s = max 1 hodina). Preto doména dočasne nejde, hoci je všetko správne nastavené. **Vyrieši sa samo do ~1 h.**

## Čo dokončiť, keď DNS nabehne (~do 1 h)
1. Over: `dig +short @8.8.8.8 dk.it-dk.sk` → musí vrátiť GitHub IP.
2. GitHub sám vystaví Let's Encrypt certifikát (15–60 min po nábehu DNS).
3. Zapnúť vynútené HTTPS:
   ```
   gh api -X PUT repos/sjanot/dolny-kubin-2026/pages -F https_enforced=true
   ```
4. Over: `https://dk.it-dk.sk` → HTTP 200.

## Aktualizácia obsahu
Uprav `index.html`, potom:
```
cd /home/stef/PersonalProjects/primator
git add -A && git commit -m "..." && git push
```
GitHub Pages sa prebuilduje automaticky (~1 min).
