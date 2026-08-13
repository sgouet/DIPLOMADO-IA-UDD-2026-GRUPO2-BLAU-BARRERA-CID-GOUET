# Guía visual — Clase 22

**Diplomado IA UDD 2026 · Prof. Darío Osorio**

Esta guía es la versión rápida para que la tengas al lado durante la clase online.

## Antes de la clase

- [ ] Tener cuenta Google activa.
- [ ] Zoom/Teams instalado y funcionando.
- [ ] Chrome o Firefox actualizados.

## Durante la clase — parte práctica

### Cómo abrir Google Colab

1. Abrir Chrome → ir a `colab.research.google.com`.
2. Iniciar sesión con tu cuenta Google.
3. Verás la ventana de bienvenida. Cerrar el diálogo si aparece.
4. Ir a `Archivo → Nuevo cuaderno` (o abrir el que se comparta en el chat).

### Cómo se ejecuta una celda de código

- Poner el cursor en la celda.
- Presionar el botón "Play" a la izquierda (o `Shift + Enter`).
- La primera vez que ejecutes una celda, Colab te preguntará si confías en el cuaderno → decir que sí.
- Si aparece "conectando a runtime" — espera unos segundos, es normal.

### Si algo falla

- **Error en `!pip install`**: reintenta la celda, suele ser conexión.
- **Runtime desconectado**: `Entorno de ejecución → Reiniciar` y volver a ejecutar celda por celda.
- **Nada carga**: pedir ayuda en el chat de la clase. No se queda peleando con Colab en soledad.

## GitHub para el diplomado — configuración inicial

### Por qué necesitas GitHub

Todo lo que produzcas en el semestre va a vivir en un repositorio público de GitHub: notebooks, documentos, capturas, bitácora. Es la manera estándar de compartir trabajo profesional.

### Crear cuenta 

1. Ir a [github.com/signup](https://github.com/signup).
2. Usar tu correo (puede ser el UDD o personal).
3. Elegir nombre de usuario descriptivo (ej: `mariapaz-udd`).
4. Verificar correo.

### Crear el repositorio del diplomado 

1. Al iniciar sesión, click en el botón verde `Create repository` (o `+` arriba a la derecha → `New repository`).
2. Nombre: `diplomado-ia-udd-2026-tuapellido`.
3. Descripción: `Diplomado IA Aplicada al Diseño · UDD 2026 · Unidad 3`.
4. Público (importante).
5. Marcar `Add a README file`.
6. Marcar `Add .gitignore` → template `Python`.
7. Click en `Create repository`.

### Subir tu primera evidencia 

Al final de la clase, subirás tu ficha del proyecto y una captura del ejercicio de embeddings:

1. Completar `Clase_22_ficha_proyecto_template.md` y renombrarlo `ficha_proyecto.md`.
2. En tu repositorio, crear la carpeta `docs/` si no existe, y dentro click en `Add file → Upload files`.
3. Arrastrar `ficha_proyecto.md` + la captura del ejercicio de embeddings.
4. En "Commit changes" escribir: `Clase 22 - ficha proyecto y captura embeddings`.
5. Click en `Commit changes`.

Listo. Tu trabajo está guardado, versionado y compartible por URL.


