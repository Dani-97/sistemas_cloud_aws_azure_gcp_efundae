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

En la realización de este curso, se enuncian una serie de Retos, que se tratan de pequeños supuestos prácticos para aprender y demostrar los conocimientos en el uso de las plataformas y sus herramientas principales. En mi caso personal, he decidido no centrarme tanto en los retos individuales, porque considero que la mejor demostración de la habilidad que uno tiene en este tipo de entornos es el hecho de poder crear una aplicación funcional creando una arquitectura cloud de cierta complejidad que engloba diferentes servicios. Por eso, he realizado algunos supuestos prácticos más complejos, disponibles en repositorios públicos de GitHub. 

A pesar de todo, me gustaría cubrir uno por uno los retos que se enuncian en el curso. En algunos casos, me limitaré a hacer referencia a la documentación disponible online, en otros hablaré de los comandos que se deben ejecutar para realizar las diferentes tareas y, en aquellos casos donde haya implementado un supuesto práctico más elaborado, haré referencia a él.

## Curso Sistemas Cloud - Nivel 3 (Amazon, Google y Microsoft)

### Reto: Crear y configurar una cuenta en AWS y GCP

La creación de una cuenta en las diferentes plataformas es algo bastante sencillo e inmediato, además de intuitivo. La única complejidad reside en el hecho de tener que introducir la tarjeta de crédito para poder acceder a las opciones de prueba de cada plataforma. Por ello, no me voy a centrar en esta parte y voy a pasar a los puntos siguientes.

### Reto: Desplegar una instancia de EC2 en AWS

EC2 permite crear instancias de máquinas virtuales en AWS. Esto es algo que ya he hecho previamente en <a href="https://github.com/Dani-97/clip_imagesearch_aws_telegram_bot">clip_imagesearch_aws_telegram_bot</a>. En términos generales, la creación de una máquina virtual involucra seleccionar sus características software y hardware (teniendo en cuenta el Sistema Operativo y los elementos hardware más importantes como es el caso del número de vCPUs, la cantidad de RAM o el tamaño del disco duro). Una vez seleccionado todo lo que deseamos, tendremos nuestra máquina virtual, con la que podremos conectar de múltiples maneras, pero una de las más estándar es utilizando un cliente SSH. La dificultad, en este caso, es disponer de un par de claves SSH para poder acceder a la máquina (ya que, de lo contrario, el acceso será denegado y no podremos acceder a ella directamente). Dentro de la instancia de EC2, podremos trabajar como si se tratase de cualquier otro tipo de máquina virtual, adaptándonos al sistema operativo que hayamos instalado en cada caso.

### Reto: Almacenar y recuperar archivos en S3 y Google Cloud Storage

En el caso de AWS S3, también he creado un repositorio que se puede encontrar haciendo <a href="https://github.com/Dani-97/telegram_bot_aws_s3_notification">click aquí</a>. En este caso, el proyecto que desarrollé involucra la creación de un bucket S3 y de dos funciones lambda (la opción Serverless Computing que ofrece AWS). En este caso, lo que hace la implementación desarrollada es conectar las funciones lambda con diferentes eventos vinculados al bucket (en este caso, la creación y eliminación de archivos o, como denomina la plataforma en este caso, objetos) y notificar a un usuario por medio de un bot de Telegram. En concreto, cada vez que un archivo se sube al bucket, se notifica al usuario de ese hecho y, por la otra parte, si un archivo se elimina, también se notifica al usuario.

Google Cloud Storage, por su parte, <code>ESTÁ PENDIENTE DE LLEVARSE A CABO</code>

### Reto: Desplegar una máquina virtual en GCP y Microsoft Azure

El despliegue de una máquina virtual es muy similar en todas las plataformas. Las únicas diferencias existentes reside en cómo trabaja cada una de ellas. El objetivo final sigue siendo el mismo que con AWS: configurar y crear la máquina virtual para más tarde conectar con ella por medio de SSH. Para utilizar tanto los servicios de máquinas virtuales como los de serverless computing, he replicado este proyecto <a href="https://github.com/Dani-97/clip_imagesearch_aws_telegram_bot">clip_imagesearch_aws_telegram_bot</a> previamente descrito en AWS para las otras dos plataformas Cloud. De este modo, en <a href="https://github.com/Dani-97/clip_imagesearch_gcp_telegram_bot">clip_imagesearch_gcp_telegram_bot</a> y <a href="https://github.com/Dani-97/clip_imagesearch_azure_telegram_bot">clip_imagesearch_azure_telegram_bot</a> se encuentran los repositorios de las implementaciones con Google Cloud Platform y Microsoft Azure, respectivamente.

## Curso Sistemas Cloud - Nivel 4 (Amazon, Google y Microsoft)

### Reto: Gestión de Identidades y Control de Acceso en la Nube.

<code>PENDIENTE DE CUBRIR</code>

### Reto: Configurar alertas y monitoreo básico

<code>PENDIENTE DE CUBRIR</code>

### Reto: Desplegar una aplicación web básica en la nube

Teniendo en cuenta las implementaciones de los repositorios <a href="https://github.com/Dani-97/clip_imagesearch_aws_telegram_bot">clip_imagesearch_aws_telegram_bot</a>, <a href="https://github.com/Dani-97/clip_imagesearch_gcp_telegram_bot">clip_imagesearch_gcp_telegram_bot</a> y <a href="https://github.com/Dani-97/clip_imagesearch_azure_telegram_bot">clip_imagesearch_azure_telegram_bot</a>, este punto ya quedaría cubierto. Estos repositorios no solo implementan una aplicación web básica, si no que además plantean una arquitectura de cierta complejidad en la que intervienen diferentes módulos separados como son, en este caso, el serverless computing y las instancias de máquinas virtuales. Además, dentro de las máquinas virtuales, hago uso de la herramienta DevOps Docker para facilitar el proceso de despliegue en todos los casos.

### Reto: Escalar una aplicación en la nube

<code>PENDIENTE DE CUBRIR</code>

### Reto: Configurar un balanceador de carga en la nube

<code>PENDIENTE DE CUBRIR</code>

## Curso Sistemas Cloud - Nivel 5 (Amazon, Google y Microsoft)

### Reto: Servidor apache en una instancia Amazon EC2

Nuevamente, doy este punto por cubierto teniendo en cuenta la implementación que he hecho en el repositorio <a href="https://github.com/Dani-97/clip_imagesearch_aws_telegram_bot">clip_imagesearch_aws_telegram_bot</a>. Si bien es cierto que no se trata de un servidor apache, la implementación del mencionado repositorio utiliza una instancia de EC2 como servidor de una aplicación web (en este caso, el comportamiento de un bot de Telegram). Además, como primeros pasos para probar que había configurado bien la máquina virtual, hice una pequeña prueba con el servidor HTTP que incorpora Python y que se puede desplegar más fácilmente incluso que un servidor Apache (aunque bien es cierto que el servidor Python tiene una implementación menos preparada para entornos reales en comparación a un servidor apache, pero para la realización de este curso es algo a lo que no le he otorgado importancia). Este servidor se ejecuta con <code>python3 -m http.server</code> y permite hacer unas pruebas rápidas como, por ejemplo, ver si los puertos correspondientes para poder exponer el servidor públicamente están abiertos.

### Reto: Almacenamiento de archivos en Amazon S3

Los puntos de este reto ya están cubiertos en el repositorio <a href="https://github.com/Dani-97/telegram_bot_aws_s3_notification">telegram_bot_aws_s3_notification</a> ya que, en este caso, se necesita la creación de un bucket S3 para subir o eliminar archivos y poder notificar más tarde al bot de Telegram.

### Reto: Creación de una base de datos en Google Cloud SQL

<code>PENDIENTE DE CUBRIR</code>

### Reto: Creación de una función de Google Cloud Functions

La creación de una función de Google Cloud Run ya se ha cubierto en este repositorio <a href="https://github.com/Dani-97/clip_imagesearch_gcp_telegram_bot">clip_imagesearch_gcp_telegram_bot</a>, como bien se ha descrito en retos anteriores.


## Curso Sistemas Cloud - Nivel 6 (Amazon, Google y Microsoft)

### Reto: Creación y configuración de una máquina virtual de Microsoft Azure

Este reto ya ha sido cubierto previamente en el curso de nivel 3.

### Reto: Almacenamiento de archivos en Azure Blob Storage

<code>PENDIENTE DE CUBRIR</code>

### Reto: Creación de una base de datos en Azure SQL Database

<code>PENDIENTE DE CUBRIR</code>

### Reto: Creación de una función de Azure Functions

Este reto ya ha sido cubierto, como bien se describe en varios de los retos anteriores, con la realizaciòn del repositorio que se puede encontrar en este enlace <a href="https://github.com/Dani-97/clip_imagesearch_azure_telegram_bot">clip_imagesearch_azure_telegram_bot</a>. La implementación de una función de Azure Functions se llevó a cabo para comunicarse con un Space de HuggingFace que realiza una búsqueda de imágenes a partir de texto. La salida de esta función es utilizada posteriormente por el contenedor Docker de una máquina virtual, la cual a su vez gestiona el comportamiento de un bot de Telegram.

### Reto: Integración de servicios en la nube

<code>PENDIENTE DE CUBRIR</code>
