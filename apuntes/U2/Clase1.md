# Clase 29/8/2023

## Bases de datos relacionales

### Bases de datos transaccionales

Son bases de datos que buscan **asegurar la consistencia** de las operaciones realizadas sobre esta. Para esto se utilizan *transacciones* las cuales son capaces de **revertirlas** en caso de algun error.

#### Caracteristicas

- Permiten un **gran numero de transacciones cortas** *en linea*
- Manejan datos de sitemas [*OLTP*](#glosario)
- Optimizadas para la actualización en tiempo real (corta y rápida).

#### Ventajas

- Integridad en los datos (*main feature*)
- Baja latencia y rapidez

#### Desventajas

- Limitacion para *generar informes*
- Historial de datos *limitado a datos actuales* (o recientes)

#### Ejemplos

- Transferencias bancarias: Las transacciones se emplean aqui para validar o deshacer la transferencia en cuestión. Dado que las transferencias bancarias son dos operaciones distintas (primero se saca del origen y luego se lo da al destino) es necesario que si una falla, fallen las dos.

- Sistemas de venta online: Una venta, un ingreso de dinero y el descuento del stock son operaciones que precisan de la mayor integridad posible.


## Bases de datos vs Data Warehouse vs Data Lake

### Bases de datos

Normalmente son **muy estructuradas** y estan **optimizadas para transacciones** y tiene un diseño *OLTP*. Normalmente son usados para la introduccion y modificacion (CRUD o ABM) de datos en el sistema (Ej: Detras de cada formulario en tu pagina web hay una base de datos relacional).

### Data Warehouse (DWH)

Construido encima de todas las bases de datos OLTP y que se usa como fuente de datos para hacer *Business Intelligence* (BI). El DWH obtiene la información de distintos sistemas y bases de datos y los unifica y almacena todo en una estructura [*OLAP*](#glosario) generando una capa de datos optimizada para hacer analisis de esa información.
Por lo tanto, para ver informacion de desempeño y performance del negocio y tomar decisiones a futuro utilizo el data warehouse y no las bases de datos productivas. De esta manera, no afecto la base de datos haciendo consultas pesadas y, por otro lado, consulto una base optimizada para esas consultas.

### Data Lake (DL)

Es un concepto aun menos estructurado que el DWH ya que aqui no es necesario aplicar ningún tipo de estructuración a los datos. Los datos son almacenados tal cual en su sistema origen

### Similitudes y diferencias entre DWH y DL

#### Similitudes

- Son repositorios centralizados
- Pueden datos estructurados en tiempo real

#### Diferencias

- DL almacena datos **no** estructurados (tal cual llegan).
- DL **no** almacena datos de manera optima para su consulta.
- **DWH almacena y analiza datos estructurados** mientras que **DL almacena datos no estructurados** pero no tanto para su análisis.


#### Modo de uso

- Si disponemos solo de datos estructurados entonces usamos un DWH

- Si disponemos de datos estructurados y no estructurados, entonces:

1. Capturamos todos los datos en un DL
2. Los datos estructurados los procesamos y organizamos en un DWH
3. Los datos no estructurados quedaran en el DL para ser accedidos cuando sea necesario

> **NOTA:** De esto puede deducirse que podemos tener un DWH sin un DL, pero rara vez tendremos un DL sin un DWH.

## Motor de base de datos (RDBMS o SGBD)


### Conexion a un motor de base de datos

### Collate - Intercalación

Intercalacion (Collation) hace referencia al **patrón de bits utilizado para representar/almacenar cada carácter** y, por consecuencia, a las **reglas utilizadas para ordenar y comparar los caracteres** de las strings.

Esto permite distinguir entre mayúsculas y minúsculas y entre acentuados y no acentuados.

#### CS/CI: Case Sensitive Case Insensitive

Indica si la tabla hace diferencia entre mayusculas y minusculas

#### AS/AI Accent Sensitive / Accent Insensitive

Indica si la tabla hace diferencia entre dos strings acentuadas

> **NOTA:** Segun la region donde se instale la base de datos esta configuracion puede variar!

> **NOTA:** Conviene siempre hacer explicita la collation al hacer comparacion entre dos strings

## Base de datos en memoria

### ¿Por que?

Con el crecimiento de [*IoT*](#glosario) y de las soluciones basadas en la nube, las empresas precisan procesar datos en tiempo real.

### Bases en Memoria vs Bases en Disco

- ...
- ...
- ...


### Tabla Variable vs Tabla Temporal vs Tabla en Memoria

#### Tabla variable

##### Alcance
Limitado al módulo en ejecución (como una variable en un script)

##### Donde esta
Intenta mantenerse en memoria pero no se garantiza (luego va a tempdb)

##### Sintaxis
Se indica en `DECLARE` con `@` como las otras variables

##### Contenido
Se pierde al quedar fuera de alcance

##### Indices
No tiene indices ni estadisticas


#### Tabla temporal

##### Alcance
Igual que las tablas variables salvo las temporales globales

##### Donde esta
Van directo a tempdb (este se vacía en cada reinicio)

##### Sintaxis
Se indica en `CREATE` con `#` o `##` para globales

##### Contenido
Se pierde al quedar fuera de alcance, excepto globales

##### Indices
Admite indices y estadisticas

#### Tabla en memoria

##### Alcance
Alcance identico a otras tablas

##### Donde esta
Se mantiene en memoria

##### Sintaxis
Se indica en `CREATE` con una clausula

##### Contenido
Solo se pierde ante un reinicio

##### Indices
Admite indices

## ODBC y JDBC

**O**pen **D**ata **B**ase **C**onnectivity es una API (escrita en Lenguaje C) para aplicaciones que quieren comunicarse con motores de base de datos

Esta permite la comunicación con el motor de base de datos a travez de una serie de metodos, objetos y funciones

---


## Glosario

> OLTP: (Online Transaction Processing) Tipo de procesamiento de datos que consiste en ejecutar una serie de transacciones que ocurren simultáneamente en la banca en línea, las compras, la entrada de pedidos o el envío de mensajes de texto, por ejemplo.

> OLAP: (Online Analytical Processing) ...

> IoT: (Internet of Things) ...

## Bibliografia

- [PPT de la Clase en MIeL](https://miel.unlam.edu.ar/data7/data2/contenido/3641/2023-BBDD-Unidad-2.pdf)
- [Definición de OLTP](https://www.oracle.com/mx/database/what-is-oltp/)