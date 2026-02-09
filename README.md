# Análisis de la Deforestación en la Selva Amazónica

Este repositorio contiene el análisis completo de la deforestación en el Bosque Nacional Jamanxim (2000-2019) utilizando técnicas de segmentación de imágenes.

## Estructura del Proyecto

```
└── analysis/                       # Visualizaciones (9 gráficos)
├── Act.3_pdf.md                    # Informe científico (Markdown)
├── quantification_results.csv      # Resultados de cuantificación (CSV)
├── README.md                       # Documentación del proyecto

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
