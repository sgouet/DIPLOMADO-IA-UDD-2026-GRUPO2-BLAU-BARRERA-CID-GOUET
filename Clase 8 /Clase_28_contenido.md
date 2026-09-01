# Clase 28 — ¿Qué es un agente de IA? Primer contacto práctico

**Diplomado IA Aplicada al Diseño · UDD · 2026**
Profesor: Darío Osorio
Fecha: Jueves 3 de septiembre de 2026 · 18:30–21:00 hrs
Modalidad: **online sincrónico** · Unidad 3 · Sesión 7 de 10 · **Propuesta D**

---

## Apertura

Hasta acá usaste modelos que **responden**. Un agente **actúa**: planifica, decide, usa herramientas externas (buscar en internet, escribir archivos, ejecutar código) y trabaja hacia un objetivo con autonomía. Es la categoría más importante del 2026 en IA aplicada.

Esta clase te presenta agentes de forma práctica: usando ChatGPT (con GPTs / o1) y Claude (con Projects / Computer Use). Nada de programar agentes desde cero — vamos a construirlos con las herramientas ya existentes.

## Resultado de aprendizaje

Al finalizar la clase el estudiante podrá:

1. **Explicar** la diferencia entre un LLM y un agente (percepción → razonamiento → acción).
2. **Construir un mini-agente** en Claude (usando Projects + Skills + Tools) o ChatGPT (Custom GPT con acciones).
3. **Diseñar el flujo agéntico** de su proyecto: objetivo, herramientas, límites.
4. **Identificar** los riesgos: alucinación, cost overrun, cascada de errores, human-in-the-loop.

## Glosario clave

| Término | Definición |
|---------|------------|
| **Agente** | Sistema que percibe → razona → actúa en loop hasta alcanzar un objetivo. |
| **Herramienta (tool)** | Función que el agente puede invocar (búsqueda, calculadora, código, API). |
| **Loop agéntico** | Ciclo repetido: pensar → actuar → observar → ajustar. |
| **ReAct** | Patrón donde el agente alterna razonamiento y acción explícita. |
| **Human-in-the-loop** | El agente pide aprobación humana para acciones críticas. |
| **MCP (Model Context Protocol)** | Estándar 2024 de Anthropic para conectar agentes con herramientas externas. |
| **Skill** | Habilidad pre-empaquetada que un agente puede usar (buscar, resumir, escribir docs). |
| **Custom GPT** | Asistente configurable de ChatGPT con instrucciones, archivos y acciones. |
| **Claude Skills** | Skills pre-armadas o custom que Claude puede invocar (2025). |

---

## Parte 1 — Materia (30 min)

### Bloque 1 (10 min): De LLM a agente

**LLM puro**:
```
Prompt → LLM → Respuesta
```

**Agente**:
```
Objetivo → LLM piensa → Herramienta 1 (busca) → observa →
LLM re-piensa → Herramienta 2 (escribe) → observa →
LLM decide terminar → Respuesta final
```

La diferencia:
- Un agente **decide qué hacer**, no solo qué decir.
- **Usa herramientas reales** que afectan el mundo (busca en web, edita archivos, manda emails).
- **Itera** sobre resultados.

**Ejemplo concreto**:
- LLM puro: "Sintetiza las últimas guías WCAG" → responde con conocimiento entrenado (puede estar desactualizado).
- Agente: mismo prompt → busca en la web las guías actualizadas → descarga → sintetiza con citas.

La diferencia entre esos dos outputs es la diferencia entre "demo divertida" y "herramienta de trabajo".

### Bloque 2 (10 min): Patrón ReAct

El patrón fundacional de los agentes modernos. Alterna dos modos:

```
[RAZONAMIENTO] El agente "piensa en voz alta":
   "Necesito buscar las últimas guías WCAG. Usaré el buscador."
       ↓
[ACCIÓN] Ejecuta una herramienta concreta:
   buscar_web("WCAG 2.2 updates 2026")
       ↓
[OBSERVACIÓN] Recibe resultado:
   [lista de páginas]
       ↓
[RAZONAMIENTO] "El primer resultado parece oficial. Lo leo."
       ↓
[ACCIÓN] leer_url("https://w3.org/...")
       ↓
   ... y así hasta terminar.
```

Ese "pensar en voz alta" no es decorativo — mejora significativamente la calidad de las acciones.

### Bloque 3 (10 min): Límites y riesgos

Los agentes son poderosos pero frágiles:

| Riesgo | Cómo se ve | Mitigación |
|--------|------------|------------|
| **Loops infinitos** | Agente repite acciones sin avanzar | Límite máximo de iteraciones |
| **Alucinación** | Inventa datos, cita URLs falsas | Verificar outputs críticos |
| **Costo descontrolado** | Cada acción es 1 llamada al LLM | Presupuesto por sesión |
| **Acción irreversible** | Borra archivos, manda emails | Human-in-the-loop |
| **Cascada de errores** | Error del paso 1 se amplifica en 2, 3, 4 | Trazabilidad + validación |

**Regla de oro**: para acciones con consecuencias externas (mandar correos, hacer compras, borrar), **siempre human-in-the-loop**.

---

## Parte 2 — Ejercicios prácticos (90 min)

**Herramientas**:
- [Claude](https://claude.ai) (Projects + Skills + Computer Use)
- [ChatGPT](https://chatgpt.com) (Custom GPT con Actions)

### Ejercicio 1 — Setup del agente en Claude Projects (20 min)

1. En [claude.ai](https://claude.ai) → Projects → New project.
2. Nombrarlo `Asistente de investigación · [tu proyecto]`.
3. **Custom instructions** (system prompt):

```
Eres un asistente de investigación de diseño para el proyecto [nombre].
El problema que abordamos: [heredado de Unidad 2].

Cuando te pida algo:
1. Piensa paso a paso antes de actuar.
2. Si necesitas información externa, indícalo explícitamente.
3. Si estás inseguro, dilo — no inventes.
4. Cita fuentes cuando uses información específica.

FORMATO: siempre estructurado con títulos y bullets.
NUNCA: inventar datos, citas o URLs.
```

4. **Knowledge**: subir 2-3 fuentes clave del proyecto (transcripciones, papers, brief).
5. Empezar a chatear.

### Ejercicio 2 — Probar Claude Skills / Computer Use (20 min)

*Nota*: Skills están disponibles según plan. Si tu plan no incluye, hacer solo con Projects.

Con Skills disponibles:

1. En el chat, activar `skills` desde el menú.
2. Pedirle a Claude que haga algo que requiera herramientas:
   - "Busca en la web los últimos 3 papers sobre inteligencia artificial y diseño inclusivo. Resume cada uno en 3 puntos."
   - "Analiza esta imagen [subir un screenshot de una interfaz] y proponme 3 mejoras de accesibilidad."
3. Observar el "razonamiento visible" del agente mientras trabaja.

### Ejercicio 3 — Custom GPT alternativo (15 min)

Para quienes tengan ChatGPT Plus:

1. Explore GPTs → Create.
2. Configure:
   - Nombre: `Asistente Diseño [tu proyecto]`.
   - Instructions: el mismo system prompt de Claude.
   - Knowledge: subir 2-3 archivos del proyecto.
   - Capabilities: activar Web Browsing + DALL·E + Code Interpreter.
3. Actions: si te sientes con ánimo, agregar una acción custom (ej: llamar a una API pública).
4. Probar el mismo prompt del Ejercicio 2.

### Ejercicio 4 — Diseñar el flujo agéntico de tu proyecto (10 min)

Completar el template `Clase_28_arquitectura_agente_template.md` (incluido) con:

- Objetivo del agente en 1 frase.
- Herramientas necesarias.
- Puntos donde requiere aprobación humana.
- Límites explícitos (qué NO debe hacer).

### Ejercicio 5 — Instalar y conectar el MCP de Adobe Illustrator (20 min)

*Objetivo*: vivir el loop agéntico completo — percepción → razonamiento → acción — con una herramienta real de diseño, no solo con texto.

1. **Instalar el MCP de Adobe Illustrator**:
   - Abre Claude Desktop → *Settings* → *Connectors* (o *Developer* → *MCP Servers* si usas Claude Code).
   - Agrega el conector **Adobe for Creativity / Illustrator MCP** (búscalo en el marketplace de conectores de tu cliente Claude; el nombre exacto puede variar según la versión de la app).
   - Autoriza el acceso con tu cuenta de Adobe (Creative Cloud).
   - Confirma que el conector queda activo (ícono verde / "conectado").

2. **Abrir el archivo de trabajo**:
   - Abre `Illustrator_mcp.ai` (incluido en esta misma carpeta) en Adobe Illustrator y déjalo abierto — el agente necesita el documento activo para leerlo y modificarlo.

3. **Pedirle algo concreto al agente** (elige una o combina varias):
   - "Revisa las capas de `Illustrator_mcp.ai` y dime qué elementos tiene el artboard."
   - "Cambia el color de fondo del artboard a un tono que combine con la paleta de mi proyecto."
   - "Reordena o ajusta los elementos y expórtame una versión en PNG."

4. **Observar el loop agéntico en vivo**:
   - ¿Qué "piensa" el agente antes de actuar?
   - ¿Qué herramienta (tool) invoca exactamente? ¿Coincide con el patrón ReAct del Bloque 2?
   - ¿Te pidió aprobación antes de modificar el archivo? Si no lo hizo, ¿debería haberlo hecho? (conecta con la Regla de oro del Bloque 3).

5. **Registrar evidencia**: screenshot del antes/después de `Illustrator_mcp.ai` + una frase describiendo qué acción ejecutó el agente y con qué herramienta.

> *Si no tienes Adobe Illustrator o Creative Cloud instalado*: trabaja en pareja con alguien que sí tenga acceso, u observa una demo del docente y documenta el proceso igual.

### Ejercicio 6 — Subir evidencia (5 min)

- `docs/arquitectura_agente.md` (completado).
- Screenshots del agente funcionando (incluye el antes/después de `Illustrator_mcp.ai`).
- Link al Project o Custom GPT.

---

## Parte 3 — Revisiones en salas (30 min)

**Formato**: salas breakout de 3-4 estudiantes.

### Consigna

Cada estudiante (5-7 min):

1. Comparte su agente funcionando en vivo.
2. Ejecuta un caso de uso relevante para su proyecto.
3. El grupo propone UN límite adicional que debería tener el agente.

### Cierre en plenario (5 min)

- ¿Qué agente les pareció más útil?
- ¿Alguien vio a su agente hacer algo inesperado?
- ¿En qué caso, dentro de sus proyectos, sí o sí necesita human-in-the-loop?

---

## Trabajo autónomo (~2 h)

1. **Iterar el system prompt** hasta que el agente responda de forma consistente y útil (1 h).
2. **Documentar 5 casos de uso** concretos donde el agente ayuda (30 min).
3. **Anticipar 3 casos de falla** posibles y cómo manejarlos (15 min).
4. **Subir todo al repo** (15 min).

---

## Conexión con el entregable de posta

Al cerrar tienes:
- Agente funcional (Claude Project o Custom GPT).
- Arquitectura documentada (`docs/arquitectura_agente.md`).
- 5 casos de uso probados.

---

## Recursos útiles

- Anthropic — [*Building effective agents*](https://www.anthropic.com/engineering/building-effective-agents).
- OpenAI — [*Introducing GPTs*](https://openai.com/index/introducing-gpts/).
- Yao et al. (2023) [*ReAct: Synergizing Reasoning and Acting*](https://arxiv.org/abs/2210.03629) — paper fundacional, leer solo abstract + intro.
- [Model Context Protocol](https://modelcontextprotocol.io) — el estándar abierto para tools.
- Adobe — conectores MCP para Creative Cloud (Illustrator, Photoshop) — revísalos en el marketplace de conectores de tu cliente Claude.

---

## Referencias culturales y casos LATAM

- **[Cocos Capital](https://cocos.capital) (Argentina)** — experimenta con agentes para asesoría financiera.
- **DevAgent (México)** — agentes para investigación legal.
- **Casos chilenos**: municipalidades usando agentes para responder consultas ciudadanas. Discutir tensiones.
- **Voces críticas**: [Margaret Mitchell](https://huggingface.co/meg) (riesgos de delegación); [Emily Bender](http://faculty.washington.edu/ebender/) (simulación vs razonamiento real).

---

## Pregunta abierta de cierre

> Un agente puede investigar, escribir, ejecutar, decidir. ¿Cuál es la última decisión que sigue siendo necesariamente tuya en tu proyecto? Y si esa también puedes automatizarla — ¿por qué NO lo harías?
