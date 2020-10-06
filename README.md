**Arquitectura de microservicios**

José Santos Salvador

1.  **Introducción a los servicios web y microservicios**

Los **servicios web** son aplicaciones accesibles por un protocolo web estandar (HTTP), permitiendo la comunicación entre otros programas, se encajan dentro de SOA (service-oriented architecture). La información que procesan hace uso de XML o JSON entre otros, los clientes acceden al servicio mediante mensajes formateados con XML. Todo ello gracias al protocolo SOAP (o REST) que permite usando XML empaquetar mensajes. Para la interacción con los cliente, se hace uso de IDL y WSDL para describir los servicios disponibles y definir la interfaz .Y se usa UDDI; servicio de directorio para publicar y encontrar servicios web.

**Microservicios** se denomina a una aplicación que contiene una colección de pequeños servicios, los cuales se comunican mediante mecanismos ligeros (API con recursos HTTP). Estos servicios son independiente y se encargan de una funcionalidad concreta, con una gran capacidad para poder ser mantenidos, lanzados y testados de forma unitaria, siendo esta una de sus principales diferencias respecto a los servicios web o SOA \[3\].

Son un subtipo de SOA, mientras que SOA(service-oriented architecture) normalmente está relacionado con SOAP, WSDL. Los microservicios por su parte lo están con REST y HTTP, se aplican para construir una solución individual y SOA como una solución de integración \[4\].

Cuando hablamos de servicios (Web Services), lo hacemos con una granularidad gruesa y cuando hablamos de microservicios lo hacemos con granularidad fina. El diseño Web Services normalmente está construido sobre Java EE que en esencia es una gran aplicación monolítica. Una API de pago se divide en microservicios para este diseño y la API sirve como fachada (facade), a diferencia del servicio web que lo hace todo la misma aplicación, la API de pago de microservicios, llamará al servicio de cliente para obtener su información, obtendrá la cuenta del servicio de cuenta para el saldo y verificará el cliente con el servicio de autenticación (para un análisis más profundo de las diferencias entre SOA y MSOA \[13\]). La principal diferencia está en que los microservicios son independientes y los servicios no.

A lo largo de los siguiente apartados, se hablará de lo que es un diseño basado en microservicios y las ventajas que puede tener respecto a otros diseños (como puede ser Web Services y monolítico), así como sus principales diferencias.

1.  **Microservicios**

El término de microservicios o microservicio es difícil de definir y una de las formas más correctas de hacerlo es explicando y analizando sus características, no es necesario que las contenga todas pero si son las más comunes. Tanto los microservicios (o por lo menos surgieron de ahí) como web services son SOA.

SOA es un diseño que se basa en múltiples servicios colaborando para proporcionar una serie de funcionalidades. La comunicación entre estos servicios se realiza mediante llamadas a través de la red. Surgió como enfoque para los problemas de las grandes aplicaciones monolíticas, su objetivo es promover la reutilización del software y facilitar su mantenimiento. Es una buena idea de diseño pero en la práctica no se ha consensuado como hacer bien este diseño SOA. Uno de sus problemas es la falta de explicación a cómo dividir una aplicación, formas de garantizar que los servicios no se acoplen. Y todo esto es lo que trata de solucionar el diseño de microservicios.

Este enfoque de microservicios ha surgido del mundo real, de la práctica para realizar una arquitectura SOA de forma correcta.

1.  1.  **¿Qué son los microservicios? - Características**

Un sistema basado en microservicios sigue un modelo de servicios por componentes. Siendo un componente una unidad software que es reemplazable y actualizable de forma independiente.

Los microservicios están compuestos de componentes que se comunican con un mecanismo ligero (petición web, RPC, etc). La principal razón de usar los servicios como componentes es que los servicios se pueden desplegar independientemente. Si tienes una aplicación con múltiples librerías, tendrías que desplegar la aplicación de forma completa. Otra característica los microservicios, es la interfaz explícita que dan los componentes y que algunos lenguajes no tienen \[5\].

Un servicio puede estar compuesto por múltiples procesos que trabajan y se implementan juntos. Para un desarrollo software basado en microservicios, es necesario que cada equipo que se encarga de un servicio sea multidisciplinar y no en equipo de trabajo divididos por funciones (como puede ser en un desarrollo monolítico con las líneas de negocio que puede ser el equipo de middleware, BD o de interfaz de usuario), esto provoca que en los microservicios se agilice el proceso de desarrollo y un cambio simple no supondría tanto tiempo como en los SOA \[6\].

Otra de las características de un desarrollo basado en microservicios consiste en eliminar la idea de que cuando acabas el software, pasa un equipo de mantenimiento y el equipo que lo ha creado se olvida. El equipo de desarrollo se hace responsable del software en producción. Y este mantenimiento se reduce su complejidad debido a la arquitectura modular del sistema de microservicio.

Para la comunicación hace uso de un estilo de diseño llamado; smart endpoints and dumb pipes. Las aplicaciones en los microservicios tratan de ser lo más desacopladas y cohesivas posibles. Reciben una petición, aplican una lógica y producen una respuesta. Utilizan protocolos REST y los más usados HTTP request-response con recursos APIs y mensajería ligera.

El control en las aplicaciones basadas en microservicios, está descentralizado y esto permite utilizar distintas tecnologías para cada solución (servicio de pago podría usar una tecnología y el servicio de atención al cliente otra), permitiendo así mayor flexibilidad al ahora de abordarlas. Esto provoca también que haya una gran escalabilidad, ya que las mejoras o cambios se realizan por microservicios y si hay un problema de cuello de botella, es cuestión de actualizar ese servicio en concreto y no todo el sistema.

Así como el control, también se descentraliza la gestión de los datos usando el enfoque; Domain Driven Design (divide un dominio complejo en múltiples contextos delimitados y se marcan las relaciones entre ellos). Se beneficia más del diseño en microservicios ya que hay una correlación entre servicio y contexto y además descentralizan las decisiones de almacenamiento.

Al usar los servicios como componentes, las aplicaciones tienen que estar diseñadas para garantizar tolerancia a los fallos. Es importante poder detectar estos fallos de forma rápida para recuperar el servicio, usando un monitoreo en tiempo real de cada servicio de la aplicación con el fin de solventar este problema.

Muchos de estos enfoques pueden llevarse a cabo en un desarrollo para un servicio web (SOA), sin embargo la granularidad más pequeña de los microservicios, lo facilita aún más.

El uso de microservicios permite tener una funcionalidad degradante (tolerancia a los fallos) y permite que aunque falle por ejemplo un microservicio, mantener el resto funcionando, dando ventaja respecto a otros diseños.

Algunas de las desventajas que pueden presentar los microservicios son; los sistemas distribuidos son más difíciles de programar y las llamadas remotas pueden fallar, mantener una consistencia fuerte en este tipo de sistema es una tarea ardua y deben manejar por tanto una consistencia eventual y se necesita un equipo con experiencia capaz de administrar los servicios que se están redistribuyendo regularmente. (He decido no seguir hablando de los microservicios porque podría alargarse mucho, para saber más Capítulo 1 referencia 7).

1.  **Construcción de un sistema basado en microservicios**

A lo largo de este apartado se hablará de los principios, técnicas, reglas y tecnologías a usar en un diseño basado en microservicios, todo ello ilustrado por algunos ejemplos.

1.  1.  **Decisión sobre el uso de un diseño basado en microservicios**

El diseño de una aplicación basada en microservicios, no es una tarea fácil y aunque ha ganado mucha popularidad hay que analizar bien si este diseño es el más conveniente para nuestro caso, si necesitamos una gran modularidad, desarrollo independiente gracias a los servicios o una gran diversidad tecnológica, los microservicios pueden ser nuestra solución.Los microservicios son un tipo de diseño flexible, si nuestra visión tiene muchas restricciones quizás no es una elección.En el caso de que nuestra aplicación tenga una gran complejidad, realizarla sobre un diseño basado en servicios o monolítico, provocaría un gran esfuerzo en mantenimiento y poca escalabilidad. En este caso un acercamiento a los microservicios podría funcionar. Casos como The Guardian \[5\] que aún manteniendo su núcleo monolítico, hace uso de los microservicios para nuevas funcionalidad y comunicación o Netflix. Sin embargo, habría que lidiar con las desventajas de los microservicios y si no somos capaces de por ejemplo asumir una tolerancia a los fallos, no es recomendable hacer uso de microservicios. Una de las formas de llevar a cabo esta decisión consiste en hacer una encuesta al equipo sobre algunos aspecto y requisitos no funcionales (requisitos de calidad) y en función de la importancia numérica que le den, decidir si los microservicios son la mejor opción para satisfacerlos o se adaptan bien a estos \[7\].

Tras realizar esta encuesta e identificar los posibles problemas para su diseño, se obtiene un tercer informe sobre los beneficios que trae este diseño a nuestro objetivo y se decide su uso. Estos pueden ser:

Mejorar del matenimiento, mejora de la escalabilidad, reducción de la complejidad de la arquitectura, simplificación del trabajo distribuido, mejora del rendimiento, testeabilidad y separación de responsabilidades, responsabilidad claras y únicas.

Otra de las técnicas utilizadas se basa en un proceso de respuesta a una serie de cuestiones, ¿Cuáles son las propiedades claves de MSA(arquitectura de microservicios)?, ¿Cómo MSA guía el análisis arquitectónico?. \[5\] figura 1.

1.  1.  **La figura del arquitecto en el diseño**

Cuando comienza el diseño del sistema, coge una gran importancia el papel del **arquitecto**, que se centra más bien en qué pasa entre servicios o grupos de servicios. Dentro de cada servicio puedes permitir el uso de una tecnología diferente o un tipo de almacenamiento diferente para llegar a una mejor solución, el problema puede llegar a la hora de mantener 10 tecnologías diferentes, siendo complicado contratar a personas o mover entre equipos (de otros servicios). La experiencia puede complicar el proceso de escalado a la hora de tener diferentes tecnologías de almacenamiento. Netflix por ejemplo trabaja sobre Cassandra y prima el valor de desarrollar herramientas y soluciones en torna a esta que trabajar con distintas tecnologías a las que mantener y soportar para escalar. Este ejemplo saca a relucir que la gran importancia que tiene la escalabilidad en este empresa y cómo se ajusta el diseño de microservicios a cada caso concreto.

El foco de atención del arquitecto ha de estar en las posibles comunicaciones e intercambios entre servicios, pudiendo ser una tarea compleja si por ejemplo un servicio usar REST a través de HTTP, otro hace uso de protocolos de buffer y el último usa Java RMI.

Es importante señalar que el arquitecto también debería unirse a los distintos equipos, trabajar periodos de tiempo y observarlos, con el objetivo de crear un sistema comprensible y legible \[3\] \[17\].

El arquitecto ha de tener un visión global del sistema y ser capaz de ver las desviaciones de nuestra visión técnica y ser capaz de controlarlas y equilibrarlas (gobernancia \[12\]).

1.  1.  **Estrategia global, principios y prácticas**

Durante el proceso de diseño se han de tomar ciertas **decisiones **como ya se han ido viendo en función de nuestro caso, para poder hacerlas de forma correcta se profundiza en una serie de apartados.

La estrategia global viene impuesta por la compañía y es el objetivo que se tiene que lograr, compuesta por varios objetivos. Mientras que los **principios **son reglas que pueden cambiar y que te acercan a ciertos objetivos. Si uno de los objetivos es disminuir el tiempo para crear nuevas funcionalidades en la aplicación, se podría definir un principio por el cual un equipo tenga control absoluto del ciclo de vida de su software para enviar cuando puedan sin depender de otros equipos (visión de microservicios comentada con anterioridad). Es recomendable tener un número bajo de principios para que que no creen contradicciones entre ellos y los empleados puedan recordarlos. También se puede usar de forma complementario los principios de diseño de Heroku’s 12 Factor (archivo JSON con dependencias) \[8\].** Las prácticas **nos sirven como herramienta para llevar a cabo estos principios. Si uno de nuestros principios es que el equipo tenga el control del ciclo de vida de nuestro sistema, para llevarlo a cabo se usará una práctica en la que todos los servicios apunten a cuentas AWS que proporcionan autogestión de los recursos y aislamiento de equipos.

Otro ejemplo podría ser en el que tuviésemos un principio por el cual cada equipo se encarga del ciclo de vida del software, donde se comparten las responsabilidades (tal y como hemos visto anteriormente), entonces cuando crea este software, no se lo delega a otro equipo de mantenimiento y para llevar a cabo esta práctica se puede hacer uso de **DevOps**. Para ello hace falta que no existan silos (servicios o componentes que no se comunican con el resto de servicios \[9\]) entre desarrollo y operaciones, trata de desdibujar los roles del desarrollador y el personal de operaciones. Otro requisito básico para usar DevOps es la autonomía de los equipos para posibilitar probar los nuevos cambios y colaborar eficazmente. Por ejemplo se puede tener una nueva funcionalidad y usando el control de versiones como git, se puede añadir a este sin la firma y así acelerar los **ciclos de prueba**.

Tambíen se puede ver que se cumple otro requisito como puede ser la facilidad para añadir nuevo código en producción, para asegurar y valorar la calidad de la construcción en el proceso de desarrollo se pueden usar técnicas como Continuos Deliver (garantiza la configuración necesaria para avanzar en la producción) y SelfTestingCode.

Si al pasar el tiempo, nuestros sistemas se desvían de nuestros principios y prácticas, habrá que adaptarlo al mundo real y a la situación.

1.  1.  **Supervisión de los objetivos**

Todas estas guías de diseño se tienen que cumplir y una forma de hacerlo es proporcionar ejemplos perfectos para que la gente pueda verlo en código (siendo más atractivo que la documentación para algunos desarrolladores). Así mismo se pueden usar plantillas de servicio a medida que permite a los desarrolladores tener todo el código que necesitas. Se pueden usar tecnologías como Dropwizard and Karyon JVM basadas en microcontenedores, permitiendo tener un servicio completo (métricas, monitorización, HTTP) para ser lanzado desde línea de comandos. Por ejemplo puede pasar que necesites mandar todas tus métricas a un servidor Graphite, usando una librería como Dropwizard’s Metrics configura para ello. Con esto los equipos de trabajo lo hacen de forma más rápida y te aseguras de que se realiza un correcto comportamiento. Hay que tener cuidado porque puede ser una forma de imponer ciertos lenguajes en los equipos. Netflix por ejemplo es centra más bien en la tolerancia de fallos y si una persona quiere utilizar una nueva tecnología tiene que reproducir todo el esfuerzo previo que se ha hecho sobre la tecnología antigua y su plantilla \[11\].

1.  1.  **Modelando servicios**

Tenemos una empresa llamada Musiclandia dedicada a la música que con el cambio del mercado, sus esfuerzos se han centrado en el mercado online y han decido que la mejor opción es usar un diseño basado en microservicios para realizar los cambios de la mejor forma posible, invirtiendo en un equipo software experto (empleados) en este tipo de diseño en lugar de invertir ingentes cantidades de dinero en equipos muy caros que no va a saber usar el equipo actual y facilitar ese cambio en la medida de lo posible a los empleados actuales. Su principal objetivo es la escalabilidad (ya que como han visto con spotify y la caída de los vinilos que todo cambia muy rápido), disponibilidad y mantenimiento (su actual servicio les hace perder mucho tiempo y apenas pueden dedicar sus esfuerzos en nuevas funciones). Y por supuesto un bajo acoplamiento y alta cohesión.

Para realizar un buen diseño basado en microservicios es necesario tener un **bajo acoplamiento y una alta cohesión**, con el objetivo de delimitar el comportamiento de un servicio y que no se una estrechamente con otro, para que a la hora de realizar cambios en los servicios, no se tenga que cambiar en más lugares, facilitando estos cambios y el tiempo invertido (en contraposición a otra técnicas de diseño donde la granularidad es más alta y es difícil de cumplir esto) y permitiendo reutilizar código.

1.  1.  1.  **El contexto**

Ya hemos hablado antes del** Domain-Driven Design (DDD)**, en el caso de Musiclandia tenemos que nuestro dominio es todo el negocio en el que operamos, al dividir este dominio podemos obtener una parte que gestiona los pedidos, departamento de finanzas, gestión de empleados, gestión de clientes, etc. Por ejemplo tenemos que el departamento de finanzas y el almacén tiene dos contextos limitadas separados. Tienen un interfaz con el mundo exterior y es la que usan el resto de contexto para obtener información, el departamento de finanzas no necesita saber cómo funciona el almacén, pero necesita saber información sobre los niveles de existencias. Hay veces que es necesario compartir ciertos modelos (una representación externa) para el correcto funcionamiento mediante intercambio de información .** Esta técnica facilita el bajo acoplamiento al decidir qué modelos compartir y los límites dentro de estos. Estos límites se convierten en perfectos candidatos para microservicios. **Los microservicios tienen que alinearse con contextos delimitados.

Estos contextos a su vez pueden ser divididos en más contextos con un grano más fino y aquí reside una de las ventajas de los microservicios y que otras técnicas de SOA no te aportan (Web Services). El almacén puede ser descompuesto a su vez en recepción de mercancía, gestión de productos defectuosos, etc.

1.  1.  **Integración**

Es vital la elección de la tecnología de integración que se va a usar en los microservicios. Y mantener las API utilizadas para la comunicación entre servicios independientes, es importante para evitar que éstas dicten las tecnologías a usar para la integración.

Pensando en el ejemplo de Musiclandia, la forma más común de integración es mediante un BD (tal y como se hace en Web Services normalmente) de integración y relacionar con esta los distintos servicios. Imagínate que tienes un nuevo cliente, sería tan fácil como añadirlo a la base de datos por el servicio de registro y a su vez cualquier otro servicio que necesite ese información accede a la BD. El principal problema de esto, es que está muy ligada la implementación del servicio de clientes con los clientes, así como “obligando” una tecnología (ligado a BD relacional por ejemplo), eliminando el** bajo acoplamiento** (se pierde la autonomía a la hora de cambiar nuestro componentes internos al exponer la implementación a los clientes) y la **cohesión **(ya que los clientes tienen la lógica de la BD y puede cambiarla).

1.  1.  1.  **Comunicación entre servicios**

La comunicación puede ser asíncrona o síncrona y dependiendo esto se hará uso de un diseño **respuesta/petición** (funciona para ambas) y** basada en eventos **(de una carácter más asíncrono) más relacionada con la nuevas tecnologías y dispositivos móviles.

1.  1.  1.  **Gestión de servicios**

Existen dos estilos arquitectónicos para realizar la gestión, orchestration (un servicio central que guía al resto) y choreography (se informa al resto de sistema y cada uno actúa en base a eso).

Con Musiclandia, se podría usar un estilo arquitectónico de choreography, si se registra un nuevo cliente, el servicio de clientes crea un evento y el resto de servicios se suscriben y actúan de forma correcta (el servicio de correo le envía un correo a nuevo cliente por ejemplo). Esto permite un mayor desacoplamiento, más flexibles y fáciles de cambiar, pero con un costo mayor en monitorización y rastreo como es lógico, ya que este estilo se ve beneficiado del carácter asíncrono de un diseño basado en eventos.

Para un diseño respuesta/petición, se pueden usar tecnologías como RPC y Rest. Ambas tecnologías puede tener algunas desventajas para un acercamiento a los microservicios, usando Rest hay que tener cuidado porque puede provocar un acoplamiento alto (como pasan en servicios Web) y RPC puede atarte a ciertas tecnologías \[6\].

Un diseño asíncrono basado en evento puede hacer uso de una tecnología como RabbitMQ para emit eventos y que los clientes pueden encontrar esos evento y ver qué ha pasado para reaccionar. El uso de esta tecnología conlleva una complejidad inherente en el desarrollo de procesos porque es otro sistema que hay que desarrollar y testear pero te da escalabilidad y resiliencia. También se puede usar ATOM.

1.  1.  1.  **Integración con compañías externas**

Para lograr integrar nuestros microservicios con código y software de compañías externas, un patrón útil es el Strangler Application Pattern \[14\]. Se sigue el principio de inversión de dependencias de SOLID, dependiendo de cosas/clases abstractas y no concretas, dependiendo de una almacén de datos y no de una base de datos concreta. Y en nuestro con Musiclandia este almacén de datos se inyecta en la clase o sistema que gestiona la información de los artistas y álbumes para mostrar.

1.  1.  1.  **Migración de Monolítico a Microservicios**

Hay libros enteros hablando de esta migración o cambio \[16\] pero para hablar un poco sobre nuestro caso Musiclandia, lo primero que hay que realizar es identificar los contextos de nuestro sistema (DDD), crear paquetes que los representen y mover su funcionamiento ahí (hay muchas tecnologías que te ayudan con esto mediante refactorización) y luego testear y comprobar que no haya ningún error con este cambio. Musiclandia tiene cuatro contexto que se puede obtener de este sistema monolítico, catálogo, finanzas y clientes. Y también habrá que realizar una descentralización de la base de datos permitiendo que cada servicio maneje su propia base de datos (diferentes instancias de la misma base de datos o base de datos diferentes). Para manejar las actualizaciones (updates) en las base de datos de los clientes por ejemplo, se hace uso de transactions para garantizar la consistencia. Usar las transactions impone un acoplamiento temporal y algunas veces se opta por trabajar con estas inconsistencias (mecanismo de gestión de errores) para manejar una mayor rapidez de respuesta a la demanda.

1.  1.  **Despliegue**

1.  1.  1.  **Integración continua**

Con ella se intenta mantener todo sincronizado, asegurando que el código recién registrado se integre con el código existente. Para esto el servidor detecta que el código se ha subido, lo comprueba, realiza las verificaciones necesarias como compilar y que pasen los tests necesarios. Se usan herramientas de control de versiones como Git y sus ganchos. Musiclandia necesita mantener los fallos reducidos al mínimo y tener la seguridad de que cuando se lance este nuevo cambio, no va a producir errores de última hora, por eso la integración continua soluciona muchas de estas necesidades, además de tener un mayor control en que está pasando y desarrollando. Ya que al usarla, los errores de última hora para la fecha de entrega se minimizan y se puede integrar con pruebas unitarias o tests y monitorización continua (como se aborda en los siguientes puntos). Para nuestro caso se hará uso de la tecnología Git (también de Github) y Travis para poder llevar a cabo esta integración. También se ha escogido Git porque al ser popular, es más fácil que los empleados que ya estaban en Musiclandia se puedan pasar a este tecnología sin muchas dificultades.

 Los beneficios que trae son; retroalimentación en la calidad del código, creación de artefactos, nivel de trazabilidad.

La integración continua en los microservicios trata de resolver cómo asignar microservicios individuales a las build de la integración continua y al código fuente. Con el objetivo de permitir cambios en los servicios de forma independiente.

Hay varios enfoques para esto tener una única build de integración continua para todo el código o tener una variación de este con un solo árbol fuente y con múltiples asignaciones de build.

Pero el enfoque que más ventaja puede sacar de los microservicios es tener una build por cada microservicios que nos permita realizar cambios y validarlo. Y los test se ejecutan de forma específica para cada build del microservicio.

1.  1.  1.  **Entrega continua (continuous delivery)**

Con la entrega continua se usan pipeline para las pruebas más rápidas y una para las más lentas. Nos permite rastrear el progreso de nuestro software de forma clara en cada etapa. Obtenemos feedback constante sobre la producción. También es importante seguir un versionado semántico (MAJOR.MINOR.PATCH), todo ello además con el patrón de Expand and Contract. Branch by Abstraction es de especial utilidad para Musicalandia ya que le permite hacer cambios a gran escala de forma gradual e ir publicando esos cambios poco a poco.

1.  1.  1.  **Contenedores o imágenes (de lo físico a lo virtual).**

A la hora de usar técnicas como la integración continua, si como parte del desarrollo es necesario instalar las mismas herramientas o dependencias todo el rato, se convierte en una pérdida de tiempo. Una forma de reducir este tiempo es crear una imagen con todas las dependencias que se usan y lanzarla cuando se necesite. Este acercamiento puede presentar un inconveniente debido al gran tiempo que puede llevar crear una imagen o el tamaño de las mismas. Para ello se usa la tecnología de contenedores (Docker), donde se palian todas estas desventajas mediante el uso de contenedor en vez de imágenes. También ayuda a la hora de ejecutar muchos servicios con objetivos de desarrollo y prueba como pueden ser los test automáticos en Travis, ya que reduce su tiempo.. Docker por sí solo no permite solucionar todo lo que se necesita para un diseño en microservicio, es necesario un orquestador como Kubernetes que nos dote de una capa. Como se ha ido mencionando, este tipo de tecnologías encajan de una forma muy sencilla con el diseño en microservicios. El uso de contenedores en lugar de imágenes, beneficia de forma directa nuestro caso de Musiclandia, ya que es una empresa de música que no tiene mucha capacidad de cómputo detrás, por lo tanto la rapidez de los contenedores es ideal para este caso y también se beneficia para el testeo.

1.  1.  **Testeo**

El uso de todas las tecnologías ya comentadas (integración continua, control de versiones, etc) se integran de forma muy natural con la automatización de tests. Todo ello con el objetivo de testear servicios concretos y aislarlos del resto para su desarrollo independiente y ágil. Hay muchos tipos de tests, definiciones o clasificaciones. Realizar este testeo en sistemas monolíticos es bastante más complicado.

Hay un modelo llamado Test Pirámide \[15\], que nos dice que test automáticos podemos necesitar.

Los **test unitarios** nos permite comprobar una función concreta o una llamada a un método, son rápidos y es recomendable tener bastantes. ** Los test de servicios**, comprueban un servicio concreto sin colaboración externa, para eliminar esta colaboración externa es necesario hacer uso de técnicas como mocking o stubbing. Puede ser igual de rápidos que los unitarios pero encontrar el fallo es algo más difícil de encontrar. **Los test end-to-end **se usan para comprobar el sistema completo (son el último punto de la pirámide). También mencionar los test de cobertura que miden cuánto código está cubierto por tests.

En Musiclandia se hará uso de test automáticos mediante Travis y Github Action como ya se ha comentado siguiendo TDD (test driven de development), con el objetivo de conseguir un software de calidad y testeado. Es de especial importancia dado nuestro caso, los **test de integración** (se usa esta terminología porque hay diversas discusiones con el término) ya que es necesario comprobar que la integración sea correcta.

1.  1.  **Monitorización**

Uno de los retos asociados al uso de microservicios y su naturaleza de grano fino. Teniendo que monitorizar e identificar donde ocurren los problemas. La clave para este control reside en monitorizar las cosas pequeñas y mediante agregación tener la imagen completa y global.

La estrategia comienza con un único servidor por servicio, se aumenta la abstracción y tenemos un servidor para múltiples servicios (y sus servidores) con un balanceo de carga. Y por último múltiples servicios con múltiples servidores. Kibana es un sistema de seguridad para ver registro y que puede facilitar el trabajo con toda la cantidad de registros que se puede generar con este sistema de monitorización.

1.  1.  **Seguridad**

Musiclandia no tenía muy en cuenta la seguridad y todo se envía por HTTP, como podía ser la comunicación entre el navegador, la página web y el catálogo o el servicio de proveedores. Para la información de los datos del catálogo (discos en stock, artistas y álbumes) queremos que se comparta y para ello se usan API Key y poder controlar quien las usa. Respecto al navegador se usa una combinación de HTTP estándar para contenido no seguro y permitir que se almacene en caché. Para las páginas seguras y conectadas se enviará a traves de HTTPS para proteger a los clientes. El sistema de pago es de una compañía externa (hay que tener cuidado con esto). En la seguridad de la red interna, se hace uso de firewall configurado para verificar tráfico malicioso (escaneo de puertos, etc). Para los datos de nuestros clientes y proveedores, se cifran estos datos para protegerlo de posibles ataques. Mencionar también el uso de tecnologías como SAML o OpenID Connect para la autenticación y autorización de clientes y hacer uso de API keys para por ejemplo mostrar el estado de los pedidos o el rastreo, confiando en estas llamadas porque se han hecho desde nuestro ámbito. Sin embargo es necesario una especial atención al *confused deputy problem* que se tiene.

1.  1.  **Tolerancia a los fallos**

Un patrón que se usa para aislar los fallos es Bulkeads. En un envío bulkead es una puerta que se puede cerrar para proteger el resto del servicio, entonces si tienes una fuga, puedes cerrar estas puertas, pierdes información pero salvas el resto.

1.  **Conclusión**

Tras todos estos puntos, queda claro el concepto de microservicios y las ventajas y cambios que puede provocar respecto a otro diseño SOA como los servicios Web. A lo largo de este trabajo he conseguido ver la importancia y ventajas que tiene este diseño basado en microservicios. No es que este diseño sea el futuro y todo se va a convertir en microservicios, el resto de soluciones se mantendrán, lo que hace tan bueno a este diseño es la versatilidad que ofrece en contraposición a otros, permitiendo utilizar de forma natural muchas nuevas tecnologías, patrones, metodologías o diseños que se integran bien conjuntamente, frente a la rigidez de los servicios web. Sin embargo para poder aprobar este diseño es necesario realizar un estudio sobre los requisitos (tal y como hemos visto con los no funcionales) y decidir si se le va a sacar partido. Para ello es necesario tener a un equipo de personas con experiencia en este tipo de diseños, ya que realizar un mal diseño de microservicios puede provocar un caos. Prestando especial atención en no alinar este diseño si no encaja con nuestra empresa (tal y como dice la ley de Conway). Con algunos esfuerzos adicionales en la monitorización, rastreo de fallos (algo más complejos de identificar) y tolerancia a estos, que no suelen presentarse en otros diseños.

1.  **Autoevaluación**

<!-- -->

1.  **¿La explicación es clara y el contenido está estructurado?**

La explicación comienza con una breve introducción de los temas centrales, SOA, Servicios Web y microservicios. Después se desarrolla de forma más completa los microservicios y sus características. Tras esto se habla de la creación de un sistema basado en un diseño de microservicios y se da una conclusión. Una estructura clara y ordenada.

1.  **¿Queda reflejado que se han estudiado y entendido las cuestiones de diseño cliente/servidor, modelos de replicación, metodologías de desarrollo, arquitecturas dirigidas por eventos, tecnologías middleware, etc, contenidas en la bibliografía proporcionada para las clases?**

A lo largo de todo el trabajo se hace uso de estos términos en el contexto que nos acontece con los microservicios, demostrando así el entendimiento de los mismos fuera de las explicaciones de teoría.

1.  **¿Queda reflejado en el trabajo que se ha buscado y analizado suficiente bibliografía adicional y se ha comparado/contrastado la información entre las diferentes referencias encontradas (incluidas en el informe) y con la bibliografía proporcionada para las clases? **

Queda reflejado la biografía adicional que se ha usado, siendo de especial importancia la calidad de la misma. La mayoría referente dentro de este tema de los microservicios como la página de MartinFowler que es referenciada en la mayoría de páginas sobre microservicios (como he podido comprobar, al final siempre acaba en MartinFowler, por ejemplo desde artículos de IEEE). Haciendo uso también de libros de O'Reilly que he podido leer y usar por la

1.  **¿La conclusión final a la que se ha llegado en el informe ha sido resultado de un estudio y análisis en profundidad y ha requerido una aportación extra por mi parte? **

La conclusión ha sido el resultado del estudio y análisis de los microservicios, he tenido que reflexionar sobre todo lo estudiado y leído y llegar a la aportación de que los microservicios tienen grandes ventajas, en especial su versatilidad pero que también hay inconvenientes y no en todos los casos hay que usarlo. Ya que en la mayoría de sitios solo hablan de sus bondades.

1.  **¿El informe realizado me ha llevado tiempo y servido para comprender la solución al problema abordado? **

El desarrollo de este informe me ha permitido comprender de una forma bastante precisa, lo que son los microservicios y cómo puede cambiar el panorama actual. Así como ilustrar de una forma clara, el uso de ciertas tecnologías como los contenedores, la integración continua y los test automáticos (Travis, etc) que tanto se escuchan. Todo ello con el objetivo de de dar solución al problema planteado

1.  **¿Se ha realizado alguna aportación adicional más allá de lo que en esencia pedía este trabajo? **

Creo que he realizado un diseño bastante completo desde cero, enfocandome en los principales puntos de un diseño en microservicios (algunos los he omitido por falta de páginas) y no solo me he quedado en explicar qué son los microservicios como se pedía, también he hablado del uso de ciertas tecnologías, buenas prácticas, posibles fallos y todo ello buscando en libros sobre el tema.

La calificación numérica que me pongo por este trabajo es: 9

**Bibliografía**

1.  Coulouris, G. Dollimore,J. Kindberg, T. 1998. *Distributed Systems: Concepts and Design. *Addison Wesley.
2.  Larrucea,X. Santamaría,I. Colomo-Palacios,R. Ebert,C. Microservices. IEEE. [*enlace*](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8354423)
3.  Francesco,P. Architecting Microservices. IEEE. [*enlace*](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=7958492)
4.  Bakshi,K. Microservices-Based Software Architecture and Approaches. IEEE. [*enlace*](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=7943959)
5.  Characteristics of a Microservice Architecture, [*enlace*](https://www.martinfowler.com/articles/microservices.html#CharacteristicsOfAMicroserviceArchitecture)
6.  Newman,S. 2014. *Building microservices. *O'Reilly.
7.  Taibi,D. Lenarduzzi,V. Pahl,C. Processes, Motivations, and Issues for Migrating to Microservices Architecture [*enlace*](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8125558&tag=1)
8.  The Twelve-Factor App, [*enlace*](https://www.12factor.net/)
9.  DevOps Culture, [*enlace*](https://www.martinfowler.com/bliki/DevOpsCulture.html)
10. Branch By Abstraction, [*enlace*](https://martinfowler.com/bliki/BranchByAbstraction.html)
11. [*https://netflix.github.io/*](https://netflix.github.io/)
12. Governance ensures that enterprise objectives are achieved by evaluating stakeholder needs, conditions and options; setting direction through prioritisation and decision making; and monitoring performance, compliance and progress against agreed-on direction and objectives. COBIT 5
13. Differences Between Model-driven Development of Service-oriented and Microservice Architecture, [*enlace*](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=7958454&tag=1)
14. Strangler Application, [*enlace*](https://martinfowler.com/bliki/StranglerFigApplication.html)
15. Cohn,M. 2009. *Succeeding with Agile*. Addison-Wesley.
16. Newman,S. 2014.* Monolith to microservices. *O'Reilly.
17. The Joel Test, [*enlace*](https://dev.to/checkgit/the-joel-test-20-years-later-1kjk)
