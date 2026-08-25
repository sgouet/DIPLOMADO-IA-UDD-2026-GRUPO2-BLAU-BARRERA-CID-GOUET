# Clase 26 — Hugging Face: el ecosistema de la IA

**Diplomado IA Aplicada al Diseño · UDD · 2026**
Profesor: Darío Osorio
Fecha: Jueves 27 de agosto de 2026 · 18:30–21:00 hrs
Modalidad: **online sincrónico** · Unidad 3 · Sesión 5 de 10 · **Propuesta D**

---

## Apertura

Hugging Face es "el GitHub de la IA": el catálogo público donde viven cientos de miles de modelos, datasets y demos ejecutables. Para un diseñador, es la puerta al ecosistema open source — la alternativa a depender solo de OpenAI, Anthropic o Google.

Esta clase la trabajamos **desde el navegador**, sin código. Vas a aprender a buscar modelos, probarlos sin instalar nada (vía Spaces), y usar la Inference API para incluirlos en un flujo simple.

## Resultado de aprendizaje

Al finalizar la clase el estudiante podrá:

1. **Navegar el Hugging Face Hub** y filtrar modelos por tarea, licencia y tamaño.
2. **Probar modelos gratis** vía Spaces (interfaz web).
3. **Leer una model card** e interpretar sus campos.
4. **Identificar 2-3 modelos open source** aplicables a su proyecto.

## Glosario clave

| Término | Definición |
|---------|------------|
| **Hugging Face** | Empresa + comunidad + plataforma. Hospeda modelos, datasets y demos. |
| **Hub** | El catálogo principal de HF ([huggingface.co/models](https://huggingface.co/models)). |
| **Spaces** | Demos ejecutables directamente en el navegador. Cientos de miles disponibles. |
| **Model Card** | Ficha del modelo: quién lo hizo, para qué, cómo se usa, limitaciones. |
| **License** | Términos legales de uso. Los más comunes: MIT, Apache 2.0, Llama Community License. |
| **Inference API** | Servicio para llamar a modelos vía HTTP sin descargarlos. |
| **Open weights vs Open source** | *Open weights* = los pesos están disponibles pero no todo el proceso. *Open source* = incluye datos, código, licencia libre. |

---

## Parte 1 — Materia (30 min)

### Bloque 1 (10 min): Qué es Hugging Face y por qué importa

Fundada en 2016 por franceses (Clément Delangue, Julien Chaumond). Hoy es el estándar de facto del ecosistema abierto de IA. Hospeda:

- ~500.000 modelos (LLMs, visión, audio, multimodal).
- ~100.000 datasets.
- ~200.000 Spaces (demos ejecutables).

**Por qué importa para diseño**:
- Alternativa a depender solo de las 3 grandes (OpenAI, Anthropic, Google).
- Modelos gratis y ejecutables sin cuenta paga.
- Transparencia: model cards estandarizadas, licencias claras.
- Casos de uso latinoamericanos: BETO (español), Bloomz (multilingüe), Patagón (Chile).

### Bloque 2 (10 min): Cómo se elige un modelo

Al abrir [huggingface.co/models](https://huggingface.co/models), ves un catálogo enorme. Cómo filtrar bien:

1. **Task** (columna izquierda): text-generation, text-classification, image-generation, audio-to-text, etc.
2. **Language**: filtrar por español si tu proyecto es local.
3. **License**: si vas a usarlo comercialmente, importa. MIT y Apache 2.0 son las más permisivas.
4. **Trending / Most downloads**: buenos indicadores de calidad y adopción.
5. **Model size**: modelos chicos (<3B) corren en tu computador; grandes (>30B) requieren GPU pesada o API.

### Bloque 3 (10 min): Model card — cómo leerla

Cada modelo tiene una "ficha" estandarizada. Los campos clave:

- **Model description**: qué es y qué hace.
- **Intended use**: para qué se pensó (y para qué no).
- **Training data**: con qué se entrenó.
- **Bias, risks and limitations**: honesto sobre lo que falla.
- **How to use**: código o comando de ejemplo.
- **License**: siempre revisar antes de usar en un proyecto real.
- **Metrics**: rendimiento comparativo.

**Regla de oro para diseñadores**: si la model card es escueta o falta, sospechar. Los buenos modelos vienen con documentación seria.

---

## Parte 2 — Ejercicios prácticos (90 min)

**Herramienta**: [huggingface.co](https://huggingface.co) (cuenta gratis).

### Ejercicio 1 — Explorar el Hub (20 min)

1. Crear cuenta en huggingface.co (gratis).
2. Ir a `Models`. Filtrar por:
   - Task: `Text Generation`.
   - Language: `Spanish`.
   - Sort by: `Most Downloads`.
3. Elegir 3 modelos que te llamen la atención. Para cada uno anotar en la bitácora:
   - Nombre completo.
   - Autor / Organización.
   - Tamaño (número de parámetros).
   - Licencia.
   - Una limitación declarada en la model card.

### Ejercicio 2 — Probar modelos vía Spaces (25 min)

1. Ir a `Spaces`. Filtrar por: `Text-to-Image`.
2. Elegir 2 Spaces populares (ej: uno de Stable Diffusion, uno de Flux).
3. Probar con el mismo prompt en los 2. Comparar outputs, velocidad, calidad.
4. Repetir con `Text-Generation` (probar 2 LLMs open source vía Spaces).

### Ejercicio 3 — Buscar modelos para tu proyecto (25 min)

Basado en el problema de tu proyecto (heredado de Unidad 2), buscar en HF:
- 1 modelo generativo relevante.
- 1 modelo analítico relevante.
- 1 dataset que podrías usar.

Para cada uno, documentar en tu bitácora: nombre, tarea, licencia, por qué te sirve.

### Ejercicio 4 — Duplicar un Space y personalizarlo (15 min)

*Nota*: este ejercicio es opcional pero abre posibilidades enormes.

1. Elegir un Space útil (ej: uno de análisis de sentimiento).
2. Click en `Duplicate this Space` (arriba a la derecha).
3. Ahora tienes tu copia editable.
4. En `Files → app.py` puedes ver el código (no hay que modificarlo si no quieres).
5. Cambiar el `README.md` con tu nombre y proyecto.
6. Guardar → tu Space queda live en `huggingface.co/spaces/tu-usuario/nombre-space`.

### Ejercicio 5 — Subir evidencia al repo (5 min)

- `docs/modelos_hf_candidatos.md` — los 3 modelos que elegiste para tu proyecto.
- Screenshots de las pruebas en Spaces.

---

## Parte 3 — Revisiones en salas (30 min)

**Formato**: salas breakout de 3-4 estudiantes.

### Consigna

Cada estudiante (5-7 min):

1. Comparte los 3 modelos que eligió para su proyecto.
2. Muestra 1 Space que probó en vivo.
3. El grupo propone 1 modelo alternativo que no había considerado.

### Cierre en plenario (5 min)

- ¿Alguien encontró un modelo hecho en Latinoamérica?
- ¿Qué tanto pesó la licencia en tu decisión?
- ¿Cambió tu opinión sobre depender de OpenAI/Anthropic ahora que viste el catálogo abierto?

---

## Trabajo autónomo (~2 h)

1. **Explorar profundamente** los 3 modelos elegidos: leer model card completa, probar en Space (1 h).
2. **Escribir 1 párrafo** por cada modelo justificando por qué (no) sirve para tu proyecto (30 min).
3. **Actualizar el repo** con la evidencia (30 min).

---

## Conexión con el entregable de posta

Al cerrar tienes:
- 3 modelos open source candidatos documentados.
- Al menos 1 Space probado con éxito.
- Comparativa mínima entre modelos cerrados (OpenAI/Anthropic/Google) y abiertos (HF).

---

## Recursos útiles

- [Hugging Face Learn](https://huggingface.co/learn) — cursos gratis muy accesibles.
- [Awesome Hugging Face Spaces](https://github.com/huggingface/awesome-huggingface) — curación de los mejores Spaces.
- [Canal YouTube de Hugging Face](https://www.youtube.com/@huggingface) — tutoriales cortos y actualizados.

---

## Referencias culturales y casos LATAM

- **[BETO](https://huggingface.co/dccuchile/bert-base-spanish-wwm-cased)** (Universidad de Chile) — primer BERT para español. Punto de partida clásico.
- **[MarIA](https://huggingface.co/PlanTL-GOB-ES/roberta-base-bne)** (Barcelona Supercomputing Center) — LLM español europeo.
- **Patagón** ([CENIA Chile](https://www.cenia.cl)) — modelo entrenado con foco chileno.
- **[Aya](https://huggingface.co/CohereLabs/aya-101)** (Cohere for AI) — modelo open multilingüe con soporte para 101 idiomas.

---

## Pregunta abierta de cierre

> Cuando descubres que hay un modelo open source hecho en Chile, o entrenado en español rioplatense, o con licencia libre — ¿cambia algo? ¿Por qué no lo estabas usando? ¿Qué te hace elegir el modelo "de moda" sobre el modelo "adecuado"?
