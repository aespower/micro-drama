---
name: micro-drama
description: Crea micro dramas verticales con IA (Google Flow) de principio a fin — guion por escenas, auditoría con las 5 Story Rules (question first, make us care, viewer knows more, every beat turns, pay off then reopen), master sets, retratos, clip prompts encadenados segundo a segundo y plan de edición con coste en créditos. Úsala cuando el usuario quiera escribir, revisar o producir un episodio de micro drama, serie corta vertical, drama de 9:16, "short drama", o pida auditar un episode-NN-script.md contra las story rules.
---

# Micro Drama (Google Flow)

Flujo de seis pasos de la plantilla *AI Micro Drama Prompt Template* + las 5 Story Rules como control de calidad narrativo.

Archivos de referencia (léelos cuando llegues al paso que los usa):
- `references/story-rules.md` — las 5 reglas, criterios PASA/FALLA, tabla de auditoría, política de corrección.
- `references/prompt-templates.md` — formato de escena, master set, retrato, clip prompt, AVOID, transiciones, gramática de cámara, rechazos de Flow, mapa regla → plano.
- `references/production.md` — encadenado de frames, checklist de edición, costes.
- `assets/episode-template.md` — plantilla de `episode-NN-script.md`.

## Modos

Detecta el modo por la petición:

| Petición | Modo | Pasos |
|---|---|---|
| "Escribe / crea el episodio…" | Completo | A → B → (pausa) → C → D → E |
| "Revisa / audita / check episode-NN…" | Auditoría | B y para |
| "Haz los prompts de…" (guion ya aprobado) | Producción | C → D → E |

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

## C · Set y reparto (pasos 2–3)

Con `references/prompt-templates.md`:
1. Un **master set** por localización (image prompt, 9:16, sin personas, lista de props fijos).
2. Un **retrato limpio** por personaje, dentro del master set, misma luz. Nunca hojas multi-ángulo.
3. Keyframe de apertura de cada escena con todos sus personajes en cuadro.

## D · Clip prompts (pasos 4–5)

Para cada `T`, genera un bloque:
```
### SC#-T# · [CONTINUE SHOT | CUT SHOT] · [6|8|10] s · [créditos]
Start frame: [último frame de SC#-T# | keyframe nuevo: "same moment, same place, same light, camera now at …"]
[CAMERA] … [ACTION] … [DIALOGUE] … [LOOK] … [AVOID] …
```
- Acción segundo a segundo, con la mano concreta. Sin nombres: usa los descriptores fijos.
- Elige plano con la gramática de cámara y el mapa regla → plano (p. ej. la ventaja del espectador de la regla 3 suele ser un CUT SHOT aparte).
- Marca `RE-ANCHOR` cada ~4 clips encadenados (retrato fresco como referencia).
- `[AVOID]` completo en cada clip + elementos específicos de ese clip.

## E · Edición y presupuesto (paso 6)

Con `references/production.md`:
- Plan de corte: cortar solo en ángulo o hablante nuevo (~5 s), crossfade de 4 frames entre clips encadenados.
- Checklist de audio y color.
- Tabla de créditos: clips × coste, total y estimación con repeticiones (marcada como estimación; los precios vienen de la plantilla y pueden haber cambiado).
- Recomienda probar una escena antes de generar el episodio completo.

## Reglas generales

- Prompts de Flow en inglés; explicaciones al usuario en su idioma.
- No presentes como verificado algo que no se ha generado o probado en Flow.
- Entregables como archivos `.md` en el directorio de trabajo: `episode-NN-script.md`, `episode-NN-prompts.md`, `episode-NN-edit.md`.
