# 🐾 Vet Active Pro — Mini-Reporte Consolidado

**Fecha:** Septiembre 2026  
**Proyecto:** Vet Active Pro — App móvil para clínica veterinaria  
**Autor:** Hermes Grupo 2 — Diplomado AI

---

## Resumen Ejecutivo

Este mini-reporte consolida tres ejes del proyecto Vet Active Pro: (1) los **3 casos más citados de sesgo en apps veterinarias** identificados en la investigación 2024–2026, (2) la **clasificación de archivos** del proyecto, y (3) las **implicaciones de diseño** derivadas para la app. Vet Active Pro implementa un sistema de triaje con tres niveles (🔴 Nivel 1 crítico ≤1h, 🟡 Nivel 2 prioritario 1-2h, 🟢 Nivel 3 normal) y dos perfiles de usuario (tutores y colaboradores). Los hallazgos muestran que el sesgo racial, algorítmico y speciesista en herramientas veterinarias es un riesgo real que debe abordarse desde el diseño del triaje digital.

---

## 1. Hallazgos de Investigación: Sesgo en Apps Veterinarias (2024–2026)

### Caso 1: Sesgo de raza en la evaluación del dolor veterinario

| Campo | Detalle |
|-------|---------|
| **Fuente** | *"Tailoring treatment: dog breed status influences pain assessment and treatment in emergency veterinary care"* — Caddiell RMP et al., Frontiers in Pain Research (2025) |
| **DOI/URL** | [10.3389/fpain.2025.1589082](https://doi.org/10.3389/fpain.2025.1589082) |
| **Descripción** | Estudio retrospectivo de 3,744 pacientes caninos (69 razas) en sala de emergencias universitaria. Los veterinarios asignaron puntuaciones de dolor y planes de analgesia significativamente influidos por la raza, no por la severidad real. Golden Retrievers, Boxers y Doberman recibieron puntuaciones más bajas y menos analgesia; Chihuahuas y Dachshunds recibieron puntuaciones más altas. El efecto raza fue estadísticamente robusto (p = 8.01×10⁻³ para dolor; p = 3.66×10⁻³ para manejo). |
| **Relevancia para Vet Active Pro** | El triaje digital **no debe usar raza como variable de decisión**. Un modelo entrenado con datos históricos de una clínica puede heredar y reproducir automáticamente estos sesgos raciales en la priorización. |

### Caso 2: Sobre-triaje de ChatGPT en emergencias veterinarias caninas

| Campo | Detalle |
|-------|---------|
| **Fuente** | *"When used for veterinary triage, artificial intelligence models recognise emergencies but are more likely than veterinary staff to flag non-urgent cases"* — Wong A et al., Veterinary Record (2026) |
| **DOI/URL** | [10.1002/vetr.6126](https://doi.org/10.1002/vetr.6126) |
| **Descripción** | Estudio comparativo de ChatGPT-3.5, ChatGPT-4.0, veterinarios y enfermeras en triaje canino. Los modelos identificaron correctamente el 83-93% de casos graves, pero **sobre-triaron ~60% de casos no urgentes** como requiriendo atención inmediata. Precisión global de triaje inferior al 50%. El sobre-triaje genera presión innecesaria sobre recursos y fatiga de alerta. Cuando se combinó con enfermeras, la sensibilidad para casos graves subió al 95%, pero el costo fue un aumento masivo de falsos positivos. |
| **Relevancia para Vet Active Pro** | **El caso más directamente aplicable** al sistema de triaje 🔴🟡🟢. Un LLM usado para asignar niveles de urgencia tenderá a desplazar demasiados casos al nivel rojo, sobrecargando al personal y reduciendo la confiabilidad del sistema. Es fundamental que tu app no dependa de un LLM general para triaje sin ajuste de umbrales específicos. |

### Caso 3: Especiesismo en IA — Sesgo contra animales en modelos de lenguaje y visión

| Campo | Detalle |
|-------|---------|
| **Fuente** | *"Speciesist bias in AI: how AI applications perpetuate discrimination and unfair outcomes against animals"* — Hagendorff et al., AI and Ethics (Springer Nature, 2022; relevancia 2024–2026) |
| **DOI/URL** | [10.1007/s43681-022-00199-9](https://link.springer.com/article/10.1007/s43681-022-00199-9) |
| **Descripción** | Primer estudio sistemático sobre speciesist bias en IA: discriminación contra animales en visión computacional, word embeddings y modelos de lenguaje. Fotos de perros clasificadas como "small mammal"; modelos minimizan la gravedad de síntomas en mascotas vs. humanos. |
| **Relevancia para Vet Active Pro** | El **bot de triaje por WhatsApp/Chat** debe diseñarse para no subestimar la gravedad de síntomas. Todo modelo de lenguaje debe entrenarse con datos veterinarios específicos, no generalistas de salud humana. |

### Hallazgo adicional: Brecha de transparencia en IA veterinaria comercial

| Fuente | Hallazgo |
|--------|----------|
| *"A systematic audit of transparency and validation disclosure in commercial veterinary artificial intelligence"* — Brundage D., Frontiers in Veterinary Science (Marzo 2026, DOI: 10.3389/fvets.2026.1761038) | Auditoría de 71 productos de IA veterinaria comercial. **Puntuación media de transparencia: 6.4%**. El **63.3%** no reveló ninguna métrica de validación. Solo **1.4%** divulgó distribución demográfica de datos de entrenamiento. **0%** reportaron intervalos de confianza. Es **"imposible la evaluación independiente de sesgo algorítmico"** sin datos de entrenamiento. |

### Hallazgo adicional: Sesgo diagnóstico en LLMs veterinarios

| Fuente | Hallazgo |
|--------|----------|
| *"ChatGPT in Veterinary Medicine: A Practical Guidance"* — PMC (2024) | GPT-4 coincidió con el diagnóstico final en solo el **39%** de los casos. El **33%** incluyó el diagnóstico en el top differential pero omitió condiciones críticas. Los chatbots tienden a **"falsamente tranquilizar"** (dar "this can wait" a animales gravemente enfermos). |

---

## 2. Clasificación de Archivos del Proyecto

### 🎨 Diseño y Wireframes (Frontend)
| Archivo | Tipo | Tamaño | Descripción |
|---------|------|--------|-------------|
| `screens/vet_active_pro_wireframes.html` | HTML/CSS/JS | 66.4 KB | Wireframes interactivos (21 pantallas), responsive mobile |

### 🔧 Scripts y Herramientas
| Archivo | Tipo | Tamaño | Descripción |
|---------|------|--------|-------------|
| `generate_wireframes.py` | Python script | 61.8 KB | Generador de wireframes HTML |

### 📋 Documentación y Reportes (Markdown)
| Archivo | Tipo | Tamaño | Descripción |
|---------|------|--------|-------------|
| `screens/reporte_sesgo.md` | Markdown | 6.7 KB | Reporte de sesgo en apps veterinarias (3 casos + hallazgo LLM) |
| `screens/clasificacion_archivos.md` | Markdown | 3.3 KB | Clasificación de archivos por categoría |
| `screens/mini_reporte.md` | Markdown | 10.9 KB | Mini-reporte consolidado (investigación + clasificación + implicaciones) |

### 🔍 Datos de Investigación (JSON)
| Archivo | Tipo | Tamaño | Descripción |
|---------|------|--------|-------------|
| `breed_pain_bias.json` | JSON | 5.7 KB | Artículo: sesgo de raza en dolor canino (Frontiers 2025) |
| `extracted_articles.json` | JSON | 11.1 KB | Artículos extraídos (Frontiers, PetMonitor, Springer) |
| `search_results_1.json` | JSON | 11.6 KB | Resultados búsqueda 1: sesgo general en IA veterinaria |
| `search_results_2.json` | JSON | 33.8 KB | Resultados búsqueda 2: sesgo de raza en IA veterinaria |
| `search_results_3.json` | JSON | 11.9 KB | Resultados búsqueda 3: chatbots veterinarios |
| `search_results_4.json` | JSON | 9.6 KB | Resultados búsqueda 4: ChatGPT + veterinaria |
| `search_results_5.json` | JSON | 0.3 KB | Resultados búsqueda 5: wearables y monitoreo |

### 📊 Distribución por Funcionalidad
| Categoría | Archivos | Tamaño total | % |
|-----------|----------|-------------|---|
| Frontend (HTML/CSS/JS) | 1 | 66.4 KB | ~30% |
| Scripts (Python) | 1 | 61.8 KB | ~28% |
| Documentación (Markdown) | 3 | 19.2 KB | ~9% |
| Datos de investigación (JSON) | 7 | 84.0 KB | ~38% |
| **Total** | **12** | **~231.4 KB** | **100%** |

### 📁 Estructura del Proyecto
```
HERMES GRUPO 2 WP/
├── screens/
│   ├── vet_active_pro_wireframes.html  ← Wireframes principales (21 pantallas)
│   ├── reporte_sesgo.md                ← Reporte de sesgos
│   ├── clasificacion_archivos.md       ← Clasificación de archivos
│   └── mini_reporte.md                 ← Mini-reporte consolidado
├── generate_wireframes.py              ← Script generador de wireframes
├── search_results_*.json               ← Búsquedas web (5 archivos)
├── extracted_articles.json             ← Artículos extraídos
└── breed_pain_bias.json                ← Artículo clave raza-dolor
```

> **Nota:** No existen carpetas de imágenes/screenshots (.png, .jpg). Los wireframes son HTML interactivo que se renderiza en el navegador.

---

## 3. Implicaciones para el Diseño de Vet Active Pro

### Tabla de Riesgos y Mitigaciones

| # | Riesgo | Fuente | Pantalla(s) afectada(s) | Mitigación propuesta |
|---|--------|--------|------------------------|----------------------|
| 1 | **Sesgo de raza en evaluación de dolor** | Caso 1 (Caddiell et al., Frontiers 2025) | Triaje Digital, Triaje Resultado | Triaje basado en **síntomas observables** (respiración, mucosas, consciencia, comportamiento), sin campos de raza como variable de decisión |
| 2 | **Sobre-triaje de LLMs en emergencias** | Caso 2 (Wong et al., Vet Record 2026) | Triaje Digital, Alerta Emergencia Nivel 1 | **No usar LLM general para triaje sin ajuste de umbrales**. Validar toda clasificación Nivel 1 con veterinario humano |
| 3 | **Subestimación de gravedad en chatbots (speciesismo)** | Caso 3 (Hagendorff et al.) | Triaje Digital (WhatsApp/Chat) | **Human-in-the-loop**: toda clasificación de triaje validada por veterinario antes de comunicar al tutor |
| 4 | **Diagnósticos incorrectos de LLM** | Hallazgo adicional (PMC 2024) | Triaje Digital, Alerta Emergencia Nivel 1 | **No usar IA para diagnóstico final**; solo para triaje inicial con escalamiento obligatorio a profesional |
| 5 | **Falsas tranquilizaciones a tutores** | Hallazgo adicional (PMC 2024) | Triaje Resultado (semáforo), Alerta Emergencia | El semáforo 🔴/🟡/🟢 debe ser **indicativo, no conclusivo**; incluir disclaimer y botón de "consultar veterinario ahora" |
| 6 | **Datos de entrenamiento desbalanceados** | Caso 2 + Caso 3 | Todas las pantallas con IA | Implementar política de **datos representativos** y revisión periódica de equidad algorítmica |
| 7 | **Falta de transparencia algorítmica** | Hallazgo adicional (Brundage, Frontiers 2026) | Todas | Reportar distribución demográfica de datos y métricas de sesgo; evaluación independiente del algoritmo |

### Consideraciones de diseño transversales

- **Raza como dato demográfico, no como variable de triaje:** Se puede incluir raza en el perfil de la mascota (Mis Mascotas) para contexto clínico, pero **nunca como input en el algoritmo de triaje**.
- **Equidad en notificaciones:** El sistema de alertas (Nivel 1/2/3) debe funcionar con la misma sensibilidad para todas las razas y tamaños, evitando que razas miniaturas reciban menor prioridad por sesgo histórico en datos.
- **Bot de WhatsApp/Chat con supervisión veterinaria:** El chatbot de triaje debe tener un **umbral de escepticismo bajo**: ante cualquier ambigüedad, escalar a colaborador humano (pantalla Triaje Recepción).
- **Transparencia al tutor:** En cada resultado de triaje (pantalla Triaje Resultado), mostrar brevemente qué criterios se evaluaron (síntomas observados) para generar confianza y evitar la "falsa tranquilización".
- **Validación externa obligatoria:** Cualquier modelo de IA usado en Vet Active Pro debe pasar por validación externa con datasets diversos antes del despliegue (Brundage, Frontiers 2026).
- **Sensibilidad ajustada por nivel:** El sobre-triaje de ChatGPT implica que el umbral para Nivel 1 debe ser más estricto que el de un LLM genérico. Considerar un **doble filtro**: LLM para detección inicial + algoritmo de umbral calibrado + validación humana para Nivel 1.

---

*Generado: Septiembre 2026 | Proyecto Vet Active Pro — Diplomado AI*
