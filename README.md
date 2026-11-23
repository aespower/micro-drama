# micro-drama

Plugin de Claude Code para crear micro dramas verticales (9:16) con IA en Google Flow.

Combina el flujo de seis pasos de la plantilla *AI Micro Drama Prompt Template* con cinco reglas narrativas (Story Rules) que se usan para diseñar y auditar cada episodio.

## Qué hace

| Modo | Petición de ejemplo | Resultado |
|---|---|---|
| Completo | "Crea el episodio 1 de un micro drama sobre…" | Guion → auditoría → (pausa para aprobar) → Flow Agent Brief → plan de edición |
| Auditoría | "Revisa episode-01-script.md" | Tabla de auditoría, veredicto PASA/FALLA por regla y corrección solo de lo que falla |
| Producción | "Haz el brief de Flow del episodio 1" | Un bloque por escena para pegar en el modo Agent de Flow (ingredientes, keyframe y todos los shots) + presupuesto |

Entregables: `episode-NN-script.md`, `episode-NN-flow-agent.md` (principal) y `episode-NN-edit.md`. Si pides prompts manuales, también `episode-NN-prompts.md`.

### Usar el Flow Agent Brief
1. En Google Flow, activa **Agent** en la caja de prompt.
2. Pega el bloque de la escena 1 entero y espera a que genere ingredientes, keyframe y clips.
3. Revisa con la checklist del documento y pega el bloque de la escena siguiente en el mismo proyecto.

## Story Rules

1. **QUESTION FIRST** – abre con un momento que haga preguntar "¿por qué?"; retén la respuesta.
2. **MAKE US CARE** – pronto, el protagonista hace algo amable o justo y lo tratan mal por ello.
3. **THE VIEWER KNOWS MORE** – muestra al espectador un peligro o secreto que el protagonista no ve.
4. **EVERY BEAT TURNS** – cada beat invierte bueno/malo; enlaza con "pero" o "por lo tanto", nunca "y entonces".
5. **PAY OFF, THEN REOPEN** – da la victoria esperada, abre una pregunta mayor y corta.

Texto original y criterios de verificación: [`skills/micro-drama/references/story-rules.md`](skills/micro-drama/references/story-rules.md).

## Instalación

En Claude Code:

```
/plugin marketplace add aespower/micro-drama
/plugin install micro-drama@micro-drama
```

O copia `skills/micro-drama/` en `~/.claude/skills/` (usuario) o `.claude/skills/` (proyecto).

## Estructura

```
.claude-plugin/
  plugin.json
  marketplace.json
skills/micro-drama/
  SKILL.md
  references/story-rules.md
  references/prompt-templates.md
  references/production.md
  references/flow-agent-format.md
  assets/episode-template.md
```

## Limitaciones

- La skill genera el documento; no llama a Google Flow. Hay que pegarlo en Flow (o conectar un MCP de Flow).
- El límite de longitud del prompt del modo Agent no está documentado; cada bloque se mantiene por debajo de ~6.000 caracteres.
- Los costes en créditos vienen de la plantilla original y pueden cambiar; verifícalos en Flow.
