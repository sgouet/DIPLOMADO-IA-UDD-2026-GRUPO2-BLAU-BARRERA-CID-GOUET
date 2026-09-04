# Clase 30 — Hermes Agent Desktop: un agente en tu computador

**Diplomado IA Aplicada al Diseño · UDD · 2026**
Profesor: Darío Osorio
Fecha: Jueves 10 de septiembre de 2026 · 18:30–21:00 hrs
Modalidad: **online sincrónico** · Unidad 3 · Sesión 9 de 10 · **Propuesta D**

---

## Apertura

**Hermes** (de Nous Research) es el primer agente open source (MIT) que se instala en tu computador como aplicación nativa. No corre en el navegador — vive en tu Mac, Windows o Linux, con memoria persistente, conexión a canales (Slack, Discord, WhatsApp, Telegram, email), subagentes aislados y automatización programada.

Para un diseñador, Hermes representa algo nuevo: un asistente que **no depende de una empresa cerrada** y que puede integrarse a tu flujo de trabajo diario. Esta clase es hands-on: instalar, configurar, poner en funcionamiento.

## Resultado de aprendizaje

Al finalizar la clase el estudiante podrá:

1. **Instalar Hermes Agent Desktop** en su computador.
2. **Configurar memoria persistente** y al menos una conexión (canal externo o skill).
3. **Delegar una tarea recurrente** al agente y verificar su ejecución autónoma.
4. **Comparar** un agente local (Hermes) con uno cerrado (Claude/ChatGPT).

## Glosario clave

| Término | Definición |
| --------- | ------------ |
| **Hermes Agent** | Agente open source (MIT) de Nous Research. Corre localmente. |
| **Memoria persistente** | El agente recuerda proyectos y decisiones entre sesiones (no se pierde el contexto). |
| **Skill** | Habilidad instalable en Hermes (buscar web, procesar imágenes, etc.). |
| **Subagent** | Agente aislado con conversación, terminal y scripts propios. |
| **Backend de ejecución** | Dónde corre Hermes: local, Docker, SSH remoto, Singularity, Modal. |
| **Sandbox** | Entorno aislado donde el agente ejecuta código sin tocar el sistema. |
| **Portal de Nous** | Sitio para gestión de plan, créditos y suscripción. |

---

## Parte 1 — Materia (30 min)

### Bloque 1 (10 min): Qué es Hermes y por qué importa

Hermes Agent es lanzado por **Nous Research** — un colectivo/empresa de investigación open source, conocido por sus modelos LLM (Nous Hermes 2, Hermes 3) y ahora por este agente. Repositorio oficial: [github.com/NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent).

**Diferencias clave con Claude / ChatGPT**:

| Aspecto | Claude / ChatGPT | Hermes Desktop |
| --------- | ------------------ | ----------------- |
| Dónde corre | Servidores de la empresa | Tu computador |
| Licencia | Cerrada | MIT (open source) |
| Datos | Viajan a la nube | Se quedan localmente (por default) |
| Memoria | Solo dentro del hilo | Persistente entre sesiones |
| Canales | Web / apps oficiales | Slack, Discord, WhatsApp, Telegram, email, CLI |
| Subagentes | Limitado | Ilimitado |
| Costo | Suscripción mensual | Gratis (paga solo el compute LLM que use) |
| Complejidad de setup | Cero | Media (instalación local) |

Para diseño profesional donde los datos importan, Hermes es una alternativa relevante.

### Bloque 2 (10 min): Features principales

Del sitio oficial:

1. **Conectar (Vive en todas partes)**: Telegram, Discord, Slack, WhatsApp, Signal, Email, CLI. Un agente, una memoria, todas las superficies.

2. **Recordar (Memoria persistente)**: Aprende tus proyectos, genera skills automáticamente, recuerda cómo resolvió un problema antes.

3. **Programar (Automatización)**: Programa informes, backups, resúmenes en lenguaje natural. Se ejecutan sin supervisión.

4. **Delegar (Tareas multiplicadas)**: Subagentes aislados con sus propias conversaciones, terminales y scripts RPC.

5. **Buscar (Navega la web)**: Búsqueda web, automatización del navegador, visión, generación de imágenes, voz, razonamiento multi-modelo.

6. **Experimentar (Entorno aislado)**: Cinco backends de ejecución: local, Docker, SSH, Singularity, Modal.

### Bloque 3 (10 min): Casos de uso para diseño

- **Asistente de research permanente**: cargás tus proyectos una vez, y Hermes los recuerda semanas después.
- **Bot de tu propio Discord de equipo**: responde consultas sobre el proyecto sin exponer datos a APIs externas.
- **Automatización de reportes**: cada viernes, genera un resumen de progreso semanal.
- **Backup y organización de archivos**: agente que revisa tu carpeta de proyecto, sugiere reorganizaciones.
- **Reemplazo parcial de suscripciones**: donde antes usabas ChatGPT/Claude para tareas repetitivas, Hermes puede hacerlo local.

**Consideración**: Hermes no reemplaza a Claude/ChatGPT para todo. Está optimizado para automatización y workflows agénticos, no para conversación casual pulida.

---

## Parte 2 — Ejercicios prácticos (90 min)

**Herramienta**: [hermes-ai.net/es/desktop](https://hermes-ai.net/es/desktop/)

### Ejercicio 1 — Instalación (20 min)

**Mac**:

1. Ir a [hermes-agent.nousresearch.com/desktop](https://hermes-agent.nousresearch.com/desktop).
2. Descargar el DMG para macOS.
3. Arrastrar a Applications. Abrir.
4. Aceptar permisos.

**Windows**:

1. Descargar el installer.
2. Ejecutar. Aceptar permisos.

**Linux / cualquier sistema con terminal**:

```bash
curl -fsSL https://hermes-agent.nousresearch.com/install.sh | bash
hermes desktop
```

**Windows PowerShell**:

```
iex (irm https://hermes-agent.nousresearch.com/install.ps1)
```

### Ejercicio 2 — Setup inicial (15 min)

1. Al abrir, Hermes pide configurar el modelo LLM que usará por debajo (puedes conectar Claude API, OpenAI API, o modelo local con Ollama).
2. Elegir carpeta de trabajo (por default: `~/hermes-workspace`).
3. Activar memoria persistente.

### Ejercicio 3 — Primera conversación y memoria (20 min)

1. Escribile: `Te voy a contar sobre mi proyecto del diplomado. El problema que estoy trabajando es X. Los usuarios son Y. Ya hicimos investigación con NotebookLM y encontramos [3 hallazgos].`
2. Cerrar Hermes.
3. Volver a abrirlo.
4. Preguntarle: `¿Qué te conté ayer sobre mi proyecto?`
5. Debe recordar. Si no, revisar configuración de memoria.

### Ejercicio 4 — Delegar una tarea con subagentes (20 min)

Prompt de ejemplo:

```
Necesito que hagas 3 cosas en paralelo:
1. Busca en la web los 3 casos más citados de sesgo en apps
   bancarias 2024-2026.
2. Analiza mi carpeta de screenshots y clasificalos por tipo.
3. Genera un mini-reporte con lo encontrado.

Puedes usar subagentes.
```

Hermes descompone la tarea, crea subagentes especializados, ejecuta en paralelo, sintetiza. Observa cómo trabaja.

### Ejercicio 5 — Programar tarea recurrente (10 min)

```
Cada viernes a las 17:00, revisa mi carpeta de proyecto
y generame un resumen de lo que se agregó esa semana.
Guardalo como `weekly_report_YYYY-MM-DD.md`.
```

Hermes programa la tarea. Se ejecutará automáticamente sin que abras la app.

### Ejercicio 6 — Documentar el flujo (5 min)

En el repo:

- `docs/hermes_setup.md` — cómo lo instalaste y configuraste.
- `docs/hermes_casos_uso.md` — los 2-3 casos que probaste.
- Screenshots del agente trabajando.

---

## Parte 3 — Revisiones en salas (30 min)

**Formato**: salas breakout de 3-4 estudiantes.

### Consigna

Cada estudiante (5-7 min):

1. Muestra Hermes corriendo en su máquina.
2. Ejecuta un caso de uso relevante en vivo.
3. Discute: ¿lo vas a seguir usando después del curso? ¿Por qué sí o no?

### Cierre en plenario (5 min)

- ¿Quién pudo instalarlo sin dramas?
- ¿A quién le costó y por qué?
- Comparativa: ¿Hermes reemplaza tu uso de ChatGPT/Claude, o es complementario?

---

## Trabajo autónomo (~2 h)

1. **Programar 2 tareas recurrentes** útiles para tu proyecto (30 min).
2. **Escribir reflexión** en la bitácora: ¿qué gana un diseñador con un agente open source y local vs. depender de APIs cerradas? (30 min).

---

## Conexión con el entregable de posta

Al cerrar tienes:

- Hermes instalado y funcionando.
- Al menos 1 caso de uso agéntico documentado.
- Comparativa práctica local vs. cloud.

---

## Recursos útiles

- [Documentación oficial Hermes](https://hermes-agent.nousresearch.com/docs/) — quickstart, installation, features.
- [GitHub Nous Research](https://github.com/NousResearch/hermes-agent) — código, issues, comunidad.
- [Discord de Nous Research](https://discord.gg/NousResearch) — comunidad muy activa.
- [Agent Skills Hub](https://agentskills.io/) — catálogo de skills instalables.

---

## Referencias culturales y casos LATAM

- **[Nous Research](https://nousresearch.com)** — colectivo independiente que ha democratizado modelos y agentes open source. Casos donde su trabajo enfrentó a las grandes empresas.
- **Soberanía tecnológica**: usar Hermes en un proyecto del Estado chileno vs. contratar OpenAI/Anthropic. Discutir consecuencias operativas y políticas.
- **Comparativa 2026**: Hermes vs. [OpenHands](https://github.com/OpenHands/OpenHands) (ex OpenDevin, open source) vs. [Cline](https://cline.bot) / [Roo Code](https://github.com/RooCodeInc/Roo-Code) vs. [Aider](https://aider.chat) — panorama del ecosistema open agentic.

---

## Pregunta abierta de cierre

> Un agente local, open source, con licencia MIT, que puede reemplazar buena parte de lo que haces con ChatGPT — pero requiere que lo instales, configures y mantengas. ¿Qué te ofrece que las herramientas cerradas no? ¿Y qué te cuesta a cambio?
