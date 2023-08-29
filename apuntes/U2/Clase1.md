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

> Transferencias bancarias: Las transacciones se emplean aqui para validar o deshacer la transferencia en cuestión. Dado que las transferencias bancarias son dos operaciones distintas (primero se saca del origen y luego se lo da al destino) es necesario que si una falla, fallen las dos.

> Sistemas de venta online: Una venta, un ingreso de dinero y el descuento del stock son operaciones que precisan de la mayor integridad posible.


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

> De esto puede deducirse que podemos tener un DWH sin un DL, pero rara vez tendremos un DL sin un DWH.



---

## Glosario

> OLTP: (Online Transaction Processing) Tipo de procesamiento de datos que consiste en ejecutar una serie de transacciones que ocurren simultáneamente en la banca en línea, las compras, la entrada de pedidos o el envío de mensajes de texto, por ejemplo.

> OLAP: (Online Analytical Processing) ...

## Bibliografia

- [PPT de la Clase en MIeL](https://miel.unlam.edu.ar/data7/data2/contenido/3641/2023-BBDD-Unidad-2.pdf)
- [Definición de OLTP](https://www.oracle.com/mx/database/what-is-oltp/)