<!-- ARCHIVO LISTO PARA USAR (Capa 2 · por proyecto).
     Copia TODO el contenido de abajo a un archivo  CLAUDE.md  en la raíz del repo.
     Reemplaza los [placeholders] y borra lo que no aplique.
     Se combina con el CLAUDE.md global (~/.claude/CLAUDE.md), que aporta identidad,
     principios de trabajo y seguridad. Aquí va SOLO lo específico del proyecto.
     La guía de cómo usar esta plantilla está en capacitacion-claude.md. -->

# [Nombre del proyecto]

## Contexto del proyecto

[Qué es en 1-3 frases y qué stack usa.] Para arquitectura y diagramas, ver README.md.

## Quick Start

```bash
[comando de setup]
cp .env.example .env   # completar credenciales (NUNCA commitear el .env real)
[comando para levantar el servicio]
```

## Comandos comunes

```bash
[build]        # compilar / construir
[test]         # correr tests
[lint]         # linter
[deploy]       # desplegar (si aplica)
```

## Convenciones de código

- Lenguaje y estilo: [ej. type hints; snake_case en Python, camelCase en JS/TS]
- Estructura: [ej. un modelo por archivo en models/]
- Remotes / despliegue: [ej. GitHub para X, GitLab corporativo para Y] (si aplica)
- [Otras convenciones del equipo]

## Seguridad del proyecto

- Secretos solo en `.env` (debe estar en `.gitignore`); mantener `.env.example` con placeholders.
- [Datos sensibles propios de este repo y cómo tratarlos, si aplica.]
- El resto de principios de trabajo y reglas de seguridad vienen del `CLAUDE.md` global.

## Recursos

- README.md — arquitectura y setup
- CHANGELOG.md — historial de cambios (referencia issues)
- [docs, dashboards, APIs relevantes]
