# 📊 Analisis ventas

1. 📖 Contexto y Problema Actual

    El actual proyecto se basa en el análisis de un conjunto de datos que nos proporciona una empresa en la que su canal comercial quiere conocer el estado de sus ventas en los últimos dos años para poder trazar una estratégia de mejora en el serivio de las mismas para no perder crecimiento. Para ello realizaremos un EDA (Ánalisis exploratorio del dato) en el cual buscaremos tendencias de cumplimiento/incumplimiento del servicio, tipologias de producto con mayor índice de venta, anulaciones y sus motivos, etc. Antes de realizar objeto principal de este proyecto, deberemos realizar una ETA (Extracción, Transformación y Carga de los Datos) en la cual en primer lugar cifraremos los datos sensibles para la protección y privacidad, estudiaremos la validez y coheréncia de los datos, por último realizaremos la carga en nuestro archivo para el ánalisis.

2. 🎯 Objetivos

    El objetivo principal de este proyecto es crear uno o mas Dashboard interactivos que faciliten la visualización de los datos y proporcionen insights que ayuden a la toma de decisiones estratégicas. Los insights proporcionarán:

    - Cumplimiento del servicio (principal).
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
    - Area_ventas: Texto que indica para que área del mundo se ha realizado el pedido. Siendo "USCA" para la zona de Estados Unidos y Cánada, "LATM" para la zona de Latino Ámerica, "IBLA" para España, "EMEA" para Europa y Asia occidental y "ASIA" para la zona mas oriental del contiente Asiático.
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

    SESIÓN 1:

    - Creación repositorio GitHub.
    - Generación archivos Readme y gitignore (protección datos originales).
    - ETL:
        - Extracción y cifrado de los datos originales (Datos_originales_cifrados.xlsx).
        - Transformación de los datos y creación archivo Datos_transformados, en el creamos nuevos campos calculados (medidas) y analizamos la validez de cada uno de los registros (linias).
        - Exportación de los datos ya transformados a csv (csv_datos_transformados.csv).
        - Carga y creación archivo para el analisis (EDA.xlsx), confirmamos con Power Query los tipos de datos (texto, calendiario, numericos: entero o decimal) por campo y filtramos en "Validez_registro" por "Registro_erroneo".
    - Comprimir archivo Datos_transformados por su peso superor a 100 MB.     

    SESIÓN 2:

    - Análisis estadístico descriptivo de los campos númericos.
    - Análisis de los campos categóricos.
    - Análisis de los campos temporales.
    - Análisis multifactorial.
    - Análisis relacional.

    SESIÓN 3:

    - Creación DashBoard.
    - Revision Reglas de calidad.


6. 🔚 Conclusiones.

    - Análisis descriptivo númericos: Los numéricos estan formados por 5 campos, sin embargo 2 han resultado ser los mas relevantes, Antelación_pedido y Tiempo_preparacion_disponible. Antelacion_pedido muestra que el 90% de los pedidos se graban con una adelante a la fecha a la que se solicita igual o superior a 4 meses. Teniendo en cuenta que el tiempo estandar de produccion para los origenes con un mayor tiempo de producciones de 4 meses (1 mes de aprovisionamiento, 1 mes de produccion y 2 meses de transito), entonces este indicador nos dice que si el 10% restante se produce en origenes con menor lead time, estariamos 100% cubiertos para cumplir el servicio. Ademas, la media se situa en casi 6 meses (175 dias). El objetivo deberia ser subir este indicador por encima de los 180 dias, y que solo el 5% estuviera por debajo de los 4 meses, dando mas margen y tiempo de planificacion, mejorando la productividad y asegurando mas el servicio. Tiempo_preparacion_disponible indica que el 88% de los pedidos se entregan en almacen con un tiempo igual o superior a 2 dias para preparar y enviar a cliente. Esto deja el 12% de los registros fuera. Es un indicador a reducir, el maximo de pedidos tarde debe ser del 5%. El resto de campos muestran el tiempo promedio de entrega que vemos que es inferior (139) al promedio de antelacion de pedido, lo que quiere decir que hay mas tiempo medio en la antelacion de los pedidos que en la entrega de los mismos. Y por ultimo los pares por pedido, que nosmuestra un intervalo de entre 1 y 10 de pares por pedido, el promedio es 17 porque se ve afectado por los outliers.

    - Análisis categóricas: En este apartado se muestra de forma sencilla la distribucion de cada uno de los campos que categorizan los datos. Se ve como el 85% de la venta se produce por fabricacion directa, que el fabricante con mayor volumen es X31B y el segundo M04P. Los anulados representan casi un 25%, un dato relevante pero cuando vemos los motivos vemos que casi el 80% es debido a una situacion habitual de anulacion de pedidos stock. Un tercio de las ventas son stock y el resto pedidos de clientes. España, Mexico y Estados Unidos representan mas del 70% de la venta. La distrubucion por genero muestra un predominancia de las ventas en señora y por categoria, los deportivos suponen la mayor venta en casi un 30%.

    - Análisis temporales: La temporalidad esta fuertemente marcada, excluyendo la fechas de anulacion, se ve como los pedidos se graban en a penas 3 meses para las temporadas de invierno (febrero) y en alguno mas para las temporadas de verano (julio, agosto y septiembre), pero con picos muy marcados. En las fechas de servicio se sigue viendo epocas pico pero algo menos marcadas y ya las fecha de llegada y de expedicion se mantienen mas constantes durante el año, aunque tambien con ligeros epocas de valle.

    - Análisis multifactorial: El analisis a pesar de haber visto que habian solo un 0,27% de anulaciones por llegar tarde, se ha querido centrar el foco en el servicio. Se puede observar como M04P es el proveedor con mayor incumplimiento, tanto en stock como en clientes, suponiendo mas de un 24% de toda la produccion que llega tarde. Es normal ver un valor mayor a mayor volumen de produccion, pero en este caso seria el segundo con mayor volumen y ademas siendo de los proveedores menor tiempo de entrega, ya no solo por datos que seria el tercero con menor tiempo de entrega, sino tambien por ser el proveedor con menor tiempo de transito, reduciendo tiempo y sobretodo posibles cuellos de botellas o problemas de aduana. esto muestra el punto clave donde trabajar.

    - Análisis relacional: En este analisis se ha visto la relacion directa o inversa entre algunos campos, aportando lo que mas o menos ya se podia saber. Antelacion pedido con tiempo entrega y tiempo preparacion real con tiempo preparacion disponible muestran una relacion directa, cuanto mayor tiempo se dispone o para fabricar o para prepara, mas tiempo se termina utilizando. Pasa lo contrario entre tiempo entrega con tiempo preparacion tanto real como disponible, con una relacion inversa, cuanto mas tiempo consume la entrega menos se dispone para preparar.

Conclusiones finales: Como conclusión general podemos ver que el % de incumplimiento es de 11'5% y la empresa quiere establecer un objetivo de máximo del 5%.

Analizando mas en detalle, el 11'5 tarde es sobre el total de pares ya entregados 4.335.780, por lo que hay 497.823 pares tarde y 3.837.957 entregados en fecha.

Al filtrar por los 497.823 pares entregados tarde vemos que M04P el proveedor con mayor servicio tarde, 24'15% a pesar de ser el segundo proveedor con mayor volumen de ventas fabricado 18%. También se observa que la antelación de pedido baja aunque no es muy relevante y que el promedio de los partes tarde pasa a ser de 11 días tarde en su entrega.

Dentro de lo que ha llegado tarde se puede observar que los pedidos de stock predominan sobre los de clientes en un 60%-40% aproximadamente, algo relevante ya que ante la decisión de elegir que llega tarde es preferible que llegue tarde el stock antes que los clientes.

Si enfocamos solo en los 207.133 pares tarde de iniciales, vemos que de nuevo M04P es el primero con 30'4% y ahora por mayor volumen y mayor diferencia respecto al segundo. El resto de características se mantienen acorde al volumen.

Al filtrar por los pedidos tarde de stock se observa que el tiempo de antelación de pedido si se ve reducido notablemente a 126 días, una posible causa del motivo del retraso.

Proveedor a proveedor, viendo su incumplimiento respecto a sus respectivas producciones M04P supone un 14'4% siendo un valor intermedio a pesar de que como se ha visto en volumen absoluto es la que mas afecta. El peor proveedor en este caso seria Z12 con un 36'5% y el mejor X37 con un 6%.

Por lo que, para mejorar el % de incumplimiento los puntos a enfocarse serian:

 trabajar en aumentar la antelación de los pedidos sobre todo para el caso de los de stock. 
Enfocarse en los peores proveedores con mayor % particular de incumplimiento.
Enfocarse en M04P como proveedor que mas esta contribuyendo a traer pares tarde.



7. ✒️ Autor

    - Álex Candela Asencio