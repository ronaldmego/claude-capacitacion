# Curaduria de guias Claude - BPO, Cowork y Code

> Mapa de fuentes existentes para preparar capacitaciones y charlas sobre Claude
> (Enterprise / Cowork / Code). No intenta reemplazar las guias oficiales: las
> ordena, resume y aterriza por audiencia.
>
> **Naturaleza y uso:** material **genérico y reutilizable** para estudiar, dar
> charlas y capacitar equipos en Claude. Pensado para reutilizarse tal cual: copiar
> las plantillas, adaptar la propuesta de sesiones y tomar la curaduría de fuentes.
> Si necesitas casos específicos de tu organización (datasets internos, flujos
> propietarios), mantenlos en tu propio repo — aquí solo vive lo genérico.
>
> Estado: v2.6, 2026-06-22 (v2.6 suma **The Founder's Playbook** — guia oficial
> Anthropic por etapa de startup, fila "Founder / startup" en guias por funcion;
> base para recomendar a founders solos). v2.5, 2026-06-20 (v2.3 Claude for Small Business; v2.4 "Configurar un
> proyecto con Claude Code" — abre bocas track Code con los 4 habitos de un Claude Code confiable,
> estructura `.claude/` oficial y `deny` para secretos verificado; v2.5 suma la
> **plantilla `CLAUDE.md` de empresa lista para distribuir**, sanitizada). La v1
> era demasiado prescriptiva; esta version prioriza fuentes oficiales/originales,
> videos con senales objetivas y posts sociales utiles.

## Materiales de esta carpeta

Este documento es la **guía** (la SSOT — el *por qué* y cómo armar la capacitación).
Desde aquí se llega a los entregables visuales y listos para repartir:

- 📊 **Diagrama de capas** — [`diagrama-capas-claude-empresa.md`](diagrama-capas-claude-empresa.md):
  infográfico ASCII del modelo en capas. Ideal como handout/slide.
- 📄 **Plantilla global lista** — [`global-claude-md-empresa.md`](global-claude-md-empresa.md):
  `CLAUDE.md` para `~/.claude/` (capa 1, compartible con cualquier empleado).
- 📄 **Plantilla por proyecto lista** — [`proyecto-claude-md-empresa.md`](proyecto-claude-md-empresa.md):
  `CLAUDE.md` para la raíz de un repo (capa 2).
- ⚙️ **Settings sample** — [`settings-json-empresa.md`](settings-json-empresa.md):
  `settings.json` con `deny` para proteger secretos (acompaña a las plantillas).

## Como usar este documento

Hay dos tracks:

1. **BPO / negocio / no tecnico**: Legal, RRHH, operaciones, back office,
   finanzas operativas, managers. Superficie principal: Claude Cowork + Chat +
   skills/plugins/conectores.
2. **Tecnico / data / developer**: data engineering, analytics engineering,
   BI/data analysts, developers. Superficie principal: Claude Code + skills +
   `CLAUDE.md` + hooks + subagents + MCP.

La capacitacion debe apoyarse en fuentes existentes:

- **Oficial Anthropic/Claude**: fuente normativa.
- **Repos oficiales Anthropic**: ejemplos reutilizables de skills/plugins.
- **YouTube**: material complementario; priorizado por views/likes y relevancia.
- **X/LinkedIn**: ejemplos virales o visuales para explicar conceptos.

## Repos publicos de alta senal para skills/plugins

Estos repos son publicos y compartibles. Usarlos como fuentes de
referencia o discovery, no como instalacion automatica.

| Repo | Senal | Uso potencial |
|---|---:|---|
| [anthropics/skills](https://github.com/anthropics/skills) | Oficial Anthropic; ~139K stars al 2026-06 | Fuente first-party de Agent Skills. Revisar primero cuando se busquen skills oficiales. |
| [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official) | Oficial Anthropic; ~25K stars | Directorio oficial de plugins Claude; candidato para mostrar a admins/champions. |
| [anthropics/claude-for-legal](https://github.com/anthropics/claude-for-legal) | Oficial Anthropic | Plugins/skills legales listos para usar como ejemplo: commercial legal, employment legal, privacy/compliance, litigation support. |
| [anthropics/knowledge-work-plugins](https://github.com/anthropics/knowledge-work-plugins) | Oficial Anthropic | Plugins para trabajo de conocimiento; encaja con BPO, Legal, finance, ops y soporte. |
| [mattpocock/skills](https://github.com/mattpocock/skills) | Repo publico de Matt Pocock; ~136K stars | Skills reales desde una carpeta `.claude` de engineer avanzado. Muy bueno para mostrar calidad de ejemplos, no para instalar sin revisar. |
| [ComposioHQ/awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills) | Awesome-list; ~61K stars | Discovery de skills Claude. No instalar sin vetting. |
| [hesreallyhim/awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) | Awesome-list; ~44K stars | Lista amplia de skills, hooks, slash-commands, orchestrators y plugins para Claude Code. |
| [BehiSecc/awesome-claude-skills](https://github.com/BehiSecc/awesome-claude-skills) | Awesome-list; ~9K stars | Otra lista de discovery de Claude Skills; usar solo como entrada para evaluar. |
| [K-Dense-AI/scientific-agent-skills](https://github.com/K-Dense-AI/scientific-agent-skills) | Skills sectoriales; ~25K stars | Skills de research, ciencia, ingenieria, analisis y finanzas; potencial para data/analytics, con revision previa. |
| [midudev/autoskills](https://github.com/midudev/autoskills) | Instalador/stack; ~5.6K stars | Interesante por SHA/lockfile; no usar en produccion sin revision de seguridad. |
| [jdepoix/youtube-transcript-api](https://github.com/jdepoix/youtube-transcript-api) | Utilidad popular; ~7.6K stars | Alternativa tecnica para transcripts de YouTube si se necesita auditar videos publicos. |

Regla practica: para capacitacion, usar repos oficiales como demo; usar
awesome-lists solo para descubrir ideas. Antes de instalar o ejecutar una skill,
leer `SKILL.md` y cualquier script incluido.

## Lectura minima recomendada

Si solo hay tiempo para 8 piezas:

| Prioridad | Fuente | Track | Por que importa |
|---|---|---|---|
| 1 | [How Anthropic enables self-service data analytics with Claude](https://claude.com/blog/how-anthropic-enables-self-service-data-analytics-with-claude) | Tecnico/data | Caso interno de Anthropic: self-service analytics, skills, fuentes de verdad, validacion y mantenimiento. Es el blueprint para equipos de datos. |
| 2 | [Get started with Claude Cowork](https://support.claude.com/en/articles/13345190-get-started-with-claude-cowork) | BPO | Manual oficial: como empezar, permisos, proyectos y modos de operacion. |
| 3 | [Use Claude Cowork safely](https://support.claude.com/en/articles/13364135-use-claude-cowork-safely) | BPO/admin | Base para guardrails: file access, scope creep, scheduled tasks, datos sensibles. |
| 4 | [Set up Claude Cowork to work the way you do](https://claude.com/resources/tutorials/cowork-onboarding-guide) | BPO | Explica Cowork Project, folder, tools, browser, instrucciones y plugins. |
| 5 | [Using Claude Cowork for legal: answer fast questions on past decisions](https://claude.com/resources/tutorials/using-claude-cowork-for-legal-question-briefing) | BPO/legal | Caso concreto de Legal: preguntar sobre decisiones pasadas con contexto y citas. |
| 6 | [Claude for Human Resources](https://claude.com/resources/tutorials/claude-for-human-resources) | BPO/RRHH | Ejemplos oficiales para politicas, entrevistas, comunicaciones y tareas HR. |
| 7 | [Best practices for Claude Code](https://code.claude.com/docs/en/best-practices) | Tecnico | Guia oficial para equipos tecnicos: contexto, iteracion, verificacion, hooks. |
| 8 | [Extend Claude Code](https://code.claude.com/docs/en/features-overview) | Tecnico | Mapa oficial de cuando usar `CLAUDE.md`, skills, subagents, hooks, MCP y plugins. |

## Track BPO / no tecnico

### Guia oficial principal

| Fuente | Resumen util para capacitacion |
|---|---|
| [Get started with Claude Cowork](https://support.claude.com/en/articles/13345190-get-started-with-claude-cowork) | Punto de partida para usuarios: Cowork corre desde Claude Desktop, trabaja con archivos y proyectos, y requiere configurar acceso. |
| [Delegating your first task in Claude Cowork](https://claude.com/resources/tutorials/delegating-your-first-task-in-claude-cowork) | Sirve como demo inicial: dar acceso a carpeta/conectores, delegar una tarea completa y revisar el plan antes de cambios. |
| [Set up Claude Cowork to work the way you do](https://claude.com/resources/tutorials/cowork-onboarding-guide) | Muy buena para explicar proyectos, contexto, instrucciones, conectores, plugins y scheduled tasks. |
| [Choosing between Claude Cowork or Chat](https://claude.com/resources/tutorials/choosing-between-claude-cowork-or-chat) | Ayuda a evitar confusion: Chat para conversaciones; Cowork para trabajo con archivos, herramientas y tareas. |
| [Use Claude Cowork safely](https://support.claude.com/en/articles/13364135-use-claude-cowork-safely) | Debe estar en todo training corporativo: acceso selectivo a archivos, monitoreo de tareas, cuidado con scheduled tasks. |
| [Organize your tasks with projects in Claude Cowork](https://support.claude.com/en/articles/14116274-organize-your-tasks-with-projects-in-claude-cowork) | Para ensenar que cada equipo debe tener un workspace ordenado, no tareas sueltas. |
| [Use Claude Cowork on Team and Enterprise plans](https://support.claude.com/en/articles/13455879-use-claude-cowork-on-team-and-enterprise-plans) | Para administradores y champions: condiciones de despliegue en Team/Enterprise. |
| [Claude Cowork desktop architecture overview](https://support.claude.com/en/articles/14479288-claude-cowork-desktop-architecture-overview) | Importante para seguridad: la arquitectura y la visibilidad de endpoint/security tooling deben entenderse antes del rollout. |

### Guias oficiales por funcion

| Funcion | Fuente | Que sacar para la capacitacion |
|---|---|---|
| RRHH | [Claude for Human Resources](https://claude.com/resources/tutorials/claude-for-human-resources) | Politicas, comunicaciones, interview prep, employee communications. Usar como base para RRHH/BPO People. |
| RRHH/Excel | [How to use Claude in Excel for HR: Headcount planning](https://claude.com/resources/tutorials/how-to-use-claude-in-excel-for-hr-headcount-planning) | Buen puente para usuarios de Excel: planeamiento, tablas, escenarios y resumen. |
| Legal | [Using Claude Cowork for legal: answer fast questions on past decisions](https://claude.com/resources/tutorials/using-claude-cowork-for-legal-question-briefing) | Caso canonico de Legal: responder preguntas sobre decisiones previas usando documentos y contexto. |
| Legal/plugins | [anthropics/claude-for-legal](https://github.com/anthropics/claude-for-legal) | Suite oficial de plugins/skills legales: commercial legal, employment legal, privacy/compliance, litigation support. |
| Knowledge work | [anthropics/knowledge-work-plugins](https://github.com/anthropics/knowledge-work-plugins) | Repositorio oficial de plugins para trabajadores de conocimiento; built for Cowork y compatible con Code. |
| **Small business** ★ | [Claude for Small Business (anuncio)](https://www.anthropic.com/news/claude-for-small-business) · [solutions page](https://claude.com/solutions/small-business) | **Paquete oficial Anthropic para back-office no tecnico** (13-may-2026): 15 workflows agenticos + 15 skills listos por funcion (payroll/cierre mensual/forecast, lead triage, dashboards). Conectores QuickBooks, PayPal, HubSpot, Canva, DocuSign, Google Workspace, M365. **El mejor ejemplo "listo para usar" para BPO.** |
| **Founder / startup** ★ | [The Founder's Playbook](https://claude.com/blog/the-founders-playbook) | **Guia oficial Anthropic para founders** (14-may-2026): mapea el uso de Claude por etapa de startup — Idea, MVP, Launch, Scale — con frameworks, ejercicios y prompts. Tesis: el founder pasa de "individual contributor" a "orchestrator" (Claude hace dev inicial, automatizacion de workflows y operaciones; el humano se queda con lo estrategico). Casos: Ambral, Carta Healthcare, HumanLayer. **Base para recomendar a un founder solo sin equipo.** |
| Administradores | [Claude Enterprise Administrator Guide](https://claude.com/resources/tutorials/claude-enterprise-administrator-guide) | Para owners/admins: adopcion, politicas, rollout, ejemplos por funcion. |

### Videos YouTube recomendados para BPO/Cowork

Datos consultados con YouTube Data API el 2026-06-19. Los conteos cambian.
Ordenado por relevancia para usuarios no tecnicos, no solo por vistas.

| Prioridad | Video | Canal | Duracion | Views | Likes | Uso recomendado |
|---|---|---:|---:|---:|---:|---|
| 1 | [Introducing Cowork: Claude Code for the rest of your work](https://www.youtube.com/watch?v=UAmKyyZ-b9E) | Anthropic | 1:09 | 753K | 6.8K | Intro oficial para abrir la capacitacion. |
| ★ ES | [Tutorial completo de Claude Co-work: de cero a avanzado](https://www.youtube.com/watch?v=exZfoIxHKEQ) | Migue Baena IA | 32:50 | 24.8K | 909 | **Pieza base BPO en espanol.** Zero-to-advanced con seguridad primero: carpeta dedicada, instrucciones base, `mi-contexto/` (perfil/escritura/memoria), conectores, skills vs plugins vs tareas programadas. Replicar su escalera. |
| 2 | [Learn 80% of Claude Cowork in Under 20 Minutes](https://www.youtube.com/watch?v=z9rdrNrkvDY) | Jeff Su | 18:55 | 1.04M | 20.3K | Mejor prework general para usuarios de negocio. |
| 3 | [Claude COWORK Clearly Explained](https://www.youtube.com/watch?v=ZeWfksNXlbU) | Eliot Prince | 18:29 | 967K | 12.6K | Explicacion clara para principiantes; buen puente Chat vs Cowork. |
| 4 | [Set Up Claude Cowork better than 99% of people](https://www.youtube.com/watch?v=pl90LATQlHI) | Systems Made Better | 47:53 | 503K | 10.4K | Bueno para champions/power users, no para todos. |
| 5 | [Claude Cowork Full Tutorial](https://www.youtube.com/watch?v=vMo-yRCN3QM) | Bart Slodyczka | 14:23 | 312K | 4.8K | Resumen de workflow, plugins y tareas. |
| 6 | [How to Use Claude Cowork Better Than 99% of People](https://www.youtube.com/watch?v=f95-O8C88uw) | AI for Non Techies | 20:43 | 206K | 4.8K | Muy alineado con audiencia no tecnica; lenguaje accesible. |
| 7 | [Claude Cowork - Full Course for Beginners](https://www.youtube.com/watch?v=tf_KmDNZXzI) | Tech With Tim | 24:16 | 164K | 2.7K | Buen video si alguien quiere entender diferencias con Claude Code. |

### Posts X/LinkedIn utiles para BPO

Notas:

- X/LinkedIn cambian metricas y pueden ocultar contenido segun login.
- Estos links son ejemplos para inspirar slides o casos; no son fuente normativa.

| Fuente | Tema | Por que sirve |
|---|---|---|
| [@alliekmiller - Legal plugin / `/legal:triage-nda`](https://x.com/alliekmiller/status/2021586268573024337) | Legal plugin aplicado a NDA triage. | Ejemplo visual de un skill real de Legal. |
| [@law_ninja - lawyers should use Claude Cowork smartly](https://x.com/law_ninja/status/2026263310661021773) | Legal, contract review, compliance workflows. | Buen framing para Legal: acelerar revision, no reemplazar criterio. |
| [HelloParalegal - What Claude Cowork Actually Is](https://x.com/helloparalegal/article/2028449520498164172) | Legal operations y paralegal work. | Caso BPO/legal: reducir primera revision y dejar humana la decision. |
| [@coreyganim - 21 Claude Cowork plugins](https://x.com/coreyganim/status/2027481262668054788) | Plugins de Cowork por funcion. | Sirve para mostrar amplitud: legal, finance, ops, etc. |
| [@RyanJAyala - Cowork for non-technical people](https://x.com/RyanJAyala/status/2029942669527470087) | Cowork como "Claude Code sin terminal". | Mensaje simple para adopcion. |
| [Hannah Stulberg - CLAUDE.md files](https://www.linkedin.com/posts/hannah-stulberg_claudemd-files-are-the-most-underused-feature-activity-7426982758331199488-UZzF) | Instrucciones persistentes para Claude. | Llevar a BPO como "instrucciones del area / playbook". |

## Track tecnico / data / developers

### Guia oficial principal

| Fuente | Resumen util para capacitacion |
|---|---|
| [How Anthropic enables self-service data analytics with Claude](https://claude.com/blog/how-anthropic-enables-self-service-data-analytics-with-claude) | Lectura central para data teams. Anthropic reporta 95% de consultas de business analytics automatizadas con ~95% accuracy agregada. La tesis: la precision en analytics es problema de contexto/verificacion, no solo generacion de SQL. |
| [Best practices for Claude Code](https://code.claude.com/docs/en/best-practices) | Buenas practicas oficiales: contexto, iteracion, verificacion, hooks para acciones obligatorias. |
| [Extend Claude Code](https://code.claude.com/docs/en/features-overview) | Mapa para decidir entre `CLAUDE.md`, skills, subagents, hooks, MCP y plugins. |
| [How Claude remembers your project](https://code.claude.com/docs/en/memory) | Explica `CLAUDE.md`, memoria del proyecto y auto-memory. |
| [Explore the .claude directory](https://code.claude.com/docs/en/claude-directory) | Estructura oficial: instrucciones, settings, skills, subagents y memoria. |
| [Extend Claude with skills](https://code.claude.com/docs/en/skills) | Como crear, administrar y compartir skills en Claude Code. |
| [Create custom subagents](https://code.claude.com/docs/en/sub-agents) | Para code review, data validation, debugging y separacion de contexto. |
| [Automate actions with hooks](https://code.claude.com/docs/en/hooks-guide) | Para reglas deterministicas: tests, lint, bloqueos de comandos, seguridad. |
| [Hooks reference](https://code.claude.com/docs/en/hooks) | Referencia tecnica de eventos y configuracion de hooks. |

### Resumen de la guia Anthropic de self-service analytics

Fuente: [How Anthropic enables self-service data analytics with Claude](https://claude.com/blog/how-anthropic-enables-self-service-data-analytics-with-claude).

Puntos que deben entrar en la capacitacion de data:

1. **Data is not software**: en analytics suele haber una respuesta correcta,
   una fuente correcta y muchas formas de equivocarse sin que el usuario lo note.
2. **Tres fallas principales**:
   - ambiguedad concepto-entidad: el agente elige mal tabla, metrica, columna o
     definicion;
   - staleness: schemas, fuentes y definiciones cambian;
   - retrieval failure: la informacion existe pero el agente no la encuentra.
3. **Data foundations**: modelos canonicos, datasets gobernados, metadata,
   ownership, freshness, tests y docs siguen siendo la base.
4. **Sources of truth**: semantic layer, lineage, transformation graph,
   referencia estructurada y contexto de negocio.
5. **Skills como conocimiento procedimental**: no solo docs; una skill define
   que fuentes consultar, en que orden, como resolver ambiguedad y como validar.
6. **Pairwise skills**: una skill router + skills/domain docs especializadas.
   Esto reduce la busqueda desde "todo el warehouse" hacia fuentes curadas.
7. **Mantenimiento de skills**: si el modelo de datos cambia y la skill no, la
   precision cae. Anthropic trata skill maintenance como trabajo de ingenieria.
8. **Validacion**: offline evals, online validation, adversarial review y metricas
   de efectividad.

Traduccion aplicada (equipos de datos):

- Para Data Engineering: cada dominio de datos importante debe tener una skill
  que apunte a tablas canonicas, grain, filtros, owners, gotchas y ejemplos.
- Para BPO/self-service: no soltar a usuarios sobre raw tables; darles dominios
  curados, ejemplos y rutas de escalamiento.
- Para governance: OpenMetadata/lineage/glosarios pueden ser la capa de contexto,
  pero solo si estan mantenidos y la skill sabe consultarlos.

### Videos YouTube recomendados para Code/skills

Datos consultados con YouTube Data API el 2026-06-19.

| Prioridad | Video | Canal | Duracion | Views | Likes | Uso recomendado |
|---|---|---:|---:|---:|---:|---|
| 1 | [What are skills?](https://www.youtube.com/watch?v=bjdBVZa66oU) | Claude | 2:54 | 1.24M | 16.0K | Video corto para explicar skills a ambos tracks. |
| 2 | [Mastering Claude Code in 30 minutes](https://www.youtube.com/watch?v=6eBSHbLKuN0) | Anthropic | 28:07 | 1.41M | 26.8K | Video oficial principal para tecnicos. |
| 3 | [Don't Build Agents, Build Skills Instead](https://www.youtube.com/watch?v=CEvIs9y1uog) | AI Engineer | 16:22 | 1.43M | 29.1K | Charla clave: skills > agents genericos. Muy relevante para arquitectura de skills/agents. |
| 4 | [Full Walkthrough: Workflow for AI Coding — Matt Pocock](https://www.youtube.com/watch?v=-QFHIoCo-Ko) | AI Engineer | 1:36:30 | 982K | 20.6K | Walkthrough largo y fuerte para champions tecnicos; no para clase corta. |
| 5 | [Claude Code best practices](https://www.youtube.com/watch?v=gv0WHhKelSE) | Anthropic | 25:53 | 505K | 9.1K | Buen material oficial para engineering practices. |
| 6 | [How AI agents & Claude skills work](https://www.youtube.com/watch?v=S_oN3vlzpMw) | Greg Isenberg | 35:26 | 537K | 13.6K | Buena explicacion divulgativa de skills/agents. |
| 7 | [How to 10x your Claude with 4 .md files](https://www.youtube.com/watch?v=ovLAIhbk3ek) | Greg Isenberg | 0:47 | 661K | 32.0K | Micro-video viral para explicar `CLAUDE.md`/markdown context. |
| 8 | [5 Claude Code skills I use every single day](https://www.youtube.com/watch?v=EJyuu6zlQCg) | Matt Pocock | 16:42 | 413K | 10.4K | Practico para developers: skills reales en uso diario. |
| 9 | [Claude Code Essentials](https://www.youtube.com/watch?v=brLhhkUqcn4) | freeCodeCamp | 12:20:10 | 429K | 14.6K | Curso largo; no para taller, si para referencia profunda. |
| 10 | [The 7 phases of AI-driven development](https://www.youtube.com/watch?v=Ah9p7v7nJWg) | Matt Pocock | 8:27 | 56.0K | 1.9K | Framework conciso de 7 fases (idea→research→prototype→PRD→kanban→execution→QA). Marco mental rapido para el flujo AI-driven; complementa el walkthrough largo (#4). |

### Posts X/LinkedIn utiles para Code/data

| Fuente | Tema | Por que sirve |
|---|---|---|
| [@_catwu - self-service data analytics post](https://x.com/_catwu/status/2062408623565984209) | Link original/social del blog de analytics. | Buen punto de entrada para el caso interno de Anthropic. |
| [@sh_reya - skill docs/data model changing daily](https://x.com/sh_reya/status/2062347411511746874) | Mantenimiento de skill docs. | Refuerza que skills son assets vivos, no docs muertos. |
| [@Mnilax - Don't build agents, build skills instead](https://x.com/Mnilax/status/2060422436370210922) | Skills vs agents. | Frase potente para data/dev: encapsular procedimiento. |
| [@cyrilXBT - Anthropic skills talk](https://x.com/cyrilXBT/status/2054033707296547043) | Skills y mantenimiento. | Complementa el video AI Engineer. |
| [Brij Kishore Pandey - Claude Code project structure](https://www.linkedin.com/posts/brijpandeyji_the-claude-code-project-structure-i-wish-activity-7441293017766051840-oMkH) | Estructura `.claude/`, skills, commands, agents, hooks. | Util como slide visual de la estructura `.claude/`. |
| Los 4 habitos de un Claude Code confiable | `CLAUDE.md` estable (no dump), Plan Mode, prompts→skills, hooks para lo deterministico. | Base del "abre bocas" del track Code (ver seccion "Configurar un proyecto con Claude Code"). Buen slide de habitos. |

## Skills/plugins existentes que si conviene mostrar

### Para BPO / Cowork

| Recurso | Fuente | Para quien | Que mostrar |
|---|---|---|---|
| **Claude for Small Business** ★ | [anuncio](https://www.anthropic.com/news/claude-for-small-business) · [solutions](https://claude.com/solutions/small-business) | Duenos/equipos de back-office | 15 workflows + 15 skills listos (payroll, cierre mensual, forecast, lead triage, dashboards). Demo "listo para usar" mas convincente para BPO no tecnico. Aprobacion del usuario antes de actuar; respeta permisos existentes. |
| Knowledge Work Plugins | [anthropics/knowledge-work-plugins](https://github.com/anthropics/knowledge-work-plugins) | Legal, finance, ops, marketing, sales | Plugins por rol: no empezar desde prompt vacio. |
| Claude for Legal | [anthropics/claude-for-legal](https://github.com/anthropics/claude-for-legal) | Legal/compliance | Commercial legal, employment legal, privacy/compliance, litigation support. |
| Legal vendor agreement review | [vendor-agreement-review skill](https://github.com/anthropics/claude-for-legal/blob/main/commercial-legal/skills/vendor-agreement-review/SKILL.md) | Procurement/legal | Severidad contra playbook: Critical/High/Medium, no opinion suelta. |
| Employment hiring review | [hiring-review skill](https://github.com/anthropics/claude-for-legal/blob/main/employment-legal/skills/hiring-review/SKILL.md) | HR/legal | Offer letters, jurisdiction checks, restrictive covenants, citas y contexto. |
| Skills directory | [Browse skills, connectors, and plugins](https://support.claude.com/en/articles/14328846-browse-skills-connectors-and-plugins-in-one-directory) | Admins/champions | Como descubrir y provisionar recursos. |
| Organization skills management | [Provision and manage skills](https://support.claude.com/en/articles/13119606-provision-and-manage-skills-for-your-organization) | Owners/admins | Compartir skills deliberadamente; revisar antes de org-wide sharing. |

### Para Code / data

| Recurso | Fuente | Para quien | Que mostrar |
|---|---|---|---|
| Claude Code skills | [Extend Claude with skills](https://code.claude.com/docs/en/skills) | Developers/data engineers | Skills como runbooks versionados. |
| `.claude` directory | [Explore the .claude directory](https://code.claude.com/docs/en/claude-directory) | Developers/champions | Estructura de memoria, settings, skills, subagents. |
| Claude memory | [How Claude remembers your project](https://code.claude.com/docs/en/memory) | Developers/data | `CLAUDE.md` como contexto persistente. |
| Subagents | [Create custom subagents](https://code.claude.com/docs/en/sub-agents) | Devs/data | Code review, data validation, debugging, research. |
| Hooks | [Automate actions with hooks](https://code.claude.com/docs/en/hooks-guide) | Devs/platform | Tests/lint/security deterministico. |
| Official plugins directory | [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official) | Admins/tech leads | Directorio de plugins; confiar pero revisar. |

## Buenas practicas por track

### BPO / Cowork

Estas buenas practicas salen de las guias oficiales anteriores, no de inventar un
framework nuevo:

1. **Empezar con una carpeta dedicada**: no dar acceso amplio al disco. Cowork es
   mas facil de supervisar cuando trabaja en un folder de tarea/proyecto.
2. **Configurar Project instructions**: rol, formato esperado, tono, restricciones,
   fuentes permitidas y que debe preguntar antes de acciones sensibles.
3. **Usar plugins/skills antes de prompts sueltos**: Legal/RRHH/ops funcionan
   mejor con playbooks que con instrucciones improvisadas.
4. **Revisar el plan antes de ejecutar**: Cowork puede hacer cambios; el usuario
   debe mirar si la tarea se esta expandiendo fuera del alcance.
5. **Pedir evidencias/citas**: archivo, seccion, fila, fecha o fuente. Sin cita,
   el output es borrador, no respuesta final.
6. **No usarlo para decisiones finales**: contratacion, despido, sancion, pago,
   aprobacion legal, cambios regulatorios o comunicaciones sensibles requieren
   responsable humano.
7. **Scheduled tasks solo para procesos claros**: resumen semanal, monitoreo de
   carpeta, briefing; no para acciones irreversibles.

### Code / data

1. **`CLAUDE.md` primero**: contexto de repo, comandos, arquitectura, permisos,
   fuentes de verdad y criterios de done.
2. **Skills para dominios repetibles**: no pedir "analiza ventas"; crear skill
   por dominio con tablas canonicas, grain, filtros, owners, gotchas y ejemplos.
3. **Hooks para reglas no negociables**: tests, lint, secrets scan, blocklists,
   proteccion de carpetas criticas.
4. **Subagents para revision independiente**: code review, data validation,
   hallucination check, security review.
5. **Fuentes de verdad antes que SQL creativo**: semantic layer, lineage,
   OpenMetadata, dashboards canonicos, docs de metricas.
6. **Mantenimiento como parte del PR**: si cambia un modelo, metrica o tabla, debe
   cambiar la skill/doc correspondiente.
7. **Evals de analytics**: medir accuracy con preguntas conocidas, no solo demo
   feliz. La guia de Anthropic muestra que sin skills la precision se degrada.

## Seguridad por track (las preguntas que SI van a salir)

> El tema de seguridad es **distinto en cada track** y casi siempre sale en la
> capacitacion. Tener la respuesta lista evita improvisar. Fuentes oficiales:
> [Use Cowork safely](https://support.claude.com/en/articles/13364135-use-claude-cowork-safely)
> (BPO) y [Settings / permissions](https://code.claude.com/docs/en/settings) (Code).

### BPO / Cowork — el riesgo es **acceso y acciones**, no codigo

A esta audiencia no le hables de `.env` ni de permisos en JSON. Su modelo mental
es "un asistente con acceso a mis archivos y herramientas". Las preguntas reales:

1. **"¿Puede ver TODO mi ordenador?"** → No si lo configuras bien. Regla #1
   (oficial): **carpeta dedicada**, no acceso amplio. Lo que no esta en la carpeta,
   no lo ve. Mantener backups de lo importante.
2. **"¿Y si borra o manda algo por error?"** → Cowork **pide permiso explicito**
   antes de borrar definitivamente (prompt "Allow"). Regla: revisar el **plan
   antes** de ejecutar, y vigilar **scope creep** (¿accede a archivos/webs que no
   mencionaste? -> parar). El modo "Act without asking" **sube mucho** el riesgo
   de prompt injection: solo bajo supervision activa.
3. **"¿Manda emails / hace compras solo?"** → No debe. Configurar **preparar
   borrador, nunca enviar/comprar/publicar** sin confirmacion. Esto se fija en las
   instrucciones base (manual del asistente).
4. **"¿Y los datos sensibles de la empresa?"** → No darle acceso a documentos con
   credenciales, datos financieros o PII salvo necesidad clara y anonimizada.
   Evitar Claude-en-Chrome para informacion sensible. Respetar las politicas de la
   empresa (si no se permite, esa es otra conversacion con IT/seguridad).
5. **"¿Las tareas programadas no se descontrolan?"** → Empezar simple (resumenes,
   recopilar info), nunca acciones dificiles de deshacer en automatico. Revisar
   outputs y pausar las que no se usan.
6. **Conectores/plugins**: solo los del directorio verificado de Claude; evaluar
   los permisos que pide cada extension antes de instalar.

**Mensaje de una linea para BPO:** *"Cowork mira, resume y prepara; tu decides y
confirmas. Carpeta acotada + revisar el plan + nada irreversible en automatico."*

### Code / Data — el riesgo es **secretos, permisos y ejecucion**

Aqui SI hay que entrar a `.env`, permisos y hooks. Las preguntas tipicas:

1. **"¿Como evito que filtre secretos / API keys?"** Tres capas, defensa en
   profundidad (no son alternativas):
   - **Disciplina (lo mas importante):** consumir el secreto **dentro del comando**
     (`set -a; source .env; set +a; tool --token "$VAR"`), **nunca** `echo`/`cat`
     del valor a la salida. Esto tapa el vector Bash, que es el real.
   - **`deny` en settings (backstop gratis):** `Read(./.env)`, `Read(./.env.*)`,
     `Read(./secrets/**)`. Bloquea que el agente **lea** el archivo a contexto.
     **Ojo (gotcha clave):** el `deny: Read` **solo** afecta la herramienta `Read`;
     **no** bloquea `cat .env` en Bash. Por eso no sustituye a la disciplina —
     la complementa. Y por eso **no rompe** flujos que hacen `source` en Bash.
   - **Hook PreToolUse (opcional):** inspecciona el comando y bloquea/redacta
     patrones peligrosos (`cat *secret*`, `echo $TOKEN`). Potente pero con costo de
     mantenimiento; justificado en orgs con muchos operadores, overkill para 1 user.
2. **"¿`.env` en el repo?"** Nunca. `.gitignore` cubre `.env`, `*.key`,
   `*credentials*`; verificar `git diff --staged` antes de commitear. Usar
   `.env.example` con placeholders para onboarding.
3. **"¿Como limito que ejecute cosas peligrosas?"** `permissions` allow/deny en
   `settings.json` (ej. `deny: Bash(curl *)`), y **hooks** para reglas no
   negociables (tests/lint/secrets-scan antes de actuar, bloquear comandos).
4. **"¿Los subagentes/MCP ven mis credenciales?"** Dar a cada agente/conector solo
   el scope que necesita; los MCP heredan permisos — revisar que un conector no
   exponga mas de lo necesario.

**Mensaje de una linea para Code/Data:** *"El agente no necesita VER el secreto;
lo usa dentro del comando sin imprimirlo. `deny: Read(.env)` es red de seguridad,
no reemplaza la disciplina de no imprimir."*

### Nota transversal (sirve a los dos)

El principio comun: **minimo privilegio + humano en las decisiones irreversibles**.
Para BPO se expresa como carpeta acotada y confirmacion; para Code como permisos,
`deny` y hooks. Mismo concepto, distinto vocabulario.

## Configurar un proyecto con Claude Code (abre bocas — track Code)

> Buen **abre bocas** para abrir el track tecnico: como deberia lucir un proyecto
> bien configurado. Dos piezas: (a) los 4 habitos que lo hacen confiable, (b) la
> estructura de archivos `.claude/`. Aterriza la idea de "sacar lo correcto del
> prompt y meterlo en el entorno".

### Los 4 habitos (modelo mental)

Material divulgativo para explicar el cambio de mentalidad:

1. **No conviertas `CLAUDE.md` en un volcado de instrucciones.** Solo lo
   **estable**: contexto del proyecto, arquitectura, convenciones, comandos
   importantes. Si algo es un *procedimiento repetible / checklist / playbook*,
   va en otro lado (una **skill**), no en `CLAUDE.md`.
2. **Usa Plan Mode antes de cambios grandes.** Multi-file, refactors o algo
   "desordenado": es mas seguro dejar que Claude inspeccione y planifique antes de
   tocar codigo.
3. **Convierte prompts repetidos en skills.** Si tecleas seguido "review this",
   "debug this" o "prepara esto para deploy", esa es la senal de que el workflow
   debe volverse reutilizable, no reescrito cada vez.
4. **Usa hooks para lo que debe pasar siempre.** Formato, validacion, guardrails,
   notificaciones — cualquier cosa **deterministica** la maneja mejor el sistema
   que "esperar a que el modelo se acuerde".

> **La idea de fondo (one-liner):** *mover las cosas correctas fuera del prompt y
> dentro del entorno.* `CLAUDE.md` para lo estable, skills para lo repetible,
> hooks para lo deterministico, permisos para lo peligroso.

### Estructura de un proyecto (oficial)

```
mi-proyecto/
├── CLAUDE.md               # instrucciones del proyecto; se cargan cada sesion
├── .mcp.json               # conectores MCP del proyecto (GitHub, DB, Slack…); versionado
└── .claude/
    ├── settings.json       # permisos (allow/deny), hooks, modelo — versionado (equipo)
    ├── settings.local.json # overrides personales — gitignored
    ├── skills/             # runbooks reutilizables (/nombre); se cargan on-demand
    │   └── deploy/SKILL.md
    ├── commands/           # slash-commands simples (mismo mecanismo que skills)
    ├── agents/             # subagentes especializados (contexto aislado, p.ej. code-reviewer)
    ├── rules/              # reglas modulares por tema (style, testing, api-design)
    └── hooks/              # scripts disparados por evento (los CONFIGURA settings.json)

~/.claude/                  # GLOBAL — transversal a todos los proyectos (avanzado)
├── CLAUDE.md               # convenciones que aplican a TODA la maquina
└── settings.json           # permisos/deny globales (p.ej. proteger .env en todos lados)
```

Notas de precision (correcciones a infograficos que circulan):
- Es `.mcp.json` (no `.mcp.jason`).
- `CLAUDE.local.md` es **legacy**; hoy los overrides van en `settings.local.json`.
- Los **hooks se configuran en `settings.json`**; la carpeta `hooks/` solo guarda
  los scripts. No es un directorio "magico" por si solo.
- `commands/` y `skills/` son el mismo mecanismo (`/nombre`); para workflows nuevos,
  preferir **skills** (permiten empaquetar archivos de apoyo).

### Como se recomienda dejar la configuracion

1. **Un `CLAUDE.md` por proyecto — siempre.** Es lo primero que lee Claude. Solo
   lo estable (habito #1). Es el equivalente tecnico del "manual del asistente"
   que en BPO se pone en las instrucciones de Cowork.
2. **`CLAUDE.md` global (`~/.claude/CLAUDE.md`) — usuarios avanzados.** Convenciones
   transversales a todos los proyectos de la maquina (estilo de trabajo, reglas que
   no quieres repetir por repo). Se combina con el del proyecto.
3. **`settings.json` con `deny` para proteger secretos.** Ejemplo recomendado
   (generico — bloquea que el agente *lea* archivos de secretos a contexto):

   ```json
   {
     "permissions": {
       "deny": [
         "Read(./.env)",
         "Read(./.env.*)",
         "Read(./**/.env)",
         "Read(./secrets/**)"
       ]
     }
   }
   ```

   **Gotcha clave (verificado en pruebas):** `deny: Read(.env)` bloquea **solo la
   herramienta `Read`** — el agente ya no puede abrir el `.env` a la conversacion.
   **No** bloquea un `cat .env` en Bash. Por eso este `deny` es una **red de
   seguridad** que se suma a la disciplina de *consumir el secreto dentro del
   comando sin imprimirlo* (ver "Seguridad por track / Code"); no la reemplaza. Y
   por lo mismo **no rompe** flujos que cargan secretos via `source` en Bash.
4. **Hooks para reglas no negociables** (habito #4) y **skills para lo repetible**
   (habito #3): el `CLAUDE.md` no debe cargar con eso.

### Plantillas listas para distribuir

El modelo es en **dos capas** (ver el diagrama
[`diagrama-capas-claude-empresa.md`](diagrama-capas-claude-empresa.md)). Hay un
**archivo listo para copiar por cada capa** — sanitizados (sin identidades ni datos
de ningun empleador), solo reemplazar placeholders y borrar lo que no aplique:

- **Capa 1 · global** → [`global-claude-md-empresa.md`](global-claude-md-empresa.md):
  identidad corporativa + principios de trabajo + seguridad. Su cuerpo **es** el
  `CLAUDE.md`; se copia a `~/.claude/CLAUDE.md`. Compartible con cualquier empleado.
- **Capa 2 · por proyecto** → [`proyecto-claude-md-empresa.md`](proyecto-claude-md-empresa.md):
  contexto + quick start + comandos + convenciones + seguridad del repo. Se copia a
  un `CLAUDE.md` en la raiz del proyecto; se combina con el global.
- **Settings** → [`settings-json-empresa.md`](settings-json-empresa.md): `settings.json`
  con `deny` para proteger secretos. Acompaña a las plantillas (global o por proyecto).

Estos son los **archivos** (copiar tal cual); esta guia explica el **por que**.
Buen entregable para compartir con un equipo tras la capacitacion del track Code.

## Propuesta de capacitacion basada en fuentes

### Sesion 1 - BPO/Cowork: "No es chat, es delegacion supervisada"

Prework:

- Video oficial: [Introducing Cowork](https://www.youtube.com/watch?v=UAmKyyZ-b9E)
- Guia oficial: [Delegating your first task](https://claude.com/resources/tutorials/delegating-your-first-task-in-claude-cowork)
- Seguridad: [Use Claude Cowork safely](https://support.claude.com/en/articles/13364135-use-claude-cowork-safely)

Demo:

- Crear proyecto con carpeta dedicada.
- Conectar una fuente controlada.
- Delegar una tarea con output verificable.
- Revisar plan y resultado.

### Sesion 2 - BPO por funcion: Legal/RRHH/Ops

Prework:

- [Claude for Human Resources](https://claude.com/resources/tutorials/claude-for-human-resources)
- [Using Claude Cowork for legal](https://claude.com/resources/tutorials/using-claude-cowork-for-legal-question-briefing)
- [anthropics/claude-for-legal](https://github.com/anthropics/claude-for-legal)

Demo:

- Legal: NDA triage o vendor agreement review.
- RRHH: politica interna con citas o headcount planning en Excel.
- Ops: QA de casos contra checklist.

### Sesion 3 - Code/data: "Self-service analytics sin caos"

Prework:

- [How Anthropic enables self-service data analytics with Claude](https://claude.com/blog/how-anthropic-enables-self-service-data-analytics-with-claude)
- [Mastering Claude Code in 30 minutes](https://www.youtube.com/watch?v=6eBSHbLKuN0)
- [Don't Build Agents, Build Skills Instead](https://www.youtube.com/watch?v=CEvIs9y1uog)

Demo:

- `CLAUDE.md` de un repo.
- Skill de dominio de datos: grain, filtros, tablas, gotchas.
- Query/analysis + subagent de validacion.
- Hook que exige actualizar skill cuando cambia un modelo.

## Próximos pasos (para quien adapte esta capacitación)

- Probar los plugins/skills oficiales en una máquina de demo antes de mostrarlos.
- Definir datasets sintéticos de práctica para los tracks BPO y data.
- Validar métricas actuales de los posts citados antes de usarlos en slides
  (los conteos cambian con el tiempo).
- Convertir esta curaduría a deck o página de notas cuando se apruebe el enfoque.
