---
name: micro-drama
description: Crea micro dramas verticales con IA (Google Flow) de principio a fin — guion por escenas, auditoría con las 5 Story Rules (question first, make us care, viewer knows more, every beat turns, pay off then reopen) y un Flow Agent Brief por escena listo para copiar y pegar en el modo Agent de Flow, que genera ingredientes, keyframes y todos los clips; más plan de edición con coste en créditos. Úsala cuando el usuario quiera escribir, revisar o producir un episodio de micro drama, serie corta vertical, drama de 9:16, "short drama", o pida auditar un episode-NN-script.md contra las story rules.
---

# Micro Drama (Google Flow)

Flujo de seis pasos de la plantilla *AI Micro Drama Prompt Template* + las 5 Story Rules como control de calidad narrativo.

Archivos de referencia (léelos cuando llegues al paso que los usa):
- `references/story-rules.md` — las 5 reglas, criterios PASA/FALLA, tabla de auditoría, política de corrección.
- `references/prompt-templates.md` — formato de escena, master set, retrato, clip prompt, AVOID, transiciones, gramática de cámara, rechazos de Flow, mapa regla → plano.
- `references/production.md` — encadenado de frames, checklist de edición, costes.
- `references/flow-agent-format.md` — formato del Flow Agent Brief (salida principal de producción).
- `assets/episode-template.md` — plantilla de `episode-NN-script.md`.

## Modos

Detecta el modo por la petición:

| Petición | Modo | Pasos |
|---|---|---|
| "Escribe / crea el episodio…" | Completo | A → B → (pausa) → C+D → E |
| "Revisa / audita / check episode-NN…" | Auditoría | B y para |
| "Haz los prompts / el brief de Flow de…" (guion ya aprobado) | Producción | C+D → E |

## A · Guion (paso 1: escenas, no clips)

1. Si faltan datos, pregunta solo lo que cambia el resultado: premisa, protagonista, antagonista, nº de episodio, duración objetivo. Lo demás, decide tú y decláralo.
2. Escribe `episode-NN-script.md` con `assets/episode-template.md`:
   - 2–3 escenas reales por episodio. 2–3 personas hablando entre sí. **Máximo 4 personajes por episodio.**
   - Cada `T` es un clip de 6/8/10 s; cada escena termina en un giro.
   - Diseña desde el inicio con las 5 Story Rules (no las añadas después).
   - Evita en pantalla lo que Flow rechaza (ataúdes, uniformes de policía, arrestos): resuélvelo fuera de cámara.
   - Asigna a cada personaje un **descriptor visual fijo** en inglés; se usará en lugar del nombre en los prompts.

## B · Auditoría con las Story Rules

1. Lee `references/story-rules.md`.
2. Imprime la tabla con columnas exactas:
   `time | what happens | open question | who we hope for | what the viewer knows | before → after | but/therefore`
   Una fila por beat (`T`), tiempo acumulado.
3. Debajo, veredicto por regla: `PASA` / `FALLA` + beat que lo demuestra.
4. **Corrige solo lo que falla.** Edita el archivo, muestra cada cambio como antes/después y re-audita solo las filas afectadas.
5. **Detente y espera** el siguiente mensaje del usuario. No sigas a producción sin aprobación.

Si el archivo indicado no existe, dilo y pide el guion; no inventes uno para auditarlo.

## C+D · Flow Agent Brief (pasos 2–5) — SALIDA PRINCIPAL

Lee `references/flow-agent-format.md` y `references/prompt-templates.md`. Genera `episode-NN-flow-agent.md`: **un bloque de código por escena**, listo para pegar en Google Flow con **Agent** activado, que crea la escena completa sin más intervención.

Cada bloque incluye, en este orden:
1. GOAL (trabajar sin preguntas, no saltar ni reordenar shots).
2. SETTINGS (9:16, modelo, audio de diálogo, sin música ni texto).
3. INGREDIENTS: master set de la localización + un retrato limpio por personaje de la escena, con etiquetas neutras `CHAR-A`, `CHAR-B`… (nunca nombres propios).
4. GLOBAL AVOID.
5. CONTINUITY: reglas CONTINUE / CUT y plan B si el agente no puede usar el último frame.
6. SHOT 1…n: tipo, duración, start, cámara, acción segundo a segundo con la mano concreta, diálogo con voz, look, avoid específico. Marca `RE-ANCHOR` cada ~4 clips encadenados.
7. IF A SHOT FAILS y DELIVER.

Reglas:
- Prompts en inglés; diálogos en el idioma elegido.
- Elige planos con la gramática de cámara y el mapa regla → plano (la ventaja del espectador de la regla 3 suele ser un CUT shot aparte).
- ≤ 6.000 caracteres por bloque; si no cabe, divide en PART 1 · INGREDIENTS y PART 2 · SHOTS.
- La cabecera del documento (en el idioma del usuario) explica cómo pegarlo, los créditos por escena y qué revisar.

Si el usuario pide prompts manuales (sin Agent), genera además `episode-NN-prompts.md` con las plantillas de `references/prompt-templates.md`.

## E · Edición y presupuesto (paso 6)

Con `references/production.md`:
- Plan de corte: cortar solo en ángulo o hablante nuevo (~5 s), crossfade de 4 frames entre clips encadenados.
- Checklist de audio y color.
- Tabla de créditos: clips × coste, total y estimación con repeticiones (marcada como estimación; los precios vienen de la plantilla y pueden haber cambiado).
- Recomienda probar una escena antes de generar el episodio completo.

## Reglas generales

- Prompts de Flow en inglés; explicaciones al usuario en su idioma.
- No presentes como verificado algo que no se ha generado o probado en Flow.
- Entregables como archivos `.md` en el directorio de trabajo: `episode-NN-script.md`, `episode-NN-flow-agent.md` (principal), `episode-NN-edit.md` y, solo si se pide, `episode-NN-prompts.md`.
