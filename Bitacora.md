# Bitácora / Registro de Cambios – Exportador de Estructura de Carpetas a CSV

**Nota terminológica:**  
En contextos de TI también se utiliza el término *Registro de Cambios* o *Change Log*.  
El término **Bitácora** es válido y apropiado en documentación técnica en español, especialmente para el registro cronológico de decisiones, criterios de diseño y evolución de soluciones técnicas.

---

## Contexto inicial

La documentación de estructuras de carpetas y archivos se realizaba de forma manual o mediante listados simples, lo que generaba:

- Baja estandarización en la representación de jerarquías.
- Dificultad para analizar estructuras profundas.
- Escasa trazabilidad en procesos de auditoría, migración o control documental.
- Resultados poco legibles al ser consumidos en herramientas como Excel.

Ante esta necesidad, se planteó el desarrollo de un script que permitiera **exportar de forma automática, completa y consistente** la estructura de un directorio, manteniendo claridad visual y reutilización del resultado.

---

## Decisión 1: Uso de PowerShell como tecnología base

Se seleccionó PowerShell como lenguaje de implementación debido a que:

- Es una herramienta nativa en entornos Windows corporativos.
- Permite interacción directa y eficiente con el sistema de archivos.
- No requiere dependencias externas ni instalaciones adicionales.
- Facilita la automatización y futura integración con otros scripts.

---

## Decisión 2: Modelo jerárquico por niveles

Se definió un modelo de representación basado en columnas jerárquicas (`Nivel1`, `Nivel2`, ..., `NivelN`), donde:

- Cada nivel corresponde a un segmento de la ruta.
- La cantidad de niveles se calcula dinámicamente según la profundidad máxima encontrada.
- El modelo se adapta a cualquier estructura, sin límites predefinidos.

Este enfoque permite una **lectura tabular clara** y facilita análisis posteriores.

---

## Decisión 3: Formato en cascada

Se adoptó un formato en cascada en el archivo de salida, dejando en blanco los niveles que se repiten entre filas consecutivas, con el objetivo de:

- Mejorar la legibilidad visual.
- Reducir redundancia en el archivo CSV.
- Facilitar su uso en reportes y revisiones manuales.

---

## Decisión 4: Exportación en formato CSV

El formato CSV fue elegido por su:

- Compatibilidad con herramientas de análisis y ofimática.
- Simplicidad para integrarse en flujos existentes.
- Facilidad de apertura, filtrado y validación.

El archivo se genera sin encabezados para permitir su incorporación directa en plantillas o procesos donde los encabezados se gestionan externamente.

---

## Decisión 5: Inclusión completa de elementos

Se decidió incluir:

- Carpetas y archivos.
- Elementos ocultos del sistema.

Esto garantiza una **visión completa y real** de la estructura analizada, especialmente relevante en procesos de auditoría técnica.

---

## Decisión 6: Ruta de salida estandarizada

Se estableció una ruta fija de salida (`C:\Script\Estructura`) con el fin de:

- Garantizar consistencia entre ejecuciones.
- Facilitar automatizaciones futuras.
- Reducir errores derivados de rutas variables.

---

## Proximos pasos (pendiente)

- Parametrización de la ruta de salida.
- Inclusión opcional de encabezados.
- Exportación directa a Excel.
- Inclusión de metadatos adicionales.
- Integración con procesos de inventario documental.
- Validación de existencia de la ruta origen.
- Solicitud interactiva de ruta cuando no se pasa como parámetro.
- Manejo de carpetas sin contenido.
- Mensajes informativos y de error controlados.

---
