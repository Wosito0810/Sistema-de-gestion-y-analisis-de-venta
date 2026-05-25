#  TechStore – Sistema de Gestión de Ventas

Sistema de gestión de ventas desarrollado en Python para Google Colab y entornos locales con Jupyter Notebook. Permite registrar y administrar ventas, aplicar análisis estadístico, comparar algoritmos de ordenamiento y búsqueda, demostrar recursividad y exportar reportes en formato TXT y CSV.

---

##  Tabla de contenidos

- [Características](#características)
- [Requisitos](#requisitos)
- [Instalación y ejecución](#instalación-y-ejecución)
- [Estructura del menú](#estructura-del-menú)
- [Módulos del sistema](#módulos-del-sistema)
- [Algoritmos implementados](#algoritmos-implementados)
- [Exportación de reportes](#exportación-de-reportes)
- [Datos de ejemplo](#datos-de-ejemplo)
- [Consideraciones](#consideraciones)

---

##  Características

- CRUD completo de registros de venta con validación de campos.
- Análisis estadístico: total, promedio, mediana, máximo, mínimo, top productos y rendimiento por vendedor.
- Cuatro algoritmos de ordenamiento con conteo de pasos e intercambios.
- Cuatro algoritmos de búsqueda iterativos y recursivos con conteo de comparaciones.
- Módulo de demostración de recursividad (suma, conteo, búsqueda por ID y factorial).
- Exportación de reportes en `.txt` y `.csv`.
- Carga automática de 12 registros de ejemplo al iniciar.
- Compatible con Google Colab y entornos locales.

---

##  Requisitos

- Python 3.7 o superior
- Google Colab (recomendado) o Jupyter Notebook

No requiere librerías externas. Solo usa módulos estándar de Python:

```
csv, os, datetime
```

---

##  Instalación y ejecución

### En Google Colab

1. Sube el archivo `.py` o pega el código en una celda de Colab.
2. Ejecuta la celda. El sistema cargará automáticamente 12 registros de ejemplo.
3. Navega por el menú interactivo en la consola de salida.

> La exportación de reportes usa `google.colab.files.download()` y solo funciona en el entorno Colab.

### En entorno local

1. Descarga o clona el archivo del proyecto.
2. Ejecuta directamente con Python:

```bash
python techstore.py
```

> En entorno local, la descarga de archivos no se activará automáticamente; los archivos `.txt` y `.csv` se guardarán en el directorio de trabajo.

---

##  Estructura del menú

```
MENÚ PRINCIPAL
├── 1. Gestión de Registros
│   ├── Ingresar nueva venta
│   ├── Mostrar todos los registros
│   ├── Modificar venta por ID
│   └── Eliminar venta por ID
├── 2. Análisis Estadístico
├── 3. Ordenamiento
├── 4. Búsqueda
├── 5. Recursividad (demostración)
├── 6. Reportes (TXT / CSV)
└── 0. Salir
```

---

##  Módulos del sistema

### 1. Gestión de Registros (RF-01 a RF-05)

Operaciones CRUD sobre los registros de venta.

| Campo | Descripción | Validación |
|---|---|---|
| ID | Generado automáticamente | Autoincremental |
| Producto | Nombre del producto | No vacío, máx. 50 caracteres |
| Cantidad | Unidades vendidas | Entero ≥ 1 |
| Precio | Precio unitario | Flotante > 0.01 |
| Total | Calculado automáticamente | `cantidad × precio` |
| Fecha | Fecha de la venta | Formato `DD/MM/AAAA` |
| Vendedor | Nombre del vendedor | No vacío, máx. 50 caracteres |
| Sucursal | Ciudad o sede | No vacío, máx. 50 caracteres |

- **Modificar:** permite editar cualquiera de los 6 campos ingresables; el total se recalcula automáticamente.
- **Eliminar:** solicita confirmación antes de remover el registro.

### 2. Análisis Estadístico (RF-06 a RF-11)

| Indicador | Descripción |
|---|---|
| RF-06 | Total acumulado de ventas (iterativo y recursivo) |
| RF-07 | Promedio de ventas (iterativo y recursivo) |
| RF-08 | Venta máxima y mínima por monto total |
| RF-09 | Mediana del conjunto de ventas |
| RF-10 | Top 3 productos con mayor cantidad vendida |
| RF-11 | Suma, promedio y número de transacciones por vendedor |

### 3. Ordenamiento (RF-12 a RF-16)

Permite ordenar los registros de forma ascendente o descendente y comparar el rendimiento de cada algoritmo. Ver sección [Algoritmos implementados](#algoritmos-implementados).

### 4. Búsqueda (RF-17 a RF-20)

Búsqueda por campo de texto o por monto exacto con comparativa de comparaciones entre algoritmos. Ver sección [Algoritmos implementados](#algoritmos-implementados).

### 5. Recursividad (RF-21 a RF-24)

Módulo didáctico que ejecuta y muestra los resultados de cuatro funciones recursivas:

| RF | Función | Descripción |
|---|---|---|
| RF-21 | `suma_recursiva` | Suma acumulada de todos los totales |
| RF-22 | `conteo_recursivo` | Cuenta ventas que superan un umbral dado |
| RF-23 | `busqueda_recursiva_id` | Búsqueda por ID con retroceso (backtracking) |
| RF-24 | `factorial_recursivo` | Cálculo de n! de forma recursiva |

---

##  Algoritmos implementados

### Ordenamiento

| Algoritmo | RF | Clave de ordenamiento | Complejidad promedio |
|---|---|---|---|
| Burbuja | RF-12 | Monto total | O(n²) |
| Inserción | RF-13 | Fecha | O(n²) |
| Selección | RF-14 | Nombre de producto | O(n²) |
| Quicksort | RF-15 | Monto total | O(n log n) |

Todos retornan el número de **pasos** y **intercambios** realizados. La opción de comparativa (RF-16) ejecuta los cuatro algoritmos y presenta los resultados en una tabla.

### Búsqueda

| Algoritmo | RF | Tipo | Campo |
|---|---|---|---|
| Lineal Iterativa | RF-17 | Iterativo | ID, producto, vendedor |
| Binaria Iterativa | RF-18 | Iterativo | Monto total (lista ordenada) |
| Lineal Recursiva | RF-19 | Recursivo | ID, producto, vendedor |
| Binaria Recursiva | RF-19 | Recursivo | Monto total (lista ordenada) |

> La búsqueda binaria requiere que la lista esté ordenada previamente por `total`. El sistema aplica Quicksort de forma automática antes de ejecutarla.

Todos los algoritmos retornan el número de **comparaciones** realizadas. La opción comparativa (RF-20) muestra los cuatro valores en una tabla.

---

##  Exportación de reportes

| Formato | Archivo generado | Contenido |
|---|---|---|
| TXT | `ventas_reporte.txt` | Encabezado con fecha, listado de ventas en texto plano |
| CSV | `ventas.csv` | Todos los campos separados por comas, compatible con Excel |

> En Google Colab, los archivos se descargan automáticamente al navegador mediante `google.colab.files.download()`.

---

##  Datos de ejemplo

Al iniciar, el sistema carga automáticamente 12 registros de ejemplo con productos tecnológicos, vendedores y sucursales distribuidas en varias ciudades de Colombia.

| Producto | Vendedor | Sucursal |
|---|---|---|
| Laptop HP 15 | Carlos Ruiz | Bogotá |
| Mouse Logitech | Ana Torres | Medellín |
| Teclado Mecánico | Pedro Gómez | Cali |
| Monitor Samsung | Carlos Ruiz | Bogotá |
| Auriculares Sony | Ana Torres | Barranquilla |
| Tablet Lenovo | María López | Bucaramanga |
| Webcam Logitech | Pedro Gómez | Cali |
| SSD Kingston | María López | Medellín |
| Router TP-Link | Luis Herrera | Bogotá |
| Impresora Epson | Luis Herrera | Barranquilla |
| Laptop Dell XPS | Carlos Ruiz | Bucaramanga |
| Memoria RAM 16GB | Ana Torres | Cali |

---

##  Consideraciones

- Los IDs son autoincrementales y no se reutilizan tras eliminar un registro.
- Las fechas deben ingresarse en formato `DD/MM/AAAA`; el sistema las valida y reintenta en caso de error.
- El carácter `|` no se usa como separador en este sistema; no hay restricción sobre su uso en textos.
- Los datos se almacenan en memoria RAM durante la sesión; al cerrar el entorno se pierden si no se exportaron.
- La exportación a TXT y CSV utiliza `google.colab.files`; en entorno local, los archivos se guardan en el directorio actual sin descarga automática.
- El módulo de recursividad puede presentar errores de límite de pila (`RecursionError`) para conjuntos de datos muy grandes; está diseñado con fines didácticos.

##  Autor

- David Santiago Vargas Parra
- Universidad de Santander
- Ingeniera de Software
