# {{PROJECT_NAME}}

Projekt vyvíjený agenty ve spolupráci s člověkem podle provozního řádu
v [`AGENTS.md`](AGENTS.md).

> Aktuální stav, fázi a bod pokračování najdeš vždy v [`PROJECT.md`](PROJECT.md).
> Tento soubor stav nekopíruje.

## Mapa dokumentace

| Dokument | Účel |
| --- | --- |
| [`CLAUDE.md`](CLAUDE.md) | Vstupní bod Claude Code – pouze importuje `AGENTS.md`. |
| [`AGENTS.md`](AGENTS.md) | Provozní řád: proces, autonomie, schvalování, evidence, definice hotovo. |
| [`PROJECT.md`](PROJECT.md) | Aktuální fáze, aktivní přírůstek, otevřené otázky, bod pokračování. |
| [`SPEC.md`](SPEC.md) | Účel, rozsah, požadavky, omezení, akceptační kritéria. |
| [`TASKS.md`](TASKS.md) | Úkoly, závislosti, stav, ověření, důkazy. |
| [`DECISIONS.md`](DECISIONS.md) | Rozhodnutí, důvody, záznamy schválení. |
| `IDEAS.md` | Nápady – vznikne až s prvním nápadem. |

## Jak začít

Projekt je po bootstrapu ve fázi `pripraveno-ke-specifikaci`. Specifikace
aplikace zatím neexistuje – vzniká v discovery, které **zahajuje člověk**.

### V Claude Code (VS Code rozšíření nebo CLI)

1. Otevři projekt; Claude Code automaticky načte `CLAUDE.md` → `AGENTS.md`.
2. Spusť `/discover-project`.
3. Postupuj podle otázek agenta; rozsah ke schválení ti předloží explicitně.

Další vstupní body:

| Příkaz | Použij když |
| --- | --- |
| `/discover-project` | Zahajuješ nebo obnovuješ specifikaci. |
| `/plan-increment` | Máš schválený rozsah a chceš návrh řešení a úkoly. |
| `/work-task T-xxx` | Chceš realizovat konkrétní úkol. |

### V jiném nástroji

Otevři odpovídající soubor v `.claude/commands/`, zkopíruj jeho tělo (část pod
frontmatterem) jako zadání agentovi, nahraď `$ARGUMENTS` skutečným argumentem
a připoj pokyn, aby nejprve načetl `AGENTS.md` a `PROJECT.md`.

## Co tu (zatím) není

Instalace, spouštění, CI, licence a architektura aplikace budou doplněny až
po příslušných rozhodnutích v `DECISIONS.md`. Nehledej je zde dříve.
