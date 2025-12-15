# 📊 Analisis ventas

1. 📖 Contexto y Problema Actual

    El actual proyecto se basa en el análisis de un conjunto de datos que nos proporciona una empresa en la que su canal comercial quiere conocer el estado de sus ventas en los últimos dos años para poder trazar una estratégia dedicada al crecimiento de las mismas. Para ello realizaremos un EDA (Ánalisis exploratorio del dato) en el cual buscaremos tendencias de crecimento/decrecimento, tipologias de producto con mayor índice de venta, anulaciones y sus motivos, etc. Antes de realizar objeto principal de este proyecto, deberemos realizar una ETA (Extracción, Transformación y Carga de los Datos) en la cual en primer lugar cifraremos los datos sensibles para la protección y privacidad, estudiaremos la validez y coheréncia de los datos, por último realizaremos la carga en nuestro archivo para el ánalisis.

2. 🎯 Objetivos

    El objetivo principal de este proyecto es crear uno o mas Dashboard interactivos que faciliten la visualización de los datos y proporcionen insights que ayuden a la toma de decisiones estratégicas.Los insights proporcionarán:

    - Tendencias de venta.
    - Tasa de anulación de pedidos.
    - Productos y tipologias de producto con mayor venta.

    Tambien, de forma paralela se estable otro objetivo que requiere la compañia, la cual ha empezado un Gobierno del Dato en la compañia y nos pide evaluar la validez de los datos con el objetivo de mejorar la calidad del mismo. En este apartado el objetivo es:

    - Hallar los datos incoherentes para su procesamiento.
    - Establecer las reglas de calidad que mantengan una buena calidad del dato.

    En resumen, hallar tendencias y patrones para tomar las decisiones con mayor fiabilidad de éxito, y garantizar la fiablidad de los datos en la compañia.



3. 🗂️ Estructura del Proyecto

    ├── .gitignore

    ├── Datos_originales_cifrados.xlsx

    ├── Datos_transformados.zip ├── Datos_transformados.xlsx

    ├── csv_datos_transformados.csv

    ├── EDA.xlsx

    ├── README.md # Descripción del proyecto

4. 🛠️ Descripcion de los campos

    VENTA:

    - Pedido: Número entero identificador del pedido de venta del cliente.
    - Acoplado: Booleano que indica si el pedido se servirá o no desde el stock.
    - Fabricado: Booleano que indica si el pedido se servirá o no mediante su producción.
    - Anulada: Booleano que indica si el pedido ha sido anulado o no por el cliente.
    - Motivo_anulacion: Texto que indica el motivo de la anulacion para cuando el campo "Anulada" toma el valor "SI".
    - Fecha_anulacion: Fecha que indica el dia de la anulación para cuando el campo "Anulada" toma el valor "SI".
    - Temporada: Texto que indica la temporada a la que pertenece el pedido. Siendo "V" Verano e "I" Invierno junto con un número que indica el año.
    - Clase_pedido: Texto que indica desde que área se ha realizado el pedido. Siendo "Pedido Inicial WH" los pedidos realizados por clientes externos a la empresa y "Pedido Reserva Plan" los realizados internamente para stock.
    - Fecha_pedido: Fecha que indica el dia que se realizó el pedido.
    - Fecha_servicio: Fecha que indica el dia para el cual se necesita servir el pedido.
    - Area_ventas: Texto que indica para que área del mundo se ha realizado el pedido. Siendo "USCA" para la zona de Estados Unidos y Cánada, "LATM" para la zona de Latino Ámerica, "IBLA" para España, "EMEA" para Europa excepto España y Asia occidental y "ASIA" para la zona mas oriental del contiente Asiático.
    - Pais_cliente: Texto que indica el pais del cliente.
    - Cliente: Texto que indica el nombre del cliente, en este caso codificado.
    
    PRODUCTO:

    - Genero: Texto que indica el género del artículo, en este caso del zapato.
    - Seccion: Texto que indica una linea de artículo, en este caso del zapato.
    - Modelo: Texto que identifica un modelo del artículo, en este caso del zapato.
    - Color: Texto que indica el color del artículo, en este caso del zapato.
    - Categoria: Texto que indica la categoría del artículo, en este caso del zapato.

    
    PRODUCCIÓN & LOGÍSTICA:
    
    - Proveedor: Texto que indica el proveedor que servirá el pedido, en este caso codificado.
    - Fecha_recepcion: Fecha en la que se ha recibido el pedido.
    - Fecha_albaran: Fecha en la que se expide el pedido al cliente.
    - Centro: Texto que indica el centro desde el que se expedirá el pedido.
    - Almacen: Texto que indica el almacen donde se ubicará el pedido hasta su expedición
    - Total: Número entero que indica la cantidad del pedido, en este caso la cantidad de pares de zapatos.
    
    MEDIDAS:

    - Proveedor_validez_dato: Texto que indica la validez del valor que toma el campo "Proveedor".
    - Anulada_validez_dato: Texto que indica la validez del valor que toma el campo "Anulada".
    - Antelacion_pedido_dias: Número entero que indica la diferencia de dias entre Fecha_servicio" y "Fecha_pedido".
    - Antelacion_pedido_validez_dato: Texto que indica si el valor de la medida esta dentro de un rango coherente devolviendo "Dato_valido" o devolviendo la casuistica del error en su defecto.
    - Tiempo_entrega_dias: Número entero que indica la diferencia de dias entre "Fecha_recepcion" y "Fecha_pedido".
    - Tiempo_preparacion_real: Número entero que indica la diferencia de dias entre "Fecha_albaran" y "Fecha_recepcion".
    - Tiempo_preparacion_real_validez_dato: Texto que indica si el valor de la medida esta dentro de un rango coherente devolviendo "Dato_valido" o devolviendo la casuistica del error en su defecto.
    - Tiempo_preparacion_disponible: Número entero que indica la diferencia de dias entre "Fecha_servicio" y "Fecha_recepcion".
    - Validez_registro: Texto que indica si el registro contiene o no algún campo con datos erroneos o no.


5. 🔄 Recap sesiones.

    SESION 1:

    - Creación repositorio GitHub.
    - Generación archivos Readme y gitignore (protección datos originales).
    - ETL:
        - Extracción y cifrado de los datos originales (Datos_originales_cifrados.xlsx).
        - Transformación de los datos y creación archivo Datos_transformados, en el creamos nuevos campos calculados (medidas) y analizamos la validez de cada uno de los registros (linias).
        - Exportación de los datos ya transformados a csv (csv_datos_transformados.csv).
        - Carga y creación archivo para el analisis (EDA.xlsx), confirmamos con Power Query los tipos de datos (texto, calendiario, numericos: entero o decimal) por campo y filtramos en "Validez_registro" por "Registro_erroneo".
    - Comprimir archivo Datos_transformados por su peso superor a 100 MB.     

    SESION 2:

    - Analisis estadístico descriptivo de los campos númericos.




6. ✒️ Autor

    - Álex Candela Asencio