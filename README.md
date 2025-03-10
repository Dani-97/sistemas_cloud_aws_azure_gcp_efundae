# Curso Itinerario Formativo - Sistemas Cloud (Amazon, Google y Microsoft)

Tal y como se muestra en el presente curso de la Fundae, del cual se puede encontrar más información <a href="https://experienciafundae.es/buscador/ficha-eFundae-itinerario/3029/5">en este enlace</a>:

> Este itinerario formativo está diseñado para proporcionarte una formación integral en las tecnologías clave de sistemas Cloud de los principales proveedores del mercado. Está dividido en 4 niveles, alineados con el marco de competencias digitales de la Comisión Europea.

> Los objetivos de aprendizaje de este intinerario formativo incluyen:

> Entender los fundamentos de la computación en la nube y sus ventajas.

> Conocer y utilizar los principales servicios de:

> Amazon Web Services (AWS): EC2, S3, RDS y Lambda.

> Google Cloud Platform (GCP): Compute Engine, Cloud Storage, Cloud SQL y Cloud Functions.

> Microsoft Azure: Virtual Machines, Blob Storage, Azure SQL Database y Azure Functions.

> Conocer las herramientas y servicios de administración y monitorización proporcionados por los principales proveedores de servicios en la nube.

> Aprender las técnicas y herramientas para el despliegue de aplicaciones en la nube, incluyendo CI/CD y contenedores.

En la realización de este curso, se enuncian una serie de Retos, que se tratan de pequeños supuestos prácticos para aprender y demostrar los conocimientos en el uso de las plataformas y sus herramientas principales. En mi caso personal, he decidido no centrarme tanto en los retos individuales, porque considero que la mejor demostración de la habilidad que uno tiene en este tipo de entornos es el hecho de poder crear una aplicación funcional con una arquitectura cloud de cierta complejidad que engloba diferentes servicios. Por eso, he realizado algunos supuestos prácticos más complejos, disponibles en repositorios públicos de GitHub. 

A pesar de todo, me gustaría cubrir uno por uno los retos que se enuncian en el curso. En algunos casos, me limitaré a hacer referencia a la documentación disponible online y, en aquellos casos donde haya implementado un supuesto práctico más elaborado, haré referencia a él.

## Curso Sistemas Cloud - Nivel 3 (Amazon, Google y Microsoft)

### Reto: Crear y configurar una cuenta en AWS y GCP

La creación de una cuenta en las diferentes plataformas es algo bastante sencillo e inmediato, además de intuitivo. La única complejidad reside en el hecho de tener que introducir la tarjeta de crédito para poder acceder a las opciones de prueba de cada plataforma. Por ello, no me voy a centrar en esta parte y voy a pasar a los puntos siguientes.

### Reto: Desplegar una instancia de EC2 en AWS

EC2 permite crear instancias de máquinas virtuales en AWS. Esto es algo que ya he hecho previamente en <a href="https://github.com/Dani-97/clip_imagesearch_aws_telegram_bot">clip_imagesearch_aws_telegram_bot</a>. En términos generales, la creación de una máquina virtual involucra seleccionar sus características software y hardware (teniendo en cuenta el Sistema Operativo y los elementos hardware más importantes como es el caso del número de vCPUs, la cantidad de RAM o el tamaño del disco duro). Una vez seleccionado todo lo que deseamos, tendremos nuestra máquina virtual, con la que podremos conectar de múltiples maneras, pero una de las más estándar es utilizando un cliente SSH. La dificultad, en este caso, es disponer de un par de claves SSH para poder acceder a la máquina (ya que, de lo contrario, el acceso será denegado y no podremos acceder a ella directamente). Dentro de la instancia de EC2, podremos trabajar como si se tratase de cualquier otro tipo de máquina virtual, adaptándonos al sistema operativo que hayamos instalado en cada caso.

### Reto: Almacenar y recuperar archivos en S3 y Google Cloud Storage

En el caso de AWS S3, también he creado un repositorio que se puede encontrar haciendo <a href="https://github.com/Dani-97/telegram_bot_aws_s3_notification">click aquí</a>. En este caso, el proyecto que desarrollé involucra la creación de un bucket S3 y de dos funciones lambda (la opción Serverless Computing que ofrece AWS). En este caso, lo que hace la implementación desarrollada es conectar las funciones lambda con diferentes eventos vinculados al bucket (en este caso, la creación y eliminación de archivos o, como denomina la plataforma en este caso, objetos) y notificar a un usuario por medio de un bot de Telegram. En concreto, cada vez que un archivo se sube al bucket, se notifica al usuario de ese hecho y, por la otra parte, si un archivo se elimina, también se notifica al usuario.

Para Google Cloud Storage, por su parte, el funcionamiento es muy similar, así que me limitaré a dejar un tutorial de los pasos más fundamentales con esta plataforma. <a href="https://medium.com/@4get.prakhar/creating-and-managing-google-cloud-storage-buckets-on-gcp-5948f109be5c">Click aquí para acceder al tutorial</a>.

### Reto: Desplegar una máquina virtual en GCP y Microsoft Azure

El despliegue de una máquina virtual es muy similar en todas las plataformas. Las únicas diferencias existentes reside en cómo trabaja cada una de ellas. El objetivo final sigue siendo el mismo que con AWS: configurar y crear la máquina virtual para más tarde conectar con ella por medio de SSH. Para utilizar tanto los servicios de máquinas virtuales como los de serverless computing, he replicado este proyecto <a href="https://github.com/Dani-97/clip_imagesearch_aws_telegram_bot">clip_imagesearch_aws_telegram_bot</a> previamente descrito en AWS para las otras dos plataformas Cloud. De este modo, en <a href="https://github.com/Dani-97/clip_imagesearch_gcp_telegram_bot">clip_imagesearch_gcp_telegram_bot</a> y <a href="https://github.com/Dani-97/clip_imagesearch_azure_telegram_bot">clip_imagesearch_azure_telegram_bot</a> se encuentran los repositorios de las implementaciones con Google Cloud Platform y Microsoft Azure, respectivamente.

## Curso Sistemas Cloud - Nivel 4 (Amazon, Google y Microsoft)

### Reto: Gestión de Identidades y Control de Acceso en la Nube.

En este reto, he preferido no hacer capturas de los pasos que seguí yo mismo por cuestiones de seguridad. En su lugar y, dado que no he cubierto esta tarea en puntos anteriores, voy a describir brevemente algunas de las cuestiones fundamentales en lo que respecta a creación de usuarios y gestión de permisos. Dentro de AWS y las múltiples plataformas cloud populares, existe una herramienta denominada IAM. 

- **AWS:** Cuando alguien crea una cuenta en la plataforma AWS, esa cuenta tendrá permisos de root. Acceder a los diferentes servicios por medio de esta cuenta está desaconsejado, ya que permite hacerlo absolutamente todo. En su lugar, lo más aconsejable, es acceder por medio de una cuenta que tenga única y exclusivamente los permisos que necesita (principio del menor privilegio). Por tanto, esta fase de creación de usuarios no solo implica crearlo si no también asignarle los permisos que necesita. Para ello, existen las denominadas políticas de permisos. AWS dispone de algunas políticas predefinidas. Podemos consultarlas y seleccionar aquello que se desea. Por ejemplo, si queremos darle permisos a alguien para que pueda trabajar con un bucket de S3, podemos buscar "S3" dentro de esa lista y ver cuál de las políticas se adapta mejor. Hay algunas políticas que permiten un acceso completo, mientras que otras solo permiten un acceso limitado (por ejemplo, hay algunas que permiten un acceso de solo lectura). En función de las necesidades, habrá que seleccionar una política u otra.

> <a href="https://www.techtarget.com/searchcloudcomputing/tutorial/Step-by-step-guide-on-how-to-create-an-IAM-user-in-AWS">Click aquí para acceder a un tutorial de cómo crear nuevos usuarios en AWS</a>.

- **Google Cloud Platform:** en este caso, el funcionamiento es bastante similar, así que sencillamente me limitaré a referenciar a un tutorial.

> <a href="https://www.howtogeek.com/devops/how-to-add-new-users-to-your-google-cloud-platform-projects/">Tutorial para crear usuarios en Google Cloud Platform</a>.

- **Azure:** en este caso, aplica lo mismo que describo en Google Cloud Platform.

> <a href="https://thinkcloudly.com/blogs/azure/create-users-in-azure-ad/">Tutorial para crear usuarios en Microsoft Azure</a>.

### Reto: Configurar alertas y monitoreo básico

Con respecto a este reto, me voy a centrar un poco más en AWS (ya que es la plataforma en la que he trabajado con esto) y me limitaré a mostrar tutoriales de cómo utilizarlo en las otras dos plataformas:

- **AWS:** Para este caso, existe una herramienta llamada Amazon CloudWatch. Configurar un sistema de notificación es una tarea muy sencilla y bastante intuitiva de entender. Por ejemplo, en el caso del uso excesivo de CPU, se puede poner un umbral en torno al porcentaje de utilización. Cuando se supera ese porcentaje, se notifica al usuario por el medio que se especifique (siendo correo y SMS los canales más comunes). Para las notificaciones relacionadas con el tráfico de red, la configuración es, de nuevo, bastante similar.

> <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/US_AlarmAtThresholdEC2.html">Click aquí para acceder a un tutorial sobre cómo crear alarmas de uso de CPU en AWS CLI.</a>.

> <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch-IM-create-alarm.html">Click aquí para acceder a un tutorial sobre cómo crear alarmas de tráfico en AWS CLI</a>.

- **Google Cloud Platform:** <a href="https://cloud.google.com/monitoring/alerts/target-configuration-library">Creación de alertas en Google Cloud Platform</a>.

- **Azure:** <a href="learn.microsoft.com/en-us/azure/azure-monitor/vm/monitor-virtual-machine-alerts">Creación de alertas en Microsoft Azure</a>.

### Reto: Desplegar una aplicación web básica en la nube

Teniendo en cuenta las implementaciones de los repositorios <a href="https://github.com/Dani-97/clip_imagesearch_aws_telegram_bot">clip_imagesearch_aws_telegram_bot</a>, <a href="https://github.com/Dani-97/clip_imagesearch_gcp_telegram_bot">clip_imagesearch_gcp_telegram_bot</a> y <a href="https://github.com/Dani-97/clip_imagesearch_azure_telegram_bot">clip_imagesearch_azure_telegram_bot</a>, este punto ya quedaría cubierto. Estos repositorios no solo implementan una aplicación web básica, si no que además plantean una arquitectura de cierta complejidad en la que intervienen diferentes módulos separados como son, en este caso, el serverless computing y las instancias de máquinas virtuales. Además, dentro de las máquinas virtuales, hago uso de la herramienta DevOps Docker para facilitar el proceso de despliegue en todos los casos.

### Reto: Escalar una aplicación en la nube

Para escalar una aplicación en la nube de AWS, se pueden utilizar los grupos de autoescalado. Para poder utilizar la herramienta y obtener un escalado automático, se debe crear una plantilla donde se especifican cómo son las instancias que se van a crear. Más adelante, se especifica qué eventos deben lanzar esas instancias. Por ejemplo, igual que ocurre con las alertas, se puede utilizar el uso de la CPU como umbral. Si una instancia supera un tanto por ciento de uso de CPU, entonces se creará una nueva. En el momento que la carga de CPU de la nueva instancia caiga por debajo de ese umbral, se elimina y se vuelve a la disposición original. Se pueden modificar múltiples parámetros, además (por ejemplo, el número mínimo y el número máximo de instancias que puede llegar a haber).

> <a href="https://docs.aws.amazon.com/autoscaling/ec2/userguide/create-your-first-auto-scaling-group.html">Click aquí para acceder al tutorial de cómo crear grupos de autoescalado en AWS</a>.

Para el escalado de una aplicación en la nube para otras plataformas, se puede consultar <a href="https://learn.microsoft.com/en-us/azure/azure-monitor/autoscale/autoscale-overview">la guía para utilizar Autoscale de Azure</a> y el <a href="https://cloud.google.com/compute/docs/autoscaler">Autoscaling de Google Cloud Platform</a>. 

### Reto: Configurar un balanceador de carga en la nube

Los balanceadores de carga permiten tener múltiples instancias y que cada instancia se encargue de cierto número de peticiones. Esto normalmente se utiliza para aplicaciones web, en las que queremos que existan una serie de instancias virtuales que se encarguen de la forma más equitativa posible de las peticiones web. Es decir, si por ejemplo llegan 100 peticiones HTTP en un momento dado y nos es suficiente con tener 5 instancias, cada una de esas 5 instancias idealmente debería encargarse de 20 peticiones. Evidentemente, en la práctica, no va a ser al 100% así, pero el principal objetivo de los balanceadores de carga es llegar a ese equilibrio. De esta forma, evitamos que ocurran cosas como que una instancia tenga 80 peticiones y el resto solo 5 cada una. Esto haría sobrecargar a una de las instancias, perjudicando a la experiencia de los usuarios que tuvieron la mala fortuna de ser servidos por dicha instancia.

He decidido no entrar en mayores detalles de este apartado puesto que, con ausencia de tráfico real y con limitaciones en el presupuesto a la hora de utilizar la plataforma, puede resultar un poco complicado de probar.

> <a href="https://docs.aws.amazon.com/elasticloadbalancing/latest/application/application-load-balancer-getting-started.html">Click aquí para acceder al tutorial de cómo crear un balanceador de carga</a>.

En el caso de Microsoft Azure, haré referencia a <a href="https://mslabs.cloudguides.com/en-us/guides/Azure%20Networking%20Solutions%20-%20Exercise%203">este tutorial</a> y, para Google Cloud Platform, a <a href="https://cloud.google.com/load-balancing?hl=en">esta guía de aquí</a>.

## Curso Sistemas Cloud - Nivel 5 (Amazon, Google y Microsoft)

### Reto: Servidor apache en una instancia Amazon EC2

Nuevamente, doy este punto por cubierto teniendo en cuenta la implementación que he hecho en el repositorio <a href="https://github.com/Dani-97/clip_imagesearch_aws_telegram_bot">clip_imagesearch_aws_telegram_bot</a>. Si bien es cierto que no se trata de un servidor apache, la implementación del mencionado repositorio utiliza una instancia de EC2 como servidor de una aplicación web (en este caso, el comportamiento de un bot de Telegram). Además, como primeros pasos para probar que había configurado bien la máquina virtual, hice una pequeña prueba con el servidor HTTP que incorpora Python y que se puede desplegar más fácilmente incluso que un servidor Apache (aunque bien es cierto que el servidor Python tiene una implementación menos preparada para entornos reales en comparación a un servidor apache, pero para la realización de este curso es algo a lo que no le he otorgado importancia). Este servidor se ejecuta con <code>python3 -m http.server</code> y permite hacer unas pruebas rápidas como, por ejemplo, ver si los puertos correspondientes para poder exponer el servidor públicamente están abiertos.

### Reto: Almacenamiento de archivos en Amazon S3

Los puntos de este reto ya están cubiertos en el repositorio <a href="https://github.com/Dani-97/telegram_bot_aws_s3_notification">telegram_bot_aws_s3_notification</a> ya que, en este caso, se necesita la creación de un bucket S3 para subir o eliminar archivos y poder notificar más tarde al bot de Telegram.

### Reto: Creación de una base de datos en Google Cloud SQL

Con respecto a los apartados de creación de bases de datos SQL en las diferentes plataformas, no quiero entrar en demasiados detalles ya que suelen ser servicios bastante costosos y todos ellos tienen un funcionamiento bastante similar. Por lo general, en la experiencia que he tenido con estas plataformas, es mejor centrarse en alguna que conozcamos bien (por ejemplo, en mi caso, MySQL) y avancemos con ello. La idea básica en lo que yo he hecho para probar la creación de bases de datos SQL consistó en ir a la plataforma, crear la base de datos siguiendo los pasos correspondientes y conectar con ella por medio de un cliente SQL (en este caso, el cliente de MySQL). Una vez probado que se puede acceder al servidor de base de datos, se pueden hacer algunas consultas SQL para probar que todo está funcionando bien.

> <a href="https://cloud.google.com/sql/docs/mysql/create-manage-databases#console">Tutorial para la creación de una base de datos MySQL en Google Cloud Platform y realización de los primeros pasos</a>.

### Reto: Creación de una función de Google Cloud Functions

La creación de una función de Google Cloud Run ya se ha cubierto en este repositorio <a href="https://github.com/Dani-97/clip_imagesearch_gcp_telegram_bot">clip_imagesearch_gcp_telegram_bot</a>, como bien se ha descrito en retos anteriores.

## Curso Sistemas Cloud - Nivel 6 (Amazon, Google y Microsoft)

### Reto: Creación y configuración de una máquina virtual de Microsoft Azure

Este reto ya ha sido cubierto previamente en el curso de nivel 3.

### Reto: Almacenamiento de archivos en Azure Blob Storage

El funcionamiento de Blob Storage es muy similar al de los S3 Buckets de AWS, de modo que no entraré en grandes detalles de cómo se utiliza en este reto. Sencillamente, me limitaré a dejar un tutorial de cómo es la utilización de esta herramienta.

> <a href="https://learn.microsoft.com/en-us/azure/storage/blobs/storage-quickstart-blobs-portal">Tutorial para el trabajo con objetos de Azure Blob Storage</a>.

### Reto: Creación de una base de datos en Azure SQL Database

Del mismo modo que en la parte de Google Cloud SQL, en este caso me voy a limitar a dejar un tutorial sobre cómo crear y trabajar con estos servidores de bases de datos. Personalmente, no he trabajado con SQL Server y su sintaxis resulta un poco confusa para mí. Por eso, para aquellos que no están acostumbrados a esta plataforma de bases de datos SQL, alternativamente existe, por ejemplo, Azure Database for MySQL, ya que Azure ofrece también soporte con algunos de los SGBD más populares. 

> <a href="https://www.dataquest.io/blog/tutorial-azure-sql-database/">Tutorial de uso de Azure SQL Database</a>.

> <a href="https://learn.microsoft.com/es-es/purview/register-scan-azure-mysql-database">Tutorial de uso de Azure Database for MySQL</a>.

### Reto: Creación de una función de Azure Functions

Este reto ya ha sido cubierto, como bien se describe en varios de los retos anteriores, con la realizaciòn del repositorio que se puede encontrar en este enlace <a href="https://github.com/Dani-97/clip_imagesearch_azure_telegram_bot">clip_imagesearch_azure_telegram_bot</a>. La implementación de una función de Azure Functions se llevó a cabo para comunicarse con un Space de HuggingFace que realiza una búsqueda de imágenes a partir de texto. La salida de esta función es utilizada posteriormente por el contenedor Docker de una máquina virtual, la cual a su vez gestiona el comportamiento de un bot de Telegram.

### Reto: Integración de servicios en la nube

En este reto del curso, se habla de la integración de los siguientes servicios:

- **Función sin servidor:** En este caso, ya he integrado una función sin servidor con otros módulos en la nube (incluso en otras plataformas externas a AWS, Azure y GCP como es el caso de HuggingFace). Esto se puede encontrar en repositorios como <a href="https://github.com/Dani-97/clip_imagesearch_gcp_telegram_bot">clip_imagesearch_gcp_telegram_bot</a> y <a href="https://github.com/Dani-97/clip_imagesearch_azure_telegram_bot">clip_imagesearch_azure_telegram_bot</a>.

- **Base de datos en la nube:** He decidido no trabajar con bases de datos en este caso, debido al elevado coste que tienen con respecto a otros servicios (por ejemplo, en el caso de AWS, sin haber hecho nada, solo configuración, el coste ya asciende a unos 50 centavos). En su lugar, he implementado un proyecto que integra el uso de un contenedor Docker (que se puede ejecutar tanto localmente como en la nube) con un bucket S3, utilizando Python y la librería <code>boto3</code>, que permite realizar la conexión y la interacción con ese bucket de S3. <a href="https://github.com/Dani-97/ai_files_manager">Click aquí para ver el respositorio de AI Files' Manager</a>.

- **Página web estática:** En ocasiones puntuales y a modo de prueba, he utilizado tanto el servidor HTTP que incluye Python (<code>python3 -m http.server</code>) como un Apache Server. Sin embargo, me he centrado más en integrar diferentes módulos para crear aplicaciones web dinámicas (como es el caso de los repositorios personales que he ido mencionado a lo largo de este README), lo cual deja más que demostradas mis destrezas trabajando desarrollando este tipo de tareas. En resumen, este sería el caso de la creación de un bot de Telegram funcional o el desarrollo de contenedores Docker que utilizan la librería <code>gradio</code> para ejecutar un servidor, siendo ejecutables en local pero fácilmente extrapolables a cualquier entorno de la nube (sobre todo si estamos hablando de instancias virtuales para cómputo como EC2, Compute Engine o Azure VM).
