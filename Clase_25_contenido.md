# Clase 25 — LLMs conversacionales para diseño (ChatGPT, Claude, DeepSeek)

**Diplomado IA Aplicada al Diseño · UDD · 2026**
Profesor: Darío Osorio
Fecha: Martes 25 de agosto de 2026 · 18:30–21:00 hrs
Modalidad: **online sincrónico** · Unidad 3 · Sesión 4 de 10 · **Propuesta D**

---

## Apertura

ChatGPT, Claude, DeepSeek. Tres LLMs conversacionales, tres "personalidades", tres formas de ayudarte con tu proyecto. Esta clase es sobre **cómo se usan bien** y **cómo se comparan** para tareas de diseño reales. Nada de Colab: todo pasa en la interfaz web de cada uno.

## Resultado de aprendizaje

Al finalizar la clase el estudiante podrá:

1. **Distinguir** los tres LLMs y elegir el adecuado según la tarea.
2. **Diseñar prompts profesionales** con los 6 componentes: rol, contexto, instrucción, formato, ejemplos, restricciones.
3. **Comparar en vivo** los outputs de ChatGPT vs Claude vs DeepSeek para el mismo prompt.
4. **Construir un "asistente" personalizado** para su proyecto en al menos una de las plataformas.

## Glosario clave

| Término | Definición |
|---------|------------|
| **LLM** | Large Language Model. Modelo grande de lenguaje entrenado para predecir el siguiente token. |
| **Prompt** | Instrucción que le das al modelo. |
| **System prompt** | Instrucción persistente que define el rol y comportamiento del modelo. |
| **Contexto (context window)** | Cuánto texto puede procesar el modelo en una interacción. Claude Opus: 200K; GPT-4o: 128K; DeepSeek: 128K. |
| **Temperatura** | Cuán "creativo" es el output. 0 = determinístico; 1 = variado. |
| **Custom GPT / Project / Agent** | Asistente personalizado con instrucciones + archivos + herramientas. |

---

## Parte 1 — Materia (30 min)

### Bloque 1 (10 min): Tres modelos, tres personalidades

| Aspecto | ChatGPT (OpenAI) | Claude (Anthropic) | DeepSeek |
|---------|------------------|--------------------|-----------|
| Contexto | 128K tokens | 200K tokens | 128K tokens |
| Fortaleza | Multimodal, código, análisis | Escritura, instrucciones largas | Razonamiento (R1), open weights |
| Multimodal | Sí (imagen, audio, video) | Sí (imagen) | Solo texto (V3) |
| Plan gratuito | Limitado | Limitado | Generoso |
| Plan pagado | ChatGPT Plus $20/mes | Claude Pro $20/mes | Muy barato ($0.14/1M tokens API) |
| Personalización | Custom GPTs, Projects | Projects, Artifacts | Menos maduro |
| País | EEUU | EEUU | China |
| Uso en diseño | Prototipado rápido, análisis | Investigación densa, brief writing | Alternativa low-cost, razonamiento matemático |

**Recomendación operativa**: tener cuenta en al menos dos de las tres. Cada una tiene "personalidad" distinta. Para tareas críticas, comparar.

### Bloque 2 (10 min): Prompt engineering — los 6 componentes

Un prompt profesional tiene 6 elementos. Los primeros 4 son obligatorios, los últimos 2 opcionales pero recomendados:

```
1. ROL          — quién es el modelo en esta tarea
2. CONTEXTO     — información de fondo necesaria
3. INSTRUCCIÓN  — qué exactamente quieres
4. FORMATO      — cómo quieres la respuesta
5. EJEMPLOS     — 1-3 muestras del output esperado (opcional)
6. RESTRICCIONES — qué NO debe hacer (opcional)
```

**Ejemplo malo vs. bueno**:

Malo:
```
Resumime estas entrevistas y dame insights.
```

Bueno:
```
Eres un investigador UX senior con 10 años de experiencia en banca chilena.

Te paso 5 transcripciones de entrevistas con usuarios de la app [Nombre].

Tu tarea:
1. Identifica los 3 patrones más fuertes de frustración.
2. Cita textualmente cada patrón.
3. Marca cuando aparece en varias entrevistas (fuerte) vs una sola (débil).

FORMATO: tabla con columnas: Patrón, Cita, Fuerza (fuerte/débil).

NO hagas: recomendaciones de diseño (eso lo hago yo), especulaciones sin
cita, análisis de una sola entrevista como si fuera tendencia.

[transcripciones...]
```

Diferencia entre los dos: ~90 segundos extra de trabajo, y el output pasa de "insights de manual" a evidencia utilizable.

### Bloque 3 (10 min): Buenas prácticas mínimas

- **Empieza específico, no general.** Cuanto más contexto pertinente, mejor calibrado el output.
- **Itera el prompt, no acumules mensajes.** Si la primera respuesta no sirve, mejora el prompt antes que pedirle "otra vez pero mejor".
- **Guarda tus prompts.** Un buen system prompt vale como pieza de trabajo. Versionalo en tu repo.
- **Verifica outputs críticos.** Los LLMs alucinan datos, citas, cifras. Especialmente con nombres propios y fechas.
- **Cuidado con datos sensibles.** Cada mensaje viaja al servidor. Para datos del cliente: leer términos de servicio o usar modelos locales.

---

## Parte 2 — Ejercicios prácticos (90 min)

**Herramientas**:
- [chatgpt.com](https://chatgpt.com) (OpenAI)
- [claude.ai](https://claude.ai) (Anthropic)
- [chat.deepseek.com](https://chat.deepseek.com) (DeepSeek)

### Ejercicio 1 — Setup de las 3 cuentas (10 min)

- [ ] Cuenta en ChatGPT (gratis alcanza).
- [ ] Cuenta en Claude (gratis alcanza).
- [ ] Cuenta en DeepSeek (gratis, generoso).
- [ ] Tener las 3 pestañas abiertas simultáneamente para comparar.

### Ejercicio 2 — Bench en vivo: el mismo prompt en las 3 (25 min)

Usar este prompt exacto (o adaptado a tu proyecto) en las 3 plataformas y comparar:

```
Eres un investigador UX senior especializado en usuarios chilenos.

Te paso un fragmento de una entrevista con Maria (45 años, Concepción):
"Yo entro a la app y la cosa es que no encuentro nunca el botón de
transferir. Está escondido en un menú de tres líneas que ni se ve.
Mi mamá ni cacha cómo usarlo, le tengo que hacer las transferencias
yo todas las semanas."

Tu tarea:
1. Identifica el principal punto de dolor (en 1 frase).
2. Cita textualmente la evidencia.
3. Propone 1 oportunidad de diseño concreta.
4. Estima severidad: alta / media / baja.

FORMATO estructurado con negritas.
```

Comparar en las 3 y anotar:
- ¿Cuál fue más específico?
- ¿Cuál usó mejor las citas?
- ¿Cuál propuso la mejor solución de diseño?
- ¿Cuál sonó más "chileno" o "genérico"?

### Ejercicio 3 — Diseñar el system prompt de tu proyecto (25 min)

Escribe un system prompt para el asistente de research de tu proyecto. Usar los 6 componentes vistos en la materia.

Pruébalo en Claude Projects (o Custom GPT en ChatGPT):

**En Claude**:
1. Ir a Projects → New project.
2. Nombrarlo `Research asistente [tu proyecto]`.
3. En "Custom instructions" pegar tu system prompt.
4. En "Knowledge" subir 2-3 fuentes clave del proyecto.
5. Chatear con el asistente.

**En ChatGPT** (equivalente):
1. Explore GPTs → Create.
2. Definir instrucciones (equivalente a system prompt).
3. Subir archivos.
4. Probar.

### Ejercicio 4 — Iterar el prompt (20 min)

Probar 3 versiones distintas del system prompt:
- v1: básico (rol + instrucción).
- v2: con formato explícito.
- v3: con ejemplos few-shot.

Documentar en la bitácora qué versión funcionó mejor y por qué.

### Ejercicio 5 — Guardar evidencia (10 min)

Subir a tu repositorio:
- `docs/system_prompt_v3.md` — la versión definitiva.
- `docs/comparativa_llms.md` — mini-tabla comparando los 3 modelos con tu prompt.

---

## Parte 3 — Revisiones en salas (30 min)

**Formato**: salas breakout de 3-4 estudiantes.

### Consigna

Cada estudiante (5-7 min):

1. Comparte pantalla y muestra su system prompt v3.
2. Ejecuta en vivo con el grupo mirando.
3. El grupo propone UN ajuste al prompt. Se aplica y se ejecuta de nuevo.

### Cierre en plenario (5 min)

- ¿Qué modelo terminó siendo el favorito del grupo? ¿Por qué?
- ¿Alguien encontró que un modelo pequeño (DeepSeek) igualó a los grandes en su caso?
- ¿Qué patrón de prompt engineering fue más productivo?

---

## Trabajo autónomo (~2.5 h)

1. **Refinar el system prompt del proyecto** hasta al menos v4 (1 h).
2. **Crear un Claude Project o Custom GPT** funcional con tus fuentes cargadas (45 min).
3. **Documentar 3 casos de uso concretos** del asistente para tu proyecto (30 min).
4. **Subir todo al repo** (15 min).

---

## Conexión con el entregable de posta

Al cerrar tienes:
- Asistente conversacional funcional en al menos una plataforma.
- System prompt versionado en el repo.
- Comparativa documentada de los 3 modelos para tu caso.

---

## Recursos útiles

- OpenAI — [*Prompt engineering guide*](https://platform.openai.com/docs/guides/prompt-engineering).
- Anthropic — [*Prompt engineering overview*](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview).
- [promptingguide.ai](https://promptingguide.ai) — recurso gratuito y muy completo.
- DeepSeek — documentación oficial en [deepseek.com](https://www.deepseek.com).

---

## Referencias culturales y casos LATAM

- **[Latam-GPT](https://dcc.ing.uc.cl/latam-gpt-el-modelo-de-lenguaje-con-identidad-latinoamericana-que-lidera-alvaro-soto-a-traves-de-cenia/) (Universidad de Chile)** — LLM en construcción para LATAM, anunciado 2024 con apoyo del Estado.
- **Comparativa práctica**: probar los 3 modelos con expresiones chilenas coloquiales ("filete", "cuático", "ya po") y ver cuál responde mejor.
- **Karen Hao** — su libro [*Empire of AI*](https://www.penguinrandomhouse.com/books/743569/empire-of-ai-by-karen-hao/) documenta cómo se comparan las políticas de las grandes empresas.

---

## Pregunta abierta de cierre

> Cada LLM tiene sesgos distintos, políticas distintas, procedencia distinta. Si tienes que elegir uno solo para trabajar todo el semestre — ¿en base a qué criterios eliges? ¿Rendimiento, precio, procedencia geopolítica, licencia? ¿Qué dice esa elección sobre tu posición como diseñador?
