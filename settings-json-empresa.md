<!-- ARCHIVO LISTO PARA USAR (acompaña a las plantillas CLAUDE.md).
     Copia el bloque JSON de abajo a un archivo settings.json:
       • ~/.claude/settings.json        → red de seguridad para TODA la máquina
       • <repo>/.claude/settings.json   → versionado, compartido por el equipo del repo
     Ajusta/añade reglas según tu proyecto. -->

# `settings.json` — sample (proteger secretos)

```json
{
  "permissions": {
    "allow": [
      "Bash",
      "Edit",
      "Write",
      "WebFetch",
      "WebSearch"
    ],
    "deny": [
      "Read(./.env)",
      "Read(./.env.local)",
      "Read(./.env.production)",
      "Read(./.env.staging)",
      "Read(./.env.development)",
      "Read(./.env.test)",
      "Read(./**/.env)",
      "Read(./**/.env.local)",
      "Read(./**/.env.production)",
      "Read(./**/.env.staging)",
      "Read(./**/.env.development)",
      "Read(./**/.env.test)",
      "Read(./secrets/**)"
    ]
  }
}
```

## Qué hace y qué no (verificado en pruebas)

- Bloquea que el agente **lea** esos archivos con la herramienta `Read` — no entran
  a la conversación.
- **No** bloquea un `cat .env` en Bash. Por eso es una **red de seguridad** que se
  suma a la disciplina de *consumir el secreto dentro del comando sin imprimirlo*,
  no un reemplazo.
- Por lo mismo, **no rompe** flujos que cargan variables con `source .env` en Bash.

## Dónde ponerlo

- **Global** (`~/.claude/settings.json`): protege `.env`/secretos en **todos** los
  proyectos de la máquina a la vez. Acompaña al `CLAUDE.md` global.
- **Por proyecto** (`<repo>/.claude/settings.json`): versionado y compartido por el
  equipo; aquí también van permisos (`allow`/`deny`), hooks y selección de modelo.

## Cuándo aplicarlo (criterio)

El `deny` es más valioso cuanto **menos confiable o más compartida** es la máquina:

- **Servidores, equipos corporativos o compartidos** → ponlo. Es donde un descuido
  expone secretos de la empresa.
- **Dispositivo personal de confianza** → opcional; puedes omitirlo si solo tú lo usas.

## Opcional: bóveda de secretos fuera del repo

Si guardas secretos en una carpeta fuera del proyecto (p. ej. `~/.secrets/`), añade
su **ruta absoluta** al `deny` para que tampoco se lean a contexto:

```json
"Read(/ruta/absoluta/a/.secrets/**)"
```
