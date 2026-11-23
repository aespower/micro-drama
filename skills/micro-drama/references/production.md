# Producción: encadenado, edición y costes

## Encadenado de frames (pasos 4)

1. Keyframe de apertura con **todos** los personajes de la escena ya en cuadro.
2. Genera 8 s (12 créditos). Prompt con "continuous take, no cuts" y sin nombres.
3. Extrae el último frame y súbelo como start frame del siguiente clip.
4. Une con un crossfade de 4 frames (izquierda: último frame; derecha: primer frame del siguiente).
5. Re-ancla cada ~4 clips con un retrato fresco: las caras derivan (en *The Valet* el aparcacoches perdió la barba en el clip 4).

## Checklist de edición (paso 6)

- [ ] Una toma continua por clip. Recorta solo cabeza y cola. Nunca trocees un clip en jump cuts.
- [ ] Corta solo en un ángulo nuevo o un hablante nuevo, ~cada 5 s.
- [ ] Aísla las voces (Demucs, gratis). Elimina el ruido de fondo de los clips.
- [ ] Iguala el color de cada clip al primero de la escena; después un grade común.
- [ ] Una sola cama musical bajo toda la escena.

## Costes (Google Flow, Omni 1.1 Flash, 720p)

Datos tomados de la plantilla; **verificar en Flow antes de presupuestar**, los precios y modelos cambian.

| Elemento | Créditos | Nota |
|---|---|---|
| Imagen (keyframe, set, retrato) | 0 | Nano Banana Pro es gratis en Flow |
| Clip 6 s / 8 s / 10 s | 10 / 12 / 15 | 10 s solo si acción + diálogo no caben en 8 |
| Escena de 7 planos | ~84 | *The Valet*, escena 2 |
| Temporada de 32 episodios | ~7.300 | Rodar por actos; medir tras el acto 1 |

Fórmula de estimación por episodio: `Σ créditos por clip × (1 + tasa de repetición)`. Usa 0,5 como tasa de repetición inicial si no hay datos reales; marca la cifra como estimación.

## Regla de validación

Prueba una escena antes de gastar los créditos de un episodio completo. Si no aguanta 30 segundos, no aguantará 3 minutos.
