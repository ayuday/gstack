<!-- language -->
[English](README.md) | [简体中文](README_zh-CN.md) | [Русский](README_ru.md) | [日本語](README_ja.md) | [한국어](README_ko.md) | [Français](README_fr.md) | [Deutsch](README_de.md) | [Italiano](README_it.md)| [Español](README_es.md) | [Português](README_pt.md) | [العربية](README_ar.md) | [ไทย](README_th.md) | [Tiếng Việt](README_vi.md)

# gstack

> « Je ne pense pas avoir tapé une ligne de code depuis décembre, fondamentalement, ce qui est un changement extrêmement important. » — [Andrej Karpathy](https://fortune.com/2026/03/21/andrej-karpathy-openai-cofounder-ai-agents-coding-state-of-psychosis-openclaw/), podcast No Priors, mars 2026

Quand j'ai entendu Karpathy dire cela, j'ai voulu savoir comment. Comment une personne peut-elle livrer comme une équipe de vingt ? Peter Steinberger a construit [OpenClaw](https://github.com/openclaw/openclaw) — 247K étoiles GitHub — essentiellement seul avec des agents IA. La révolution est là. Un seul constructeur avec les bons outils peut aller plus vite qu'une équipe traditionnelle.

Je suis [Garry Tan](https://x.com/garrytan), Président & CEO de [Y Combinator](https://www.ycombinator.com/). J'ai travaillé avec des milliers de startups — Coinbase, Instacart, Rippling — quand elles n'étaient qu'une ou deux personnes dans un garage. Avant YC, j'étais l'un des premiers ingénieurs/PM/designers chez Palantir, j'ai cofondé Posterous (vendu à Twitter), et j'ai construit Bookface, le réseau social interne de YC.

**gstack est ma réponse.** Je construis des produits depuis vingt ans, et maintenant je livre plus de code que jamais. Au cours des 60 derniers jours : **plus de 600 000 lignes de code de production** (35% de tests), **10 000 à 20 000 lignes par jour**, à temps partiel, tout en dirigeant YC à temps plein. Voici mon dernier `/retro` sur 3 projets : **140 751 lignes ajoutées, 362 commits, ~115k LOC net** en une semaine.

**2026 — 1 237 contributions et ça continue :**

![Contributions GitHub 2026 — 1 237 contributions, accélération massive en janv-mars](docs/images/github-2026.png)

**2013 — quand j'ai construit Bookface chez YC (772 contributions) :**

![Contributions GitHub 2013 — 772 contributions construisant Bookface chez YC](docs/images/github-2013.png)

Même personne. Époque différente. La différence, c'est l'outillage.

**gstack est ma façon de faire.** Il transforme Claude Code en une équipe d'ingénierie virtuelle — un PDG qui repense le produit, un responsable technique qui verrouille l'architecture, un designer qui repère le contenu IA de mauvaise qualité, un réviseur qui trouve les bugs de production, un responsable QA qui ouvre un vrai navigateur, un responsable sécurité qui exécute des audits OWASP + STRIDE, et un ingénieur de release qui livre la PR. Vingt spécialistes et huit outils puissants, tous des commandes slash, tous en Markdown, tous gratuits, licence MIT.

Ceci est mon usine de logiciel open source. Je l'utilise tous les jours. Je le partage parce que ces outils devraient être accessibles à tous.

Forkez-le. Améliorez-le. Faites-le vôtre. Et si vous voulez critiquer le logiciel open source gratuit — vous êtes les bienvenus, mais je préférerais que vous l'essayiez d'abord.

**Pour qui :**
- **Fondateurs et PDG** — surtout les techniques qui veulent encore livrer
- **Utilisateurs de Claude Code pour la première fois** — des rôles structurés au lieu d'un prompt vide
- **Tech leads et ingénieurs staff** — révision rigoureuse, QA et automatisation des releases sur chaque PR

## Démarrage rapide

1. Installez gstack (30 secondes — voir ci-dessous)
2. Exécutez `/office-hours` — décrivez ce que vous construisez
3. Exécutez `/plan-ceo-review` sur toute idée de fonctionnalité
4. Exécutez `/review` sur toute branche avec des modifications
5. Exécutez `/qa` sur votre URL de staging
6. Arrêtez-vous là. Vous saurez si c'est pour vous.

## Installation — 30 secondes

**Prérequis :** [Claude Code](https://docs.anthropic.com/en/docs/claude-code), [Git](https://git-scm.com/), [Bun](https://bun.sh/) v1.0+, [Node.js](https://nodejs.org/) (Windows uniquement)

### Étape 1 : Installer sur votre machine

Ouvrez Claude Code et collez ceci. Claude fait le reste.

> Installer gstack : exécutez **`git clone https://github.com/garrytan/gstack.git ~/.claude/skills/gstack && cd ~/.claude/skills/gstack && ./setup`** puis ajoutez une section "gstack" à CLAUDE.md qui dit d'utiliser la compétence /browse de gstack pour toute navigation web, ne jamais utiliser les outils mcp__claude-in-chrome__*, et liste les compétences disponibles : /office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review, /design-consultation, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse, /qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /retro, /investigate, /document-release, /codex, /cso, /autoplan, /careful, /freeze, /guard, /unfreeze, /gstack-upgrade. Puis demandez à l'utilisateur s'il veut aussi ajouter gstack au projet actuel pour que les coéquipiers l'aient.

### Étape 2 : Ajouter à votre repo pour que les coéquipiers l'aient (optionnel)

> Ajouter gstack à ce projet : exécutez **`cp -Rf ~/.claude/skills/gstack .claude/skills/gstack && rm -rf .claude/skills/gstack/.git && cd .claude/skills/gstack && ./setup`** puis ajoutez une section "gstack" au CLAUDE.md de ce projet qui dit d'utiliser la compétence /browse de gstack pour toute navigation web, ne jamais utiliser les outils mcp__claude-in-chrome__*, liste les compétences disponibles : /office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review, /design-consultation, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse, /qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /retro, /investigate, /document-release, /codex, /cso, /careful, /freeze, /guard, /unfreeze, /gstack-upgrade, et dit à Claude que si les compétences gstack ne fonctionnent pas, exécutez `cd .claude/skills/gstack && ./setup` pour construire le binaire et enregistrer les compétences.

Les vrais fichiers sont commités dans votre repo (pas un sous-module), donc `git clone` fonctionne simplement. Tout vit dans `.claude/`. Rien ne touche votre PATH ou ne s'exécute en arrière-plan.

### Codex, Gemini CLI, ou Cursor

gstack fonctionne sur tout agent qui prend en charge le [standard SKILL.md](https://github.com/anthropics/claude-code). Les compétences vivent dans `.agents/skills/` et sont découvertes automatiquement.

```bash
git clone https://github.com/garrytan/gstack.git ~/.codex/skills/gstack
cd ~/.codex/skills/gstack && ./setup --host codex
```

Ou laissez setup détecter automatiquement quels agents vous avez installés :

```bash
git clone https://github.com/garrytan/gstack.git ~/gstack
cd ~/gstack && ./setup --host auto
```

Cela installe dans `~/.claude/skills/gstack` et/ou `~/.codex/skills/gstack` selon ce qui est disponible. Les 28 compétences fonctionnent sur tous les agents pris en charge. Les compétences de sécurité basées sur des hooks (careful, freeze, guard) utilisent une prose de sécurité inline sur les hôtes non-Claude.

## Voyez-le fonctionner

```
Vous :   Je veux construire une appli de briefing quotidien pour mon calendrier.
Vous :   /office-hours
Claude : [demande la douleur — des exemples concrets, pas des hypothèses]

Vous :   Plusieurs calendriers Google, événements avec infos périmées,
         mauvais lieux. La préparation prend une éternité et les
         résultats ne sont pas assez bons...

Claude : Je vais contester le cadrage. Vous avez dit "appli de briefing
         quotidien". Mais ce que vous décrivez vraiment est un chef de
         cabinet personnel IA.
         [extrait 5 capacités que vous ne réalisiez pas décrire]
         [conteste 4 prémisses — vous êtes d'accord, pas d'accord, ou ajustez]
         [génère 3 approches d'implémentation avec estimations d'effort]
         RECOMMANDATION : Livrez le coin le plus étroit demain, apprenez
         de l'usage réel. La vision complète est un projet de 3 mois —
         commencez par le briefing quotidien qui fonctionne vraiment.
         [écrit un doc de conception → alimente automatiquement les compétences en aval]

Vous :   /plan-ceo-review
         [lit le doc de conception, conteste le scope, exécute une révision en 10 sections]

Vous :   /plan-eng-review
         [diagrammes ASCII pour le flux de données, machines d'état, chemins d'erreur]
         [matrice de test, modes de défaillance, préoccupations de sécurité]

Vous :   Approuver le plan. Sortir du mode plan.
         [écrit 2 400 lignes dans 11 fichiers. ~8 minutes.]

Vous :   /review
         [AUTO-FIXED] 2 problèmes. [ASK] Condition de course → vous approuvez la correction.

Vous :   /qa https://staging.myapp.com
         [ouvre un vrai navigateur, clique dans les flux, trouve et corrige un bug]

Vous :   /ship
         Tests : 42 → 51 (+9 nouveaux). PR : github.com/you/app/pull/42
```

Vous avez dit "appli de briefing quotidien". L'agent a dit "vous construisez un chef de cabinet IA" — parce qu'il a écouté votre douleur, pas votre demande de fonctionnalité. Huit commandes, de bout en bout. Ce n'est pas un copilote. C'est une équipe.

## Le sprint

gstack est un processus, pas une collection d'outils. Les compétences s'exécutent dans l'ordre où un sprint s'exécute :

**Penser → Planifier → Construire → Réviser → Tester → Livrer → Réfléchir**

Chaque compétence alimente la suivante. `/office-hours` écrit un doc de conception que `/plan-ceo-review` lit. `/plan-eng-review` écrit un plan de test que `/qa` reprend. `/review` attrape les bugs que `/ship` vérifie être corrigés. Rien ne passe à travers les mailles du filet parce que chaque étape sait ce qui l'a précédée.

| Compétence | Votre spécialiste | Ce qu'il fait |
|-------|----------------|--------------|
| `/office-hours` | **YC Office Hours** | Commencez ici. Six questions contraignantes qui recadrent votre produit avant d'écrire du code. Conteste votre cadrage, défie les prémisses, génère des alternatives d'implémentation. Le doc de conception alimente chaque compétence en aval. |
| `/plan-ceo-review` | **PDG / Fondateur** | Repensez le problème. Trouvez le produit 10 étoiles caché dans la demande. Quatre modes : Expansion, Expansion sélective, Maintenir le scope, Réduction. |
| `/plan-eng-review` | **Responsable technique** | Verrouillez l'architecture, le flux de données, les diagrammes, les cas limites et les tests. Force les hypothèses cachées à se révéler. |
| `/plan-design-review` | **Designer senior** | Note chaque dimension de conception 0-10, explique à quoi ressemble un 10, puis modifie le plan pour y arriver. Détection de contenu IA de mauvaise qualité. Interactif — une AskUserQuestion par choix de conception. |
| `/design-consultation` | **Partenaire design** | Construisez un système de design complet from scratch. Recherche le paysage, propose des risques créatifs, génère des maquettes produit réalistes. |
| `/review` | **Ingénieur staff** | Trouve les bugs qui passent la CI mais explosent en production. Corrige automatiquement les évidents. Signale les lacunes de complétude. |
| `/investigate` | **Débogueur** | Débogage systématique de cause racine. Loi de fer : pas de corrections sans investigation. Trace le flux de données, teste les hypothèses, s'arrête après 3 corrections échouées. |
| `/design-review` | **Designer qui code** | Même audit que /plan-design-review, puis corrige ce qu'il trouve. Commits atomiques, captures avant/après. |
| `/qa` | **Responsable QA** | Teste votre appli, trouve les bugs, les corrige avec des commits atomiques, revérifie. Génère automatiquement des tests de régression pour chaque correction. |
| `/qa-only` | **Rapporteur QA** | Même méthodologie que /qa mais rapport seulement. Pur rapport de bug sans changements de code. |
| `/cso` | **Chief Security Officer** | OWASP Top 10 + modèle de menace STRIDE. Zéro bruit : 17 exclusions de faux positifs, porte de confiance 8/10+, vérification indépendante des trouvailles. Chaque trouvaille inclut un scénario d'exploitation concret. |
| `/ship` | **Ingénieur de release** | Synchronise main, exécute les tests, audite la couverture, push, ouvre la PR. Bootstrap les frameworks de test si vous n'en avez pas. |
| `/land-and-deploy` | **Ingénieur de release** | Fusionne la PR, attend la CI et déploie, vérifie la santé en production. Une commande de "approuvé" à "vérifié en production". |
| `/canary` | **SRE** | Boucle de surveillance post-déploiement. Surveille les erreurs console, régressions de performance, échecs de page. |
| `/benchmark` | **Ingénieur performance** | Référence les temps de chargement de page, Core Web Vitals, et tailles de ressources. Compare avant/après sur chaque PR. |
| `/document-release` | **Rédacteur technique** | Met à jour toute la documentation du projet pour correspondre à ce que vous venez de livrer. Attrape les README périmés automatiquement. |
| `/retro` | **Responsable technique** | Rétro hebdomadaire consciente de l'équipe. Ventilations par personne, séries de livraisons, tendances de santé des tests, opportunités de croissance. `/retro global` s'exécute sur tous vos projets et outils IA (Claude Code, Codex, Gemini). |
| `/browse` | **Ingénieur QA** | Vrai navigateur Chromium, vrais clics, vraies captures. ~100ms par commande. |
| `/setup-browser-cookies` | **Gestionnaire de session** | Importe les cookies de votre vrai navigateur (Chrome, Arc, Brave, Edge) dans la session headless. Teste les pages authentifiées. |
| `/autoplan` | **Pipeline de révision** | Une commande, plan entièrement révisé. Exécute automatiquement révision CEO → design → technique avec des principes de décision encodés. Ne surface que les décisions de goût pour votre approbation. |

### Outils puissants

| Compétence | Ce qu'elle fait |
|-------|-------------|
| `/codex` | **Deuxième avis** — révision de code indépendante depuis OpenAI Codex CLI. Trois modes : révision (porte pass/échec), défi adversarial, et consultation ouverte. Analyse inter-modèles quand `/review` et `/codex` ont tous deux tourné. |
| `/careful` | **Garde-fous de sécurité** — avertit avant les commandes destructrices (rm -rf, DROP TABLE, force-push). Dites "be careful" pour activer. Outre-passez tout avertissement. |
| `/freeze` | **Verrouillage d'édition** — restreint les éditions de fichier à un dossier. Empêche les changements accidentels hors scope pendant le débogage. |
| `/guard` | **Sécurité complète** — `/careful` + `/freeze` en une commande. Sécurité maximale pour le travail en prod. |
| `/unfreeze` | **Déverrouiller** — retire la limite `/freeze`. |
| `/setup-deploy` | **Configurateur de déploiement** — configuration unique pour `/land-and-deploy`. Détecte votre plateforme, URL de production, et commandes de déploiement. |
| `/gstack-upgrade` | **Auto-metteur à jour** — met à jour gstack vers la dernière version. Détecte l'installation globale ou vendored, synchronise les deux, montre ce qui a changé. |

**[Plongées profondes avec exemples et philosophie pour chaque compétence →](docs/skills.md)**

## Sprints parallèles

gstack fonctionne bien avec un sprint. Ça devient intéressant avec dix qui tournent en même temps.

[Conductor](https://conductor.build) exécute plusieurs sessions Claude Code en parallèle — chacune dans son propre espace de travail isolé. Une session sur `/office-hours`, une autre sur `/review`, une troisième implémente une fonctionnalité, une quatrième exécute `/qa`. Toutes en même temps. La structure du sprint est ce qui rend le parallélisme possible — sans processus, dix agents sont dix sources de chaos. Avec un processus, chaque agent sait exactement quoi faire et quand s'arrêter.

---

Gratuit, licence MIT, open source. Pas de niveau premium, pas de liste d'attente.

J'ai open sourcé ma façon de construire des logiciels. Vous pouvez le forker et le faire vôtre.

> **Nous recrutons.** Vous voulez livrer 10K+ LOC/jour et aider à durcir gstack ?
> Venez travailler chez YC — [ycombinator.com/software](https://ycombinator.com/software)
> Salaire et actions extrêmement compétitifs. San Francisco, quartier Dogpatch.

## Documentation

| Doc | Ce qu'il couvre |
|-----|---------------|
| [Plongées profondes sur les compétences](docs/skills.md) | Philosophie, exemples et workflow pour chaque compétence (inclut l'intégration Greptile) |
| [Éthos du constructeur](ETHOS.md) | Philosophie du constructeur : Boil the Lake, Chercher avant de construire, trois couches de connaissance |
| [Architecture](ARCHITECTURE.md) | Décisions de conception et internes du système |
| [Référence du navigateur](BROWSER.md) | Référence complète des commandes pour `/browse` |
| [Contribuer](CONTRIBUTING.md) | Configuration dev, tests, mode contributeur, et mode dev |
| [Changelog](CHANGELOG.md) | Quoi de neuf dans chaque version |

## Confidentialité et Télémétrie

gstack inclut une télémétrie d'usage **opt-in** pour aider à améliorer le projet. Voici exactement ce qui se passe :

- **Désactivé par défaut.** Rien n'est envoyé nulle part sauf si vous dites explicitement oui.
- **Au premier lancement,** gstack demande si vous voulez partager des données d'usage anonymes. Vous pouvez dire non.
- **Ce qui est envoyé (si vous optez in) :** nom de la compétence, durée, succès/échec, version gstack, OS. C'est tout.
- **Ce qui n'est jamais envoyé :** code, chemins de fichiers, noms de repo, noms de branche, prompts, ou tout contenu généré par l'utilisateur.
- **Changer à tout moment :** `gstack-config set telemetry off` désactive tout instantanément.

Les données sont stockées dans [Supabase](https://supabase.com) (alternative open source à Firebase). Le schéma est dans [`supabase/migrations/001_telemetry.sql`](supabase/migrations/001_telemetry.sql) — vous pouvez vérifier exactement ce qui est collecté. La clé publiable Supabase dans le repo est une clé publique (comme une clé API Firebase) — les politiques de sécurité au niveau des lignes la restreignent à un accès en insertion uniquement.

**L'analytique locale est toujours disponible.** Exécutez `gstack-analytics` pour voir votre tableau de bord d'usage personnel depuis le fichier JSONL local — aucune donnée distante nécessaire.

## Dépannage

**La compétence ne s'affiche pas ?** `cd ~/.claude/skills/gstack && ./setup`

**`/browse` échoue ?** `cd ~/.claude/skills/gstack && bun install && bun run build`

**Installation périmée ?** Exécutez `/gstack-upgrade` — ou définissez `auto_upgrade: true` dans `~/.gstack/config.yaml`

**Utilisateurs Windows :** gstack fonctionne sur Windows 11 via Git Bash ou WSL. Node.js est requis en plus de Bun — Bun a un bug connu avec le transport pipe de Playwright sur Windows ([bun#4253](https://github.com/oven-sh/bun/issues/4253)). Le serveur de browse retombe automatiquement sur Node.js. Assurez-vous que `bun` et `node` sont dans votre PATH.

**Claude dit qu'il ne voit pas les compétences ?** Assurez-vous que le `CLAUDE.md` de votre projet a une section gstack. Ajoutez ceci :

```
## gstack
Utilisez /browse de gstack pour toute navigation web. N'utilisez jamais les outils mcp__claude-in-chrome__*.
Compétences disponibles : /office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review,
/design-consultation, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse,
/qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /retro,
/investigate, /document-release, /codex, /cso, /autoplan, /careful, /freeze, /guard,
/unfreeze, /gstack-upgrade.
```

## Licence

MIT. Gratuit pour toujours. Allez construire quelque chose.