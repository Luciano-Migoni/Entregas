# Introducción

Los procesos simulados y los diseños computarizados son herramientas
fundamentales en la Ingeniería Industrial moderna porque permiten
analizar, optimizar y validar sistemas antes de implementarlos en la
realidad, reduciendo costos, tiempos y riesgos.

Los procesos simulados y los diseños computarizados constituyen pilares
de la Industria 4.0 porque permiten a los ingenieros industriales
diseñar, analizar y optimizar sistemas complejos de manera eficiente. Su
utilización contribuye a aumentar la productividad, mejorar la calidad,
reducir costos operativos y facilitar la innovación, convirtiéndose en
herramientas indispensables para la competitividad de las organizaciones
modernas.

## Importancia de los Procesos Simulados

La simulación consiste en construir un modelo virtual de un proceso,
sistema productivo o cadena logística para estudiar su comportamiento
bajo diferentes condiciones.\
Sus principales ventajas son:

- Reducir costos de prueba y error, ya que los cambios pueden evaluarse
  virtualmente antes de realizar inversiones reales.

- Mejorar la toma de decisiones, permitiendo comparar distintas
  alternativas de operación.

- Identificar cuellos de botella en líneas de producción, almacenes o
  sistemas de transporte.

- Optimizar recursos, como personal, maquinaria, materias primas y
  energía.

- Evaluar escenarios futuros, por ejemplo, aumentos de demanda,
  incorporación de nuevas máquinas o cambios en la distribución de
  planta.

- Incrementar la seguridad, al analizar situaciones potencialmente
  peligrosas sin exponer personas ni equipos.

Por ejemplo, antes de instalar una nueva línea de producción, un
ingeniero industrial puede simular diferentes configuraciones para
determinar cuál ofrece la mayor productividad con el menor costo.

# Desarrolo

## Industria Cervecera

Para ofrecer una introducción breve al analisis de la industria
analizada, hablaremos un poco acerca de la cerveza.\
La cerveza es una de las bebidas alcohólicas más antiguas y consumidas
del mundo, con una historia que se remonta a miles de años y una
presencia significativa en diversas culturas y mercados. Su producción
ha evolucionado desde métodos artesanales hasta complejos procesos
industriales altamente automatizados, capaces de elaborar grandes
volúmenes de producto manteniendo estándares rigurosos de calidad,
seguridad e inocuidad.\
En la actualidad, la industria cervecera constituye un sector de gran
relevancia económica debido a su impacto en la generación de empleo, el
desarrollo de cadenas de suministro y la demanda de materias primas
provenientes de la agricultura, como la cebada y el lúpulo. Además, los
avances tecnológicos han permitido optimizar las distintas etapas del
proceso productivo, mejorando la eficiencia operativa, reduciendo costos
y garantizando una mayor uniformidad en las características del producto
final.\
La elaboración de cerveza implica una serie de operaciones físicas,
químicas y biológicas que transforman materias primas seleccionadas en
una bebida con propiedades sensoriales específicas. Entre las
principales materias primas se encuentran el agua, la malta, el lúpulo y
la levadura, cuyos aportes individuales y su interacción durante el
proceso determinan aspectos fundamentales como el sabor, el aroma, el
color y la graduación alcohólica de la cerveza.\
El presente informe tiene como objetivo simular el proceso productivo
industrial de la cerveza, considerando diversas variables como
estaciones de trabajo (molinos, fermentadores, filtradores, envasadoras,
etc).

## Planteamiento del Problema

Al enfocar el análisis del presente informe hacia el modelado del
proceso y su simulación mediante herramientas digitales, requerimos de
conocer que nos moviliza a tomar la mencionada acción.\
La industria cervecera presenta un proceso productivo bastante rígido,
visualmente puede representarse mediante un diagrama de flujo de la
siguiente forma:\
![image](./Diagrama_de_flujo_Industria_Cervecera.png){width="100%"}

Para fines prácticos de la aplicación, el modelo se simplifica tomando
solo los siguientes pasos:\
![image](./Diagrama_de_flujo_Industria_Cervecera_2.png){width="100%"}

La idea es simular las etapas anteriores y poder identificar puntos
críticos. Por ejemplo, estaciones de trabajo donde existan cuellos de
botella, estaciones de trabajo con demasiado tiempo muerto, falencias en
la cadena, etc.

# Simulación

Para lograr un proceso bastante cercano a la realidad, se consideran los
siguientes criterios:

- Tiempos Críticos: Se tiene en cuenta la demora en los tiempos de cada
  estación (Recepción de materia prima, cocción, fermentación, etc.).

- Escalamiento Temporal: Capacidad del proceso de ejecutarse
  indefinidamente bajo condiciones ideales de trabajo.

- Mano de Obra: Especialización o Antigüedad, impacto directo en los
  tiempos de trabajo y errores cometidos.

- Integración de la demanda con la producción: Gestión en conjunto de
  los procesos de producción y comercialización.

- Evaluación de la Rentabilidad: Ajustar costos en función de los
  ingresos.

## Herramientas Utilizadas

Para desarrollar la simulación se utilizó el software SIMUL8\
SIMUL8 es un software comercial de simulación de eventos discretos que
se utiliza para modelar, visualizar y optimizar procesos reales.\
Su objetivo principal es servir como un laboratorio virtual para tomar
decisiones y probar cambios en un proceso antes de gastar dinero y
asumir muchos riesgos en implementaciones reales.

## Componentes de la simulación

El modelo se divide en dos bloques funcionales que representan la cadena
productiva y el sector comercial. Ambos bloques convergen a un punto en
común.\
Visualmente el proceso simulado tiene esta apariencia:\
![image](./Esquema_Simulacion.png){width="100%"}\
Se analiza entonces Cadena Productiva, Sector Comercial, Punto de
convergencia, Puntos de salida, Recursos Humanos y Costos.

### Cadena Productiva

Encargada de la elaboración de la cerveza.

- Materia Prima (Entry Point): Llegada de Materia Prima. Ingreso por
  lotes y una vez por semana laboral.

- Almacén de Entrada (Storage Bin): Recepción de Materia Prima. Dilata
  los tiempos de procesamiento de la materia prima.

- Elaboración del mosto (Work Center): Duración moderada. Agrupa las
  etapas de molienda y cocción, junto a sus costos.

- Almacén de Mosto: Dilata los tiempos de procesamiento del mosto. Evita
  saturar las instancias siguientes de la cadena.

- Fermentadores (Work Center): etapa central y de mayor duración del
  proceso. Requiere supervición constante.

- Macerador (Storage Bin): Duración prolongada, aunque inferior al
  fermentador. Ayuda a no saturar las etapas siguientes de la cadena.

- Filtrado (Work Center): Duración Breve. Supervición constante.

- Envasado (Work Center): Duración Breve. Operación constante.

- Etiquetado (Work Center): Duración Breve. Operación constante.

- Empaquetado (Work Center): Duración Breve. Operación constante.

- Despacho (Work Center): Duración Breve. Operación constante.

### Sector Comercial

Encargado de recibir ordenes de compra, gestionarlas, ordenar los
despachos y cobrar.

- Encargos (Work Entry Point): Ingreso de órdenes de compra.

- Recepción de pedidos (Storage Bin):Procesamiento de ordenes de compra.

### Punto de Convergencia

Punto de unión de las 2 cadenas principales (Producción y
Comercialización)

- Clasificación de pedidos (Work Center): Separar ordenes de compra
  según tipo de comprador (Mayorista o Minorista). Duración Moderada y
  operación constante. Reparticion 75/25 (Mayorista/Minorista)

### Puntos de Salida

Son aquellos puntos donde culmina el proceso y se comercializa el
producto. Es el punto de retribución económica del proceso (Ingresa
dinero por las ventas)

- Mayorista (Work Complete): Mayor retribución económica y mayor consumo
  de unidades producidas.

- Minorista (Work Complete): Menor retribución económica y menor consumo
  de unidades producidas.

### Recursos Humanos

Dado que cada etapa requiere de operarios, se tienen los siguientes:

- Operario de Producción (Resource): Cantidad 4. Exclusivos de la
  elaboración de mosto y de los fermentadores.

- Operario de Filtrado (Resource): Cantidad 1.

- Operario de Envasado (Resource): Cantidad 1.

- Operario de Etiquetado (Resource): Cantidad 1.

- Operario de Empaquetado (Resource): Cantidad 1.

- Transporte Interno (Resource): Cantidad 1.

### Costos

Se consideran costos de servicios (Luz, Agua, Gas, Internet, etc.),
costos de elaboración (Compra de materia prima y operación de
maquinaria), salarios, costos por incontingencias (reparaciones, etc.).\
Tras determinar costos fijos, se fijó un punto de equilibrio
determinando **egresos** por compra de materia prima, salarios
diferenciados en antigüedad y puesto, reparaciones, servicios, etc. e
**ingresos** por ventas.\
Se obtuvo el siguiente resumen a 52 semanas de servicio (aproximadamente
2 años laborales, sin contar feriados):\
![image](./Costos_Cervecera.png){width="100%"}\
\

## Detalles menores

Se ajustaron cuestiones como imagenes, conexiones entre componentes,
diseños, etc, con el fin de hacer visualmente agradable la simulación.\
Se utilizaron iconos de camiones para los puntos de entrada de materia
prima y ventas mayoristas, dinero para la venta minorista, personas para
los operarios, etc.\
Ésto le otorga identidad visual y personalización al proceso diseñado,
todo siempre utilizando la interfaz y las opciones de personalizacion
integradas en SIMUL8.\

# Funcionamiento Detallado

El modelo final integrado en SIMUL8 representa la combinación de flujo
físico de materia prima, reglas de negocio, restricciones laborales y
dinámicas comerciales solicitadas en la reingeniería del sistema.\
Debe tenerse en cuenta, como se mencionó anteriormente, que el sistema
se diseñó bajo supuestos que idealizaban los sistemas productivo y
comercial del proceso. En casos reales muchos factores eludidos deben
ser considerados para la correcta toma de una decisión, la evaluación de
la rentabilidad, optimizaciones y demás posibles acciones.\

## Análisis de Errores

Durante el desarrollo de la simulación, debieron ajustarse diversos
valores temporales, de costos, estructurales y demás.\
En un primer prototipo de la simulación, los tiempos esquematizados para
las etapas de fermentacion (120 horas o 7200 minutos) y elaboración de
mosto (4 horas o 240 minutos) generaban un cuello de botella importante
que hacía incluso que la simulación colapsara y se detuviera.\
En prototipos siguientes debieron ajustarse los costos, puesto que los
valores configurados generaban pérdidas millonarias al corto plazo y
recuperaciones muy escasas al largo plazo (una rentabilidad poco
atractiva).\
En los ultimos prototipos se terminaron de ajustar valores de la cadena
de suministro (tiempos de llegada de materia prima) y del sector
comercial (costos de empleados, costos de ventas, etc).\

# Conclusión

El desarrollo de la simulación del proceso productivo de la industria
cervecera permitió comprender de manera integral la complejidad de las
operaciones involucradas en la elaboración y comercialización de la
cerveza. A través del modelado de las distintas etapas productivas,
desde la recepción de materias primas hasta la distribución del producto
terminado, fue posible analizar la interacción entre recursos, tiempos
de proceso, capacidades operativas y variables económicas, evidenciando
la importancia de una gestión eficiente para garantizar la rentabilidad
y el correcto funcionamiento del sistema.\
La utilización del software SIMUL8 demostró el valor de las herramientas
de simulación dentro de la Ingeniería Industrial, ya que permitió
representar un entorno productivo cercano a la realidad, identificar
restricciones operativas y evaluar el impacto de diferentes decisiones
sin necesidad de intervenir físicamente sobre el sistema. Asimismo, la
simulación facilitó la detección de cuellos de botella, especialmente en
las etapas de fermentación y elaboración del mosto, permitiendo ajustar
parámetros operativos y mejorar el desempeño general del modelo.\
Por otra parte, el trabajo puso de manifiesto la relevancia de integrar
la gestión productiva con los procesos comerciales, los recursos humanos
y la estructura de costos, ya que el desempeño global de una
organización depende de la coordinación eficiente de todos estos
elementos. La evaluación de aspectos como tiempos de procesamiento,
utilización de recursos, demanda, costos e ingresos permitió obtener una
visión sistémica del proceso y comprender cómo pequeñas modificaciones
pueden generar impactos significativos sobre la productividad y la
rentabilidad.\
Finalmente, se concluye que los procesos simulados constituyen una
herramienta fundamental para la mejora continua y la toma de decisiones
en entornos industriales complejos. En el caso de la industria
cervecera, la simulación permitió validar hipótesis, optimizar recursos
y anticipar problemas potenciales, demostrando que el uso de tecnologías
digitales y diseños computarizados resulta indispensable para aumentar
la competitividad, reducir riesgos y favorecer el desarrollo de sistemas
productivos más eficientes y sostenibles.
