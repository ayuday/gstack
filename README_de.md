<!-- language -->
[English](README.md) | [简体中文](README_zh-CN.md) | [Русский](README_ru.md) | [日本語](README_ja.md) | [한국어](README_ko.md) | [Français](README_fr.md) | [Deutsch](README_de.md) | [Italiano](README_it.md)| [Español](README_es.md) | [Português](README_pt.md) | [العربية](README_ar.md) | [ไทย](README_th.md) | [Tiếng Việt](README_vi.md)

# gstack

> „Ich glaube, ich habe seit Dezember wahrscheinlich keine Zeile Code mehr getippt, im Grunde, was eine extrem große Veränderung ist." — [Andrej Karpathy](https://fortune.com/2026/03/21/andrej-karpathy-openai-cofounder-ai-agents-coding-state-of-psychosis-openclaw/), No Priors Podcast, März 2026

Als ich Karpathy das sagen hörte, wollte ich herausfinden, wie. Wie kann eine Person wie ein zwanzigköpfiges Team liefern? Peter Steinberger hat [OpenClaw](https://github.com/openclaw/openclaw) gebaut — 247K GitHub-Sterne — im Wesentlichen allein mit KI-Agenten. Die Revolution ist da. Ein einzelner Builder mit dem richtigen Werkzeug kann schneller arbeiten als ein traditionelles Team.

Ich bin [Garry Tan](https://x.com/garrytan), Präsident & CEO von [Y Combinator](https://www.ycombinator.com/). Ich habe mit Tausenden von Startups gearbeitet — Coinbase, Instacart, Rippling — als sie noch ein oder zwei Leute in einer Garage waren. Vor YC war ich einer der ersten Ingenieure/PM/Designer bei Palantir, habe Posterous mitgegründet (an Twitter verkauft) und Bookface gebaut, YCs internes soziales Netzwerk.

**gstack ist meine Antwort.** Ich baue seit zwanzig Jahren Produkte, und jetzt liefere ich mehr Code als je zuvor. In den letzten 60 Tagen: **über 600.000 Zeilen Produktionscode** (35% Tests), **10.000-20.000 Zeilen pro Tag**, teilzeit, während ich YC vollzeit leite. Hier ist mein letzter `/retro` über 3 Projekte: **140.751 Zeilen hinzugefügt, 362 Commits, ~115k Netto-LOC** in einer Woche.

**2026 — 1.237 Beiträge und weiter geht's:**

![GitHub Beiträge 2026 — 1.237 Beiträge, massive Beschleunigung Jan-Mär](docs/images/github-2026.png)

**2013 — als ich Bookface bei YC baute (772 Beiträge):**

![GitHub Beiträge 2013 — 772 Beiträge beim Bau von Bookface bei YC](docs/images/github-2013.png)

Dieselbe Person. Andere Ära. Der Unterschied ist das Werkzeug.

**gstack ist, wie ich es mache.** Es verwandelt Claude Code in ein virtuelles Engineering-Team — einen CEO, der das Produkt überdenkt, einen Engineering-Manager, der die Architektur festlegt, einen Designer, der KI-Schrott erkennt, einen Reviewer, der Produktionsfehler findet, einen QA-Leiter, der einen echten Browser öffnet, einen Sicherheitsbeauftragten, der OWASP + STRIDE-Audits durchführt, und einen Release-Ingenieur, der die PR liefert. Zwanzig Spezialisten und acht Power-Tools, alles Slash-Befehle, alles Markdown, alles kostenlos, MIT-Lizenz.

Dies ist meine Open-Source-Software-Fabrik. Ich benutze sie jeden Tag. Ich teile sie, weil diese Werkzeuge für alle verfügbar sein sollten.

Forken Sie es. Verbessern Sie es. Machen Sie es zu Ihrem. Und wenn Sie kostenlose Open-Source-Software hassen wollen — Sie sind willkommen, aber ich würde lieber, dass Sie es zuerst ausprobieren.

**Für wen dies ist:**
- **Gründer und CEOs** — besonders technische, die noch liefern wollen
- **Erstmalige Claude Code-Benutzer** — strukturierte Rollen statt leerer Prompt
- **Tech Leads und Staff-Ingenieure** — rigorose Überprüfung, QA und Release-Automatisierung bei jeder PR

## Schnellstart

1. Installieren Sie gstack (30 Sekunden — siehe unten)
2. Führen Sie `/office-hours` aus — beschreiben Sie, was Sie bauen
3. Führen Sie `/plan-ceo-review` bei jeder Funktionsidee aus
4. Führen Sie `/review` bei jedem Branch mit Änderungen aus
5. Führen Sie `/qa` auf Ihrer Staging-URL aus
6. Hören Sie dort auf. Sie werden wissen, ob dies für Sie ist.

## Installation — 30 Sekunden

**Anforderungen:** [Claude Code](https://docs.anthropic.com/en/docs/claude-code), [Git](https://git-scm.com/), [Bun](https://bun.sh/) v1.0+, [Node.js](https://nodejs.org/) (nur Windows)

### Schritt 1: Auf Ihrem Rechner installieren

Öffnen Sie Claude Code und fügen Sie dies ein. Claude erledigt den Rest.

> gstack installieren: Führen Sie **`git clone https://github.com/garrytan/gstack.git ~/.claude/skills/gstack && cd ~/.claude/skills/gstack && ./setup`** aus und fügen Sie dann einen "gstack"-Abschnitt zu CLAUDE.md hinzu, der besagt, dass /browse von gstack für alle Web-Browsing verwendet werden soll, niemals mcp__claude-in-chrome__*-Tools verwendet werden sollen, und listet die verfügbaren Fähigkeiten auf: /office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review, /design-consultation, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse, /qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /retro, /investigate, /document-release, /codex, /cso, /autoplan, /careful, /freeze, /guard, /unfreeze, /gstack-upgrade. Fragen Sie dann den Benutzer, ob er gstack auch zum aktuellen Projekt hinzufügen möchte, damit Teamkollegen es bekommen.

### Schritt 2: Zu Ihrem Repo hinzufügen, damit Teamkollegen es bekommen (optional)

> gstack zu diesem Projekt hinzufügen: Führen Sie **`cp -Rf ~/.claude/skills/gstack .claude/skills/gstack && rm -rf .claude/skills/gstack/.git && cd .claude/skills/gstack && ./setup`** aus und fügen Sie dann einen "gstack"-Abschnitt zu CLAUDE.md dieses Projekts hinzu, der besagt, dass /browse von gstack für alle Web-Browsing verwendet werden soll, niemals mcp__claude-in-chrome__*-Tools verwendet werden sollen, listet die verfügbaren Fähigkeiten auf: /office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review, /design-consultation, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse, /qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /retro, /investigate, /document-release, /codex, /cso, /careful, /freeze, /guard, /unfreeze, /gstack-upgrade, und sagt Claude, dass, wenn gstack-Fähigkeiten nicht funktionieren, `cd .claude/skills/gstack && ./setup` ausgeführt werden soll, um die Binärdatei zu bauen und Fähigkeiten zu registrieren.

Echte Dateien werden in Ihr Repo committet (kein Submodule), also funktioniert `git clone` einfach. Alles lebt in `.claude/`. Nichts berührt Ihren PATH oder läuft im Hintergrund.

### Codex, Gemini CLI oder Cursor

gstack funktioniert auf jedem Agenten, der den [SKILL.md-Standard](https://github.com/anthropics/claude-code) unterstützt. Fähigkeiten leben in `.agents/skills/` und werden automatisch entdeckt.

```bash
git clone https://github.com/garrytan/gstack.git ~/.codex/skills/gstack
cd ~/.codex/skills/gstack && ./setup --host codex
```

Oder lassen Sie setup automatisch erkennen, welche Agenten Sie installiert haben:

```bash
git clone https://github.com/garrytan/gstack.git ~/gstack
cd ~/gstack && ./setup --host auto
```

Dies installiert in `~/.claude/skills/gstack` und/oder `~/.codex/skills/gstack`, je nachdem, was verfügbar ist. Alle 28 Fähigkeiten funktionieren auf allen unterstützten Agenten. Hook-basierte Sicherheitsfähigkeiten (careful, freeze, guard) verwenden Inline-Sicherheitsberatung auf Nicht-Claude-Hosts.

## Sehen Sie, wie es funktioniert

```
Sie:    Ich möchte eine tägliche Briefing-App für meinen Kalender bauen.
Sie:    /office-hours
Claude: [fragt nach dem Schmerz — konkrete Beispiele, keine Hypothesen]

Sie:    Mehrere Google-Kalender, Ereignisse mit veralteten Infos, falsche
        Orte. Die Vorbereitung dauert ewig und die Ergebnisse sind
        nicht gut genug...

Claude: Ich werde dem Framing widersprechen. Sie sagten "tägliche
        Briefing-App". Aber was Sie eigentlich beschrieben haben, ist
        ein persönlicher KI-Stabschef.
        [extrahiert 5 Fähigkeiten, von denen Sie nicht wussten, dass Sie sie beschrieben]
        [fordert 4 Prämissen heraus — Sie stimmen zu, lehnen ab oder passen an]
        [generiert 3 Implementierungsansätze mit Aufwandsschätzungen]
        EMPFEHLUNG: Liefern Sie morgen die schmalste Schneide, lernen Sie
        aus der echten Nutzung. Die vollständige Vision ist ein 3-Monats-
        Projekt — beginnen Sie mit dem täglichen Briefing, das tatsächlich
        funktioniert.
        [schreibt Design-Dokument → speist automatisch nachgelagerte Fähigkeiten]

Sie:    /plan-ceo-review
        [liest das Design-Dokument, fordert den Umfang heraus, führt 10-Abschnitte-Review durch]

Sie:    /plan-eng-review
        [ASCII-Diagramme für Datenfluss, Zustandsmaschinen, Fehlerpfade]
        [Testmatrix, Ausfallmodi, Sicherheitsbedenken]

Sie:    Plan genehmigen. Plan-Modus verlassen.
        [schreibt 2.400 Zeilen über 11 Dateien. ~8 Minuten.]

Sie:    /review
        [AUTO-FIXED] 2 Probleme. [ASK] Race Condition → Sie genehmigen Fix.

Sie:    /qa https://staging.myapp.com
        [öffnet echten Browser, klickt durch Flows, findet und behebt einen Bug]

Sie:    /ship
        Tests: 42 → 51 (+9 neue). PR: github.com/you/app/pull/42
```

Sie sagten "tägliche Briefing-App". Der Agent sagte "Sie bauen einen KI-Stabschef" — weil er auf Ihren Schmerz hörte, nicht auf Ihre Funktionsanfrage. Acht Befehle, von Ende zu Ende. Das ist kein Copilot. Das ist ein Team.

## Der Sprint

gstack ist ein Prozess, keine Sammlung von Werkzeugen. Die Fähigkeiten laufen in der Reihenfolge, in der ein Sprint läuft:

**Denken → Planen → Bauen → Überprüfen → Testen → Liefern → Reflektieren**

Jede Fähigkeit speist die nächste. `/office-hours` schreibt ein Design-Dokument, das `/plan-ceo-review` liest. `/plan-eng-review` schreibt einen Testplan, den `/qa` aufgreift. `/review` fängt Fehler, die `/ship` als behoben verifiziert. Nichts fällt durch die Ritzen, weil jeder Schritt weiß, was davor kam.

| Fähigkeit | Ihr Spezialist | Was er tut |
|-------|----------------|--------------|
| `/office-hours` | **YC Office Hours** | Hier beginnen. Sechs zwingende Fragen, die Ihr Produkt überdenken, bevor Sie Code schreiben. Widerspricht Ihrem Framing, fordert Prämissen heraus, generiert Implementierungsalternativen. Design-Dokument speist jede nachgelagerte Fähigkeit. |
| `/plan-ceo-review` | **CEO / Gründer** | Das Problem überdenken. Das 10-Sterne-Produkt finden, das in der Anfrage versteckt ist. Vier Modi: Erweiterung, Selektive Erweiterung, Umfang halten, Reduktion. |
| `/plan-eng-review` | **Engineering-Manager** | Architektur, Datenfluss, Diagramme, Randfälle und Tests festlegen. Zwingt versteckte Annahmen ans Licht. |
| `/plan-design-review` | **Senior Designer** | Bewertet jede Design-Dimension 0-10, erklärt, wie eine 10 aussieht, bearbeitet dann den Plan, um dorthin zu gelangen. KI-Schrott-Erkennung. Interaktiv — eine AskUserQuestion pro Design-Entscheidung. |
| `/design-consultation` | **Design-Partner** | Ein vollständiges Design-System von Grund auf bauen. Erforscht die Landschaft, schlägt kreative Risiken vor, generiert realistische Produkt-Mockups. |
| `/review` | **Staff-Ingenieur** | Findet die Fehler, die CI bestehen, aber in Produktion explodieren. Behebt automatisch die offensichtlichen. Markiert Vollständigkeitslücken. |
| `/investigate` | **Debugger** | Systematische Root-Cause-Fehlersuche. Eisernes Gesetz: keine Fixes ohne Untersuchung. Verfolgt Datenfluss, testet Hypothesen, stoppt nach 3 fehlgeschlagenen Fixes. |
| `/design-review` | **Designer, der codiert** | Gleiches Audit wie /plan-design-review, behebt dann, was gefunden wird. Atomare Commits, Vorher/Nachher-Screenshots. |
| `/qa` | **QA-Leiter** | Testet Ihre App, findet Fehler, behebt sie mit atomaren Commits, verifiziert neu. Generiert automatisch Regressionstests für jeden Fix. |
| `/qa-only` | **QA-Berichterstatter** | Gleiche Methodik wie /qa, aber nur Bericht. Reiner Fehlerbericht ohne Code-Änderungen. |
| `/cso` | **Chief Security Officer** | OWASP Top 10 + STRIDE-Bedrohungsmodell. Null-Rauschen: 17 False-Positive-Ausschlüsse, 8/10+ Vertrauensschwelle, unabhängige Fund-Verifizierung. Jeder Fund enthält ein konkretes Ausnutzungsszenario. |
| `/ship` | **Release-Ingenieur** | Main synchronisieren, Tests ausführen, Coverage prüfen, pushen, PR öffnen. Bootstrappt Test-Frameworks, wenn Sie keines haben. |
| `/land-and-deploy` | **Release-Ingenieur** | PR mergen, auf CI und Deployment warten, Produktionsgesundheit verifizieren. Ein Befehl von "genehmigt" zu "in Produktion verifiziert". |
| `/canary` | **SRE** | Überwachungsschleife nach dem Deployment. Überwacht Konsolenfehler, Leistungsregressionen und Seitenfehler. |
| `/benchmark` | **Leistungsingenieur** | Basiswerte für Seitenladezeiten, Core Web Vitals und Ressourcengrößen. Vergleicht Vorher/Nachher bei jeder PR. |
| `/document-release` | **Technischer Redakteur** | Aktualisiert alle Projektdokumentationen, um dem soeben Gelieferten zu entsprechen. Fängt veraltete READMEs automatisch ein. |
| `/retro` | **Engineering-Manager** | Team-bewusste wöchentliche Retro. Pro-Person-Aufschlüsselungen, Lieferstreifen, Testgesundheitstrends, Wachstumschancen. `/retro global` läuft über alle Ihre Projekte und KI-Tools (Claude Code, Codex, Gemini). |
| `/browse` | **QA-Ingenieur** | Echter Chromium-Browser, echte Klicks, echte Screenshots. ~100ms pro Befehl. |
| `/setup-browser-cookies` | **Sitzungsmanager** | Importiert Cookies von Ihrem echten Browser (Chrome, Arc, Brave, Edge) in die Headless-Sitzung. Testet authentifizierte Seiten. |
| `/autoplan` | **Review-Pipeline** | Ein Befehl, vollständig überprüfter Plan. Führt automatisch CEO → Design → Engineering-Review mit kodierten Entscheidungsprinzipien aus. Bringt nur Geschmacksentscheidungen zu Ihrer Genehmigung an die Oberfläche. |

### Power-Tools

| Fähigkeit | Was sie tut |
|-------|-------------|
| `/codex` | **Zweite Meinung** — unabhängige Code-Überprüfung von OpenAI Codex CLI. Drei Modi: Review (Pass/Fail-Tor), adversarische Herausforderung und offene Beratung. Cross-Modell-Analyse, wenn sowohl `/review` als auch `/codex` gelaufen sind. |
| `/careful` | **Sicherheitsleitplanken** — warnt vor destruktiven Befehlen (rm -rf, DROP TABLE, Force-Push). Sagen Sie "be careful" zum Aktivieren. Überschreiben Sie jede Warnung. |
| `/freeze` | **Bearbeitungssperre** — beschränkt Dateibearbeitungen auf ein Verzeichnis. Verhindert versehentliche Änderungen außerhalb des Umfangs beim Debuggen. |
| `/guard` | **Volle Sicherheit** — `/careful` + `/freeze` in einem Befehl. Maximale Sicherheit für Produktionsarbeit. |
| `/unfreeze` | **Entsperren** — entfernt die `/freeze`-Grenze. |
| `/setup-deploy` | **Deployment-Konfigurator** — einmalige Einrichtung für `/land-and-deploy`. Erkennt Ihre Plattform, Produktions-URL und Deployment-Befehle. |
| `/gstack-upgrade` | **Selbst-Updater** — aktualisiert gstack auf die neueste Version. Erkennt globale vs. vendored Installation, synchronisiert beide, zeigt Änderungen. |

**[Tiefe Einblicke mit Beispielen und Philosophie für jede Fähigkeit →](docs/skills.md)**

## Parallele Sprints

gstack funktioniert gut mit einem Sprint. Es wird interessant, wenn zehn gleichzeitig laufen.

[Conductor](https://conductor.build) führt mehrere Claude Code-Sitzungen parallel aus — jede in ihrem eigenen isolierten Arbeitsbereich. Eine Sitzung bei `/office-hours`, eine andere bei `/review`, eine dritte implementiert eine Funktion, eine vierte führt `/qa` aus. Alle gleichzeitig. Die Sprint-Struktur ist es, die Parallelität ermöglicht — ohne Prozess sind zehn Agenten zehn Quellen des Chaos. Mit einem Prozess weiß jeder Agent genau, was zu tun ist und wann zu stoppen.

---

Kostenlos, MIT-lizenziert, Open Source. Keine Premium-Stufe, keine Warteliste.

Ich habe open source gemacht, wie ich Software baue. Sie können es forken und zu Ihrem eigenen machen.

> **Wir stellen ein.** Möchten Sie 10K+ LOC/Tag liefern und helfen, gstack zu härten?
> Kommen Sie zu YC — [ycombinator.com/software](https://ycombinator.com/software)
> Extrem wettbewerbsfähiges Gehalt und Eigenkapital. San Francisco, Dogpatch-Viertel.

## Dokumentation

| Dokument | Was es abdeckt |
|-----|---------------|
| [Tiefe Einblicke zu Fähigkeiten](docs/skills.md) | Philosophie, Beispiele und Workflow für jede Fähigkeit (inklusive Greptile-Integration) |
| [Builder-Ethos](ETHOS.md) | Builder-Philosophie: Boil the Lake, Suchen vor dem Bauen, drei Schichten des Wissens |
| [Architektur](ARCHITECTURE.md) | Designentscheidungen und Systeminterna |
| [Browser-Referenz](BROWSER.md) | Vollständige Befehlsreferenz für `/browse` |
| [Beitragen](CONTRIBUTING.md) | Dev-Setup, Tests, Contributor-Modus und Dev-Modus |
| [Changelog](CHANGELOG.md) | Was neu in jeder Version ist |

## Datenschutz & Telemetrie

gstack enthält **opt-in** Nutzungstelemetrie zur Verbesserung des Projekts. Hier ist genau, was passiert:

- **Standardmäßig aus.** Nichts wird irgendwohin gesendet, es sei denn, Sie sagen explizit ja.
- **Beim ersten Start** fragt gstack, ob Sie anonyme Nutzungsdaten teilen möchten. Sie können nein sagen.
- **Was gesendet wird (wenn Sie opt-in):** Fähigkeitsname, Dauer, Erfolg/Misserfolg, gstack-Version, OS. Das ist alles.
- **Was niemals gesendet wird:** Code, Dateipfade, Repo-Namen, Branch-Namen, Prompts oder benutzergenerierte Inhalte.
- **Jederzeit ändern:** `gstack-config set telemetry off` deaktiviert alles sofort.

Daten werden in [Supabase](https://supabase.com) gespeichert (Open-Source-Firebase-Alternative). Das Schema ist in [`supabase/migrations/001_telemetry.sql`](supabase/migrations/001_telemetry.sql) — Sie können genau verifizieren, was gesammelt wird. Der Supabase-Publishable-Key im Repo ist ein öffentlicher Schlüssel (wie ein Firebase-API-Schlüssel) — Row-Level-Security-Richtlinien beschränken ihn auf Nur-Einfüge-Zugriff.

**Lokale Analysen sind immer verfügbar.** Führen Sie `gstack-analytics` aus, um Ihr persönliches Nutzungs-Dashboard aus der lokalen JSONL-Datei zu sehen — keine Remote-Daten erforderlich.

## Fehlerbehebung

**Fähigkeit wird nicht angezeigt?** `cd ~/.claude/skills/gstack && ./setup`

**`/browse` schlägt fehl?** `cd ~/.claude/skills/gstack && bun install && bun run build`

**Veraltete Installation?** Führen Sie `/gstack-upgrade` aus — oder setzen Sie `auto_upgrade: true` in `~/.gstack/config.yaml`

**Windows-Benutzer:** gstack funktioniert auf Windows 11 über Git Bash oder WSL. Node.js ist zusätzlich zu Bun erforderlich — Bun hat einen bekannten Fehler mit Playwrights Pipe-Transport unter Windows ([bun#4253](https://github.com/oven-sh/bun/issues/4253)). Der Browse-Server fällt automatisch auf Node.js zurück. Stellen Sie sicher, dass sich sowohl `bun` als auch `node` in Ihrem PATH befinden.

**Claude sagt, es kann die Fähigkeiten nicht sehen?** Stellen Sie sicher, dass das `CLAUDE.md` Ihres Projekts einen gstack-Abschnitt hat. Fügen Sie dies hinzu:

```
## gstack
Verwenden Sie /browse von gstack für alle Web-Browsing. Verwenden Sie niemals mcp__claude-in-chrome__*-Tools.
Verfügbare Fähigkeiten: /office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review,
/design-consultation, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse,
/qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /retro,
/investigate, /document-release, /codex, /cso, /autoplan, /careful, /freeze, /guard,
/unfreeze, /gstack-upgrade.
```

## Lizenz

MIT. Für immer kostenlos. Bauen Sie etwas.