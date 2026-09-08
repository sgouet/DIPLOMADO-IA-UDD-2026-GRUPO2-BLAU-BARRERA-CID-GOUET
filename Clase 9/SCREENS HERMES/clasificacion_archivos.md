# 📂 Clasificación de Archivos del Proyecto Vet Active Pro

## 🎨 Diseño y Wireframes (Frontend)
| Archivo | Tipo | Tamaño | Descripción |
|---------|------|--------|-------------|
| `screens/vet_active_pro_wireframes.html` | HTML/CSS/JS | 66.4 KB | Wireframes interactivos (21 pantallas), responsive mobile |

## 🔧 Scripts y Herramientas
| Archivo | Tipo | Tamaño | Descripción |
|---------|------|--------|-------------|
| `generate_wireframes.py` | Python script | 61.8 KB | Generador de wireframes HTML |

## 📋 Documentación y Reportes (Markdown)
| Archivo | Tipo | Tamaño | Descripción |
|---------|------|--------|-------------|
| `screens/reporte_sesgo.md` | Markdown | 6.7 KB | Reporte de sesgo en apps veterinarias (3 casos + hallazgo LLM) |
| `screens/clasificacion_archivos.md` | Markdown | 2.1 KB | Clasificación de archivos por categoría |
| `screens/mini_reporte.md` | Markdown | 9.2 KB | Mini-reporte consolidado (investigación + clasificación + implicaciones) |

## 🔍 Datos de Investigación (JSON)
| Archivo | Tipo | Tamaño | Descripción |
|---------|------|--------|-------------|
| `breed_pain_bias.json` | JSON | 5.7 KB | Artículo: sesgo de raza en dolor canino (Frontiers 2025) |
| `extracted_articles.json` | JSON | 11.1 KB | Artículos extraídos (Frontiers, PetMonitor, Springer) |
| `search_results_1.json` | JSON | 11.6 KB | Resultados búsqueda 1: sesgo general en IA veterinaria |
| `search_results_2.json` | JSON | 33.8 KB | Resultados búsqueda 2: sesgo de raza en IA veterinaria |
| `search_results_3.json` | JSON | 11.9 KB | Resultados búsqueda 3: chatbots veterinarios |
| `search_results_4.json` | JSON | 9.6 KB | Resultados búsqueda 4: ChatGPT + veterinaria |
| `search_results_5.json` | JSON | 0.3 KB | Resultados búsqueda 5: wearables y monitoreo |

---

## 📊 Distribución por Funcionalidad
| Categoría | Archivos | Tamaño total | % |
|-----------|----------|-------------|---|
| Frontend (HTML/CSS/JS) | 1 | 66.4 KB | ~45% |
| Scripts (Python) | 1 | 61.8 KB | ~42% |
| Documentación (Markdown) | 3 | 18.0 KB | ~12% |
| Datos de investigación (JSON) | 7 | 70.4 KB | ~1% |
| **Total** | **12** | **~216.6 KB** | **100%** |

## 📁 Estructura del Proyecto
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

## 📝 Notas
- El archivo `generate_wireframes.py` está en la raíz, **no** dentro de `screens/`
- El script genera el HTML en la carpeta `screens/` cuando se ejecuta
- No existen carpetas de imágenes/screenshots (.png, .jpg); los wireframes son HTML interactivo
- Los JSON de búsqueda contienen resultados crudos de búsquedas web con web_search
