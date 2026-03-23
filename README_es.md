<!-- language -->
[English](README.md) | [简体中文](README_zh-CN.md) | [Русский](README_ru.md) | [日本語](README_ja.md) | [한국어](README_ko.md) | [Français](README_fr.md) | [Deutsch](README_de.md) | [Italiano](README_it.md)| [Español](README_es.md) | [Português](README_pt.md) | [العربية](README_ar.md) | [ไทย](README_th.md) | [Tiếng Việt](README_vi.md)

# gstack

> "No creo que haya escrito una línea de código probablemente desde diciembre, básicamente, lo cual es un cambio extremadamente grande." — [Andrej Karpathy](https://fortune.com/2026/03/21/andrej-karpathy-openai-cofounder-ai-agents-coding-state-of-psychosis-openclaw/), podcast No Priors, marzo 2026

Cuando escuché a Karpathy decir esto, quise descubrir cómo. ¿Cómo puede una persona entregar como un equipo de veinte? Peter Steinberger construyó [OpenClaw](https://github.com/openclaw/openclaw) — 247K estrellas en GitHub — esencialmente solo con agentes de IA. La revolución está aquí. Un solo constructor con las herramientas adecuadas puede moverse más rápido que un equipo tradicional.

Soy [Garry Tan](https://x.com/garrytan), Presidente y CEO de [Y Combinator](https://www.ycombinator.com/). He trabajado con miles de startups — Coinbase, Instacart, Rippling — cuando eran una o dos personas en un garaje. Antes de YC, fui uno de los primeros ingenieros/PM/diseñadores en Palantir, cofundé Posterous (vendida a Twitter), y construí Bookface, la red social interna de YC.

**gstack es mi respuesta.** He estado construyendo productos durante veinte años, y ahora estoy entregando más código que nunca. En los últimos 60 días: **más de 600.000 líneas de código de producción** (35% tests), **10.000-20.000 líneas por día**, a tiempo parcial, mientras dirijo YC a tiempo completo. Este es mi último `/retro` en 3 proyectos: **140.751 líneas agregadas, 362 commits, ~115k LOC netas** en una semana.

**2026 — 1.237 contribuciones y contando:**

![Contribuciones de GitHub 2026 — 1.237 contribuciones, aceleración masiva en ene-mar](docs/images/github-2026.png)

**2013 — cuando construí Bookface en YC (772 contribuciones):**

![Contribuciones de GitHub 2013 — 772 contribuciones construyendo Bookface en YC](docs/images/github-2013.png)

La misma persona. Diferente época. La diferencia está en las herramientas.

**gstack es cómo lo hago.** Convierte Claude Code en un equipo de ingeniería virtual — un CEO que repiensa el producto, un gerente de ingeniería que bloquea la arquitectura, un diseñador que detecta la basura de IA, un revisor que encuentra bugs de producción, un líder de QA que abre un navegador real, un oficial de seguridad que ejecuta auditorías OWASP + STRIDE, y un ingeniero de release que entrega el PR. Veinte especialistas y ocho herramientas potentes, todos comandos slash, todo Markdown, todo gratis, licencia MIT.

Esta es mi fábrica de software de código abierto. La uso todos los días. La comparto porque estas herramientas deberían estar disponibles para todos.

Haz un fork. Mejóralo. Hazlo tuyo. Y si quieres odiar el software de código abierto gratuito — eres bienvenido, pero preferiría que lo pruebes primero.

**Para quién es esto:**
- **Fundadores y CEOs** — especialmente los técnicos que aún quieren entregar
- **Usuarios de Claude Code por primera vez** — roles estructurados en lugar de un prompt vacío
- **Tech leads e ingenieros staff** — revisión rigurosa, QA y automatización de releases en cada PR

## Inicio rápido

1. Instala gstack (30 segundos — ver abajo)
2. Ejecuta `/office-hours` — describe lo que estás construyendo
3. Ejecuta `/plan-ceo-review` en cualquier idea de funcionalidad
4. Ejecuta `/review` en cualquier rama con cambios
5. Ejecuta `/qa` en tu URL de staging
6. Detente ahí. Sabrás si esto es para ti.

## Instalación — 30 segundos

**Requisitos:** [Claude Code](https://docs.anthropic.com/en/docs/claude-code), [Git](https://git-scm.com/), [Bun](https://bun.sh/) v1.0+, [Node.js](https://nodejs.org/) (solo Windows)

### Paso 1: Instalar en tu máquina

Abre Claude Code y pega esto. Claude hace el resto.

> Instalar gstack: ejecuta **`git clone https://github.com/garrytan/gstack.git ~/.claude/skills/gstack && cd ~/.claude/skills/gstack && ./setup`** luego agrega una sección "gstack" a CLAUDE.md que dice usar la habilidad /browse de gstack para toda navegación web, nunca usar las herramientas mcp__claude-in-chrome__*, y enumera las habilidades disponibles: /office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review, /design-consultation, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse, /qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /retro, /investigate, /document-release, /codex, /cso, /autoplan, /careful, /freeze, /guard, /unfreeze, /gstack-upgrade. Luego pregunta al usuario si también quiere agregar gstack al proyecto actual para que los compañeros de equipo lo obtengan.

### Paso 2: Agregar a tu repo para que los compañeros de equipo lo obtengan (opcional)

> Agregar gstack a este proyecto: ejecuta **`cp -Rf ~/.claude/skills/gstack .claude/skills/gstack && rm -rf .claude/skills/gstack/.git && cd .claude/skills/gstack && ./setup`** luego agrega una sección "gstack" al CLAUDE.md de este proyecto que dice usar la habilidad /browse de gstack para toda navegación web, nunca usar las herramientas mcp__claude-in-chrome__*, enumera las habilidades disponibles: /office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review, /design-consultation, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse, /qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /retro, /investigate, /document-release, /codex, /cso, /careful, /freeze, /guard, /unfreeze, /gstack-upgrade, y le dice a Claude que si las habilidades de gstack no funcionan, ejecuta `cd .claude/skills/gstack && ./setup` para construir el binario y registrar habilidades.

Los archivos reales se hacen commit en tu repo (no un submódulo), así que `git clone` funciona simplemente. Todo vive dentro de `.claude/`. Nada toca tu PATH o se ejecuta en segundo plano.

### Codex, Gemini CLI o Cursor

gstack funciona en cualquier agente que soporte el [estándar SKILL.md](https://github.com/anthropics/claude-code). Las habilidades viven en `.agents/skills/` y se descubren automáticamente.

```bash
git clone https://github.com/garrytan/gstack.git ~/.codex/skills/gstack
cd ~/.codex/skills/gstack && ./setup --host codex
```

O deja que setup detecte automáticamente qué agentes tienes instalados:

```bash
git clone https://github.com/garrytan/gstack.git ~/gstack
cd ~/gstack && ./setup --host auto
```

Esto instala en `~/.claude/skills/gstack` y/o `~/.codex/skills/gstack` dependiendo de lo que esté disponible. Las 28 habilidades funcionan en todos los agentes soportados. Las habilidades de seguridad basadas en hooks (careful, freeze, guard) usan prosa de seguridad inline en hosts que no son Claude.

## Mira cómo funciona

```
Tú:    Quiero construir una app de briefing diario para mi calendario.
Tú:    /office-hours
Claude: [pregunta sobre el dolor — ejemplos específicos, no hipotéticos]

Tú:    Múltiples calendarios de Google, eventos con información obsoleta,
        ubicaciones incorrectas. La preparación toma una eternidad y
        los resultados no son lo suficientemente buenos...

Claude: Voy a objetar el encuadre. Dijiste "app de briefing
        diario". Pero lo que realmente describiste es un jefe de
        gabinete personal de IA.
        [extrae 5 capacidades que no te dabas cuenta que describías]
        [desafía 4 premisas — estás de acuerdo, en desacuerdo, o ajustas]
        [genera 3 enfoques de implementación con estimaciones de esfuerzo]
        RECOMENDACIÓN: Entrega mañana la cuña más estrecha, aprende
        del uso real. La visión completa es un proyecto de 3 meses —
        comienza con el briefing diario que realmente funciona.
        [escribe documento de diseño → alimenta automáticamente habilidades posteriores]

Tú:    /plan-ceo-review
        [lee el documento de diseño, desafía el alcance, ejecuta revisión de 10 secciones]

Tú:    /plan-eng-review
        [diagramas ASCII para flujo de datos, máquinas de estado, rutas de error]
        [matriz de pruebas, modos de falla, preocupaciones de seguridad]

Tú:    Aprobar plan. Salir del modo plan.
        [escribe 2.400 líneas en 11 archivos. ~8 minutos.]

Tú:    /review
        [AUTO-FIXED] 2 problemas. [ASK] Condición de carrera → apruebas fix.

Tú:    /qa https://staging.myapp.com
        [abre navegador real, hace clic en flujos, encuentra y arregla un bug]

Tú:    /ship
        Tests: 42 → 51 (+9 nuevos). PR: github.com/you/app/pull/42
```

Dijiste "app de briefing diario". El agente dijo "estás construyendo un jefe de gabinete de IA" — porque escuchó tu dolor, no tu solicitud de funcionalidad. Ocho comandos, de extremo a extremo. Esto no es un copiloto. Esto es un equipo.

## El sprint

gstack es un proceso, no una colección de herramientas. Las habilidades se ejecutan en el orden en que se ejecuta un sprint:

**Pensar → Planificar → Construir → Revisar → Probar → Entregar → Reflexionar**

Cada habilidad alimenta a la siguiente. `/office-hours` escribe un documento de diseño que `/plan-ceo-review` lee. `/plan-eng-review` escribe un plan de pruebas que `/qa` recoge. `/review` captura bugs que `/ship` verifica que están arreglados. Nada se cae por las grietas porque cada paso sabe qué vino antes.

| Habilidad | Tu especialista | Lo que hace |
|-------|----------------|--------------|
| `/office-hours` | **YC Office Hours** | Comienza aquí. Seis preguntas obligatorias que reformulan tu producto antes de escribir código. Objecta tu encuadre, desafía premisas, genera alternativas de implementación. El documento de diseño alimenta cada habilidad posterior. |
| `/plan-ceo-review` | **CEO / Fundador** | Repensar el problema. Encontrar el producto de 10 estrellas oculto dentro de la solicitud. Cuatro modos: Expansión, Expansión selectiva, Mantener alcance, Reducción. |
| `/plan-eng-review` | **Gerente de Ingeniería** | Bloquear arquitectura, flujo de datos, diagramas, casos límite y pruebas. Forza las suposiciones ocultas a salir a la luz. |
| `/plan-design-review` | **Diseñador senior** | Califica cada dimensión de diseño 0-10, explica cómo se ve un 10, luego edita el plan para llegar allí. Detección de basura de IA. Interactivo — una AskUserQuestion por elección de diseño. |
| `/design-consultation` | **Socio de diseño** | Construye un sistema de diseño completo desde cero. Investiga el panorama, propone riesgos creativos, genera mockups de producto realistas. |
| `/review` | **Ingeniero staff** | Encuentra los bugs que pasan CI pero explotan en producción. Arregla automáticamente los obvios. Marca brechas de completitud. |
| `/investigate` | **Depurador** | Depuración sistemática de causa raíz. Ley de hierro: sin arreglos sin investigación. Rastrea flujo de datos, prueba hipótesis, se detiene después de 3 arreglos fallidos. |
| `/design-review` | **Diseñador que codifica** | Misma auditoría que /plan-design-review, luego arregla lo que encuentra. Commits atómicos, capturas antes/después. |
| `/qa` | **Líder de QA** | Prueba tu app, encuentra bugs, arréglalos con commits atómicos, reverifica. Genera automáticamente tests de regresión para cada arreglo. |
| `/qa-only` | **Reportero de QA** | Misma metodología que /qa pero solo informe. Puro informe de bugs sin cambios de código. |
| `/cso` | **Chief Security Officer** | OWASP Top 10 + modelo de amenaza STRIDE. Cero ruido: 17 exclusiones de falsos positivos, puerta de confianza 8/10+, verificación independiente de hallazgos. Cada hallazgo incluye un escenario de explotación concreto. |
| `/ship` | **Ingeniero de release** | Sincronizar main, ejecutar tests, auditar cobertura, push, abrir PR. Bootstrap de frameworks de test si no tienes uno. |
| `/land-and-deploy` | **Ingeniero de release** | Fusionar PR, esperar CI y deploy, verificar salud en producción. Un comando de "aprobado" a "verificado en producción". |
| `/canary` | **SRE** | Bucle de monitoreo post-deploy. Vigila errores de consola, regresiones de rendimiento y fallos de página. |
| `/benchmark` | **Ingeniero de rendimiento** | Línea base de tiempos de carga de página, Core Web Vitals y tamaños de recursos. Compara antes/después en cada PR. |
| `/document-release` | **Escritor técnico** | Actualiza toda la documentación del proyecto para coincidir con lo que acabas de entregar. Captura READMEs obsoletos automáticamente. |
| `/retro` | **Gerente de Ingeniería** | Retro semanal consciente del equipo. Desgloses por persona, rachas de entrega, tendencias de salud de tests, oportunidades de crecimiento. `/retro global` se ejecuta en todos tus proyectos y herramientas de IA (Claude Code, Codex, Gemini). |
| `/browse` | **Ingeniero de QA** | Navegador Chromium real, clics reales, capturas reales. ~100ms por comando. |
| `/setup-browser-cookies` | **Gerente de sesión** | Importa cookies de tu navegador real (Chrome, Arc, Brave, Edge) a la sesión headless. Prueba páginas autenticadas. |
| `/autoplan` | **Pipeline de revisión** | Un comando, plan completamente revisado. Ejecuta automáticamente revisión CEO → diseño → ingeniería con principios de decisión codificados. Superficie solo decisiones de gusto para tu aprobación. |

### Herramientas potentes

| Habilidad | Lo que hace |
|-------|-------------|
| `/codex` | **Segunda opinión** — revisión de código independiente desde OpenAI Codex CLI. Tres modos: revisión (puerta pasa/falla), desafío adversarial y consulta abierta. Análisis cruzado de modelos cuando tanto `/review` como `/codex` han sido ejecutados. |
| `/careful` | **Barreras de seguridad** — advierte antes de comandos destructivos (rm -rf, DROP TABLE, force-push). Di "be careful" para activar. Anula cualquier advertencia. |
| `/freeze` | **Bloqueo de edición** — restringe ediciones de archivo a un directorio. Previene cambios accidentales fuera del alcance mientras se depura. |
| `/guard` | **Seguridad completa** — `/careful` + `/freeze` en un comando. Máxima seguridad para trabajo en producción. |
| `/unfreeze` | **Desbloquear** — elimina el límite `/freeze`. |
| `/setup-deploy` | **Configurador de deploy** — configuración única para `/land-and-deploy`. Detecta tu plataforma, URL de producción y comandos de deploy. |
| `/gstack-upgrade` | **Auto-actualizador** — actualiza gstack a la última versión. Detecta instalación global vs vendored, sincroniza ambas, muestra qué cambió. |

**[Profundizaciones con ejemplos y filosofía para cada habilidad →](docs/skills.md)**

## Sprints paralelos

gstack funciona bien con un sprint. Se vuelve interesante con diez corriendo a la vez.

[Conductor](https://conductor.build) ejecuta múltiples sesiones de Claude Code en paralelo — cada una en su propio espacio de trabajo aislado. Una sesión en `/office-hours`, otra en `/review`, una tercera implementando una funcionalidad, una cuarta ejecutando `/qa`. Todo al mismo tiempo. La estructura del sprint es lo que hace que el paralelismo funcione — sin un proceso, diez agentes son diez fuentes de caos. Con un proceso, cada agente sabe exactamente qué hacer y cuándo detenerse.

---

Gratis, licencia MIT, código abierto. Sin nivel premium, sin lista de espera.

Hice de código abierto cómo construyo software. Puedes hacer un fork y hacerlo tuyo.

> **Estamos contratando.** ¿Quieres entregar 10K+ LOC/día y ayudar a endurecer gstack?
> Ven a trabajar a YC — [ycombinator.com/software](https://ycombinator.com/software)
> Salario y capital extremadamente competitivos. San Francisco, distrito Dogpatch.

## Documentación

| Doc | Lo que cubre |
|-----|---------------|
| [Profundizaciones de habilidades](docs/skills.md) | Filosofía, ejemplos y flujo de trabajo para cada habilidad (incluye integración Greptile) |
| [Etos del constructor](ETHOS.md) | Filosofía del constructor: Hervir el lago, Buscar antes de construir, tres capas de conocimiento |
| [Arquitectura](ARCHITECTURE.md) | Decisiones de diseño e internos del sistema |
| [Referencia del navegador](BROWSER.md) | Referencia completa de comandos para `/browse` |
| [Contribuir](CONTRIBUTING.md) | Configuración de dev, pruebas, modo contribuidor y modo dev |
| [Changelog](CHANGELOG.md) | Qué hay de nuevo en cada versión |

## Privacidad y Telemetría

gstack incluye telemetría de uso **opt-in** para ayudar a mejorar el proyecto. Esto es exactamente lo que sucede:

- **Desactivado por defecto.** No se envía nada a ninguna parte a menos que digas explícitamente que sí.
- **En el primer inicio,** gstack pregunta si quieres compartir datos de uso anónimos. Puedes decir que no.
- **Lo que se envía (si optas por participar):** nombre de habilidad, duración, éxito/fallo, versión de gstack, SO. Eso es todo.
- **Lo que nunca se envía:** código, rutas de archivo, nombres de repo, nombres de rama, prompts o cualquier contenido generado por el usuario.
- **Cambiar en cualquier momento:** `gstack-config set telemetry off` deshabilita todo instantáneamente.

Los datos se almacenan en [Supabase](https://supabase.com) (alternativa open source a Firebase). El esquema está en [`supabase/migrations/001_telemetry.sql`](supabase/migrations/001_telemetry.sql) — puedes verificar exactamente qué se recopila. La clave publicable de Supabase en el repo es una clave pública (como una clave API de Firebase) — las políticas de seguridad a nivel de fila la restringen a acceso de solo inserción.

**El análisis local siempre está disponible.** Ejecuta `gstack-analytics` para ver tu panel de uso personal desde el archivo JSONL local — no se necesitan datos remotos.

## Solución de problemas

**¿La habilidad no aparece?** `cd ~/.claude/skills/gstack && ./setup`

**¿`/browse` falla?** `cd ~/.claude/skills/gstack && bun install && bun run build`

**¿Instalación obsoleta?** Ejecuta `/gstack-upgrade` — o establece `auto_upgrade: true` en `~/.gstack/config.yaml`

**Usuarios de Windows:** gstack funciona en Windows 11 a través de Git Bash o WSL. Se requiere Node.js además de Bun — Bun tiene un bug conocido con el transporte de tubería de Playwright en Windows ([bun#4253](https://github.com/oven-sh/bun/issues/4253)). El servidor de browse retrocede automáticamente a Node.js. Asegúrate de que tanto `bun` como `node` estén en tu PATH.

**¿Claude dice que no puede ver las habilidades?** Asegúrate de que el `CLAUDE.md` de tu proyecto tenga una sección de gstack. Agrega esto:

```
## gstack
Usa /browse de gstack para toda navegación web. Nunca uses las herramientas mcp__claude-in-chrome__*.
Habilidades disponibles: /office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review,
/design-consultation, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse,
/qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /retro,
/investigate, /document-release, /codex, /cso, /autoplan, /careful, /freeze, /guard,
/unfreeze, /gstack-upgrade.
```

## Licencia

MIT. Gratis para siempre. Ve a construir algo.