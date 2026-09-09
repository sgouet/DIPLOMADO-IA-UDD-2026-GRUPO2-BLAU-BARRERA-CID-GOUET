# Ficha de proyecto — Vet Active Pro

## 1. Vet Active Pro
## 2. Problema 
Las recepcionistas y coordinadoras clínicas pierden más de 3 horas diarias en tareas repetitivas de confirmación de citas y agendamiento manual por WhatsApp, lo que genera alta fricción con los tutores y fugas financieras por inasistencias (no-shows). Además, la sobrecarga administrativa durante momentos de alta tensión provoca descuadres de caja y desatención emocional de los clientes presenciales al momento de gestionar emergencias o imprevistos médicos

## 3. Usuario / cliente objetivo
Usuario principal: Recepcionista y coordinadora de clínica veterinaria.
Necesidad: Requiere agilizar la confirmación de citas, clasificar urgencias de forma empática y realizar cobros/arqueos de caja sin perder tiempo ni desatender emocionalmente al tutor presencial.
Situación actual: Actualmente realiza procesos manuales en WhatsApp/llamadas, transcripción manual de datos y cuadratura de caja bajo alta saturación y estrés operativo

## 4. Tipo de modelo que vas a necesitar
Generativo y analítico. 
Justificación: Se requiere un componente generativo para la elaboración de respuestas empáticas y personalizadas hacia los tutores por WhatsApp y pantallas, combinado con un componente analítico para clasificar el nivel de urgencia del triage (verde, amarillo, rojo) y aplicar algoritmos de reacomodo dinámico en la "Agenda Líquida" y cuadratura contable

## 5. Modelos candidatos (2-3 concretos)
Gemini / Google AI Studio (e.g. Gemini 1.5 Pro / Flash): Seleccionado como el motor orquestador hiper-empático mediante razonamiento en 3 capas (Análisis de situación/empatía, gestión de agenda dinámica y validación contable).
GPT-4o: Candidato para procesamiento analítico multimodal y asistencia en decisiones de agenda y triage rápido.
Claude 3.5 Sonnet / Llama 3 (vía Hugging Face): Candidato alternativo para la clasificación precisa de reglas de negocio en la caja y el manejo estructurado de la comunicación de contingencia
Gemini - Nano Banana: Generación de imágenes.

## 6. Roadmap del proyecto (se completa clase a clase)
- [ ] Clase 23 — Datasheet del dataset (`docs/datasheet_v1.md`)
- [ ] Clase 24 — Hallazgos NotebookLM (`docs/hallazgos_notebooklm.md`)
- [ ] Clase 25 — System prompt (`docs/system_prompt_v3.md`)
- [ ] Clase 26 — Modelos HF candidatos (`docs/modelos_hf_candidatos.md`)
- [ ] Clase 27 — Sistema visual (`docs/sistema_visual.md`)
- [ ] Clase 28 — Arquitectura del agente (`docs/arquitectura_agente.md`)
- [ ] Clase 29 — Video generativo (`docs/video_generativo.md`)
- [ ] Clase 30 — Casos de uso Hermes (`docs/hermes_casos_uso.md`)
- [ ] Clase 31 — Antigravity Loop + cierre (`docs/antigravity_loop.md`)

## 7. Notas para Mauricio (Unidad 4)
Qué necesita saber quien reciba este proyecto en la próxima unidad:

Orquestación Humano x Máquina (Synergy): La aplicación no busca reemplazar a la recepcionista, sino liberar un 40% de su jornada laboral automatizando el 80% del flujo transaccional repetitivo para potenciar su "Human Edge" (contención emocional y atención personalizada al tutor).
Motor en 3 Capas: El sistema opera bajo un pensamiento lateral orquestado: Capa 1 (Empatía & Lectura de sentimiento), Capa 2 (Triage & Reacomodo de Agenda Líquida), y Capa 3 (Precisión Contable sin descuadres de caja).
Cierre en Bucle (Closed-Loop): Probado y validado frente a escenarios límite (ej. pug en paro respiratorio, tutor agresivo y descalce contable), demostrando latencias <45ms y respuesta empática validada


