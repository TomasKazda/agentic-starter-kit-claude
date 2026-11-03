<!-- agentic-starter-kit -->
# Agentic Starter Kit (Claude Code)

Technologicky neutrální sada šablon a slash příkazů pro vývoj aplikace agenty
ve spolupráci s člověkem, připravená pro **Claude Code** (VS Code rozšíření
i CLI). Obsahuje **systém práce** (pravidla, evidence, životní cyklus, vstupní
příkazy) – neobsahuje specifikaci ani implementaci žádné aplikace.

Varianta pro GitHub Copilot: `TomasKazda/agentic-starter-kit`.

## Obsah

```
CLAUDE.md                                   # vstup Claude Code pro tento kit (nahradí se šablonou)
.claude/
  commands/
    bootstrap-agentic-environment.md        # /bootstrap-agentic-environment – založení prostředí
    discover-project.md                     # /discover-project – discovery → SPEC.md
    plan-increment.md                       # /plan-increment – návrh řešení + úkoly
    work-task.md                            # /work-task T-xxx – realizace jednoho úkolu
  templates/agentic/
    CLAUDE.md        # vstupní bod cílového projektu: pouze `@AGENTS.md`
    AGENTS.md        # provozní řád (jediný zdroj pravidel)
    README.md        # README cílového projektu
    PROJECT.md       # fáze, bod pokračování, otázky
    SPEC.md          # požadavky, omezení, AC
    TASKS.md         # úkoly a důkazy
    DECISIONS.md     # rozhodnutí a schválení
```

Příkazy jsou anglicky (přesnější instrukce pro model), generované dokumenty
a komunikace s člověkem jsou česky. Identifikátory a stavy jsou ASCII slugy.

## Jak to funguje v Claude Code

- `CLAUDE.md` v kořeni projektu se načítá automaticky při startu session.
  Šablona obsahuje jen řádek `@AGENTS.md`, takže pravidla mají jediný zdroj.
- Soubory v `.claude/commands/` jsou projektové slash příkazy; argument za
  názvem příkazu je dostupný jako `$ARGUMENTS`.
- `allowed-tools` ve frontmatteru omezuje bootstrap, discovery a plánování
  na čtení a zápis souborů (bez Bash). `work-task` dědí oprávnění session,
  protože potřebuje spouštět existující testy.

## Použití

### A. Nový projekt v tomto repozitáři

1. Zkopíruj nebo naklonuj kit jako základ projektu a otevři ho v Claude Code.
2. Spusť `/bootstrap-agentic-environment . cs write`.
3. Agent zkopíruje šablony do kořene, doplní placeholdery, nahradí tento
   README a kořenový `CLAUDE.md` šablonami a nastaví fázi
   `pripraveno-ke-specifikaci`.
4. Pokračuj příkazem `/discover-project`.

### B. Existující repozitář

1. Zkopíruj adresář `.claude/` do cílového repozitáře.
2. Spusť `/bootstrap-agentic-environment` (výchozí režim `propose` ukáže,
   co by vzniklo; přidej `write` pro zápis).
3. Existující dokumenty bootstrap nepřepisuje – navrhne jen chybějící části.
   Existující `CLAUDE.md` s pravidly zachová a navrhne doplnit import.

### C. Jiný nástroj než Claude Code

Předej agentovi tělo `bootstrap-agentic-environment.md` jako zadání.
Příkaz podle nástroje umístí vstupní postupy do `docs/workflows/` místo
`.claude/commands/` a `CLAUDE.md` nevytvoří.

## Placeholdery v šablonách

| Token | Nahrazuje se |
| --- | --- |
| `{{PROJECT_NAME}}` | název projektu |
| `{{LANGUAGE}}` | jazyk dokumentace (česky, např. `čeština`) |
| `{{APPROVER}}` | osoba/role, která schvaluje |
| `{{DATE}}` | datum bootstrapu `RRRR-MM-DD` |

## Údržba

- Pravidlo procesu měň v `templates/agentic/AGENTS.md`, ne v příkazech.
- Formát záznamu měň v příslušné šabloně (`TASKS.md`, `DECISIONS.md`…).
- Příkazy drž krátké; odkazují na sekce `AGENTS.md` a neopisují je.
- Hooks, `permissions`, subagenty a skills přidávej až po rozhodnutí
  v `DECISIONS.md` cílového projektu, ne do kitu.
