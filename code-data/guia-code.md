# Guia Claude Code — tecnico / data / developers

> **Track principal** de este kit. Para data engineering, analytics engineering,
> BI/data analysts y developers. Superficie principal: **Claude Code** + skills +
> `CLAUDE.md` + hooks + subagents + MCP.
>
> Esta guia es autocontenida: si solo te interesa la parte tecnica, lees esto y no
> necesitas el track BPO. Para el resumen/indice y el track no tecnico, ver
> [`claude-guide.md`](../claude-guide.md) (central) y [`guia-bpo.md`](../bpo/guia-bpo.md).

## Lectura minima (si solo hay tiempo para 4 piezas)

| Prioridad | Fuente | Por que importa |
|---|---|---|
| 1 | [How Anthropic enables self-service data analytics with Claude](https://claude.com/blog/how-anthropic-enables-self-service-data-analytics-with-claude) | Caso interno de Anthropic: self-service analytics, skills, fuentes de verdad, validacion y mantenimiento. Es el blueprint para equipos de datos. |
| 2 | [Best practices for Claude Code](https://code.claude.com/docs/en/best-practices) | Guia oficial para equipos tecnicos: contexto, iteracion, verificacion, hooks. |
| 3 | [Extend Claude Code](https://code.claude.com/docs/en/features-overview) | Mapa oficial de cuando usar `CLAUDE.md`, skills, subagents, hooks, MCP y plugins. |
| 4 | [Don't Build Agents, Build Skills Instead](https://www.youtube.com/watch?v=CEvIs9y1uog) | Charla clave: skills > agents genericos. Marco mental de arquitectura de skills. |

## Guia oficial principal

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

## Resumen de la guia Anthropic de self-service analytics

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
- Para self-service: no soltar a usuarios sobre raw tables; darles dominios
  curados, ejemplos y rutas de escalamiento.
- Para governance: OpenMetadata/lineage/glosarios pueden ser la capa de contexto,
  pero solo si estan mantenidos y la skill sabe consultarlos.

## Configurar un proyecto con Claude Code (abre bocas)

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
   comando sin imprimirlo* (ver "Seguridad" mas abajo); no la reemplaza. Y
   por lo mismo **no rompe** flujos que cargan secretos via `source` en Bash.
4. **Hooks para reglas no negociables** (habito #4) y **skills para lo repetible**
   (habito #3): el `CLAUDE.md` no debe cargar con eso.

### Plantillas listas para distribuir

El modelo es en **dos capas** (ver el diagrama
[`diagrama-capas-claude-empresa.md`](../comun/diagrama-capas-claude-empresa.md)). Hay un
**archivo listo para copiar por cada capa** — sanitizados (sin identidades ni datos
de ningun empleador), solo reemplazar placeholders y borrar lo que no aplique:

- **Capa 1 · global** → [`global-claude-md-empresa.md`](../comun/global-claude-md-empresa.md):
  identidad corporativa + principios de trabajo + seguridad. Su cuerpo **es** el
  `CLAUDE.md`; se copia a `~/.claude/CLAUDE.md`. Compartible con cualquier empleado.
- **Capa 2 · por proyecto** → [`proyecto-claude-md-empresa.md`](../comun/proyecto-claude-md-empresa.md):
  contexto + quick start + comandos + convenciones + seguridad del repo. Se copia a
  un `CLAUDE.md` en la raiz del proyecto; se combina con el global.
- **Settings** → [`settings-json-empresa.md`](../comun/settings-json-empresa.md): `settings.json`
  con `deny` para proteger secretos. Acompaña a las plantillas (global o por proyecto).

Estos son los **archivos** (copiar tal cual); esta guia explica el **por que**.
Buen entregable para compartir con un equipo tras la capacitacion del track Code.

## Buenas practicas Code / data

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

## Seguridad — el riesgo es **secretos, permisos y ejecucion**

> Fuente oficial: [Settings / permissions](https://code.claude.com/docs/en/settings).
>
> 🔒 **Prácticas probadas (recipe completo):** [`comun/seguridad.md`](../comun/seguridad.md)
> — deny en `settings.json`, hooks como guardrails, y el guard anti-fuga-de-secretos
> (`${VAR:+PRESENTE}`, nunca `${VAR:-}`).

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

> **Principio comun con BPO:** minimo privilegio + humano en las decisiones
> irreversibles. En Code se expresa como permisos, `deny` y hooks; en BPO como
> carpeta acotada y confirmacion. Mismo concepto, distinto vocabulario.

## Videos YouTube recomendados para Code/skills

Datos consultados con YouTube Data API el 2026-06-19. Los conteos cambian.

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

## Posts X/LinkedIn utiles para Code/data

| Fuente | Tema | Por que sirve |
|---|---|---|
| [@_catwu - self-service data analytics post](https://x.com/_catwu/status/2062408623565984209) | Link original/social del blog de analytics. | Buen punto de entrada para el caso interno de Anthropic. |
| [@sh_reya - skill docs/data model changing daily](https://x.com/sh_reya/status/2062347411511746874) | Mantenimiento de skill docs. | Refuerza que skills son assets vivos, no docs muertos. |
| [@Mnilax - Don't build agents, build skills instead](https://x.com/Mnilax/status/2060422436370210922) | Skills vs agents. | Frase potente para data/dev: encapsular procedimiento. |
| [@cyrilXBT - Anthropic skills talk](https://x.com/cyrilXBT/status/2054033707296547043) | Skills y mantenimiento. | Complementa el video AI Engineer. |
| [Brij Kishore Pandey - Claude Code project structure](https://www.linkedin.com/posts/brijpandeyji_the-claude-code-project-structure-i-wish-activity-7441293017766051840-oMkH) | Estructura `.claude/`, skills, commands, agents, hooks. | Util como slide visual de la estructura `.claude/`. |
| Los 4 habitos de un Claude Code confiable | `CLAUDE.md` estable (no dump), Plan Mode, prompts→skills, hooks para lo deterministico. | Base del "abre bocas" del track Code (ver seccion "Configurar un proyecto con Claude Code"). Buen slide de habitos. |

## Skills/plugins que conviene mostrar (Code / data)

| Recurso | Fuente | Para quien | Que mostrar |
|---|---|---|---|
| Claude Code skills | [Extend Claude with skills](https://code.claude.com/docs/en/skills) | Developers/data engineers | Skills como runbooks versionados. |
| `.claude` directory | [Explore the .claude directory](https://code.claude.com/docs/en/claude-directory) | Developers/champions | Estructura de memoria, settings, skills, subagents. |
| Claude memory | [How Claude remembers your project](https://code.claude.com/docs/en/memory) | Developers/data | `CLAUDE.md` como contexto persistente. |
| Subagents | [Create custom subagents](https://code.claude.com/docs/en/sub-agents) | Devs/data | Code review, data validation, debugging, research. |
| Hooks | [Automate actions with hooks](https://code.claude.com/docs/en/hooks-guide) | Devs/platform | Tests/lint/security deterministico. |
| Official plugins directory | [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official) | Admins/tech leads | Directorio de plugins; confiar pero revisar. |

Las **fuentes de discovery de skills/plugins** (repos publicos de alta senal,
registries como `skills.sh`) son compartidas entre tracks y viven en el central:
ver [`claude-guide.md` → Fuentes de skills/plugins](../claude-guide.md#fuentes-de-skillsplugins-discovery).

## Sesion de capacitacion — Code/data

### "Self-service analytics sin caos"

Prework:

- [How Anthropic enables self-service data analytics with Claude](https://claude.com/blog/how-anthropic-enables-self-service-data-analytics-with-claude)
- [Mastering Claude Code in 30 minutes](https://www.youtube.com/watch?v=6eBSHbLKuN0)
- [Don't Build Agents, Build Skills Instead](https://www.youtube.com/watch?v=CEvIs9y1uog)

Demo:

- `CLAUDE.md` de un repo.
- Skill de dominio de datos: grain, filtros, tablas, gotchas.
- Query/analysis + subagent de validacion.
- Hook que exige actualizar skill cuando cambia un modelo.
