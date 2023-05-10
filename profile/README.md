## Desafío elegido y el valor de la solución
Hemos elegido la sostenibilidad como tema para este proyecto, con el objetivo de hacer frente a los desafíos ambientales y sociales que enfrentamos en el mundo actual. La sostenibilidad implica la búsqueda de un equilibrio entre la protección del medio ambiente, la equidad social y el crecimiento económico a largo plazo, con el fin de garantizar la satisfacción de las necesidades actuales sin comprometer las posibilidades de las generaciones futuras.

### La solución
Nuestra propuesta es un sistema que recolecta datos de distintas webs mediante scraping web, los guarda en base de datos y los muestra de manera gráfica en una interfaz web interactiva. Para tener un foco más claro en la búsqueda de esos datos nos hemos centrado en movilidad, concretamente en valores de interés para mostrar la viabilidad que tendría el uso de carpooling en una comunidad universitaria, concretamente en Mallorca, ya que donde exista esta necesidad hay un problema de movilidad.

Además tener este foco nos permite preguntar directamente sobre la valoración que tiene el público joven sobre coches, transporte público, sus precios, su accesibilidad, etc. Al plantear una situación específica evitamos quedarnos con una pregunta abierta sobre movilidad y sostenibilidad, que a muchos jóvenes les podría costar responder.

Así que en términos generales tenemos como objetivo obtener la siguiente información útil: Demografía del municipio, hábitos de transporte, costos de transporte, infraestructura de transporte, impacto ambiental y preferencias de los usuarios.


## Análisis DAFO
El análisis DAFO es una herramienta que utilizaremos para la planificación estratégica de nuestro proyecto, para evaluar sus fortalezas, debilidades, oportunidades y amenazas (DAFO, por sus siglas en español).

### Fortalezas:
- Acciona tiene una amplia experiencia en el sector de la movilidad y puede aportar su conocimiento y recursos para el proyecto de carpooling.
- El carpooling puede ser una solución rentable y sostenible para el transporte en el municipio.
- La estrategia de cambio climático de Mallorca incluye medidas para fomentar la movilidad sostenible, lo que puede aumentar la demanda potencial de servicios de carpooling.
- El proyecto de carpooling puede mejorar la imagen de Acciona como una empresa comprometida con la sostenibilidad y la reducción de emisiones de gases de efecto invernadero.
### Debilidades:
- La falta de conciencia o interés por parte de la población sobre el carpooling puede limitar la demanda potencial del servicio.
- Pueden existir obstáculos regulatorios y legales que dificulten la implementación del proyecto a nivel nacional o internacional.
- La competencia de otros servicios de transporte compartido o alternativas de movilidad sostenible pueden limitar la adopción del carpooling.
### Oportunidades:
- El mercado potencial para el carpooling en el municipio es amplio, ya que muchos residentes están buscando soluciones de transporte más rentables y cómodas.
- Un proyecto de carpooling muy enfocado a atraer a un público joven puede atraer a los que buscan opciones de transporte más sostenibles.
- Acciona puede asociarse con otras empresas locales para crear una plataforma de carpooling que beneficie a todos los usuarios y fomente la colaboración empresarial en la sostenibilidad.
- El proyecto de carpooling puede ser una oportunidad para Acciona para ampliar su presencia en el mercado de la movilidad sostenible y desarrollar nuevas tecnologías relacionadas con la movilidad compartida.
### Amenazas:
- El proyecto de carpooling puede enfrentar la resistencia de empresas de transporte tradicionales que ven el carpooling como una amenaza a su negocio.
- Los cambios en el marco regulatorio pueden afectar la viabilidad del proyecto de carpooling.
- La falta de apoyo o financiamiento gubernamental para la movilidad sostenible puede limitar el crecimiento del proyecto.



## Análisis de stakeholders
El análisis de stakeholders (partes interesadas), es un aspecto clave que nos permite identificar y evaluar las personas/empresas que pueden tener un interés o impacto en nuestro proyecto.

En nuestro caso los principales interesados de que exista una plataforma centralizada con la información que mencionamos serían empresas que pudieran colaborar, como Acciona. Por otra parte, los interesados en que exista una plataforma de vehículo compartido serían los propios alumnos universitarios de la Universitat de les Illes Balears (UIB).

## Datos
Tenemos la visión de que una  plataforma de carpooling en Mallorca podría ser una excelente manera de contribuir a la reducción de emisiones de gases de efecto invernadero en la isla. Según el artículo 24 de la Ley 10/2019, todos están obligados a colaborar en las políticas públicas de reducción de emisiones de gases de efecto invernadero en el marco de la legislación estatal básica y de los instrumentos de planificación previstos en esta ley.

Según la [página oficial de la UIB](https://transparencia.uib.es/digitalAssets/623/623606_quinze-indicadors-institucionals.pdf ), el número de alumnos es de unos 15.000.

Los tres municipios de Mallorca con mayor número de estudiantes universitarios matriculados en la Universidad de las Islas Baleares (UIB) son Palma de Mallorca, Calvià y Manacor. Palma de Mallorca, como capital de la isla y sede principal de la UIB, concentra el mayor número de estudiantes universitarios, mientras que Calvià y Manacor también tienen una presencia significativa de estudiantes universitarios debido a la oferta educativa de la Escuela Universitaria de Turismo de las Islas Baleares y otros centros educativos.


## Captura de datos
A continuación explicaremos a alto nivel cual es la estructura de la aplicación web que vamos a desarrollar.


En el diagrama mostrado vemos 4 elementos que representan las aplicaciones que conforman la solución:
Scraper web: esta aplicación se encarga de navegar por distintas webs, emulando una interacción humana y obteniendo los datos que nos interesan.
API de base de datos: esta aplicación espera las llamadas del scraper, de manera que actúa como un intermediario, una vez recibe el input que son los datos que envía el scraper web, se encarga de subir esta información a la base de datos.
Base de datos: es el lugar donde almacenamos los datos recopilados.
Interfaz web: es un frontend web que está conectado a la base de datos de manera que su única función es permitir la visualización y el formato de datos métricos.


### Clasificación de los datos
El scraper web una vez en producción se ejecuta como una tarea cronjob, esto quiere decir que especificaremos cada cuanto y la hora a la que deben ejecutar. Como no todos los datos de las webs se actualizan con la misma frecuencia hemos adaptado el scraper para que mediante el uso de variables podamos ponerlo en marcha y scrapee solo los datos que especificamos en las variables de entorno.

De esta manera podemos tener varios cronjobs configurados y cada uno de ellos con una frecuencia de ejecución distinta. 

1. Datos que obtenemos diariamente:
[Calidad del aire (Palma de Mallorca)]
[accuweather](https://www.accuweather.com/es/es/palma/308014/air-quality-index/308014#:~:text=17%20AQI,al%20aire%20libre%20con%20normalidad) 

Precio del combustible (Baleares):
[motor.es](https://www.motor.es/energia/precios-combustible-hoy )

2. Datos que obtenemos mensualmente:
Transporte de viajeros: [ine/transporteViajeros](https://www.ine.es/jaxiT3/Tabla.htm?t=20193) [ine/transporteViajeros](https://servicios.ine.es/wstempus/js/es/DATOS_TABLA/20193?tip=AM&)

3. Datos que obtenemos anualmente:
Vehículos por cada mil habitantes 
[caib.es](https://www.caib.es/ibestat/estadistiques/per-territori/1/f4e4a288-e0d8-40ce-b53f-6ed6b0d16d7d/es/E70044_00003.px)

Población por edad (no lo actualizan cada año)
[ine/poblacion]( https://www.ine.es/jaxi/Tabla.htm?tpx=55226&L=0)


## Servicios de AWS elegidos
Nosotros utilizaremos el potencial de AWS principalmente en IaaS (infraestructura como servicio) y será la base sobre la que desarrollaremos el proyecto.

Los servicios de AWS que vamos a desplegar en la región de España (eu-south-2) son los siguientes, que detallaremos más adelante.

- AWS CloudFormation.
- AWS Identity and Access Management (IAM).
- Amazon Virtual Private Cloud (Amazon VPC).
- Amazon Elastic Kubernetes Service (EKS).
- Amazon Elastic Compute Cloud (EC2).
- Amazon Elastic Block Store (EBS).
- Amazon DocumentDB.
- Elastic Load Balancing (ELB).

A continuación, mostraremos y describiremos un diagrama sobre de qué forma implementamos estas tecnologías a nuestro proyecto.


Como podemos observar en la parte superior del diagrama tenemos la tecnología CloudFormation, esta será utilizada en segundo plano al crear nuestros recursos con la herramienta ‘eksctl’, una herramienta de interfaz de línea de comandos que nos permite crear y configurar un cluster de EKS desde nuestra terminal.

Si seguimos observando el diagrama vemos que eksctl + CloudFormation, son los responsables de crear recursos de AWS como los siguientes:

Amazon VPC: la Virtual Private Cloud es una red virtual que proporciona aislamiento y seguridad para el clúster y sus recursos. El comando de eksctl configura la VPC con una serie de subredes y grupos de seguridad para permitir que los nodos del clúster se comuniquen entre sí y con los servicios de AWS.
IAM: se crean varios roles de AWS Identity and Access Management para permitir que los recursos del clúster se comuniquen entre sí y con los servicios de AWS de manera segura.

Estas tecnologías sumadas al propio servicio de EKS, conforman lo que sería un clúster con un plano de control administrado, pero para ejecutar cargas de trabajo necesitamos nodos trabajadores (workers), que serán gestionados por el plano de control de EKS.

Aquí es donde entran las tecnologías EC2 y EBS, también desplegadas por eksctl, como grupos de nodos dentro del clúster. EC2 es el servicio de servidores virtuales y EBS es el servicio de volúmenes de almacenamiento, ambos son necesarios para conformar lo que es un nodo trabajador, capacidad de procesamiento + almacenamiento persistente. Además utilizamos servidores específicamente con procesadores Graviton que ofrecen una mayor eficiencia energética, mayor rendimiento en ciertas cargas de trabajo y mayor seguridad.

En el diagrama vemos que tanto plano de control + nodos trabajadores conforman un cluster EKS totalmente funcional.

En lo que es la parte externa al cluster también tenemos otras tecnologías, que no son desplegadas por CloudFormation. Tenemos el servicio Elastic Load Balancer, que nos permite usar balanceadores de carga para poder recibir tráfico externo de nuestros usuarios, este sería el punto de entrada al cluster por donde pasan las solicitudes a nuestras aplicaciones.

## AWS Well-Architected
Esta una metodología de arquitectura de la nube que se utiliza para diseñar y operar sistemas en la nube de Amazon Web Services. El AWS Well-Architected Framework proporciona un conjunto de mejores prácticas en cinco áreas clave de la arquitectura de la nube.

Excelencia operativa
Seguridad
Eficiencia en el rendimiento
Optimización de costos
Fiabilidad


### Excelencia operativa
Al usar EKS y herramientas como Kubernetes, Prometheus y Grafana, seguimos las mejores prácticas de AWS para la excelencia operativa. Esto nos permite automatizar el despliegue, escalabilidad y gestión de nuestras aplicaciones, aumentando su disponibilidad y reduciendo el riesgo de interrupciones. Además, la supervisión continua de nuestras aplicaciones con herramientas de monitoreo nos permite detectar y solucionar rápidamente cualquier problema para minimizar el tiempo de inactividad.

### Seguridad
EKS proporciona una capa de seguridad adicional para nuestra infraestructura, ya que es una plataforma de Kubernetes administrada y altamente segura que se encarga de la gestión y protección de nuestros nodos y del control de acceso a nuestros recursos. Además, EKS nos permite aplicar políticas de seguridad como el cifrado de datos en reposo y en tránsito, la implementación de políticas de IAM, la aplicación de parches de seguridad y la configuración de reglas de firewall para proteger nuestras aplicaciones.

Por otro lado, Kubernetes nos permite aplicar prácticas de seguridad tales como el despliegue de imágenes de contenedor seguras y la configuración de políticas de red que restringen el acceso no autorizado a nuestros servicios. Además, al utilizar herramientas de monitoreo y análisis de seguridad, podemos detectar y solucionar rápidamente cualquier vulnerabilidad o brecha de seguridad en nuestra infraestructura.

### Eficiencia en el rendimiento
Al utilizar EKS, podemos reducir los costos de infraestructura y administración, ya que podemos aprovechar los servicios gestionados de AWS. Además, al utilizar EKS, podemos garantizar un alto rendimiento y disponibilidad para nuestras aplicaciones, ya que los clusters de Kubernetes son altamente disponibles y tolerantes a fallas, y los nodos del cluster se distribuyen en diferentes zonas de disponibilidad.

Además, para lograr una mayor eficiencia en nuestro proyecto, hemos optado por utilizar procesadores ARM en lugar de los tradicionales amd64. Los procesadores ARM son conocidos por su alta eficiencia energética y por ofrecer un alto rendimiento en cargas de trabajo específicas. Al utilizar procesadores ARM, podemos reducir significativamente el consumo de energía y mejorar el rendimiento de nuestras aplicaciones en comparación con los procesadores amd64. Esto no solo nos permite ser más eficientes en cuanto a costos, sino que también nos permite ser más sostenibles y respetuosos con el medio ambiente.

### Optimización de costos
Al utilizar un cluster de Kubernetes EKS y herramientas de autoscaling de pods como Knative, podemos optimizar el uso de recursos y reducir los costos asociados con la infraestructura.

Knative es una plataforma de código abierto que se ejecuta en Kubernetes y permite construir, desplegar y manejar aplicaciones en contenedores. Al utilizar Knative, podemos aprovechar la capacidad de auto escalado horizontal de pods (incluyendo la escala a 0 réplicas), lo que significa que se crearán y destruirán pods automáticamente según la demanda de recursos de nuestra aplicación. Esto nos permite escalar automáticamente el número de pods que se ejecutan en el clúster en función de la demanda, lo que nos permite utilizar los recursos de manera más eficiente, además usamos las instancias con los recursos apropiados de manera que no nos quedamos cortos ni los desaprovechamos.

Por otro lado, podríamos implementar en el futuro Karpenter ( https://karpenter.sh/v0.26.1/getting-started/getting-started-with-eksctl/), una herramienta que nos permite escalar automáticamente el número de nodos del clúster según las necesidades de recursos de nuestras aplicaciones. Esto significa que cuando la demanda de recursos aumenta, este agregará automáticamente más nodos al clúster para proporcionar capacidad adicional. Y cuando la demanda disminuye, los nodos adicionales se eliminarán automáticamente, lo que nos permite utilizar los recursos de manera más eficiente y reducir los costos de infraestructura.

### Fiabilidad
En primer lugar, EKS utiliza una arquitectura distribuida y altamente escalable que se ejecuta en múltiples zonas de disponibilidad de AWS. Esto significa que, incluso si una zona de disponibilidad experimenta problemas, el servicio sigue estando disponible en otras zonas de disponibilidad. Además, la arquitectura basada en contenedores utilizada por EKS permite una mayor flexibilidad en la implementación y el escalado de aplicaciones.

En segundo lugar, EKS proporciona funciones de recuperación automática, como la capacidad de reemplazar automáticamente las instancias de nodos que fallan. Esto permite una rápida recuperación de errores y ayuda a garantizar la disponibilidad continua del servicio. Además, la arquitectura basada en contenedores permite una rápida recuperación de los errores, ya que solo se ve afectado un servicio en lugar de toda la aplicación.

Por último, EKS es un servicio altamente adaptable y compatible con una amplia gama de herramientas y servicios de AWS. Esto permite una mayor flexibilidad en la implementación y la integración con otros servicios de AWS. Además, EKS puede escalar según las necesidades de la aplicación, lo que ayuda a garantizar que el servicio se adapte a los requisitos cambiantes de la aplicación.


## Creando el cluster EKS
Una vez tenemos la herramienta eksctl, podemos instalar con el siguiente comando un cluster EKS con las siguientes características:

Un grupo de nodos de instancias EC2 (t4g.xlarge) con procesadores Graviton.
Estos nodos usarán la AMI de Amazon Linux 2 (sistema operativo).
Desplegamos todos los recursos en la región de España (eu-south-2).
Automáticamente se generan roles de IAM: uno de ellos es para el controlador de servicio de EKS, para poder crear recursos para el cluster como Load Balancers y Elastic Network Interfaces.
Los nodos creados se asignan a varias subredes distintas de la VPC, donde podrán ser desplegados.
Al no especificar un tamaño para los volúmenes EBS asociados, para cada instancia se creará un volumen de 20GB por defecto.

~~~
eksctl create cluster --name project01 --node-type t4g.small --nodes-min 1 --nodes-max 3 --nodes 1 --node-ami-family AmazonLinux2 --nodegroup-name graviton-worker --asg-access --region eu-south-2 
~~~

## Preparando el clúster
Para una rápida implementación de nuestras aplicaciones en el cluster de EKS, hemos decidido utilizar una herramienta de GitOps llamada ArgoCD, esta nos permite usar un repositorio de Git como ‘fuente de la verdad’, donde tenemos la configuración de todas nuestras aplicaciones, incluidas las esenciales para el correcto funcionamiento del cluster.

En el siguiente diagrama se expresa de manera sencilla el funcionamiento de ArgoCD.


Como podemos observar el ‘desarrollador’ sube los cambios a un repositorio Git y ArgoCD supervisa estos cambios y sincroniza la información con lo desplegado en nuestro clúster Kubernetes.

De esta manera, lo declarado en los manifiestos del repositorio, será lo que se despliegue en el cluster. Entre las ventajas que tenemos al desplegar/sincronizar las aplicaciones de esta manera tenemos:

Flexibilidad a la hora de querer mover o clonar nuestras aplicaciones a otros clusters de EKS, a regiones de AWS distintas, por ejemplo.
Un histórico de cambios realizados en git.
Visualización de los errores o inconsistencias de implementación.

## Preparando nuestras aplicaciones
Como las instancias con procesadores Graviton tienen una arquitectura ARM decidimos adaptar nuestra aplicación para que pueda ser ejecutada en este entorno. En nuestro caso, como utilizamos un entorno de contenedores, tuvimos en cuenta que debíamos construir nuestras imágenes de contenedor para ARM. Como nosotros usamos Docker como tecnología de contenedores para el desarrollo en local, nos apoyaremos en el plugin de Docker CLI llamado Buildx.

Gracias a esta herramienta podemos compilar nuestra imagen en diferentes arquitecturas.
La manera con la que pasaremos nuestro código a imágenes de Docker será con un pipeline de CI/CD, esto es grupo de procesos automatizados que se ejecutarán cada vez que se haga un cambio en la rama principal (master) del repositorio. El pipeline completo que usamos está disponible en cada uno de los repositorios en `.github/workflows`, pero las acciones más destacables que realiza son las siguientes:

Creamos una instancia de Buildx, con las plataformas que queremos soportar, esto desplegará varios contenedores que servirán para construir muestran imágenes en paralelo, en nuestro caso amd64 y arm64.

~~~
docker buildx create --name mybuilder --platform linux/arm64/v8,linux/amd64 --use
~~~ 

Posteriormente se realizará la construcción de las imágenes para las plataformas especificadas.
~~~
docker buildx build --platform linux/arm64/v8,linux/amd64 --no-cache -t "example:0.0.1" .
~~~

## Repositorios
Para el desarrollo y despliegue de este proyecto han sido necesarios 3 repositorios

- [data-collector](https://github.com/project-for-good/data-collector): en este repositorio se ha desarrollado el codigo del modulo que recoge los datos de internet, tambien hay archivos necesarios para la creacion de la imagen docker usada para el despliegue del modulo.
- [dbapi](https://github.com/project-for-good/dbapi): en este repositorio se ha desarrollado el codigo del modulo que recibe los datos del data-collector y se los envia a la base de datos, al igual que en el de data-collector en este repo tambien hay archivos necesarios para la creacion de la imagen docker.
- [reusable-workflows](https://github.com/project-for-good/reusable-workflows): Este repo es el que recibe informacion de los otros dos para crear sus respectivas imagenes a través de workflows.
- [argocd](https://github.com/project-for-good/argocd): en este repositorio lo creamos para preparar la infraestructura y ahorrarnos tiempo a la hora de desplegar los servicios de AWS, de esta manera consumimos menos recursos durante el aprovisionamiento de nuestras aplicaciones.

### data-collector

Este módulo se encarga de obtener información de diferentes fuentes, es debido a esto que este contenedor debe ser adaptable ya que cada fuente tiene una manera diferente de presentar la información, para que el data collector sea adaptable en torno a las fuentes que en la mayoría de casos son páginas web ha sido desarrollado en el lenguaje JavaScript ya que al estar todas las webs basadas en este lenguaje se facilita bastante la interacción con estas, y mediante la librería Puppeteer es posible desarrollar un programa capaz de navegar por webs de una manera eficiente y extraer la información aunque no esté en el formato requerido

 En algunos casos como es el de www.ine.es la información es presentada como un json por lo cual no es necesaria la implementación de un scraper. Solo se requiere de una petición para obtener el json el cual pasará por un filtro para pasarle a dbapi solo la información que necesita.

Este ejemplo muestra el proceso que el data-colector sigue para obtener la documentacion de www.ine.com:

~~~
const getData = async () => {
    const url = "https://servicios.ine.es/wstempus/js/es/DATOS_TABLA/55226?tip=AM&"


    const rawData = await axios.get(url, {});
    const filteredData = filterData(rawData)


    return filteredData
}
~~~

Este ejemplo es bastante simple, claro que en el resto de fuentes no es posible obtener la información de una manera sencilla por lo que es necesario el uso de un web scraper que navegue por la página web y extraiga de esta la información para convertirla en el formato deseado, si bien esta forma de extraer los datos es bastante más compleja y lenta, los datos proporcionados por el web scraper están ya filtrados ya que solo se obtienen los datos deseados.


Para iniciar la navegación es necesaria una configuración previa, lo primero es iniciar el navegador, y abrir una nueva pestaña dentro de este, para esta pestaña es posible definir un tamaño y el url al que se va a acceder.
~~~
    const browser = await puppeteer.launch()
    const page = await browser.newPage()
    await page.setViewport({
        width: 1920,
        height: 1080
    })
    await page.goto(url)
~~~

Una vez configurada la pestaña se puede interactuar con ella mediante los métodos del objeto “page”, estos métodos (tales como “click” para pulsar un elemento o “waitForSelector” para que el código espere a que un selector sea cargado antes de seguir ejecutándose) requieren de un parámetro para identificar el elemento de la página al que hacen referencia, este parámetro puede ser cualquier tipo de selector css como identificadores clases o etiquetas HTML por ejemplo.

~~~
    // click deny coockies so the pop up dissapears
    page.waitForSelector("#denegar_btn")
    page.click("#denegar_btn")
~~~

Además de este tipo de métodos del objeto “page” hay uno en concreto que resulta bastante útil, se trata de “evaluate” el qual acepta una funcion como parametro la cual es ejecutada dentro de la web sobre la que navegamos, esto nos permite ejecutar código JavaScript directamente en la página web de manera que es posible hacer todo tipo de acciones (tales como hacer scroll, extraer información o incluso crear un disparador de eventos sobre un componente durante la navegación actual), en este método se basan mayormente los web scrapers utilizados para este proyecto pues es utilizado para extraer la información de la página. 

Por ejemplo, en este caso se utiliza dentro de un bucle para extraer los valores deseados de las celdas de una tabla:

~~~
for (let i = 1; i < 5; i++) {
        const result = await page.evaluate((i) => {
            window.scrollTo(0, document.body.scrollHeight / 2);
            window.scrollTo(0, document.body.scrollHeight / 2);
            const div = document.querySelector(".resultados-table-wrapper")
            div.scrollBy(0, div.scrollHeight);
            const secondTable = document.querySelectorAll(`table.resultados-table`)[1]
            return secondTable.querySelector(`tbody tr:nth-child(${i}) td:nth-child(10) span`).innerHTML.replace(",",".")
        }, i)
~~~


### Dbapi
El módulo de dbapi es una API escrita en el lenguaje Node.js cuya arquitectura se basa en un controlador que reciben la información del data collector y la deriva , y un servicio que recibe la información del controlador y la almacena en base de datos. Si bien en este caso el código podría haber estado más integrado de manera que con un solo método se reciba y almacene la información se ha implementado una estructura basada en el patrón de diseño “Modelo Vista Controlador” o “MVC” para que el código sea más modular de manera que si alguno de los otros componentes cambia la migración se más sencilla y para que la aplicación tenga un principio estructurado de manera que el riesgo sea menor si esta crece.

Ya que se ha usado este patrón de diseño el módulo solo cuenta con dos componentes los cuales se separan en métodos reducidos.

Este es un ejemplo de un método del controlador:

~~~
const saveAccuwheaterData = (req, res) => {
  DataService
    .saveAccuwheaterData(req.body)
    .then((result) => res.status(200).json(result))
    .catch((error) => res.status(400).json({ message: error }))
}
~~~

Este es un ejemplo de un método del servicio:

~~~
const saveAccuwheaterData = async (data) => {
  try {
    const airQualityParams = {
      municipality: data.municipality,
      aqi: data.aqi,
      o_3: data.o_3,
      pm_2_5: data.pm_2_5,
      pm_10: data.pm_10,
      no_2: data.no_2,
      co: data.co,
      so_2: data.so_2
    }


    const airQuality = new AirQualitySchema(airQualityParams)
    await airQuality.save()
    return { success: 'true' }
  } catch (error) {
    console.log(error)
    return error
  }
}
~~~


Para mantener la base de datos actualizada hay unos cronjobs de kubernetes que se encargan de ejecutar los scrapers cada vez que la información de las fuentes se actualize.

Para esto se han creado tres cronjobs que ejecutan grupos de scrapers en función de la frecuencia con la que se actualizan las fuentes, hay uno que se ejecuta cada dia, uno que se ejecuta cada mes y uno que se ejecuta cada año.

Este es el cronjob que se ejecuta cada dia, como se puede ver crea la imagen del scraper y modifica la variable de entorno “PAGES_TO_SCRAPE” añadiendo las paginas “www.accuwheater.com” para el analisis de la calidad del aire y “www.motor.es” para el analisis del precio de combustibles.

~~~
apiVersion: batch/v1
kind: CronJob
metadata:
  name: data-collector-daily
spec:
  schedule: "0 2 * * 0"
  jobTemplate:
    spec:
      template:
        spec:
          containers:
          - name: data-collector
            image: luis13byte/tools:data-collector-master
            imagePullPolicy: IfNotPresent
          env:
            - name: PAGES_TO_SCRAPE
              value: "www.accuwheater.com;www.motor.es"
          restartPolicy: OnFailure
~~~

## Desarrollo Frontend
### Grafana

Para la visualización de datos se va a utilizar Grafana que es un software open source utilizado para la estructuración, almacenamiento y visualización de datos.

Gracias a la integración de Grafana con MongoDB es posible visualizar la información estructurada mediante diferentes tipos de gráficos utilizando queries nativas del propio MongoDB. Asi que en nuestro caso hemos configurado una conexión a la base de datos mediante un Datasource de Grafana.

Por ejemplo, esta query extrae los precios por litro de la gasolina 95 en Mallorca y los agrupa por la fecha en la que este combustible tenía ese precio, de manera que es posible plasmarlo en un gráfico lineal y de esta manera analizar de una manera sencilla la fluctuación del precio para este tipo de gasolina.

~~~
db.fuels.aggregate([
   { $match: { type: "Gasolina 95" } },
   { $group: { _id: "$types", prices: { $push: "$price_per_liter" }, createdAt: { $push: "$createdAt" } } },
   { $unwind: "$prices" },
   { $unwind: "$createdAt" },
   { $project: { _id: 0, time: { $toDate: "$createdAt" }, gasolina95: { $toDouble: "$prices" } } }
])
~~~


## Participantes
- Luis Acosta
- Mikel Burgos

## Bibliografía
- https://aws.amazon.com/es/architecture/well-architected/ 
- https://docs.aws.amazon.com/eks/latest/userguide/create-cluster.html 
- https://argo-cd.readthedocs.io/en/stable/ 
- https://knative.dev/docs/ 
- https://eksctl.io/ 
- https://aws.amazon.com/es/architecture/icons/
- https://www.ine.es/
- https://www.motor.es/energia/precios-combustible-hoy
- https://catalegdades.caib.cat/es/ 
- https://www.cdp.net/en/data
- https://datasetsearch.research.google.com/

