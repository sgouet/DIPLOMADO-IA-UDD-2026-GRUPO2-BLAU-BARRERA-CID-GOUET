# Clase 27 — Imagen generativa con Nano Banana (Gemini 2.5 Flash Image)

**Diplomado IA Aplicada al Diseño · UDD · 2026**
Profesor: Darío Osorio
Fecha: Martes 1 de septiembre de 2026 · 18:30–21:00 hrs
Modalidad: **online sincrónico** · Unidad 3 · Sesión 6 de 10 · **Propuesta D**

---

## Apertura

Imagen generativa: la clase donde la IA "dibuja" para ti. Esta versión de la clase se concentra en **una sola herramienta, bien usada**: **Nano Banana**, el apodo con el que se conoce a **Gemini 2.5 Flash Image**, el modelo nativo de generación y edición de imágenes de Google. La razón de elegir una sola herramienta en vez de repartir la clase entre cinco: Nano Banana vive dentro de una conversación — se genera, se edita, se itera y se fusionan imágenes todo en el mismo hilo, con lenguaje natural, sin curva de aprendizaje de comandos como en Midjourney ni saltos entre apps. Para un curso que ya viene usando Gemini/Google en varias clases anteriores, es también el camino de menor fricción.

Esta clase es la más "creativa" del bloque de herramientas. Vamos a **generar y editar mucho** — 30+ imágenes por estudiante en la sesión — y a discutir el uso ético y crítico de estas herramientas en proyectos profesionales de diseño.

## Resultado de aprendizaje

Al finalizar la clase el estudiante podrá:

1. **Explicar** qué hace distinto a Nano Banana de un generador de imágenes clásico (edición conversacional, consistencia de sujeto, fusión de imágenes).
2. **Diseñar prompts visuales** con estructura profesional (sujeto, estilo, composición, iluminación, parámetros).
3. **Iterar por conversación**: editar una misma imagen con instrucciones sucesivas en lenguaje natural, sin rehacer el prompt desde cero.
4. **Documentar** un mini-sistema visual reproducible para su proyecto, manteniendo un mismo sujeto/personaje coherente entre imágenes.

## Glosario clave

| Término | Definición |
|---------|------------|
| **Nano Banana** | Apodo con el que se conoce a **Gemini 2.5 Flash Image**, el modelo de generación y edición nativa de imágenes de Google. |
| **Prompt visual** | Instrucción textual para generar una imagen. |
| **Edición conversacional** | Dar instrucciones sucesivas en lenguaje natural sobre una misma imagen ("saca el fondo", "cambia la luz a cálida") en vez de reescribir el prompt completo. |
| **Fusión de imágenes (image blending)** | Combinar dos o más imágenes de referencia (sujeto + escena + estilo, por ejemplo) en una sola composición nueva. |
| **Consistencia de sujeto** | Capacidad del modelo de mantener el mismo personaje, producto o estilo reconocible a través de varias generaciones o ediciones. |
| **SynthID** | Marca de agua invisible que Google incorpora en toda imagen generada con sus modelos, para transparencia sobre el origen sintético. |
| **Aspect ratio** | Proporción de la imagen: 1:1 cuadrada, 16:9 apaisada, 9:16 vertical. |
| **Difusión (Diffusion)** | Familia de modelos generativos de imagen sobre la que se apoyan modelos como Nano Banana: parten de ruido y lo "limpian" hasta llegar a una imagen coherente. |

---

## Parte 1 — Materia (30 min)

### Bloque 1 (10 min): Cómo genera imágenes la IA (versión intuitiva)

Los modelos de imagen generativa, en su base, hacen esto:

```
1. Se entrenan a partir de imágenes con ruido añadido progresivamente.
2. Aprenden a "limpiar" el ruido en pequeños pasos.
3. Para generar: parten de ruido y lo limpian guiados por tu prompt (o por una imagen de referencia).
4. En pocos pasos, emerge una imagen coherente.
```

Es predicción estadística de píxeles guiada por texto (y, en el caso de Nano Banana, también por imágenes). No es magia — es matemática entrenada con miles de millones de imágenes.

**Lo distinto de Nano Banana**: no es solo un generador de imagen desde cero. Es un modelo **multimodal nativo** integrado en Gemini — entiende texto e imagen en la misma conversación, así que puedes subir una foto, pedirle que cambie algo puntual, y seguir iterando sin perder el hilo ni el sujeto original.

### Bloque 2 (10 min): Qué hace bien Nano Banana, y por qué esta clase no reparte entre cinco herramientas

| Capacidad | Qué significa en la práctica |
|-----------|-------------------------------|
| **Edición conversacional** | "Saca el fondo", "pon esta silla en un living con luz natural", "que la persona mire hacia la cámara" — todo en lenguaje natural, sobre la misma imagen. |
| **Ediciones locales precisas** | Desenfocar fondos, quitar manchas u objetos, cambiar poses, colorear imágenes en blanco y negro, sin rehacer toda la composición. |
| **Fusión de imágenes** | Subes 2-3 imágenes (sujeto, escena, estilo/referencia) y el modelo las combina en una escena nueva y coherente. |
| **Consistencia de sujeto** | Genera el mismo personaje o producto en distintas poses, ángulos o contextos, manteniéndolo reconocible — clave para un sistema visual de proyecto. |
| **Buena adherencia al prompt** | Sigue instrucciones complejas (varios elementos a la vez) con bastante precisión. |
| **Transparencia** | Toda imagen incluye una marca de agua invisible SynthID, identificable como generada por IA. |

**Cómo se accede**: [gemini.google.com](https://gemini.google.com) (conversación normal, gratis con cuenta Google, con cuota diaria) o [aistudio.google.com](https://aistudio.google.com) (Google AI Studio, más control técnico, útil si más adelante quieres integrarlo por API). Para uso intensivo, Google AI Pro amplía la cuota.

**Por qué no Midjourney / DALL·E / Ideogram / Stable Diffusion en esta clase**: son excelentes herramientas y las vas a encontrar en el mundo profesional — vale la pena conocer que existen (quedan mencionadas más abajo, en Recursos). Pero cada una exige su propia cuenta, su propia lógica de comandos (Discord para Midjourney, parámetros `--` distintos en cada una) y no conversan entre sí. Para una clase de 150 minutos con foco en resultado, una sola herramienta conversacional que ya conocen (Gemini) reduce la fricción y deja más tiempo para pensar el criterio de diseño, no la sintaxis de la herramienta.

### Bloque 3 (10 min): Anatomía de un prompt visual profesional

```
[SUJETO PRINCIPAL]
[ESTILO VISUAL]
[COMPOSICIÓN / ENCUADRE]
[ILUMINACIÓN]
[PALETA]
[PARÁMETROS TÉCNICOS]
```

**Ejemplo malo**: `diseñador trabajando`

**Ejemplo bueno**:
```
Diseñadora industrial chilena de 35 años trabajando en un escritorio
minimalista de madera, luz natural cálida desde la izquierda, fotografía
editorial estilo Wallpaper Magazine, paleta tierra y blanco, plano medio
frontal, profundidad de campo reducida, look hiperrealista, formato
vertical 9:16.
```

Diferencia: el segundo genera resultados **consistentes y utilizables**. El primero, genéricos.

**El paso extra que habilita Nano Banana**: una vez que tienes esa primera imagen, no hace falta escribir un prompt nuevo para ajustarla. Basta con seguir la conversación: *"mantén a la misma diseñadora pero ahora de perfil"*, *"cambia la luz a más fría"*, *"pon el mismo escritorio en un espacio más grande"*. Esa es la diferencia entre generar 30 imágenes sueltas y construir un sistema visual coherente.

---

## Parte 2 — Ejercicios prácticos (90 min)

**Herramienta principal**: [gemini.google.com](https://gemini.google.com) (Nano Banana / Gemini 2.5 Flash Image). Alternativa con más control: [aistudio.google.com](https://aistudio.google.com).

### Ejercicio 1 — Iteración 1: prompt básico vs. profesional (20 min)

Elige un concepto de tu proyecto (ej: "usuario ideal", "escena de uso", "producto conceptual"). En Gemini:

1. Generar 1 imagen con prompt básico ("usuario usando la app").
2. Generar 1 imagen con prompt profesional (7+ elementos, ver estructura del Bloque 3).
3. Comparar visualmente. Anotar diferencias.

### Ejercicio 2 — Variantes sistemáticas por edición conversacional (25 min)

Elige UN sujeto principal (fijo) y genera la primera imagen. A partir de ahí, **sin reescribir el prompt**, pide en el mismo hilo:

- Variante 1: cambia el estilo (fotografía editorial → ilustración isométrica).
- Variante 2: cambia la iluminación (cálida → fría).
- Variante 3: cambia la composición (plano medio → plano general).
- Variante 4: cambia la paleta (tierras → neones).

Documenta cada instrucción exacta que diste y compara qué tan bien mantuvo Nano Banana la identidad del sujeto entre variantes.

### Ejercicio 3 — Fusión de imágenes y edición dirigida (15 min)

En el mismo hilo de Gemini:

1. Sube 2-3 imágenes propias: una como sujeto, una como escena/fondo, una como referencia de estilo.
2. Pide que las combine en una sola composición coherente.
3. Pide al menos una edición dirigida sobre el resultado ("saca ese objeto del fondo", "que la luz venga desde la derecha").
4. Compara este enfoque con el de escribir un prompt largo desde cero: ¿cuándo conviene fusionar imágenes en vez de describir todo en palabras?

### Ejercicio 4 — Sistema visual mínimo para el proyecto (20 min)

Elige una dirección estética ganadora y genera, manteniendo el mismo sujeto/estilo entre imágenes:

- 3-5 imágenes de "usuarios" en distintas situaciones.
- 3-5 imágenes de "producto" o "escena de uso".
- 1-2 imágenes de "atmósfera" o mood.

Es tu **sistema visual v1** para el proyecto de posta.

### Ejercicio 5 — Documentar el sistema (10 min)

Crear `docs/sistema_visual.md` en el repo con:
- 6-10 imágenes seleccionadas.
- Prompt (o instrucción de edición) exacto usado para cada una.
- Herramienta: Nano Banana / Gemini 2.5 Flash Image.
- Reflexión: ¿qué agrega vs. qué limita esta herramienta?

---

## Parte 3 — Revisiones en salas (30 min)

**Formato**: salas breakout de 3-4 estudiantes.

### Consigna

Cada estudiante (5-7 min):

1. Muestra su galería de 6-10 imágenes.
2. Explica la dirección estética elegida.
3. Recibe 1 crítica constructiva y 1 propuesta de variante del grupo.

### Cierre en plenario (5 min)

- ¿Alguien encontró que la IA "no sabe" hacer algo específico de su proyecto?
- ¿Cómo lidiaste con manos, texto y detalles finos?
- ¿Qué imagen te sorprendió más — para bien o para mal?

---

## Trabajo autónomo (~2 h)

1. **Generar 20 imágenes más** iterando la dirección elegida por edición conversacional (1 h).
2. **Curar el sistema visual final** (10-15 imágenes) (30 min).
3. **Escribir 1 párrafo crítico** en la bitácora: ¿cómo cambia tu proceso creativo esta herramienta? ¿qué se pierde, qué se gana? (15 min).
4. **Actualizar el repo** (15 min).

---

## Conexión con el entregable de posta

Al cerrar tienes:
- Sistema visual v1 con 10+ imágenes seleccionadas.
- Prompts e instrucciones de edición reproducibles documentados.
- Reflexión crítica sobre el uso de imagen generativa en tu proyecto.

---

## Recursos útiles

- [Introducing Gemini 2.5 Flash Image](https://developers.googleblog.com/en/introducing-gemini-2-5-flash-image/) — Google Developers Blog, la fuente oficial sobre el modelo detrás de Nano Banana.
- [Google AI Studio](https://aistudio.google.com) — para quienes quieran ir más allá de la interfaz conversacional.
- **Otras herramientas del ecosistema** (buenas de conocer, no se usan en esta clase): [DALL·E 3](https://openai.com/index/dall-e-3/) (integrado en ChatGPT Plus), [Midjourney](https://www.midjourney.com) (máxima calidad estética vía Discord/web), [Ideogram](https://ideogram.ai) (mejor manejo de texto en imagen), [Stable Diffusion](https://stability.ai/stable-image) (open source, local).
- [Prompt Hero](https://prompthero.com) y [Lexica](https://lexica.art) — bibliotecas de prompts de referencia (pensadas para Stable Diffusion/Midjourney, pero útiles para inspirarte en estructura).

---

## Referencias culturales y casos LATAM

- **[Refik Anadol](https://refikanadol.com)** — artista turco basado en EEUU, uso de generative art en gran escala.
- **[Sofía Crespo](https://sofiacrespo.com)** (Argentina) — pionera en generative art biológico.
- **[Anna Ridler](https://annaridler.com)** — obra basada en GANs con datasets propios.
- **Manuela García** (Chile) — diseñadora usando IA generativa para editorial.
- **Ética 2026**: [caso Getty vs Stability](https://news.bloomberglaw.com/ip-law/gettys-ai-copyright-suit-survives-stabilitys-bid-for-dismissal) (juicio activo por uso no autorizado de imágenes) y el rol del watermarking (SynthID) como intento de transparencia frente a ese mismo problema. Discutir implicancias.

---

## Pregunta abierta de cierre

> Cuando la IA te genera en 30 segundos algo que te hubiera tomado 3 días — ¿es un asistente, un colaborador o un reemplazo? ¿Y quién decide cuál de esas tres cosas es en tu proyecto?
