# Guía visual — Clase 31 (Antigravity + Cierre)

## Antes de la clase
- [ ] Cuenta Google.
- [ ] Repositorio del diplomado con todos los avances de las 9 clases anteriores.
- [ ] Una tarea real y pendiente de tu proyecto para experimentar en el Ejercicio 4.

## Instalar Antigravity
- [antigravity.google](https://antigravity.google) → descargar → instalar.
- Iniciar sesión con Google.
- El free tier alcanza.

## Los dos modos
- **Editor View**: IDE con IA que autocompleta. Sincrónico.
- **Manager Surface**: dashboard donde se crean múltiples agentes en paralelo. Asíncrono.

## El sistema Loop
```
Research → Plan → Execute → Verify → Fix → (repite)
```
- El agente propone un `implementation_plan.md`.
- Tú apruebas con `Proceed`.
- El agente ejecuta hasta terminar (o hasta un checkpoint).

## Esta clase no tiene presentación final
Es una clase de **ejercicios guiados y experimentación** con Antigravity.

### Ejercicio 1 — Instalar Antigravity (15 min)
- [ ] Descargar e instalar según tu sistema operativo.
- [ ] Iniciar sesión con Google.

### Ejercicio 2 — Primer proyecto en Editor View (15 min)
- [ ] Crear una carpeta nueva con un archivo `hallazgos.md` (3-4 hallazgos reales de tu proyecto).
- [ ] Abrir la carpeta en Antigravity y pedirle un HTML simple, minimalista y responsive con esos hallazgos.
- [ ] Observar el Loop: Research → Plan → Execute → Verify.
- [ ] Abrir el HTML resultante y revisarlo.
- [ ] Pedir un segundo cambio de estilo (colores, tipografía) y ver cómo el agente vuelve a correr el Loop sobre lo ya hecho.

### Ejercicio 3 — Documentar el uso (10 min)
- [ ] Crear `docs/antigravity_loop.md`.
- [ ] Resumir en 3-5 líneas la tarea y el resultado.
- [ ] Anotar cuántas vueltas de Loop necesitó.
- [ ] Guardar 2-3 capturas (prompt, plan, resultado) en `docs/capturas/`.
- [ ] Commit con mensaje descriptivo.

### Ejercicio 4 — Experimentación libre con tu proyecto (30 min)
Elige una tarea real de tu proyecto. Si necesitas ideas:
- Visualizar datos o hallazgos en un gráfico.
- Aplicar una paleta de colores/tipografía a todo un conjunto de archivos.
- Crear un formulario o prototipo funcional simple.
- Reescribir copy de una página en otro tono.
- Generar un índice que resuma una carpeta del repo.

Aplícale el Loop completo (Editor o Manager) y anota en tu bitácora qué funcionó, qué no, y dónde tuviste que intervenir tú.

### Ejercicio 5 — Opcional: Modo Manager (20 min)
Crear 2-3 agentes en paralelo con tareas distintas y observar el dashboard mientras trabajan.

## Ejercicio 6 — Romper algo a propósito
Sobre algo que ya hiciste (Ejercicio 2 o 4): pídele a Antigravity un cambio que sepas que va a generar un error, deja correr el Loop completo, y anota cuántas vueltas de Fix necesitó y si cambió de estrategia.

## Después de la clase
Seguir documentando en tu bitácora lo que fuiste probando con Antigravity a lo largo de la unidad.
