# Guía visual — Clase 27 (Imagen generativa con Nano Banana)

## Antes de la clase
- [ ] Cuenta Google activa (para Gemini) → [gemini.google.com](https://gemini.google.com)
- [ ] Opcional: cuenta en [aistudio.google.com](https://aistudio.google.com) si quieres más control técnico

## Estructura de prompt visual
```
[SUJETO] Diseñadora chilena de 35 años en su estudio
[ESTILO] fotografía editorial, Wallpaper Magazine
[COMPOSICIÓN] plano medio, frontal, centrado
[ILUMINACIÓN] luz natural cálida desde la izquierda
[PALETA] tierras y blanco
[TÉCNICO] look hiperrealista, formato vertical 9:16
```

## Trucos con Nano Banana (Gemini 2.5 Flash Image)
- **Edición conversacional**: no reescribas el prompt completo para ajustar algo. Sigue el mismo hilo: "cambia la luz a fría", "saca el objeto del fondo", "que mire hacia la cámara".
- **Consistencia de sujeto**: pide explícitamente "mantén al mismo personaje/producto" cuando generes variantes — así no se te "transforma" entre imágenes.
- **Fusión de imágenes**: sube 2-3 imágenes de referencia (sujeto + escena + estilo) y pide que las combine, en vez de describir todo en palabras.
- **SynthID**: toda imagen que generes queda marcada como IA (marca de agua invisible). Es esperable y es parte del uso responsable — no intentes "ocultarlo".

## Documentar cada imagen
- Prompt o instrucción de edición exacta.
- Herramienta: Nano Banana (Gemini 2.5 Flash Image).
- Nombre de archivo descriptivo.

## Subir al repo
- `outputs/sistema_visual/` con las imágenes.
- `docs/sistema_visual.md` con prompts + comentarios.
