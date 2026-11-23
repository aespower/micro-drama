# Formato Flow Agent Brief

Salida principal de producción: un documento con **un bloque por escena**, listo para copiar y pegar en el prompt de Google Flow con **Agent** activado. El agente crea los ingredientes (set y personajes), el keyframe y todos los clips de la escena en orden.

## Qué se sabe del modo Agent (y qué no)

Confirmado (ayuda oficial de Google, vía búsqueda):
- Se activa con el interruptor **Agent** en la caja de prompt.
- Rinde mejor con una descripción detallada: sujeto, acción, entorno, luz y estilo.
- Puede crear varias variaciones a la vez.
- Extender un clip existente requiere suscripción Google AI Plus/Pro/Ultra y el modelo Omni Flash 1.2.

Fuentes de terceros (sin verificar):
- El agente puede hacer preguntas aclaratorias antes de generar.
- La consistencia de personajes entre planos se logra con **Ingredients**.

Desconocido: límite de longitud del prompt, si encadena el último frame automáticamente, coste exacto en modo agente. Por eso el brief:
- es **un bloque por escena** (no el episodio entero);
- se autocontiene (repite ajustes y descripciones en cada bloque);
- prohíbe preguntas y da valores por defecto;
- incluye un plan B si el agente no puede encadenar frames.

## Reglas de redacción

1. Todo en **inglés**, salvo los diálogos (en el idioma elegido, entre comillas y marcados `in Spanish`).
2. **Sin nombres propios** en acción ni etiquetas de ingrediente (Flow los bloquea como "prominent people"). Usa etiquetas neutras: `CHAR-A`, `CHAR-B`… siempre junto a su descriptor fijo. Si un diálogo contiene un nombre y Flow lo rechaza, el agente debe quitar el nombre de esa línea.
3. Pasos numerados y en orden. Cada shot indica duración, tipo de transición, cámara, acción segundo a segundo con la mano concreta, diálogo con voz, look y avoid.
4. Una lista **GLOBAL AVOID** al inicio + avoid específico por shot.
5. Instrucción explícita de **no pedir confirmación** y de **no saltar pasos**; si algo falla, regenerar ese shot hasta 2 veces y continuar.
6. Objetivo de longitud: ≤ 6.000 caracteres por bloque. Si se supera, dividir en `PART 1 · INGREDIENTS` y `PART 2 · SHOTS`.

## Plantilla

````
```
FLOW AGENT BRIEF · EP[NN] · SCENE [N] of [TOTAL] · "[title]"

GOAL
Produce this complete scene: first the ingredients, then the opening keyframe,
then every shot in order as separate video clips. Work autonomously. Do not
ask me questions; use the defaults below. Do not skip, merge or reorder shots.

SETTINGS
Aspect ratio 9:16. Photoreal, cinematic. Video model: Omni Flash (or the best
available). Clip length as stated per shot. Native dialogue audio ON. No
music, no subtitles, no on-screen text.

INGREDIENTS (create these images first; reuse them as references in every shot)
- SET-[X]: [master set prompt: location, time + light, 24mm wide, fixed props,
  empty of people]
- CHAR-A: [age, hair, eyes, face, outfit, signature detail]. Chest-up portrait
  in SET-[X], same light, single image, no panels, no text.
- CHAR-B: ...
Keep every face, hairstyle, outfit and prop identical to these ingredients in
all shots.

GLOBAL AVOID (applies to every shot)
cuts or transitions inside a clip; scene change; faces, hair or wardrobe
changing; extra people appearing or talking; people passing through objects;
objects appearing from nowhere; switching hands mid-action; colour or lighting
shift; camera shake; subtitles; on-screen text; music.

CONTINUITY
- CONTINUE shot: start from the exact last frame of the previous clip
  (use Extend if available).
- CUT shot: make a new start image from the previous clip's last frame +
  ingredients: "same moment, same place, same light, camera now at [angle]".
- If you cannot use a previous frame, build the start image from SET-[X] +
  the character ingredients, matching the described positions.

SHOT 1 · [KEYFRAME|CONTINUE|CUT] · [8] s
Start: [what the start image shows]
Camera: [shot, lens, angle, movement]
Action:
  0-2 s: ...
  2-4 s: ...
Dialogue: CHAR-[X], [voice description], in Spanish: "[line]"
Look: continuous take, no cuts, [light].
Avoid: [shot-specific items]

SHOT 2 · ...

IF A SHOT FAILS
Regenerate it up to 2 times with the same prompt. If a line with a name is
refused, remove the name from that line. Then continue with the next shot.

DELIVER
All clips of this scene in shot order, labelled "EP[NN]-SC[N]-SHOT[n]".
```
````

## Documento completo (`episode-NN-flow-agent.md`)

1. Cabecera breve en el idioma del usuario: cómo usarlo (activar Agent, pegar bloque 1, esperar, revisar, pegar bloque 2), créditos estimados por escena, avisos.
2. Un bloque de código por escena con la plantilla anterior. Cada bloque se copia entero con un clic.
3. Al final: checklist de revisión rápida por escena (caras iguales, mano correcta, diálogo completo, sin texto en pantalla).
