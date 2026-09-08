# Clase 31 — Antigravity y el sistema Loop · Cierre de la Unidad 3

**Diplomado IA Aplicada al Diseño · UDD · 2026**
Profesor: Darío Osorio
Fecha: Martes 15 de septiembre de 2026 · 18:30–21:00 hrs
Modalidad: **online sincrónico** · Unidad 3 · Sesión 10 de 10 · **CIERRE**

---

## Apertura

Última clase de la unidad. Vamos a trabajar con **Google Antigravity**, el IDE agéntico presentado junto a Gemini 3, y su arquitectura **Loop** — el patrón que probablemente marca el estándar del trabajo con IA por los próximos años.

Esta clase no tiene presentación final de proyecto: es una clase de **ejercicios y experimentación** con Antigravity, con tiempo extra al final para profundizar el Loop sobre algo que ya hiciste tú mismo.

## Glosario clave

| Término | Definición |
| --------- | ------------ |
| **Antigravity** | IDE agéntico de Google, lanzado 18 nov 2025 junto a Gemini 3. |
| **Loop** | Arquitectura de ejecución agéntica: research → plan → execute → verify → fix → repeat. |
| **Editor View** | Modo síncrono: IDE tradicional con IA que autocompleta y sugiere. |
| **Manager Surface** | Modo asíncrono: se orquestan múltiples agentes trabajando en paralelo. |
| **Artifact** | Output estructurado del agente (plan, código, análisis, validación). Es cómo el agente "muestra" su trabajo. |
| **implementation_plan.md** | Artifact especial: plan de implementación que el agente propone antes de ejecutar. |
| **Multi-tool autonomy** | Capacidad del agente de usar editor + terminal + browser en un solo flujo. |
| **Managed Agents** | Los agentes de Antigravity operan con backend gestionado por Google, no dependen de tu máquina. |

---

## Parte 1 — Materia (30 min)

### Bloque 1 (10 min): Qué es Antigravity

Google Antigravity fue anunciado el **18 de noviembre de 2025** junto al lanzamiento de Gemini 3: un IDE donde los **agentes ejecutan tareas completas**, no solo autocompletan código.

**Qué lo distingue de VS Code / Cursor / Windsurf**:

- No es "code completion con IA" — es un entorno donde los **agentes ejecutan tareas completas** de principio a fin.
- Dos modos:
  - **Editor View**: IDE clásico + IA (sincrónico).
  - **Manager Surface**: dashboard donde se crean, orquestan y observan agentes trabajando en paralelo (asíncrono).
- Multi-tool autonomy: el agente puede editar código, correr el terminal, abrir el navegador y validar comportamiento en un solo workflow.

**Planes 2026**:

| Plan | Precio | Para quién |
| ------ | -------- | ----------- |
| Free | $0 | Prueba, proyectos pequeños |
| AI Pro | $20/mes | Uso profesional individual |
| AI Ultra | $249.99/mes | Uso intensivo / equipos |

**Disponibilidad**: macOS, Linux, Windows.

### Bloque 2 (15 min): La arquitectura Loop

Este es el corazón de Antigravity. El sistema no funciona por "prompt y respuesta" — funciona por un loop de ejecución persistente:

```
┌──────────────────────────────────────────────────────────────┐
│                                                              │
│   ┌─────────┐   ┌──────┐   ┌─────────┐   ┌────────┐          │
│   │RESEARCH │→ │PLAN  │→ │EXECUTE  │→ │VERIFY  │─┐          │
│   │         │  │      │  │         │  │        │ │          │
│   └─────────┘  └──────┘  └─────────┘  └────────┘ │          │
│                                                    ↓         │
│                                              ┌────────┐      │
│                                              │  FIX   │      │
│                                              └────────┘      │
│                                                    │         │
│                                                    └────┐   │
│                                                          ↓  │
│                                              [repite hasta   │
│                                               que se cumple  │
│                                                el objetivo]  │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

**Los 5 pasos**:

1. **Research** — el agente explora tu código, tu contexto, tus fuentes.
2. **Plan** — genera un artifact llamado `implementation_plan.md` con el plan detallado.
3. **Execute** — ejecuta el plan (edita código, corre terminal, abre browser).
4. **Verify** — comprueba que lo que hizo funciona (corre tests, valida output).
5. **Fix** — si algo falla, lo arregla y vuelve a verificar.

Este loop se repite hasta que el objetivo se cumple. **Es self-correcting**: el agente no te pregunta a cada paso, sigue trabajando y solo te consulta en checkpoints críticos (típicamente después del Plan y antes de merge).

### Bloque 3 (5 min): Modo Plan vs Modo Execute — human-in-the-loop bien hecho

Cuando pides algo grande, Antigravity entra automáticamente en **modo Plan**:

- Investiga.
- Genera `implementation_plan.md` como artifact visible.
- Te presenta un botón `Proceed`.
- **Nada cambia hasta que apruebas**.

Esto es human-in-the-loop bien diseñado: el agente trabaja autónomo dentro de tareas pequeñas, pero pide aprobación antes de cambios estructurales.

**Para diseño** este patrón es replicable en tu propio flujo: automatizar la iteración pequeña, humano decide en los momentos grandes.

---

## Parte 2 — Ejercicios prácticos y experimentación (90 min)

Sin presentación final: esta parte es toda para ejercitar y experimentar con Antigravity sobre tu propio proyecto.

**Herramienta**: [antigravity.google](https://antigravity.google) (cuenta Google, free tier).

### Ejercicio 1 — Instalar Antigravity (15 min)

1. Ir a [antigravity.google](https://antigravity.google) o buscar "Google Antigravity IDE download".
2. Descargar para tu sistema operativo (Mac / Linux / Windows).
3. Instalar.
4. Iniciar sesión con Google.
5. El free tier alcanza para esta clase.

### Ejercicio 2 — Primer proyecto en Editor View (15 min)

**Parte A — Generar el primer HTML**

1. Crear una carpeta nueva en tu computador (por ejemplo `primer-proyecto-antigravity`).
2. Dentro de esa carpeta, crear un archivo `hallazgos.md` con 3-4 hallazgos reales de tu proyecto (puede ser texto simple, no hace falta que esté perfecto).
3. Abrir la carpeta en Antigravity (Archivo → Abrir carpeta).
4. Ubicar el panel de chat del agente.
5. Escribir el siguiente prompt:

   ```
   Necesito una página HTML simple que muestre los principales
   hallazgos de mi proyecto de diseño. Los datos están en
   `hallazgos.md`. Genera un HTML con estilo minimalista,
   responsive, en español.
   ```

6. Presionar enter y observar el panel de actividad: primero Research (lee `hallazgos.md`), después Plan (genera `implementation_plan.md`), después Execute (escribe el HTML).
7. Cuando el agente termina, abrir el HTML generado en el navegador (Antigravity suele ofrecer un botón de vista previa).
8. Revisar el resultado: ¿refleja bien tus hallazgos?, ¿es legible?

**Parte B — Pedir un cambio de estilo (para ver el Loop de nuevo)**

1. Escribir un segundo prompt pidiendo un cambio visual, por ejemplo:

   ```
   Cambia la paleta de colores a tonos oscuros con un acento en
   verde, y usa una tipografía sans-serif más grande para los
   títulos.
   ```

10. Observar cómo el agente vuelve a correr el Loop completo (Research del HTML existente → Plan del cambio → Execute → Verify), sin que tengas que reescribir nada desde cero.
3. Si queda tiempo, pedir un segundo ajuste (por ejemplo "hazlo responsive para celular" o "agrega un modo oscuro/claro con un botón para cambiar").

### Ejercicio 3 — Documentar el uso (10 min)

1. Crear un archivo `docs/antigravity_loop.md` en tu repositorio del proyecto.
2. Escribir un resumen breve (3-5 líneas) de qué tarea le diste a Antigravity y qué resultado obtuviste.
3. Anotar cuántas vueltas del Loop necesitó (¿resolvió todo a la primera o tuvo que corregir?).
4. Tomar 2-3 capturas de pantalla: el prompt que escribiste, el `implementation_plan.md` que generó el agente, y el resultado final.
5. Guardar las capturas en una carpeta `docs/capturas/` y enlazarlas desde `antigravity_loop.md`.
6. Hacer commit con un mensaje descriptivo (por ejemplo: "docs: agrega documentación del uso de Antigravity").

### Ejercicio 4 — Experimentación libre con tu proyecto (30 min)

Elige una tarea real y pendiente de tu propio proyecto (no un ejemplo de juguete) y aplícale el Loop completo. Si no sabes por dónde empezar, aquí tienes varios ejemplos según el tipo de proyecto — elige uno, adáptalo, o usa el tuyo propio:

- **Datos o hallazgos**: "Genera una visualización simple de estos datos en un gráfico de barras/líneas."
- **Identidad visual**: "Aplica esta paleta de colores y esta tipografía a todos los archivos HTML de mi carpeta `outputs/`."
- **Prototipo funcional**: "Crea un formulario que capture [un dato de tu proyecto] y lo guarde en un archivo JSON."
- **Contenido y copy**: "Reescribe el texto de esta página en un tono más directo (o más poético, según tu proyecto) y actualiza el HTML."
- **Organización del repo**: "Revisa toda mi carpeta `docs/` y genera un índice (`INDEX.md`) que la resuma."

Con la tarea elegida:

1. Definir con precisión qué querés lograr (mientras más concreto el pedido, mejor investiga y planifica el agente).
2. Aplicarle el Loop completo con Antigravity — Editor o Manager, el que prefieras.
3. Dejar que el agente investigue, planifique, ejecute y se corrija; intervenir solo en los checkpoints.
4. Anotar en tu bitácora: qué funcionó, qué no, y dónde tuviste que intervenir tú.

No hay expectativa de un resultado "terminado" — el objetivo es experimentar con el patrón Loop en un caso propio.

### Ejercicio 5 — Opcional: Modo Manager: agentes en paralelo (20 min)

Para quien termine antes o quiera explorar más. Cambiar a **Manager Surface**:

1. Crear 2-3 agentes en paralelo con tareas distintas:
   - Agente 1: `Genera un README.md para mi proyecto usando la datasheet.`
   - Agente 2: `Analiza mi carpeta de outputs y organízala por tipo de archivo.`
   - Agente 3: `Genera un archivo de arquitectura del sistema completo del proyecto.`
2. Observar el dashboard mientras trabajan.
3. Ver los artifacts que producen.
4. Aprobar o rechazar según revisión.

---

## Parte 3 — Profundizar el Loop: iterar sobre lo que ya hiciste (30 min)

Antes de cerrar la clase, un paso más allá de "que funcione": ver qué pasa cuando el Loop tiene que corregirse a sí mismo más de una vez.

### Bloque 4 (10 min): Cuando el Loop no cierra a la primera

- A veces Verify falla más de una vez seguida: el agente prueba, falla, ajusta, prueba de nuevo.
- Esto no es un error del sistema — es el Loop haciendo su trabajo.
- Lo que hay que mirar como diseñador: **¿el agente insiste en la misma solución rota, o realmente cambia de enfoque en cada vuelta?**
- Cuantas más vueltas de Fix necesita una tarea, más importa revisar el `implementation_plan.md` original: a veces el problema no es la ejecución, es que el plan estaba mal desde el Research.

### Ejercicio 6 — Romper algo a propósito y ver cómo lo arregla (20 min)

1. Vuelve a lo que hiciste en el Ejercicio 4 (o al HTML del Ejercicio 2).
2. Pídele a Antigravity una modificación que sepas que va a generar un conflicto o un error (por ejemplo: "cambia el formato de fecha en todo el archivo" cuando el dato no tiene ese formato, o "agrega una validación que hoy rompería el HTML actual").
3. Deja correr el Loop completo: que falle en Verify, entre a Fix, y vuelva a intentar.
4. Anota cuántas vueltas de Fix necesitó, y si en algún punto el agente cambió de estrategia o insistió en lo mismo.

No hace falta resolverlo — el objetivo es observar cómo se comporta el Loop bajo un error real, no en el caso ideal de los ejercicios anteriores.

---

## Rúbrica de evaluación (25% del diplomado)

| Criterio | Descripción | Peso |
| ---------- | ------------- | ------ |
| **Completitud** | ¿Están todos los componentes del entregable? | 25% |
| **Uso crítico de herramientas** | ¿Justificaste por qué elegiste cada herramienta? | 25% |
| **Documentación y trazabilidad** | ¿El repo permite entender el proceso? | 25% |
| **Profundidad de experimentación** | ¿Se nota que fuiste más allá de lo mínimo con Antigravity y el Loop? | 25% |

**Nota mínima**: 4.0 (escala UDD).

---

## Componentes del entregable de posta

Al cierre de esta clase debe estar todo lo siguiente en tu repositorio de GitHub público:

```
diplomado-ia-udd-2026-tuapellido/
├── README.md                              ← problema + arquitectura del sistema
├── docs/
│   ├── ficha_proyecto.md                  ← Clase 22
│   ├── datasheet_v1.md                    ← Clase 23
│   ├── hallazgos_notebooklm.md            ← Clase 24
│   ├── system_prompt_v3.md                ← Clase 25
│   ├── modelos_hf_candidatos.md            ← Clase 26
│   ├── sistema_visual.md                  ← Clase 27
│   ├── arquitectura_agente.md             ← Clase 28
│   ├── video_generativo.md                ← Clase 29
│   ├── hermes_casos_uso.md                ← Clase 30
│   └── antigravity_loop.md                ← Clase 31
├── outputs/
│   ├── sistema_visual/                    ← imágenes generadas
│   ├── videos/                            ← video conceptual
│   └── imagenes                       
├── notebooks/
│   ├── Clase_22.ipynb
│   ├── Clase_23.ipynb
│   └── Clase_24.ipynb
└── bitacora/
    └── (reflexiones por clase)
```
