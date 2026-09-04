# Guía visual — Clase 30 (Hermes Agent Desktop)

## Antes de la clase

- [ ] Computador con Mac, Windows o Linux (idealmente al menos 8GB RAM).
- [ ] Cuenta en el canal donde quieres conectar Hermes (Slack, Discord, Telegram).

## Instalación

- **Mac / Windows**: [hermes-agent.nousresearch.com/desktop](https://hermes-agent.nousresearch.com/desktop) → descargar → instalar.
- **Linux / cualquier**: `curl -fsSL https://hermes-agent.nousresearch.com/install.sh | bash` → luego `hermes desktop`.

## Setup inicial

2. Elegir workspace (carpeta local).
2. Activar memoria persistente.

## Probar memoria

1. Cerrar la app después de contarle algo.
2. Volver a abrir.
3. Preguntarle sobre lo dicho ayer.

## Conectar canal externo (Slack, Discord, Telegram)

- Menú Settings → Integrations.
- Seguir wizard: autorizar app en el canal.
- Probar: escribirle a Hermes desde el canal.

## Delegar con subagentes

Prompt de ejemplo:

```
Hacé 3 cosas en paralelo con subagentes:
1. Buscar X
2. Analizar Y
3. Generar reporte con Z
```

## Programar tarea recurrente

```
Cada viernes 17:00, hacé [tarea]. Guarda como [nombre_archivo].
```

## Subir al repo

- `docs/hermes_setup.md`
- `docs/hermes_casos_uso.md`
- Screenshots.
