# Análisis de la Deforestación en la Selva Amazónica

## Proyecto Completado 

Este repositorio contiene el análisis completo de la deforestación en el Bosque Nacional Jamanxim (2000-2019) utilizando técnicas de segmentación de imágenes.

## Estructura del Proyecto

```
.
├── images/                          # 20 imágenes satelitales extraídas (2000-2019)
├── results/                         # Resultados del procesamiento
│   ├── preprocessed/               # Imágenes preprocesadas
│   ├── segmented_otsu/             # Segmentación Otsu
│   ├── segmented_adaptive/         # Segmentación adaptativa
│   ├── segmented_lab/              # Segmentación Lab
│   ├── segmented_hsv/              # Segmentación HSV
│   ├── quantification_results.csv  # Datos cuantitativos
│   └── analysis/                    # Visualizaciones (9 gráficos)
├── scripts/                         # Scripts de procesamiento
│   ├── extract_frames.py           # Extracción de frames
│   ├── preprocessing.py            # Preprocesamiento
│   ├── segmentation.py             # Segmentación (4 métodos)
│   ├── quantification.py           # Cuantificación de áreas
│   └── analysis.py                 # Generación de visualizaciones
├── informe_deforestacion.md        # Informe científico (Markdown)
└── convert_to_pdf.sh               # Script para generar PDF
```

## Resultados Principales

### Cuantificación por Método

| Método | Área Promedio (km²) | Cambio 2000→2019 |
|--------|---------------------|------------------|
| Otsu | 4029.03 | +153.6% |
| Adaptativo | 19975.98 | +1.9% |
| Lab | 4.79 | 0.0% |
| HSV | 1613.17 | +823.8% |

**Método recomendado:** Otsu (más robusto y consistente)

### Visualizaciones Generadas

- `evolucion_temporal.png` - Evolución temporal 2000-2019
- `comparacion_metodos.png` - Comparación estadística
- `comparacion_2000_2019.png` - Años extremos
- `visual_comparison_YYYY.png` - Comparaciones visuales (5 años clave)

## Requisitos del Sistema

### Python
```bash
python3 --version  # >= 3.8
```

### Bibliotecas Python
```bash
pip3 install opencv-python numpy pandas matplotlib pillow scikit-image
```

### Para Generar PDF

**Opción 1: Pandoc (Recomendado)**
```bash
brew install pandoc
brew install --cask mactex-no-gui  # Para LaTeX/XeLaTeX
```

**Opción 2: WeasyPrint (Alternativo)**
```bash
pip3 install weasyprint markdown
```

## Uso

### 1. Ejecutar Pipeline Completo (Ya Ejecutado)

```bash
# Extraer frames
python3 scripts/extract_frames.py

# Preprocesar imágenes
python3 scripts/preprocessing.py

# Segmentar (4 métodos)
python3 scripts/segmentation.py

# Cuantificar áreas
python3 scripts/quantification.py

# Generar visualizaciones
python3 scripts/analysis.py
```

### 2. Generar PDF del Informe

**Con Pandoc:**
```bash
chmod +x convert_to_pdf.sh
./convert_to_pdf.sh
```

**Con WeasyPrint:**
```bash
python3 convert_to_pdf_alternative.py
```

**Manual:** Abrir `informe_deforestacion.md` en cualquier editor Markdown y exportar a PDF

## Contenido del Informe

El informe científico (`informe_deforestacion.md`) contiene:

1. **Resumen** - Síntesis del estudio y resultados principales
2. **Introducción** - Contexto, fundamentos teóricos y objetivos
3. **Material y Métodos** - Descripción detallada con fórmulas matemáticas
   - Preprocesamiento (CLAHE, gamma, filtros)
   - Segmentación (Otsu, adaptativo, Lab, HSV)
   - Refinamiento morfológico
   - Cuantificación (escala: 20 km = 51 px)
4. **Resultados** - Análisis cuantitativo y visualizaciones
5. **Discusión** - Eficacia de métodos y limitaciones
6. **Conclusiones** - Hallazgos y recomendaciones futuras
7. **Referencias** - Bibliografía en formato académico
8. **Anexo A** - Declaración de uso de IA (Google AI)
9. **Anexo B-C** - Datos y figuras

## Declaración sobre Uso de IA

Este proyecto utilizó Google AI (Antigravity) para:
- Generación de scripts Python de procesamiento
- Estructuración y redacción del informe científico

**Aportación personal:**
- Análisis crítico de resultados
- Interpretación de datos
- Ajuste de parámetros de procesamiento
- Evaluación de limitaciones metodológicas

Ver sección completa en el informe: **Anexo A**

## Formato de Entrega

### Especificaciones (Según Rúbrica)

- ✅ **Formato:** PDF
- ✅ **Extensión:** 8-12 páginas
- ✅ **Estructura:** Artículo científico completo
- ✅ **Portada e índice:** Incluidos
- ✅ **Referencias:** Formato APA/IEEE
- ✅ **Declaración de IA:** Incluida y detallada
- ✅ **Anexos:** Referenciados en el texto

## Archivos Entregables

### Archivo Principal
- `informe_deforestacion.pdf` (generado con `./convert_to_pdf.sh`)

### Archivos Complementarios
- `results/quantification_results.csv` - Datos cuantitativos
- `results/analysis/*.png` - Visualizaciones (9 gráficos)

## Autores

**Juan Navarro Rodriguez**  
Máster en Inteligencia Artificial  
Febrero 2026

## Licencia

Este proyecto es material académico para la asignatura de Visión Artificial.

---

## Notas Técnicas

### Metodología Aplicada

**Preprocesamiento:**
- CLAHE (clip_limit=2.5, tile_size=8×8)
- Corrección gamma (γ=1.15)
- Filtro gaussiano (kernel=3×3, σ=0.8)

**Segmentación:**
- Otsu: Umbral global automático
- Adaptativo: Ventana 35×35, C=2
- Lab: (a>128) ∧ (b>135) ∧ (L>30)
- HSV: H∈[35°,85°], S∈[30,255], V∈[30,255]

**Morfología:**
- Apertura + Cierre
- Elemento estructurante: Elipse 5×5 (Otsu/Adaptativo) o 7×7 (Lab/HSV)

### Conversión de Escala

```
Área (km²) = N_píxeles × (20/51)² = N_píxeles × 0.1537 km²/px
```

---

## Soporte

Para cualquier duda sobre la ejecución o interpretación de resultados, revisar:
- `/Users/juannavarrorodriguez/.gemini/antigravity/brain/[conversation-id]/implementation_plan.md`
- Comentarios en scripts Python (`scripts/*.py`)