# Diagrama — Claude en la empresa: cómo se construye un setup gobernado

> **Track Code / data.** Material visual para capacitación (estilo infográfico).
> Explica el modelo en **capas** de `CLAUDE.md` + `settings.json`, de lo más general
> (todos los empleados) a lo más específico (un repo). Genérico y sanitizado: sin
> identidades, hosts ni rutas propias. Acompaña a `proyecto-claude-md-empresa.md`
> (capa por proyecto) y se explica en [`guia-code.md`](guia-code.md).

```
╔══════════════════════════════════════════════════════════════════════════╗
║                      C L A U D E   E N   L A   E M P R E S A               ║
║                   Cómo se construye un setup gobernado                      ║
╚══════════════════════════════════════════════════════════════════════════╝

  Idea central: UNA identidad corporativa + reglas, en CAPAS.
  De lo más general (todos) a lo más específico (un repo).


┌───────────────────────────────────────────────────────────────────────────┐
│ CAPA 1 ·  GLOBAL  ·  compartible con CUALQUIER empleado                      │
└───────────────────────────────────────────────────────────────────────────┘

  ~/.claude/                          ◀── vive en la máquina, NO en un repo
  │
  ├── 📄 CLAUDE.md  ───────────────▶  IDENTIDAD CORPORATIVA (genérica)
  │                                   • Quién es el asistente y cómo trabaja
  │                                   • Seguridad: secretos solo en .env;
  │                                     datos sensibles/PII nunca al agente
  │                                   • Boris genérico: planifica, prueba,
  │                                     humano aprueba lo irreversible
  │                                   • CERO repos, CERO rutas personales
  │
  └── ⚙️ settings.json  ───────────▶  RED DE SEGURIDAD (toda la máquina)
                                      • deny de lectura de .env / secrets/**
                                      • permisos base

        ┌──────────────────────────────────────────────────────────────┐
        │  Mismo CONTENIDO, dos SUPERFICIES de entrega:                  │
        │   • Usa código (Claude Code)  → este ~/.claude/CLAUDE.md       │
        │   • Cowork / Desktop / web    → política Enterprise + onboarding│
        └──────────────────────────────────────────────────────────────┘


┌───────────────────────────────────────────────────────────────────────────┐
│ CAPA 2 ·  POR PROYECTO  ·  estándar recomendado (proyectos de código)       │
└───────────────────────────────────────────────────────────────────────────┘

  <mi-proyecto>/                      ◀── vive en el repo, se combina con la Capa 1
  │
  ├── 📄 CLAUDE.md  ───────────────▶  MANUAL DEL PROYECTO
  │                                   • Contexto + stack en 1-3 frases
  │                                   • Quick Start y comandos comunes
  │                                   • Convenciones, remotes (GitHub/GitLab)
  │                                   • Aquí SÍ van detalles del repo
  │
  ├── 📄 .env.example  ────────────▶  Plantilla de credenciales (.env va en .gitignore)
  ├── 🔌 .mcp.json  ───────────────▶  Integraciones MCP (GitHub, GitLab, Jira, DBs)
  │
  └── 📁 .claude/
      ├── ⚙️ settings.json  ───────▶  Permisos, hooks, modelo (versionado/equipo)
      ├── ⚙️ settings.local.json ──▶  Overrides locales (vigente, no se commitea)
      ├── 📁 skills/  ─────────────▶  Runbooks de tareas repetibles (3+ veces)
      ├── 📁 commands/  ───────────▶  Slash commands (/review, /fix-issue)
      ├── 📁 agents/  ─────────────▶  Sub-agentes con rol (code-reviewer, security)
      └── 📁 hooks/  ──────────────▶  Scripts por evento: validan, bloquean lo inseguro


┌───────────────────────────────────────────────────────────────────────────┐
│ CAPA 3 ·  (FUTURO)  ·  governance de skills compartidas                     │
└───────────────────────────────────────────────────────────────────────────┘

  📦 repo-de-skills-de-la-empresa     ◀── pointer global, aún NO activo
  │                                       (pre-cocinado para formalizar después)
  └── skills/ versionadas y revisadas ─▶  Empleados que codean parten del mismo
                                          estándar, no reinventan cada skill


   REGLA DE ORO
   ──────────────────────────────────────────────────────────────────────────
   Lo ESTABLE (identidad, seguridad, arquitectura) → CLAUDE.md
   Lo REPETIBLE (procedimientos)                   → skills/
   Lo DETERMINÍSTICO (validar, bloquear)           → hooks/ vía settings.json
   Lo SECRETO                                      → .env  (NUNCA en git ni en chat)
```

## Cómo leerlo en la capacitación

- **Capa 1 (global)** = la identidad corporativa que TODO empleado recibe. Para
  quien usa código se entrega como `~/.claude/CLAUDE.md`; para quien usa
  Cowork/Desktop, el mismo contenido se entrega como política Enterprise +
  onboarding (no como archivo).
- **Capa 2 (por proyecto)** = el estándar recomendado para repos de código; aquí
  sí entran detalles del proyecto (comandos, remotes GitHub/GitLab, convenciones).
  Es lo que cubre `proyecto-claude-md-empresa.md`.
- **Capa 3 (futuro)** = governance de skills compartidas; se deja sembrado para
  formalizarlo después.

## Nota sobre el sufijo `.local`

Es la "capa personal que no se comparte con el equipo" (va en `.gitignore`):
p. ej. `settings.local.json` para permisos/hooks que solo aplican en tu máquina,
sin afectar al resto del equipo.
