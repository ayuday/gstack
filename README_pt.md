<!-- language -->
[English](README.md) | [简体中文](README_zh-CN.md) | [Русский](README_ru.md) | [日本語](README_ja.md) | [한국어](README_ko.md) | [Français](README_fr.md) | [Deutsch](README_de.md) | [Italiano](README_it.md)| [Español](README_es.md) | [Português](README_pt.md) | [العربية](README_ar.md) | [ไทย](README_th.md) | [Tiếng Việt](README_vi.md)

# gstack

> "Acho que não digitei uma linha de código provavelmente desde dezembro, basicamente, o que é uma mudança extremamente grande." — [Andrej Karpathy](https://fortune.com/2026/03/21/andrej-karpathy-openai-cofounder-ai-agents-coding-state-of-psychosis-openclaw/), podcast No Priors, março de 2026

Quando ouvi Karpathy dizer isso, quis descobrir como. Como uma pessoa pode entregar como uma equipe de vinte? Peter Steinberger construiu [OpenClaw](https://github.com/openclaw/openclaw) — 247K estrelas no GitHub — essencialmente sozinho com agentes de IA. A revolução está aqui. Um único construtor com as ferramentas certas pode se mover mais rápido que uma equipe tradicional.

Sou [Garry Tan](https://x.com/garrytan), Presidente e CEO da [Y Combinator](https://www.ycombinator.com/). Trabalhei com milhares de startups — Coinbase, Instacart, Rippling — quando eram uma ou duas pessoas em uma garagem. Antes do YC, fui um dos primeiros engenheiros/PM/designers na Palantir, cofundei a Posterous (vendida ao Twitter), e construí o Bookface, a rede social interna do YC.

**gstack é minha resposta.** Tenho construído produtos por vinte anos, e agora estou entregando mais código do que nunca. Nos últimos 60 dias: **mais de 600.000 linhas de código de produção** (35% testes), **10.000-20.000 linhas por dia**, meio período, enquanto gerencio o YC em tempo integral. Este é meu último `/retro` em 3 projetos: **140.751 linhas adicionadas, 362 commits, ~115k LOC líquidas** em uma semana.

**2026 — 1.237 contribuições e contando:**

![Contribuições do GitHub 2026 — 1.237 contribuições, aceleração massiva em jan-mar](docs/images/github-2026.png)

**2013 — quando construí o Bookface no YC (772 contribuições):**

![Contribuições do GitHub 2013 — 772 contribuições construindo o Bookface no YC](docs/images/github-2013.png)

Mesma pessoa. Época diferente. A diferença está nas ferramentas.

**gstack é como eu faço.** Transforma o Claude Code em uma equipe de engenharia virtual — um CEO que repensa o produto, um gerente de engenharia que trava a arquitetura, um designer que identifica lixo de IA, um revisor que encontra bugs de produção, um líder de QA que abre um navegador real, um oficial de segurança que executa auditorias OWASP + STRIDE, e um engenheiro de release que entrega o PR. Vinte especialistas e oito ferramentas poderosas, todos comandos slash, tudo Markdown, tudo grátis, licença MIT.

Esta é minha fábrica de software de código aberto. Uso todos os dias. Compartilho porque essas ferramentas deveriam estar disponíveis para todos.

Faça um fork. Melhore. Torne seu. E se quiser odiar software de código aberto gratuito — você é bem-vindo, mas preferiria que experimentasse primeiro.

**Para quem é isto:**
- **Fundadores e CEOs** — especialmente os técnicos que ainda querem entregar
- **Usuários do Claude Code pela primeira vez** — papéis estruturados em vez de um prompt vazio
- **Tech leads e engenheiros staff** — revisão rigorosa, QA e automação de release em cada PR

## Início rápido

1. Instale o gstack (30 segundos — veja abaixo)
2. Execute `/office-hours` — descreva o que está construindo
3. Execute `/plan-ceo-review` em qualquer ideia de funcionalidade
4. Execute `/review` em qualquer branch com alterações
5. Execute `/qa` na sua URL de staging
6. Pare aí. Você saberá se isto é para você.

## Instalação — 30 segundos

**Requisitos:** [Claude Code](https://docs.anthropic.com/en/docs/claude-code), [Git](https://git-scm.com/), [Bun](https://bun.sh/) v1.0+, [Node.js](https://nodejs.org/) (apenas Windows)

### Passo 1: Instalar na sua máquina

Abra o Claude Code e cole isto. Claude faz o resto.

> Instalar gstack: execute **`git clone https://github.com/garrytan/gstack.git ~/.claude/skills/gstack && cd ~/.claude/skills/gstack && ./setup`** depois adicione uma seção "gstack" ao CLAUDE.md que diz usar a habilidade /browse do gstack para toda navegação web, nunca usar as ferramentas mcp__claude-in-chrome__*, e lista as habilidades disponíveis: /office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review, /design-consultation, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse, /qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /retro, /investigate, /document-release, /codex, /cso, /autoplan, /careful, /freeze, /guard, /unfreeze, /gstack-upgrade. Depois pergunte ao usuário se também quer adicionar o gstack ao projeto atual para que os colegas de equipe o obtenham.

### Passo 2: Adicionar ao seu repo para que os colegas de equipe o obtenham (opcional)

> Adicionar gstack a este projeto: execute **`cp -Rf ~/.claude/skills/gstack .claude/skills/gstack && rm -rf .claude/skills/gstack/.git && cd .claude/skills/gstack && ./setup`** depois adicione uma seção "gstack" ao CLAUDE.md deste projeto que diz usar a habilidade /browse do gstack para toda navegação web, nunca usar as ferramentas mcp__claude-in-chrome__*, lista as habilidades disponíveis: /office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review, /design-consultation, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse, /qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /retro, /investigate, /document-release, /codex, /cso, /careful, /freeze, /guard, /unfreeze, /gstack-upgrade, e diz ao Claude que se as habilidades do gstack não funcionarem, execute `cd .claude/skills/gstack && ./setup` para construir o binário e registrar habilidades.

Arquivos reais são commitados no seu repo (não um submódulo), então `git clone` simplesmente funciona. Tudo vive dentro de `.claude/`. Nada toca seu PATH ou é executado em segundo plano.

### Codex, Gemini CLI ou Cursor

gstack funciona em qualquer agente que suporte o [padrão SKILL.md](https://github.com/anthropics/claude-code). As habilidades vivem em `.agents/skills/` e são descobertas automaticamente.

```bash
git clone https://github.com/garrytan/gstack.git ~/.codex/skills/gstack
cd ~/.codex/skills/gstack && ./setup --host codex
```

Ou deixe o setup detectar automaticamente quais agentes você tem instalados:

```bash
git clone https://github.com/garrytan/gstack.git ~/gstack
cd ~/gstack && ./setup --host auto
```

Isto instala em `~/.claude/skills/gstack` e/ou `~/.codex/skills/gstack` dependendo do que está disponível. Todas as 28 habilidades funcionam em todos os agentes suportados. Habilidades de segurança baseadas em hook (careful, freeze, guard) usam prosa de segurança inline em hosts que não são Claude.

## Veja como funciona

```
Você:  Quero construir um app de briefing diário para meu calendário.
Você:  /office-hours
Claude: [pergunta sobre a dor — exemplos específicos, não hipotéticos]

Você:  Múltiplos calendários do Google, eventos com informações
       desatualizadas, locais errados. A preparação leva uma
       eternidade e os resultados não são bons o suficiente...

Claude: Vou contestar o enquadramento. Você disse "app de briefing
       diário". Mas o que você realmente descreveu é um chefe de
       gabinete pessoal de IA.
       [extrai 5 capacidades que você não percebia que estava descrevendo]
       [desafia 4 premissas — você concorda, discorda, ou ajusta]
       [gera 3 abordagens de implementação com estimativas de esforço]
       RECOMENDAÇÃO: Entregue amanhã a cunha mais estreita, aprenda
       com o uso real. A visão completa é um projeto de 3 meses —
       comece com o briefing diário que realmente funciona.
       [escreve documento de design → alimenta automaticamente habilidades subsequentes]

Você:  /plan-ceo-review
       [lê o documento de design, desafia o escopo, executa revisão de 10 seções]

Você:  /plan-eng-review
       [diagramas ASCII para fluxo de dados, máquinas de estado, caminhos de erro]
       [matriz de teste, modos de falha, preocupações de segurança]

Você:  Aprovar plano. Sair do modo plano.
       [escreve 2.400 linhas em 11 arquivos. ~8 minutos.]

Você:  /review
       [AUTO-FIXED] 2 problemas. [ASK] Condição de corrida → você aprova correção.

Você:  /qa https://staging.myapp.com
       [abre navegador real, clica nos fluxos, encontra e corrige um bug]

Você:  /ship
       Testes: 42 → 51 (+9 novos). PR: github.com/you/app/pull/42
```

Você disse "app de briefing diário". O agente disse "você está construindo um chefe de gabinete de IA" — porque ouviu sua dor, não sua solicitação de funcionalidade. Oito comandos, de ponta a ponta. Isto não é um copiloto. Isto é uma equipe.

## O sprint

gstack é um processo, não uma coleção de ferramentas. As habilidades são executadas na ordem em que um sprint é executado:

**Pensar → Planejar → Construir → Revisar → Testar → Entregar → Refletir**

Cada habilidade alimenta a próxima. `/office-hours` escreve um documento de design que `/plan-ceo-review` lê. `/plan-eng-review` escreve um plano de teste que `/qa` pega. `/review` captura bugs que `/ship` verifica estarem corrigidos. Nada cai pelas frestas porque cada passo sabe o que veio antes.

| Habilidade | Seu especialista | O que faz |
|-------|----------------|--------------|
| `/office-hours` | **YC Office Hours** | Comece aqui. Seis perguntas obrigatórias que reenquadram seu produto antes de escrever código. Contesta seu enquadramento, desafia premissas, gera alternativas de implementação. O documento de design alimenta cada habilidade subsequente. |
| `/plan-ceo-review` | **CEO / Fundador** | Repensar o problema. Encontrar o produto 10 estrelas escondido dentro da solicitação. Quatro modos: Expansão, Expansão seletiva, Manter escopo, Redução. |
| `/plan-eng-review` | **Gerente de Engenharia** | Travar arquitetura, fluxo de dados, diagramas, casos de borda e testes. Força suposições ocultas a virem à tona. |
| `/plan-design-review` | **Designer sênior** | Avalia cada dimensão de design 0-10, explica como é um 10, depois edita o plano para chegar lá. Detecção de lixo de IA. Interativo — uma AskUserQuestion por escolha de design. |
| `/design-consultation` | **Parceiro de design** | Construa um sistema de design completo do zero. Pesquisa o panorama, propõe riscos criativos, gera mockups de produto realistas. |
| `/review` | **Engenheiro staff** | Encontra os bugs que passam no CI mas explodem em produção. Corrige automaticamente os óbvios. Sinaliza lacunas de completude. |
| `/investigate` | **Debugger** | Depuração sistemática de causa raiz. Lei de ferro: sem correções sem investigação. Rastreia fluxo de dados, testa hipóteses, para após 3 correções falhadas. |
| `/design-review` | **Designer que codifica** | Mesma auditoria que /plan-design-review, depois corrige o que encontra. Commits atômicos, screenshots antes/depois. |
| `/qa` | **Líder de QA** | Testa seu app, encontra bugs, corrige com commits atômicos, reverifica. Gera automaticamente testes de regressão para cada correção. |
| `/qa-only` | **Repórter de QA** | Mesma metodologia que /qa mas apenas relatório. Puro relatório de bug sem alterações de código. |
| `/cso` | **Chief Security Officer** | OWASP Top 10 + modelo de ameaça STRIDE. Zero ruído: 17 exclusões de falsos positivos, porta de confiança 8/10+, verificação independente de descobertas. Cada descoberta inclui um cenário de exploração concreto. |
| `/ship` | **Engenheiro de release** | Sincronizar main, executar testes, auditar cobertura, push, abrir PR. Bootstrap de frameworks de teste se você não tiver um. |
| `/land-and-deploy` | **Engenheiro de release** | Mesclar PR, aguardar CI e deploy, verificar saúde em produção. Um comando de "aprovado" para "verificado em produção". |
| `/canary` | **SRE** | Loop de monitoramento pós-deploy. Vigia erros de console, regressões de desempenho e falhas de página. |
| `/benchmark` | **Engenheiro de desempenho** | Linha de base de tempos de carregamento de página, Core Web Vitals e tamanhos de recursos. Compara antes/depois em cada PR. |
| `/document-release` | **Escritor técnico** | Atualiza toda a documentação do projeto para corresponder ao que você acabou de entregar. Captura READMEs desatualizados automaticamente. |
| `/retro` | **Gerente de Engenharia** | Retro semanal consciente da equipe. Detailhes por pessoa, sequências de entrega, tendências de saúde de testes, oportunidades de crescimento. `/retro global` é executado em todos os seus projetos e ferramentas de IA (Claude Code, Codex, Gemini). |
| `/browse` | **Engenheiro de QA** | Navegador Chromium real, cliques reais, screenshots reais. ~100ms por comando. |
| `/setup-browser-cookies` | **Gerente de sessão** | Importa cookies do seu navegador real (Chrome, Arc, Brave, Edge) para a sessão headless. Testa páginas autenticadas. |
| `/autoplan` | **Pipeline de revisão** | Um comando, plano completamente revisado. Executa automaticamente revisão CEO → design → engenharia com princípios de decisão codificados. Traz à superfície apenas decisões de gosto para sua aprovação. |

### Ferramentas poderosas

| Habilidade | O que faz |
|-------|-------------|
| `/codex` | **Segunda opinião** — revisão de código independente do OpenAI Codex CLI. Três modos: revisão (porta passa/falha), desafio adversarial e consulta aberta. Análise cruzada de modelos quando tanto `/review` quanto `/codex` foram executados. |
| `/careful` | **Guardas de segurança** — avisa antes de comandos destrutivos (rm -rf, DROP TABLE, force-push). Diga "be careful" para ativar. Substitua qualquer aviso. |
| `/freeze` | **Bloqueio de edição** — restringe edições de arquivo a um diretório. Previne alterações acidentais fora do escopo durante a depuração. |
| `/guard` | **Segurança completa** — `/careful` + `/freeze` em um comando. Máxima segurança para trabalho em produção. |
| `/unfreeze` | **Desbloquear** — remove o limite `/freeze`. |
| `/setup-deploy` | **Configurador de deploy** — configuração única para `/land-and-deploy`. Detecta sua plataforma, URL de produção e comandos de deploy. |
| `/gstack-upgrade` | **Auto-atualizador** — atualiza o gstack para a versão mais recente. Detecta instalação global vs vendored, sincroniza ambas, mostra o que mudou. |

**[Aprofundamentos com exemplos e filosofia para cada habilidade →](docs/skills.md)**

## Sprints paralelos

gstack funciona bem com um sprint. Fica interessante com dez rodando ao mesmo tempo.

[Conductor](https://conductor.build) executa múltiplas sessões do Claude Code em paralelo — cada uma em seu próprio espaço de trabalho isolado. Uma sessão em `/office-hours`, outra em `/review`, uma terceira implementando uma funcionalidade, uma quarta executando `/qa`. Tudo ao mesmo tempo. A estrutura do sprint é o que torna o paralelismo possível — sem um processo, dez agentes são dez fontes de caos. Com um processo, cada agente sabe exatamente o que fazer e quando parar.

---

Grátis, licença MIT, código aberto. Sem nível premium, sem lista de espera.

Tornei de código aberto como construo software. Você pode fazer um fork e torná-lo seu.

> **Estamos contratando.** Quer entregar 10K+ LOC/dia e ajudar a fortalecer o gstack?
> Venha trabalhar no YC — [ycombinator.com/software](https://ycombinator.com/software)
> Salário e equity extremamente competitivos. San Francisco, distrito Dogpatch.

## Documentação

| Doc | O que cobre |
|-----|---------------|
| [Aprofundamentos de habilidades](docs/skills.md) | Filosofia, exemplos e fluxo de trabalho para cada habilidade (inclui integração Greptile) |
| [Ethos do construtor](ETHOS.md) | Filosofia do construtor: Ferver o lago, Buscar antes de construir, três camadas de conhecimento |
| [Arquitetura](ARCHITECTURE.md) | Decisões de design e internos do sistema |
| [Referência do navegador](BROWSER.md) | Referência completa de comandos para `/browse` |
| [Contribuir](CONTRIBUTING.md) | Configuração de dev, testes, modo contribuidor e modo dev |
| [Changelog](CHANGELOG.md) | O que há de novo em cada versão |

## Privacidade e Telemetria

gstack inclui telemetria de uso **opt-in** para ajudar a melhorar o projeto. Eis exatamente o que acontece:

- **Desativado por padrão.** Nada é enviado a lugar nenhum a menos que você diga explicitamente sim.
- **Na primeira execução,** o gstack pergunta se você quer compartilhar dados de uso anônimos. Você pode dizer não.
- **O que é enviado (se você optar por participar):** nome da habilidade, duração, sucesso/falha, versão do gstack, SO. Só isso.
- **O que nunca é enviado:** código, caminhos de arquivo, nomes de repo, nomes de branch, prompts ou qualquer conteúdo gerado pelo usuário.
- **Alterar a qualquer momento:** `gstack-config set telemetry off` desativa tudo instantaneamente.

Os dados são armazenados no [Supabase](https://supabase.com) (alternativa open source ao Firebase). O esquema está em [`supabase/migrations/001_telemetry.sql`](supabase/migrations/001_telemetry.sql) — você pode verificar exatamente o que é coletado. A chave publicável do Supabase no repo é uma chave pública (como uma chave de API do Firebase) — políticas de segurança em nível de linha a restringem a acesso apenas de inserção.

**A análise local está sempre disponível.** Execute `gstack-analytics` para ver seu painel de uso pessoal a partir do arquivo JSONL local — nenhum dado remoto necessário.

## Solução de problemas

**A habilidade não aparece?** `cd ~/.claude/skills/gstack && ./setup`

**`/browse` falha?** `cd ~/.claude/skills/gstack && bun install && bun run build`

**Instalação desatualizada?** Execute `/gstack-upgrade` — ou defina `auto_upgrade: true` em `~/.gstack/config.yaml`

**Usuários do Windows:** o gstack funciona no Windows 11 via Git Bash ou WSL. O Node.js é necessário além do Bun — o Bun tem um bug conhecido com o transporte de pipe do Playwright no Windows ([bun#4253](https://github.com/oven-sh/bun/issues/4253)). O servidor de browse retrocede automaticamente para o Node.js. Certifique-se de que tanto `bun` quanto `node` estejam no seu PATH.

**Claude diz que não consegue ver as habilidades?** Certifique-se de que o `CLAUDE.md` do seu projeto tenha uma seção gstack. Adicione isto:

```
## gstack
Use /browse do gstack para toda navegação web. Nunca use as ferramentas mcp__claude-in-chrome__*.
Habilidades disponíveis: /office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review,
/design-consultation, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse,
/qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /retro,
/investigate, /document-release, /codex, /cso, /autoplan, /careful, /freeze, /guard,
/unfreeze, /gstack-upgrade.
```

## Licença

MIT. Grátis para sempre. Vá construir algo.