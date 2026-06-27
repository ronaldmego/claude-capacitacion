# Seguridad — prácticas probadas

> El tema de seguridad es de los más recurrentes en cualquier capacitación o charla
> sobre Claude. Esta es la **sección dedicada**: primero el principio común a todos, y
> luego las prácticas técnicas **ya probadas en producción** para el track Code/data.
> Todo genérico y público-safe (sin secretos ni rutas propietarias).

## El principio (ambos tracks)

**Mínimo privilegio + humano en las decisiones irreversibles.** No importa el track:

- Dale a Claude el **acceso mínimo** que la tarea necesita, no "todo por si acaso".
- Las acciones que **no se pueden deshacer** (borrar, enviar, pagar, publicar) pasan por
  **confirmación humana**.
- Los **secretos** (tokens, API keys, contraseñas) viven **solo** en un `.env`
  gitignored. Nunca en código, commits, issues, logs, ni en la respuesta del asistente.

Mismo concepto, distinto vocabulario por audiencia:

| | BPO / Cowork | Code / data |
|---|---|---|
| Riesgo principal | **Acceso y acciones** (qué ve, qué ejecuta/envía) | **Secretos, permisos y ejecución** |
| Cómo se expresa | Carpeta acotada + confirmación | Permisos, reglas `deny`, hooks |
| Detalle | [guia-bpo → Seguridad](../bpo/guia-bpo.md#seguridad--el-riesgo-es-acceso-y-acciones-no-codigo) | [guia-code → Seguridad](../code-data/guia-code.md#seguridad--el-riesgo-es-secretos-permisos-y-ejecucion) |

## BPO / Cowork — acceso y acciones (resumen)

- **Carpeta acotada**: el proyecto/folder al que Claude accede, no toda la máquina.
- **Confirmar lo irreversible**: enviar correos, borrar, publicar → revisión humana.
- **Datos sensibles**: no subir a un proyecto lo que no debe salir de su ámbito.

Detalle y preguntas típicas: [guia-bpo → Seguridad](../bpo/guia-bpo.md#seguridad--el-riesgo-es-acceso-y-acciones-no-codigo).

## Code / data — guardrails técnicos (probados)

> Prácticas que corren en producción en setups reales. Genéricas y reutilizables.

### 1. `settings.json` con `deny` para secretos

Bloquea que el agente lea `.env` / archivos de secretos. Ver
[`settings-json-empresa.md`](settings-json-empresa.md).

### 2. Hooks como guardrails **deterministas**

Un **hook** es código que el harness ejecuta — no el modelo — así que es **determinista**
(no depende de que el agente "recuerde" portarse bien). Dos eventos útiles:

- **`PreToolUse`** — inspecciona un comando/acción **antes** de correr; puede **avisar**
  (inyectar contexto) o **bloquear**.
- **`SessionStart`** — corre chequeos al iniciar sesión (p. ej. drift de la config
  global, o paridad del setup entre máquinas).

> Regla mental: *el determinismo vive en los hooks; los procedimientos repetibles, en
> skills.*

### 3. Recipe probado — guard anti-fuga-de-secretos (`PreToolUse`, modo aviso)

**Footgun real:** chequear si un secreto existe con `${VAR:-AUSENTE}` **imprime el
valor** (la forma `:-` expande al valor cuando la variable está seteada). Este hook
**avisa** (no bloquea) cuando un comando expande una variable con **nombre de secreto**
(`*_API_KEY`, `*TOKEN*`, `*SECRET*`, `*PASSWORD*`, `*CREDENTIAL*`) usando `:-` o `:=`.

`scripts/guard-secret-print.py`:

```python
#!/usr/bin/env python3
# PreToolUse hook (Bash) — RED DE SEGURIDAD, NO BLOQUEA.
# Avisa si un comando expandiría una variable con nombre de secreto con ':-'/':=',
# que imprime el VALOR. Para chequear presencia usar solo ${VAR:+PRESENTE}.
import sys, json, re
try:
    data = json.load(sys.stdin)
except Exception:
    sys.exit(0)
cmd = (data.get("tool_input") or {}).get("command", "") or ""
PAT = re.compile(
    r"\$\{\s*[A-Za-z0-9_]*(KEY|TOKEN|SECRET|PASSWORD|CREDENTIAL|PRIVATE)[A-Za-z0-9_]*\s*:[-=]",
    re.IGNORECASE,
)
if cmd and PAT.search(cmd):
    warn = ("⚠️ Posible fuga de secreto: el comando expande una variable con nombre de "
            "secreto usando ':-' o ':=', que IMPRIME el valor. Para verificar presencia "
            "usa SOLO ${VAR:+PRESENTE}. Revisa antes de continuar.")
    print(json.dumps({"hookSpecificOutput": {"hookEventName": "PreToolUse", "additionalContext": warn}}))
sys.exit(0)
```

Cablearlo en `settings.json`:

```json
"hooks": {
  "PreToolUse": [
    {
      "matcher": "Bash",
      "hooks": [
        { "type": "command", "command": "python3 \"$CLAUDE_PROJECT_DIR/scripts/guard-secret-print.py\" 2>/dev/null" }
      ]
    }
  ]
}
```

**Regla de oro:** para verificar presencia de un secreto, usa **solo** `${VAR:+PRESENTE}`
— **nunca** `${VAR:-...}` (imprime el valor). Doble rama segura:
`[ -n "$VAR" ] && echo PRESENTE || echo AUSENTE`.

**Notas honestas:**
- Es una red de **señal alta, no un escáner universal** — detectar una fuga de secreto en
  salida arbitraria es indecidible. Cubre este patrón concreto, con casi cero falsos
  positivos.
- **No marca** el patrón legítimo `echo "$TOKEN" | sudo -S …` ni `${VAR:+PRESENTE}`.
- **Modo aviso** (`additionalContext`): inyecta la advertencia, no impide correr el
  comando — menos fricción. Si prefieres frenar, un hook PreToolUse puede **bloquear**
  con `exit 2`.

### 4. (Opcional) Self-checks al iniciar (`SessionStart`)

Mismo mecanismo, para flotas de máquinas: un hook que **avisa** si la config global
driftó (un symlink roto, ediciones sin commitear) o si una máquina quedó **desnivelada**
en plugins/skills vs un baseline declarado. Determinístico, no-mutante.

## Resumen

- **Secretos solo en `.env`**, nunca impresos. Presencia con `${VAR:+PRESENTE}`.
- **`deny` en `settings.json`** para que el agente no lea secretos.
- **Hooks = guardrails deterministas** (avisar/bloquear) que no dependen de recordar.
- **Mínimo privilegio + humano en lo irreversible** — en los dos tracks.
