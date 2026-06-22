# claude-capacitacion

> Material **genérico y sanitizado** para capacitar equipos en Claude
> (Enterprise / Cowork / Code) y para charlas de marca personal. Sin identidades,
> hosts, rutas de secretos ni datos de ningún empleador. Reutilizable para varios
> fines: estudio, charlas, posts, onboarding de equipos (incluido MIC/Tigo).

## Contenido

| Archivo | Qué es |
|---|---|
| **`capacitacion-claude.md`** | La **guía** (el *por qué* + cómo armar la capacitación: curaduría de fuentes oficiales, propuesta de sesiones). **Punto de entrada.** |
| `diagrama-capas-claude-empresa.md` | Diagrama ASCII del modelo en capas (estilo infográfico). |
| `global-claude-md-empresa.md` | Plantilla **lista**: `CLAUDE.md` global (capa 1, va en `~/.claude/`). |
| `proyecto-claude-md-empresa.md` | Plantilla **lista**: `CLAUDE.md` por proyecto (capa 2, raíz del repo). |
| `settings-json-empresa.md` | Sample **listo**: `settings.json` (deny de secretos). |

## Cómo usarlo

Lee **`capacitacion-claude.md`** (la guía) → desde su índice "Materiales de esta
carpeta" llegas al diagrama y a las plantillas listas para copiar.

## Origen

Antes vivía en `ronaldmego/monetizacion` (`servicios/capacitacion-claude/`). Se movió
a repo propio para poder **clonarlo donde se necesite** (incluida la Mac corporativa)
sin arrastrar el repo personal. Los repos que lo usan (`monetizacion`, `mic-lab`)
apuntan aquí.
