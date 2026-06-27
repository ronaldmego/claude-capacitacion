# Curaduria de guias Claude — resumen central (Code + BPO)

> Mapa de fuentes existentes para preparar capacitaciones y charlas sobre Claude.
> No reemplaza las guias oficiales: las ordena, resume y aterriza **por audiencia**.
> Este documento es el **indice/router**; el contenido detallado vive en dos guias
> separadas para que cada audiencia lea solo lo suyo.
>
> **Naturaleza y uso:** material **genérico y reutilizable** para estudiar, dar
> charlas y capacitar equipos en Claude. Pensado para reutilizarse tal cual: copiar
> las plantillas, adaptar la propuesta de sesiones y tomar la curaduría de fuentes.
> Si necesitas casos específicos de tu organización (datasets internos, flujos
> propietarios), mantenlos en tu propio repo — aquí solo vive lo genérico.
>
> Estado: v3.1, 2026-06-27 (**reorg a carpetas**: el contenido se ordenó en
> `code-data/` (track Code, principal), `bpo/` (track BPO, secundario) y `comun/`
> (núcleo compartido: plantillas + diagrama). El `README.md` trae el **índice de
> contenidos** navegable; este archivo es el router curado. Énfasis en el track Code.
> v3.0 (2026-06-25) ya había dividido la guía única en dos tracks. Historial en
> `CHANGELOG.md`).

## Las dos guias (empieza aqui)

Hay **dos tracks** y cada uno tiene su propia guia autocontenida. Abre solo la que
te interesa — no necesitas leer la otra.

| Track | Guia | Para quien | Superficie |
|---|---|---|---|
| **Code / data** ★ principal | **[`guia-code.md`](code-data/guia-code.md)** | Data engineering, analytics engineering, BI/data analysts, developers | Claude Code + skills + `CLAUDE.md` + hooks + subagents + MCP |
| BPO / negocio · secundario | [`guia-bpo.md`](bpo/guia-bpo.md) | Legal, RRHH, operaciones, back office, finanzas operativas, managers | Claude Cowork + Chat + skills/plugins/conectores |

**Por que el enfasis en Code.** Este repo es publico en GitHub y lo visitan sobre
todo coders y perfiles de data; ahi va el peso. El track BPO queda como secundario,
disponible para quien ademas quiera la parte no tecnica — pero un lector de Code
entra a `guia-code.md` y no tiene que cruzar contenido de Cowork que no le sirve.

## Materiales de esta carpeta

Ademas de las dos guias, la carpeta trae entregables visuales y listos para repartir.
**Todos pertenecen al track Code** (modelo en capas de `CLAUDE.md` + `settings.json`);
el **cómo y el por qué de usarlos** se explica en
[`guia-code.md` → Configurar un proyecto con Claude Code](code-data/guia-code.md#configurar-un-proyecto-con-claude-code-abre-bocas)
y en su sección [Plantillas listas para distribuir](code-data/guia-code.md#plantillas-listas-para-distribuir).
Aquí van solo como índice:

- 📊 **Diagrama de capas** — [`diagrama-capas-claude-empresa.md`](comun/diagrama-capas-claude-empresa.md):
  infográfico ASCII del modelo en capas. Ideal como handout/slide.
- 📄 **Plantilla global lista** — [`global-claude-md-empresa.md`](comun/global-claude-md-empresa.md):
  `CLAUDE.md` para `~/.claude/` (capa 1, compartible con cualquier empleado).
- 📄 **Plantilla por proyecto lista** — [`proyecto-claude-md-empresa.md`](comun/proyecto-claude-md-empresa.md):
  `CLAUDE.md` para la raíz de un repo (capa 2).
- ⚙️ **Settings sample** — [`settings-json-empresa.md`](comun/settings-json-empresa.md):
  `settings.json` con `deny` para proteger secretos (acompaña a las plantillas).

> El track **BPO/Cowork** no usa archivos `CLAUDE.md`/`settings.json`: su equivalente
> son las *Project instructions* dentro de Cowork (ver [`guia-bpo.md`](bpo/guia-bpo.md)).

La capacitacion debe apoyarse en fuentes existentes, en este orden de confianza:

- **Oficial Anthropic/Claude**: fuente normativa.
- **Repos oficiales Anthropic**: ejemplos reutilizables de skills/plugins.
- **YouTube**: material complementario; priorizado por views/likes y relevancia.
- **X/LinkedIn**: ejemplos virales o visuales para explicar conceptos.

## Fuentes de skills/plugins (discovery)

Fuentes **compartidas por ambos tracks** para descubrir skills/plugins. Usarlas como
referencia o discovery, **no** como instalacion automatica.

| Repo / fuente | Senal | Uso potencial |
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
| [skills.sh](https://www.skills.sh/) | Registry/buscador de skills (no un repo) | Directorio web para descubrir skills por caso de uso; buen punto de entrada en una capacitacion. Tratar como discovery: revisar `SKILL.md` y scripts antes de instalar. |
| [jdepoix/youtube-transcript-api](https://github.com/jdepoix/youtube-transcript-api) | Utilidad popular; ~7.6K stars | Alternativa tecnica para transcripts de YouTube si se necesita auditar videos publicos. |

Regla practica: para capacitacion, usar repos oficiales como demo; usar
awesome-lists/registries solo para descubrir ideas. **Antes de instalar o ejecutar
una skill, leer `SKILL.md` y cualquier script incluido** (una skill = instrucciones
+ scripts que el agente ejecuta; es superficie de code-execution / prompt-injection).

## Lectura minima cross-track (si solo hay tiempo para 8 piezas)

| Prioridad | Fuente | Track | Por que importa |
|---|---|---|---|
| 1 | [How Anthropic enables self-service data analytics with Claude](https://claude.com/blog/how-anthropic-enables-self-service-data-analytics-with-claude) | Code/data | Caso interno de Anthropic: self-service analytics, skills, fuentes de verdad, validacion y mantenimiento. Es el blueprint para equipos de datos. |
| 2 | [Best practices for Claude Code](https://code.claude.com/docs/en/best-practices) | Code | Guia oficial para equipos tecnicos: contexto, iteracion, verificacion, hooks. |
| 3 | [Extend Claude Code](https://code.claude.com/docs/en/features-overview) | Code | Mapa oficial de cuando usar `CLAUDE.md`, skills, subagents, hooks, MCP y plugins. |
| 4 | [Don't Build Agents, Build Skills Instead](https://www.youtube.com/watch?v=CEvIs9y1uog) | Code | Charla clave: skills > agents genericos. Marco mental de arquitectura de skills. |
| 5 | [Get started with Claude Cowork](https://support.claude.com/en/articles/13345190-get-started-with-claude-cowork) | BPO | Manual oficial: como empezar, permisos, proyectos y modos de operacion. |
| 6 | [Use Claude Cowork safely](https://support.claude.com/en/articles/13364135-use-claude-cowork-safely) | BPO/admin | Base para guardrails: file access, scope creep, scheduled tasks, datos sensibles. |
| 7 | [Set up Claude Cowork to work the way you do](https://claude.com/resources/tutorials/cowork-onboarding-guide) | BPO | Explica Cowork Project, folder, tools, browser, instrucciones y plugins. |
| 8 | [Claude for Human Resources](https://claude.com/resources/tutorials/claude-for-human-resources) | BPO/RRHH | Ejemplos oficiales por funcion; modelo replicable para otras areas. |

## Seguridad — nota transversal

> 🔒 **Sección dedicada: [`comun/seguridad.md`](comun/seguridad.md)** — el principio
> común + las **prácticas técnicas probadas** (deny en `settings.json`, hooks como
> guardrails, el recipe del guard anti-fuga-de-secretos). La seguridad es de los temas
> más recurrentes en capacitaciones, así que tiene su propio bloque.

El detalle (preguntas tipicas + respuestas) vive además en cada guia:
[Code → secretos, permisos, ejecucion](code-data/guia-code.md#seguridad--el-riesgo-es-secretos-permisos-y-ejecucion) ·
[BPO → acceso y acciones](bpo/guia-bpo.md#seguridad--el-riesgo-es-acceso-y-acciones-no-codigo).

El principio comun: **minimo privilegio + humano en las decisiones irreversibles**.
Para BPO se expresa como carpeta acotada y confirmacion; para Code como permisos,
`deny` y hooks. Mismo concepto, distinto vocabulario.

## Programa de capacitacion (resumen)

Propuesta de 3 sesiones; el detalle (prework + demo) vive en cada guia.

| Sesion | Track | Tema | Detalle |
|---|---|---|---|
| 1 | BPO | "No es chat, es delegacion supervisada" | [`guia-bpo.md`](bpo/guia-bpo.md#sesion-1--no-es-chat-es-delegacion-supervisada) |
| 2 | BPO | BPO por funcion: Legal/RRHH/Ops | [`guia-bpo.md`](bpo/guia-bpo.md#sesion-2--bpo-por-funcion-legalrrhhops) |
| 3 | Code | "Self-service analytics sin caos" | [`guia-code.md`](code-data/guia-code.md#sesion-de-capacitacion--codedata) |

## Proximos pasos (para quien adapte esta capacitacion)

- Probar los plugins/skills oficiales en una máquina de demo antes de mostrarlos.
- Definir datasets sintéticos de práctica para los tracks BPO y data.
- Validar métricas actuales de los posts citados antes de usarlos en slides
  (los conteos cambian con el tiempo).
- Convertir esta curaduría a deck o página de notas cuando se apruebe el enfoque.
