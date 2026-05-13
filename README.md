# TechStore — Sistema de Gestión de Ventas

Proyecto Final · Estructuras de Datos 


## Descripción

TechStore es una cadena de productos tecnológicos con cinco sucursales en el país que registraba sus transacciones manualmente en hojas de cálculo, generando inconsistencias, errores humanos y demoras en los reportes gerenciales.

Este proyecto construye el núcleo de un sistema digital de gestión de ventas utilizando exclusivamente estructuras de datos fundamentales y algoritmos implementados desde cero en Python, sin librerías externas especializadas. El sistema permite registrar, modificar, analizar, ordenar, buscar y exportar ventas, proporcionando a la gerencia información confiable para la toma de decisiones basada en datos.


## Objetivos

El objetivo general es desarrollar un sistema de gestión de ventas en Python que integre estructuras de datos, algoritmos de ordenamiento, búsqueda y recursividad, aplicando buenas prácticas de programación y validación robusta de entradas.

Los objetivos específicos son implementar un arreglo dinámico mediante lista de diccionarios para el almacenamiento de registros; desarrollar desde cero los algoritmos Burbuja, Inserción, Selección y Quicksort con soporte ascendente y descendente; implementar búsqueda lineal y binaria en sus versiones iterativa y recursiva comparando su desempeño; calcular indicadores estadísticos (total acumulado, promedio, mediana, máximo y mínimo); aplicar recursividad en al menos tres contextos distintos; y generar reportes exportables en formato `.txt` y `.csv`.


## Estructura del Proyecto

```
techstore/
│
├── techstore.py          # Código fuente principal (único archivo)
├── README.md             # Este documento
├── ventas_reporte.txt    # Generado al exportar (Módulo 6)
└── ventas.csv            # Generado al exportar (Módulo 6)
```

El sistema completo reside en un único archivo Python de 838 líneas, organizado en seis módulos lógicos claramente delimitados mediante comentarios de sección.

---

## Módulos del Sistema

### Módulo 1 — Gestión de Registros

Cubre el ciclo de vida completo de un registro de venta. Al iniciar, el sistema carga automáticamente 12 registros de ejemplo. El usuario puede ingresar ventas nuevas con validación campo a campo (precio positivo, fecha en formato DD/MM/AAAA, vendedor no vacío), visualizar todos los registros en una tabla formateada en consola, modificar cualquier campo dado el ID, y eliminar registros con confirmación previa. El ID se genera automáticamente y nunca es ingresado por el usuario.

### Módulo 2 — Análisis Estadístico

Calcula todos los indicadores del período activo: total acumulado (iterativo y recursivo), promedio (iterativo y recursivo), venta máxima y mínima con su registro completo, mediana del conjunto, top 3 de productos más vendidos por cantidad, y suma/promedio individual por vendedor.

### Módulo 3 — Ordenamiento

Implementa cuatro algoritmos desde cero, todos con soporte para orden ascendente y descendente, y con conteo de pasos e intercambios realizados:

- **Burbuja** — ordena por monto total
- **Inserción** — ordena por fecha (cronológico/inverso)
- **Selección** — ordena por nombre de producto (A-Z / Z-A)
- **Quicksort recursivo** — ordena por monto total

El módulo incluye una vista comparativa que ejecuta los cuatro algoritmos sobre el mismo conjunto de datos y muestra sus métricas lado a lado.

### Módulo 4 — Búsqueda

Ofrece búsqueda lineal iterativa y recursiva por ID, producto o vendedor (retorna todos los coincidentes), y búsqueda binaria iterativa y recursiva por monto total (requiere lista previamente ordenada). Cada búsqueda reporta el número exacto de comparaciones realizadas. El módulo también incluye una vista comparativa entre los cuatro algoritmos para el mismo criterio de búsqueda.

### Módulo 5 — Recursividad Explícita

Agrupa las funciones recursivas del sistema de forma demostrable e interactiva: suma acumulada de todos los totales, conteo de ventas que superan un umbral ingresado por el usuario, búsqueda por ID con retroceso (backtracking), y cálculo de factorial como demostración didáctica del concepto.

### Módulo 6 — Reportes

Exporta los datos en dos formatos. El archivo `ventas_reporte.txt` incluye encabezado institucional, fecha y hora de generación, tabla completa de registros y resumen final con el total acumulado. El archivo `ventas.csv` se genera con codificación UTF-8 BOM para compatibilidad directa con Microsoft Excel.

---

## Algoritmos y Estructuras de Datos

La estructura central del sistema es una lista de diccionarios de Python, que actúa como arreglo dinámico. Cada elemento representa una venta con los campos `id`, `producto`, `cantidad`, `precio`, `total`, `fecha`, `vendedor` y `sucursal`.

Los cuatro algoritmos de ordenamiento y los dos de búsqueda están escritos íntegramente desde cero, sin usar funciones de ordenamiento nativas como `sorted()` o `list.sort()`. La recursividad aparece en seis puntos del código: Quicksort, suma acumulada, promedio, conteo por umbral, búsqueda por ID con backtracking, y factorial.

---

## Requisitos

El proyecto no tiene dependencias externas. Solo requiere Python 3.8 o superior y los módulos de la biblioteca estándar `csv`, `os` y `datetime`, que vienen incluidos en cualquier instalación de Python.

---

## Instalación y Ejecución

Clonar el repositorio y ejecutar el archivo principal:

```bash
git clone https://github.com/usuario/techstore.git
cd techstore
python3 techstore.py
```

Al iniciar, el sistema carga automáticamente los datos de ejemplo y muestra el menú principal. No se requiere ninguna configuración adicional.

---

## Validaciones Implementadas

El sistema valida todas las entradas del usuario antes de procesar cualquier dato. Los precios deben ser números positivos mayores a cero. Las fechas deben tener el formato DD/MM/AAAA y representar una fecha real (por ejemplo, 31/02/2024 es rechazada). El campo vendedor no puede estar vacío ni superar 50 caracteres. Las cantidades y IDs deben ser enteros positivos. Cualquier entrada inválida muestra un mensaje descriptivo y solicita el dato nuevamente sin interrumpir el flujo del programa.

---

## Decisiones Técnicas

Se optó por un único archivo Python en lugar de múltiples módulos para simplificar la entrega y ejecución, dado que el alcance del proyecto no justifica una estructura de paquetes. Las funciones recursivas y sus equivalentes iterativos se implementaron en paralelo para facilitar la comparación directa, que es uno de los requisitos explícitos del enunciado. El contador de IDs es global y autoincremental, lo que garantiza unicidad aunque se eliminen registros intermedios.

---

## Autor

David Santiago Vargas Parra - 01240371048 

Institución: Universidad de Santander
