<!-- language -->
[English](README.md) | [简体中文](README_zh-CN.md) | [Русский](README_ru.md) | [日本語](README_ja.md) | [한국어](README_ko.md) | [Français](README_fr.md) | [Deutsch](README_de.md) | [Italiano](README_it.md)| [Español](README_es.md) | [Português](README_pt.md) | [العربية](README_ar.md) | [ไทย](README_th.md) | [Tiếng Việt](README_vi.md)

# gstack

> "Non penso di aver digitato una riga di codice probabilmente da dicembre, fondamentalmente, il che è un cambiamento estremamente grande." — [Andrej Karpathy](https://fortune.com/2026/03/21/andrej-karpathy-openai-cofounder-ai-agents-coding-state-of-psychosis-openclaw/), podcast No Priors, marzo 2026

Quando ho sentito Karpathy dirlo, volevo scoprire come. Come fa una persona a rilasciare come un team di venti? Peter Steinberger ha costruito [OpenClaw](https://github.com/openclaw/openclaw) — 247K stelle GitHub — essenzialmente da solo con agenti AI. La rivoluzione è qui. Un singolo costruttore con gli strumenti giusti può muoversi più velocemente di un team tradizionale.

Sono [Garry Tan](https://x.com/garrytan), Presidente & CEO di [Y Combinator](https://www.ycombinator.com/). Ho lavorato con migliaia di startup — Coinbase, Instacart, Rippling — quando erano una o due persone in un garage. Prima di YC, sono stato uno dei primi ingegneri/PM/designer a Palantir, ho cofondato Posterous (venduta a Twitter), e ho costruito Bookface, il social network interno di YC.

**gstack è la mia risposta.** Costruisco prodotti da vent'anni, e ora sto rilasciando più codice che mai. Negli ultimi 60 giorni: **oltre 600.000 righe di codice di produzione** (35% test), **10.000-20.000 righe al giorno**, part-time, mentre gestisco YC full-time. Questo è il mio ultimo `/retro` su 3 progetti: **140.751 righe aggiunte, 362 commit, ~115k LOC nette** in una settimana.

**2026 — 1.237 contributi e continuano:**

![Contributi GitHub 2026 — 1.237 contributi, massiccia accelerazione gen-mar](docs/images/github-2026.png)

**2013 — quando ho costruito Bookface a YC (772 contributi):**

![Contributi GitHub 2013 — 772 contributi costruendo Bookface a YC](docs/images/github-2013.png)

Stessa persona. Epoca diversa. La differenza è negli strumenti.

**gstack è come lo faccio.** Trasforma Claude Code in un team di ingegneria virtuale — un CEO che ripensa il prodotto, un engineering manager che blocca l'architettura, un designer che individua la spazzatura AI, un revisore che trova bug di produzione, un QA lead che apre un browser reale, un security officer che esegue audit OWASP + STRIDE, e un release engineer che rilascia la PR. Venti specialisti e otto strumenti potenti, tutti comandi slash, tutti Markdown, tutti gratuiti, licenza MIT.

Questa è la mia fabbrica di software open source. La uso ogni giorno. La condivido perché questi strumenti dovrebbero essere disponibili per tutti.

Forkalo. Miglioralo. Rendilo tuo. E se vuoi odiare il software open source gratuito — sei il benvenuto, ma preferirei che lo provassi prima.

**Per chi è:**
- **Fondatori e CEO** — specialmente quelli tecnici che vogliono ancora rilasciare
- **Utenti di Claude Code per la prima volta** — ruoli strutturati invece di un prompt vuoto
- **Tech lead e ingegneri staff** — revisione rigorosa, QA e automazione del rilascio su ogni PR

## Avvio rapido

1. Installa gstack (30 secondi — vedi sotto)
2. Esegui `/office-hours` — descrivi cosa stai costruendo
3. Esegui `/plan-ceo-review` su qualsiasi idea di funzionalità
4. Esegui `/review` su qualsiasi branch con modifiche
5. Esegui `/qa` sul tuo URL di staging
6. Fermati lì. Saprai se questo fa per te.

## Installazione — 30 secondi

**Requisiti:** [Claude Code](https://docs.anthropic.com/en/docs/claude-code), [Git](https://git-scm.com/), [Bun](https://bun.sh/) v1.0+, [Node.js](https://nodejs.org/) (solo Windows)

### Passaggio 1: Installa sulla tua macchina

Apri Claude Code e incolla questo. Claude fa il resto.

> Installa gstack: esegui **`git clone https://github.com/garrytan/gstack.git ~/.claude/skills/gstack && cd ~/.claude/skills/gstack && ./setup`** poi aggiungi una sezione "gstack" a CLAUDE.md che dice di usare l'abilità /browse di gstack per tutto il web browsing, non usare mai gli strumenti mcp__claude-in-chrome__*, ed elenca le abilità disponibili: /office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review, /design-consultation, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse, /qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /retro, /investigate, /document-release, /codex, /cso, /autoplan, /careful, /freeze, /guard, /unfreeze, /gstack-upgrade. Poi chiedi all'utente se vuole anche aggiungere gstack al progetto corrente così i compagni di squadra lo ottengono.

### Passaggio 2: Aggiungi al tuo repo così i compagni di squadra lo ottengono (opzionale)

> Aggiungi gstack a questo progetto: esegui **`cp -Rf ~/.claude/skills/gstack .claude/skills/gstack && rm -rf .claude/skills/gstack/.git && cd .claude/skills/gstack && ./setup`** poi aggiungi una sezione "gstack" al CLAUDE.md di questo progetto che dice di usare l'abilità /browse di gstack per tutto il web browsing, non usare mai gli strumenti mcp__claude-in-chrome__*, elenca le abilità disponibili: /office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review, /design-consultation, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse, /qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /retro, /investigate, /document-release, /codex, /cso, /careful, /freeze, /guard, /unfreeze, /gstack-upgrade, e dice a Claude che se le abilità gstack non funzionano, esegui `cd .claude/skills/gstack && ./setup` per costruire il binario e registrare le abilità.

I file reali vengono committati nel tuo repo (non un sottomodulo), quindi `git clone` funziona semplicemente. Tutto vive dentro `.claude/`. Nulla tocca il tuo PATH o viene eseguito in background.

### Codex, Gemini CLI o Cursor

gstack funziona su qualsiasi agente che supporta lo [standard SKILL.md](https://github.com/anthropics/claude-code). Le abilità vivono in `.agents/skills/` e vengono scoperte automaticamente.

```bash
git clone https://github.com/garrytan/gstack.git ~/.codex/skills/gstack
cd ~/.codex/skills/gstack && ./setup --host codex
```

Oppure lascia che setup rilevi automaticamente quali agenti hai installato:

```bash
git clone https://github.com/garrytan/gstack.git ~/gstack
cd ~/gstack && ./setup --host auto
```

Questo installa in `~/.claude/skills/gstack` e/o `~/.codex/skills/gstack` a seconda di ciò che è disponibile. Tutte le 28 abilità funzionano su tutti gli agenti supportati. Le abilità di sicurezza basate su hook (careful, freeze, guard) usano prosa di sicurezza inline su host non-Claude.

## Vedi come funziona

```
Tu:    Voglio costruire un'app di briefing quotidiano per il mio calendario.
Tu:    /office-hours
Claude: [chiede il dolore — esempi specifici, non ipotetici]

Tu:    Multipli calendari Google, eventi con informazioni vecchie,
        luoghi sbagliati. La preparazione richiede un'eternità e
        i risultati non sono abbastanza buoni...

Claude: Sto per obiettare al framing. Hai detto "app di briefing
        quotidiano". Ma quello che hai effettivamente descritto è un
        capo di stato maggiore personale AI.
        [estrae 5 capacità che non realizzavi di descrivere]
        [sfida 4 premesse — sei d'accordo, in disaccordo, o aggiusti]
        [genera 3 approcci di implementazione con stime di sforzo]
        RACCOMANDAZIONE: Rilascia domani il cuneo più stretto, impara
        dall'uso reale. La visione completa è un progetto di 3 mesi —
        inizia con il briefing quotidiano che funziona davvero.
        [scrive documento di progettazione → alimenta automaticamente le abilità a valle]

Tu:    /plan-ceo-review
        [legge il documento di progettazione, sfida lo scope, esegui revisione 10 sezioni]

Tu:    /plan-eng-review
        [diagrammi ASCII per flusso dati, macchine a stati, percorsi di errore]
        [matrice di test, modalità di fallimento, preoccupazioni di sicurezza]

Tu:    Approva piano. Esci dalla modalità piano.
        [scrive 2.400 righe su 11 file. ~8 minuti.]

Tu:    /review
        [AUTO-FIXED] 2 problemi. [ASK] Race condition → approvi fix.

Tu:    /qa https://staging.myapp.com
        [apre browser reale, clicca attraverso i flussi, trova e risolve un bug]

Tu:    /ship
        Test: 42 → 51 (+9 nuovi). PR: github.com/you/app/pull/42
```

Hai detto "app di briefing quotidiano". L'agente ha detto "stai costruendo un capo di stato maggiore AI" — perché ha ascoltato il tuo dolore, non la tua richiesta di funzionalità. Otto comandi, da capo a fondo. Questo non è un copilota. Questo è un team.

## Lo sprint

gstack è un processo, non una collezione di strumenti. Le abilità vengono eseguite nell'ordine in cui viene eseguito uno sprint:

**Pensare → Pianificare → Costruire → Revisionare → Testare → Rilasciare → Riflettere**

Ogni abilità alimenta la successiva. `/office-hours` scrive un documento di progettazione che `/plan-ceo-review` legge. `/plan-eng-review` scrive un piano di test che `/qa` riprende. `/review` cattura bug che `/ship` verifica essere risolti. Nulla cade attraverso le crepe perché ogni passo sa cosa è venuto prima.

| Abilità | Il tuo specialista | Cosa fa |
|-------|----------------|--------------|
| `/office-hours` | **YC Office Hours** | Inizia qui. Sei domande vincolanti che riformulano il tuo prodotto prima di scrivere codice. Obietta al tuo framing, sfida le premesse, genera alternative di implementazione. Il documento di progettazione alimenta ogni abilità a valle. |
| `/plan-ceo-review` | **CEO / Fondatore** | Ripensa il problema. Trova il prodotto 10 stelle nascosto dentro la richiesta. Quattro modalità: Espansione, Espansione selettiva, Mantieni scope, Riduzione. |
| `/plan-eng-review` | **Engineering Manager** | Blocca architettura, flusso dati, diagrammi, casi limite e test. Forza le ipotesi nascoste allo scoperto. |
| `/plan-design-review` | **Designer senior** | Valuta ogni dimensione di design 0-10, spiega come appare un 10, poi modifica il piano per arrivarci. Rilevamento spazzatura AI. Interattivo — una AskUserQuestion per scelta di design. |
| `/design-consultation` | **Partner di design** | Costruisci un sistema di design completo da zero. Ricerca il panorama, propone rischi creativi, genera mockup di prodotto realistici. |
| `/review` | **Ingegnere staff** | Trova i bug che passano la CI ma esplodono in produzione. Risolve automaticamente quelli ovvi. Segnala lacune di completezza. |
| `/investigate` | **Debugger** | Debug sistematico della causa radice. Legge di ferro: nessuna correzione senza indagine. Traccia il flusso dati, testa ipotesi, si ferma dopo 3 correzioni fallite. |
| `/design-review` | **Designer che codifica** | Stesso audit di /plan-design-review, poi risolve ciò che trova. Commit atomici, screenshot prima/dopo. |
| `/qa` | **QA Lead** | Testa la tua app, trova bug, risolvili con commit atomici, riverifica. Genera automaticamente test di regressione per ogni correzione. |
| `/qa-only` | **Reporter QA** | Stessa metodologia di /qa ma solo report. Puro report di bug senza modifiche al codice. |
| `/cso` | **Chief Security Officer** | OWASP Top 10 + modello di minaccia STRIDE. Zero rumore: 17 esclusioni falsi positivi, soglia di confidenza 8/10+, verifica indipendente dei risultati. Ogni risultato include uno scenario di sfruttamento concreto. |
| `/ship` | **Release Engineer** | Sincronizza main, esegui test, audita la copertura, push, apri PR. Bootstrap framework di test se non ne hai uno. |
| `/land-and-deploy` | **Release Engineer** | Unisci la PR, attendi CI e deploy, verifica la salute in produzione. Un comando da "approvato" a "verificato in produzione". |
| `/canary` | **SRE** | Ciclo di monitoraggio post-deploy. Guarda errori console, regressioni di prestazioni, fallimenti di pagina. |
| `/benchmark` | **Performance Engineer** | Baseline tempi di caricamento pagina, Core Web Vitals, e dimensioni risorse. Confronta prima/dopo su ogni PR. |
| `/document-release` | **Scrittore tecnico** | Aggiorna tutta la documentazione del progetto per corrispondere a ciò che hai appena rilasciato. Cattura README vecchi automaticamente. |
| `/retro` | **Engineering Manager** | Retro settimanale consapevole del team. Ripartizioni per persona, serie di rilasci, tendenze di salute dei test, opportunità di crescita. `/retro global` viene eseguito su tutti i tuoi progetti e strumenti AI (Claude Code, Codex, Gemini). |
| `/browse` | **QA Engineer** | Browser Chromium reale, clic reali, screenshot reali. ~100ms per comando. |
| `/setup-browser-cookies` | **Session Manager** | Importa cookie dal tuo browser reale (Chrome, Arc, Brave, Edge) nella sessione headless. Testa pagine autenticate. |
| `/autoplan` | **Pipeline di revisione** | Un comando, piano completamente revisionato. Esegue automaticamente revisione CEO → design → ingegneria con principi decisionali codificati. Porta in superficie solo decisioni di gusto per la tua approvazione. |

### Strumenti potenti

| Abilità | Cosa fa |
|-------|-------------|
| `/codex` | **Seconda opinione** — revisione codice indipendente da OpenAI Codex CLI. Tre modalità: revisione (cancello pass/fail), sfida avversariale, e consultazione aperta. Analisi cross-modello quando sia `/review` che `/codex` sono stati eseguiti. |
| `/careful` | **Guardrail di sicurezza** — avvisa prima di comandi distruttivi (rm -rf, DROP TABLE, force-push). Di' "be careful" per attivare. Scavalca qualsiasi avvertimento. |
| `/freeze` | **Blocco modifiche** — limita modifiche file a una directory. Previene modifiche accidentali fuori scope durante il debug. |
| `/guard` | **Sicurezza completa** — `/careful` + `/freeze` in un comando. Massima sicurezza per lavoro in produzione. |
| `/unfreeze` | **Sblocca** — rimuovi il confine `/freeze`. |
| `/setup-deploy` | **Configuratore di deploy** — configurazione una tantum per `/land-and-deploy`. Rileva la tua piattaforma, URL di produzione, e comandi di deploy. |
| `/gstack-upgrade` | **Auto-aggiornatore** — aggiorna gstack all'ultima versione. Rileva installazione globale vs vendored, sincronizza entrambe, mostra cosa è cambiato. |

**[Approfondimenti con esempi e filosofia per ogni abilità →](docs/skills.md)**

## Sprint paralleli

gstack funziona bene con uno sprint. Diventa interessante con dieci che girano contemporaneamente.

[Conductor](https://conductor.build) esegue più sessioni Claude Code in parallelo — ognuna nel proprio spazio di lavoro isolato. Una sessione su `/office-hours`, un'altra su `/review`, una terza implementa una funzionalità, una quarta esegue `/qa`. Tutte contemporaneamente. La struttura dello sprint è ciò che rende possibile il parallelismo — senza un processo, dieci agenti sono dieci fonti di caos. Con un processo, ogni agente sa esattamente cosa fare e quando fermarsi.

---

Gratuito, licenza MIT, open source. Nessun livello premium, nessuna lista d'attesa.

Ho reso open source il modo in cui costruisco software. Puoi forkarlo e renderlo tuo.

> **Stiamo assumendo.** Vuoi rilasciare 10K+ LOC/giorno e aiutare a rafforzare gstack?
> Vieni a lavorare da YC — [ycombinator.com/software](https://ycombinator.com/software)
> Stipendio ed equity estremamente competitivi. San Francisco, quartiere Dogpatch.

## Documentazione

| Doc | Cosa copre |
|-----|---------------|
| [Approfondimenti abilità](docs/skills.md) | Filosofia, esempi e workflow per ogni abilità (include integrazione Greptile) |
| [Etos del costruttore](ETHOS.md) | Filosofia del costruttore: Boil the Lake, Cercare prima di costruire, tre strati di conoscenza |
| [Architettura](ARCHITECTURE.md) | Decisioni di design e interni del sistema |
| [Riferimento browser](BROWSER.md) | Riferimento completo comandi per `/browse` |
| [Contribuire](CONTRIBUTING.md) | Setup dev, test, modalità contributore, e modalità dev |
| [Changelog](CHANGELOG.md) | Cosa c'è di nuovo in ogni versione |

## Privacy e Telemetria

gstack include telemetria d'uso **opt-in** per aiutare a migliorare il progetto. Ecco esattamente cosa succede:

- **Disattivato di default.** Nulla viene inviato da nessuna parte a meno che tu non dica esplicitamente sì.
- **Al primo avvio,** gstack chiede se vuoi condividere dati d'uso anonimi. Puoi dire di no.
- **Cosa viene inviato (se fai opt-in):** nome abilità, durata, successo/fallimento, versione gstack, OS. Tutto qui.
- **Cosa non viene mai inviato:** codice, percorsi file, nomi repo, nomi branch, prompt, o qualsiasi contenuto generato dall'utente.
- **Cambia in qualsiasi momento:** `gstack-config set telemetry off` disattiva tutto istantaneamente.

I dati sono archiviati in [Supabase](https://supabase.com) (alternativa open source a Firebase). Lo schema è in [`supabase/migrations/001_telemetry.sql`](supabase/migrations/001_telemetry.sql) — puoi verificare esattamente cosa viene raccolto. La chiave pubblicabile Supabase nel repo è una chiave pubblica (come una chiave API Firebase) — le policy di sicurezza a livello di riga la limitano all'accesso in sola inserimento.

**L'analitica locale è sempre disponibile.** Esegui `gstack-analytics` per vedere la tua dashboard d'uso personale dal file JSONL locale — nessun dato remoto necessario.

## Risoluzione problemi

**L'abilità non viene visualizzata?** `cd ~/.claude/skills/gstack && ./setup`

**`/browse` fallisce?** `cd ~/.claude/skills/gstack && bun install && bun run build`

**Installazione obsoleta?** Esegui `/gstack-upgrade` — o imposta `auto_upgrade: true` in `~/.gstack/config.yaml`

**Utenti Windows:** gstack funziona su Windows 11 tramite Git Bash o WSL. Node.js è richiesto oltre a Bun — Bun ha un bug noto con il trasporto pipe di Playwright su Windows ([bun#4253](https://github.com/oven-sh/bun/issues/4253)). Il server browse ripiega automaticamente su Node.js. Assicurati che sia `bun` che `node` siano nel tuo PATH.

**Claude dice che non può vedere le abilità?** Assicurati che il `CLAUDE.md` del tuo progetto abbia una sezione gstack. Aggiungi questo:

```
## gstack
Usa /browse da gstack per tutto il web browsing. Non usare mai strumenti mcp__claude-in-chrome__*.
Abilità disponibili: /office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review,
/design-consultation, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse,
/qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /retro,
/investigate, /document-release, /codex, /cso, /autoplan, /careful, /freeze, /guard,
/unfreeze, /gstack-upgrade.
```

## Licenza

MIT. Gratuito per sempre. Vai a costruire qualcosa.