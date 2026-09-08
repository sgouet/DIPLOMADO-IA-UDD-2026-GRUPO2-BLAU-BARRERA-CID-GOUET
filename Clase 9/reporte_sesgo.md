# 🐾 Vet Active Pro — Reporte de Sesgo en Apps Veterinarias (2024–2026)

## Contexto

Este documento presenta los **3 casos más citados de sesgo en aplicaciones veterinarias** identificados durante la investigación, con el objetivo de informar el diseño de *Vet Active Pro* y anticipar riesgos éticos y técnicos que deben mitigarse desde el inicio del desarrollo.

---

## Caso 1: Sesgo de raza en la evaluación del dolor veterinario

**Fuente:** *"Tailoring treatment: dog breed status influences pain assessment and treatment in dogs"* — Frontiers in Pain Research (2025)  
**DOI:** [10.3389/fpain.2025.1589082](https://doi.org/10.3389/fpain.2025.1589082)

### Qué ocurrió
Un estudio de la Universidad de NC State evaluó si las creencias específicas de raza que los veterinarios tienen sobre la sensibilidad al dolor influyen en el tratamiento real. Encuestaron a **+1,000 veterinarios** sobre 28 razas caninas y encontraron que:

- Los veterinarios asignan **scores de dolor significativamente diferentes** según la raza, sin base científica.
- Razas consideradas "menos sensibles al dolor" (como los Greyhounds o Dobermans) reciben **menos analgesia** en la práctica clínica.
- Esta creencia es **consistente entre profesionales**, lo que indica un sesgo institucionalizado, no individual.

### Relevancia para Vet Active Pro
- El triaje digital de la app **no debe usar raza como variable de decisión** en la evaluación de urgencia.
- Un algoritmo que incorpore raza en la clasificación de dolor podría replicar este sesgo en la app.
- **Recomendación:** Diseñar el triaje basado en **síntomas observables** (respiración, consciencia, mucosas, comportamiento), no en atributos raciales del paciente.

---

## Caso 2: Sesgo algorítmico en wearables y monitoreo veterinario

**Fuente:** *"Pet Technology Companies vs Legacy Vets: Quiet Failure?"* — PetMonitor (Julio 2025)  
**URL:** [petmonitor.help](https://petmonitor.help/pet-technology-companies-vs-legacy-vets-quiet-fail)

### Qué ocurrió
- Los monitores de frecuencia cardíaca con IA de empresas como **Fi** alcanzaron solo un **82% de precisión** vs. telemetría veterinaria de grado clínico en 2025.
- El **18% de los casos** presentan alarmas fallidas o advertencias perdidas, lo que puede retrasar intervenciones que salvan vidas.
- **Algorithmic bias** en plataformas cloud: los servicios priorizan datos de razas con frecuencias cardíacas naturalmente altas (Labrador Retrievers, Pastores Alemanes) mientras **ignoran razas miniaturas** que representan el 4% de la población canina.
- El resultado: los wearables y algoritmos entrenados con datos desbalanceados producen **alertas sesgadas hacia ciertas razas**.

### Relevancia para Vet Active Pro
- Cualquier componente de monitoreo remoto o sensor de la app debe asegurar **datos de entrenamiento representativos** de todas las razas y tallas.
- Si se integra funcionalidad de monitoreo, el sistema debe ser calibrado con conjuntos de datos **equilibrados** por tamaño, edad y raza.
- **Recomendación:** Auditoría de sesgo algorítmico antes del lanzamiento de cualquier feature predictivo.

---

## Caso 3: Especiesismo en IA — Sesgo contra animales en modelos de lenguaje y visión

**Fuente:** *"Speciesist bias in AI: how AI applications perpetuate discrimination and unfair outcomes against animals"* — Hagendorff et al. / AI and Ethics (Springer Nature, 2022, relevancia 2024–2026)  
**DOI:** [10.1007/s43681-022-00199-9](https://link.springer.com/article/10.1007/s43681-022-00199-9)  
**Autores:** Thilo Hagendorff, Leonie N. Bossert, Yip Fai Tse, Peter Singer

### Qué ocurrió
- Primer estudio sistemático sobre **speciesist bias** en IA: discriminación contra animales en algoritmos de visión computacional, *word embeddings* y modelos de lenguaje.
- Los modelos de IA de uso veterinario (como herramientas de triage por chat) están entrenados en datasets donde los patrones especiesistas están **solidificados**.
- Ejemplos encontrados:
  - **Visión por computadora:** Fotos de perros clasificadas como "small mammal" en lugar de por raza.
  - **Procesamiento de lenguaje:** Modelos que minimizan la gravedad de síntomas en descripciones de mascotas vs. pacientes humanos.
  - **Embeddings:** Asociaciones que vinculan "perro" con conceptos de menor complejidad médica que "humano".
- Los autores argumentan que los animales importan moralmente y que discriminar contra ellos es **poco ético** y debe abordarse en la investigación de IA justa.

### Relevancia para Vet Active Pro
- El **bot de triaje por WhatsApp/Chat** debe ser diseñado para no subestimar la gravedad de síntomas en mascotas.
- Cualquier modelo de lenguaje usado para evaluar síntomas debe ser entrenado o ajustado con **datos veterinarios específicos**, no generalistas de salud humana.
- **Recomendación:** Implementar un sistema de **human-in-the-loop** donde toda clasificación de triaje sea validada por un veterinario antes de comunicarse al tutor.

---

## 📋 Hallazgo adicional: Sesgo diagnóstico en LLMs veterinarios

**Fuente:** *"ChatGPT in Veterinary Medicine: A Practical Guidance"* — PMC (2024)  
**URL:** [pmc.ncbi.nlm.nih.gov](https://pmc.ncbi.nlm.nih.gov/articles/PMC11192069)

- GPT-4 coincidió con el diagnóstico final en solo el **39% de los casos**.
- El **33%** incluyó el diagnóstico dentro del *top differential*, pero con frecuencia omitió condiciones críticas.
- Los chatbots veterinarios actuales tienden a **"falsamente tranquilizar"** (dar "this can wait" a animales que en realidad están gravemente enfermos).

---

## ⚠️ Implicaciones directas para Vet Active Pro

| Riesgo | Fuente | Mitigación propuesta |
|--------|--------|----------------------|
| Sesgo de raza en evaluación de dolor | Caso 1 | Triaje basado en síntomas observables, no en raza |
| Alertas falsas/negadas por raza | Caso 2 | Datos de entrenamiento equilibrados por tamaño/raza |
| Subestimación de gravedad en chatbots | Caso 3 | Human-in-the-loop para toda clasificación de triaje |
| Diagnósticos incorrectos de LLM | Hallazgo adicional | No usar IA para diagnóstico final, solo para triaje inicial |

---

## 📁 Archivos de esta investigación

- `screens/vet_active_pro_wireframes.html` — Wireframes y flujos de la app (21 pantallas)
- `search_results_*.json` — Resultados crudos de búsquedas web
- `extracted_articles.json` — Contenido extraído de artículos clave
- `breed_pain_bias.json` — Artículo sobre sesgo de raza en dolor
- `screens/reporte_sesgo.md` — Este reporte

---

*Generado: Septiembre 2026 | Proyecto Vet Active Pro — Diplomado AI*
