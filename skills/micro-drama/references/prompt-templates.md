# Prompt Templates (Google Flow)

Fuente: "AI Micro Drama Prompt Template" (Hamza Shergill, ejemplo *The Valet*). Los prompts se escriben en **inglés**: es el idioma de la plantilla y el que mejor sigue el modelo.

## 1. Formato de escena (guion)

```
## SC1 · Club entrance, golden hour
T1 8s [Preston, Noah] A white convertible pulls up. Preston throws the keys at Noah.
  PRESTON: "Park it. Don't scratch it, valet."
T2 8s [Maddie, Preston, Noah] Maddie steps out, sees Noah, freezes.
  MADDIE: "...Noah?"   PRESTON: "You know the help, babe?"
T3 8s [Maddie, Preston] MADDIE: "We dated. He couldn't even afford dinner here."
T4 8s [Preston, Noah] PRESTON: "Here's your tip. Pick it up."   NOAH: "Enjoy your dinner, sir."
```

- `T#` = un clip. Duración 6 / 8 / 10 s. Usa 10 s solo si acción + diálogo no caben en 8.
- `[...]` = personajes en cuadro.
- Toda escena termina en un giro. Máximo 4 personajes por episodio.

## 2. Master set (image prompt)

```
[LOCATION], [time of day + light].
Wide establishing shot, 24mm, eye level.
Fixed props: [list every prop that recurs].
Empty of people. Photoreal, 9:16.
```

Un master set por localización. Todos los frames de esa escena salen de esta imagen.

## 3. Portrait (image prompt)

```
One person only: [age, hair, eyes, face, outfit, one signature detail].
Chest-up portrait in [master set], same light.
Single image, no panels, no text, no extra angles. 9:16.
```

Un retrato limpio por personaje. **Nunca** una hoja multi-ángulo: Flow la convierte en paneles split-screen.

## 4. Clip prompt

```
[CAMERA]   MEDIUM 3-shot, 35mm, eye level, slow push-in
[ACTION]   0.0-2.0 s: the blond man in the cream linen suit reaches into
           his jacket with his RIGHT hand.
           2.0-4.0 s: he pulls out a dollar bill in the SAME right hand
           and lets it drop at the valet's feet.
[DIALOGUE] "Here's your tip. Pick it up." (loud, smug American man)
           The valet, calm, low voice: "Enjoy your dinner, sir."
[LOOK]     continuous take, no cuts. Golden hour, same light as start frame.
[AVOID]    any cut or transition inside the clip; scene change; faces, hair or
           wardrobe changing; extra people appearing or talking; people
           passing through objects; objects appearing from nowhere;
           switching hands mid-action; the bill appearing in the other hand;
           colour or lighting shift; camera shake; subtitles; on-screen text;
           music.
```

Reglas del clip prompt:
- Acción segundo a segundo, con la mano concreta (RIGHT / LEFT) y "SAME hand" cuando se repite.
- **Sin nombres de personajes** en `[ACTION]` ni `[DIALOGUE]`: descríbelos ("the blond man in the cream linen suit", "the valet"). Mantén un descriptor fijo por personaje en todo el episodio.
- `[DIALOGUE]` incluye tono y acento de voz.
- `[AVOID]` siempre al final. Añade elementos específicos del clip (objeto en la otra mano, etc.).

## 5. Tipos de transición

| Tipo | Start frame | Instrucción |
|---|---|---|
| CONTINUE SHOT | Último frame exacto del clip anterior | "Seamless, no cut." |
| CUT SHOT | Keyframe nuevo: edición de imagen (gratis) del último frame + retratos de referencia | "same moment, same place, same light, camera now at [angle]" |

## 6. Camera grammar

| Shot | Lens | Úsalo para |
|---|---|---|
| Wide | 24mm | Abrir cada escena, llegadas, salidas |
| Medium / OTS | 35–50mm | Diálogo y confrontaciones |
| Close-up | 85mm | Reacciones, humillación, revelación |
| Low / High angle | — | Low = poder tras una revelación. High = humillación |

## 7. Lo que Flow rechaza (evitar en guion y prompts)

- Nombres de personajes en la acción ("prominent people"). Describe a las personas.
- Ataúdes, uniformes de policía, arrestos. Si la trama los necesita, resuélvelos fuera de cámara o con elipsis.
- Start frames subidos con caras reales: usa una copia generada por Flow.

## 8. Mapa regla narrativa → plano

| Regla | Plano recomendado |
|---|---|
| 1 · Question first | Abre en Wide o Medium con la acción anómala ya en curso; nada de establecer contexto. |
| 2 · Make us care | Medium con el acto amable visible; Close-up 85mm o High angle en el castigo. |
| 3 · Viewer knows more | CUT SHOT aparte (OTS o Close-up de otro personaje/objeto) fuera del campo visual del protagonista. |
| 4 · Every beat turns | Cambia de ángulo o de hablante en cada giro (también es la regla de corte de edición). |
| 5 · Pay off, then reopen | Low angle para la victoria; Close-up final para la nueva pregunta, corte seco. |
