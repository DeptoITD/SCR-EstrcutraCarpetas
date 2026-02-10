# Exportador de Estructura de Carpetas a CSV (PowerShell)

## Propósito

Este script en PowerShell permite **exportar la estructura completa de carpetas y archivos** de una ruta definida hacia un archivo CSV, representando cada nivel jerárquico en columnas (`Nivel1`, `Nivel2`, ..., `NivelN`).  
Está diseñado para **documentación, auditorías, control de estructuras, migraciones y análisis de repositorios**.

El archivo resultante utiliza un **formato en cascada**, donde los niveles repetidos se dejan en blanco para mejorar la legibilidad.

---

## Descripción técnica

El script realiza las siguientes acciones:

1. Recibe una ruta de origen como parámetro o la solicita por consola.
2. Valida la existencia de la ruta ingresada.
3. Recorre recursivamente carpetas y archivos usando `Get-ChildItem`.
4. Calcula la **profundidad máxima** de la estructura.
5. Genera dinámicamente columnas `Nivel1` hasta `NivelN`.
6. Construye filas completas con la jerarquía de cada elemento.
7. Aplica un **formato en cascada**, eliminando valores repetidos entre filas consecutivas.
8. Exporta el resultado a un archivo CSV **sin encabezados**, codificado en UTF-8.
9. Guarda el archivo en una ruta fija local.

---

## Instrucciones de uso

### Requisitos
- Windows
- PowerShell 5.1 o superior
- Permisos de lectura sobre la ruta origen
- Permisos de escritura en `C:\Script\Estructura`

### Ejecución con parámetro

```bash
.\ExportarEstructura.ps1 -RutaOrigen "D:\Proyectos\2024"
```

### Ejecución sin parámetro

```bash
.\ExportarEstructura.ps1
```

El script solicitará la ruta por consola:

```bash
Ingresa la ruta que quieres listar (ej. D:\Proyectos\2024)
```

### Salida generada

- Ruta fija de salida:

```bash
C:\Script\Estructura\
```

- Nombre del archivo:

```bash
estructura_<NombreCarpetaOrigen>.csv
```

Ejemplo:

```bash
estructura_2024.csv
```

Diagrama de secuencia (Entrada y salida)
```bash
[Usuario]
   |
   |-- (1) Ejecuta script
   |
   |-- (2) Ingresa RutaOrigen (parámetro o consola)
   |
[Script PowerShell]
   |
   |-- Valida existencia de ruta
   |-- Recorre carpetas y archivos
   |-- Calcula profundidad máxima
   |-- Genera columnas Nivel1..NivelN
   |-- Aplica formato en cascada
   |
   |-- (3) Genera archivo CSV
   |
[Salida]
   |
   |-- C:\Script\Estructura\estructura_<origen>.csv
```

### Estructura del repositorio
```bash
exportador-estructura-csv/
│
├── ExportarEstructuraCarpetas.ps1      # Script principal
├── README.md                   # Documentación técnica y funcional
├── Bitacora.md                # Bitácora de cambios
└── ejemplos/
    └── estructura_ejemplo.csv  # Ejemplo de salida (opcional)
```
