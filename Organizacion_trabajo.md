Problema actual presentado por nosotros (Sobre este problema vamos a presentar en la disertación para la siguiente "prueba"):
***Mi nombre es José Antonio de la Mercedes, soy dueño de una antigua biblioteca personal que se encuentra dentro de Puerto Montt.***

***Nunca me encontrado muy adaptado al ambiente de hoy en día, ni a la tecnología. Por esta razon seguí un modus operandi que consideraba que funcionaba muy bien.***

***Tenía gente que trabaja en mi biblioteca hace años, y les pagaba muy bien. Pero tarde o temprano se retiraron del área y ahora e buscado nuevos empleados.***

***Gracias a esto e recibido muchas quejas de mis empleados, que soy muy anticuado y esas cosas. No estoy muy acuerdo, pero tomare sus palabras.***

***Me comentaron que es incoveniente tener que registrar todos los libros a mano, que es problematico tener que usar un libro personal para tener en cuenta a todos los libros que existen dentro de la biblioteca. Esto no pasaba antes, pense que era facil saber de memoria que libros tenemos y donde se encuentran.***

***Tambien me comentaron que la biblioteca no tiene sectores claros ni a su vez divisiones. Y que a su vez, un libro (independiente de la cantidad) se deberia encontrar dentro de una sola estanteria, en vez de guardarlo en la que sea***

***También estan molestos porque decidi recientemente agregar un sistema de libros prestados. Pense que seria facil de llevar para ellos, pero me dijeron que no existe forma clara de mantener registro de quien tiene un libro y cual tiene exactamente.***

***Existe un sector que en teoría deberia funcionar para que la gente lo pueda arrendar, pero mis trabajadores se rehúsan a usarlo, porque "es inconveniente saber cuando y cual esta siendo usado".*** 

***A su vez me comentaron que no existe forma de tratar con los gente que tiene prestamos atrasados o causan inconvenientes.***

***Nunca me había dado cuenta de estos problemas, tengo esta biblioteca hace años, la razón por la que la tengo abierta es por diversión, igualmente tengo mucho dinero.***

***Considerando que no tengo mucho conocimiento, quisiera un sistema en el cual se solucione todos estos problemas. Confiare en la palabra de mis empleados, todo para que la experiencia de la gente que quiera estudiar sea mejor, y que las siguientes generaciones sean cada vez más inteligente."***
👥
Actores del problema:

1. Trabajador → Registra libros, gestiona sectores de estudio, gestiona préstamos y controla devoluciones.

2. Usuario → Busca libros y solicita préstamos, o solicita sectores de estudio.

3. Dueño → Administra la información del sistema y de los usuarios.

4. Proveedor de libros → Entrega nuevos libros a la biblioteca y proporciona información sobre ellos.

Entidades (Pueden aumentar en el futuro):

-Libro

-Ejemplar

-Usuario

-Prestamo

-Bibliotecario

-Admnistrador

-Proovedor

***Problema 1:***

El dueño de la biblioteca comenta lo siguiente:

***"Me comentaron que es incoveniente tener que registrar todos los libros a mano, que es problematico tener que usar un libro personal para tener en cuenta a todos los libros que existen dentro de la biblioteca."***

y se puede interpretar de la siguiente forma:

**"La biblioteca presenta dificultades para organizar y administrar sus libros debido a que actualmente registra la información de manera manual (En cuadernos personales). "**

Para mejorar el registro de cada libro, crearemos una **entidad libro** que almacene todos los datos importantes que facilitaran la busqueda.

**Entidad - Libro**

*Atributos:*
          - ID (PK, permite que cada libro registrado sea fundamentalmente distinto).

          - Nombre; [Permitira una busqueda mas rapida solo por su nombre].

          - Entidad auxiliar; Genero de libro [Permite clasificar a todos los libros por algun tipo de genero, permitiendo la opcion de busqueda por genero / Relacion N-M].

          - Entidad auxiliar; Autor [Permite registrarle al libro autor o distinto autores / Relacion N-M].

          - Stock [Permite conocer la cantidad de libros en esta sede (Solo en esta sede)].

          - ISBN (Es un numero unico de cada libro (como entidad, no en cantidad)).

Con todos estos datos, **el registro de un libro estaria completo** y gracias a todas estas categorias la busqueda de un libro en especifico se facilitara.

***Problema 2:***

El dueño comenta lo siguiente:

***"Tambien me comentaron que la biblioteca no tiene sectores claros ni a su vez divisiones. Y que a su vez, un libro (independiente de la cantidad) se deberia encontrar dentro de una sola estanteria, en vez de guardarlo en la que sea"***

Se puede interpretar de la siguiente forma:

**La biblioteca necesita ser divida en secciones (con nombre), con varias estanterias en cada una. Con la restricción de que un libro exacto (ISBN) no se puede encontrar en varias estanterias a la vez.**

Al tener la entidad de libro completa, tenemos que buscar formas de dividir la sede de la biblioteca para ubicar cada libro en zonas especificas.

Para esto crearemos las siguientes entidades:

**Entidad - Estanteria**

*Atributos:* 
            - ID (PK, permite que cada estanteria registrada sea distinta).

            - Nombre estanteria (Permite diferencias cada estanteria de la otra, se puede usar cualquier tipo de dato para el nombre).

**Entidad - Sección**

*Atributos:*

            - ID (PK, permite que cada Sección registrada sea distinta).

            - Nombre Sección (Permite diferencias cada Sección de la otra, se puede usar cualquier tipo de dato para el nombre).

            - ¿Es arrendable? (Permite conocer si es una sección en la cual varios o un solo alumno lo puede arrendar para su estudio personal).

Con estas entidades creadas, podemos organizar mejor la biblioteca de la siguiente forma:

*Varios libros (Incluyendo su Stock completo) se registraran como perteneciente a una estanteria en especifico. El ISBN del libro no se tiene que encontrar en mas de una estanteria distinta a la inicial; Relación 1:N.*

*Cada estanteria va a pertenecer a una sola sección en especifico (O talvez, una sección no tiene ninguna estanteria. Se pueden usar para zonas de estudio.); Relación 1:N*

Con esta distribución, se podra dividir varias estanterias distintas en secciones especificas (Matemáticas, Ciencias, Biología, o lo que el bibliotecario decida) facilitando la busqueda de cada libro mucho más.

***Problema 3:***

El dueño dice lo siguiente:

***"También estan molestos porque decidi recientemente agregar un sistema de libros prestados. Pense que seria facil de llevar para ellos, pero me dijeron que no existe forma clara de mantener registro de quien tiene un libro y cual tiene exactamente."***

Se puede interpretar de la siguiente manera:

*Es dificil saber qué libros están disponibles, cuáles están prestados, cuándo deben ser devueltos y cual es el usuario responsable.*

Para este problema, tenemos una entidad *ya definida* siendo el **Libro**. Ahora solo tenemos que complementarlo para que existan un sistema funcional de registros.

Para esto crearemos las siguientes entidades:

**Entidad - Usuario/Alumno**

*Atributos:*

            - ID (Para que todos los estudiantes en el registro sean fundamentalmente distintos).

            - Nombre_usuario (Permite conocer el nombre base del usuario/alumno).

            - RUT (Permite ser un identificador unico de cada usuario/alumno).

            - Email (Permite comunicarse con el Usuario en caso de alguna necesidad).

            - º Numero de telefono (Permite comunicarse con el Usuario en caso de alguna necesidad).

**Entidad - Arriendo_libro**

*Atributos:*
            - ID (Permite diferenciar a cada arriendo registrado en la base de datos).
            
            - Fecha_Arriendo (Para conocer el momento exacto en el ocurrio y se encuentre documentado).

            - Fecha_Devolución (Para conocer el momento en el que el usuario tiene que devolver el libro arrendado).

**Entidad - Estado_libro**

*Atributos*

            - ID

            - Descripción_estado_inicial (el trabajador antes de entregar el libro, registra su estado actual de forma vaga)
            
            - Descripción_estado_inicial (Despues de que el usuario use el libro y lo entregue, se registra el estado en el cual es entregado)

Con estas 3 entidades creadas (Se incluye la entidad Libro) se puede crear un sistema de base de datos funcional que registre al usuario cuando hace una arriendo. 

Las conexiones serian de la siguiente forma:

*La entidad Arriendo_libro tendra una Relación 1:1 con el Libro registrado (Que el usuario desee)*

*El usuario podra tener varios Arriendo_libro distintos, pero cada uno solo pertenecera a un Usuario en especifico (Relación 1:N).*

*Un Arriendo_libro puede tener varios estado_libro, pero cada estado_libro solo pertenecen a un arriendo.*

*Un libro puede tener varios estado_libro durante su historia, pero cada estado_libro solo pertenecen a un solo libro*

Con esto se podra mantener a raya a cualquier usuario que desee arrendar un libro (o varios libros).

***Problema 4:***


***DATOS DEL CANVA EXPLICACIÓN, PARA PRESERVARLO:***
***Una Sección puede tener varios Arriendo_sección durante su historia, pero cada registro pertenece a una sola sección.***
***Un Usuario puede tener varios Arriendo_sección en su historial, y un Arriendo_sección puede tener varios usuarios a la vez.***

***Cada descripción de estado_sección es unico para un unico arriendo.***
***Cada estado_sección solo pertenece a un sola sección, pero una sección puede tener varias estado_sección.***
El dueño dice lo siguiente:

***"Existe un sector que en teoría deberia funcionar para que la gente lo pueda arrendar, pero mis trabajadores se rehúsan a usarlo, porque "es inconveniente saber cuando y cual esta siendo usado"."***

Se puede interpretar de la siguiente forma:

**El sector de zona de estudio se encuentra en desuso, manteniendo el mismo problema de dificultad para mantener registro de quien lo esta usando, cual sección esta siendo usada y en que momento se esta arrendando**

Para este problema tenemos un pilar fundamental ya preparado; La entidad Usuario con sus atributos explicados. Con esto tenemos que complementarlo para que, parecido al sistema de arriendo de libros, exista uno que sea para el de secciónes.

Para esto crearemos la siguiente entidad:

**Entidad - Arriendo_Sección**

*Atributos:*

            - ID (Permite diferenciar a cada arriendo de sección registrado en la base de datos).
            
            - Hora_inicio (Para conocer el momento en el comenzara el arriendo de la sección).

            - Hora_final (Para conocer el momento en el terminara el arriendo de la sección).

            - Fecha (Permite conocer el momento que se arrendara la sede especifica).    

**Entidad - Estado_sección**

*Atributos*

            - ID

            - Descripción_estado_inicial (el trabajador antes de dar el permiso, tiene que describir vagamente como estaba la sección antes de que se arriende)
            
            - Descripción_estado_inicial (Despues de que el usuario/s usen la sección, se requiere una descripción de como se encontraba al final de este)

Con la entidad Usuario/Alumno, Arriendo_sección y Seccion se puede definir un sistema funcional para que los usuarios puedan arrendar secciones en la sede.

Las conexiones serian de la siguiente forma:

*Una sección puede tener varios Arriendo_sección a la vez, pero cada Arriendo_sección solo le pertenecen a una sola sección (1:N).*

*Un Usuario puede tener varios Arriendo_sección en su historia, y en un Arriendo_sección pueden participar varios usuarios (N:M).*

*Una Arriendo_sección solo puede tener una descripción unica con fecha precisa sobre el estado-sección, y un estado sección no se puede repetir. (1:1)*

*Una sección puede tener varios estados_sección durante su historia, pero cada arriendo_sección solo pertenecen a un sola sección (1:N)*

Con esto, un solo Usuario o varios a la vez pueden arrendar secciones especificas a la vez, con todos estos datos siendo guardados en el sistema.

***Problema 5:***

El dueño dice lo siguiente:

***"A su vez me comentaron que no existe forma de tratar con los gente que tiene prestamos atrasados o causan inconvenientes."***

Se puede interpretar de la siguiente forma:

**No existe forma clara de tratar a la gente que tiene prestamos atrasados o causa inconveniente en la zona.**

Este es el problema mas distinto, *aqui no se tienen que crear variables*; se modifica y crean atributos dentro de entidades ya existentes dentro de nuestra base de datos.

Modificaremos primero la Entidad Usuarios:

*Atributos: (Nuevos +)*

            - Faltas_arriendo_libros_usuario (Empezara idealmente en 0, permite mantener registro de cuantas faltas a tenido el usuario en la sección de arriendo de libros. El máximo de faltas y la razón de estas no lo decidimos nosotros)

            - Faltas_arriendo_sección_usuario (Empezara idealmente en 0, permite mantener registro de cuantas faltas a tenido el usuario en la sección de arriendo de secciones. El máximo de faltas y la razón de estas no lo decidimos nosotros)

Con esto se podra ver exactamente la cantidad de faltas que tiene un usuario en especifico, en estos dos sectores.

Pero para que se encuentre más completo el sistema es necesario mantener registro en **donde** se registro la falta.

Agregaremos el siguiente atributo en Arriendo_libros y Arriendo_secciones (El mismo atributo de la misma forma con las mismas caracteristicas):

*Atributos: (Nuevos +)*

            - ¿Cometio una falta? {bool, True - False} (Permite que en cada registro, al momento de entregarlo se registre si cometio una falta o no. Puede ser manualmente o automáticamente, esto no lo decidimos nosotros)

Con todos estos datos agregados, se puede tener un sistema funcional en el cual se puede mantener a raya a todos los usuarios. Todas las penalizaciones no la decidimos nosotros.

Por ahora creo que esto es todo lo que hay que hacer (Si leen esto y falta algo avisen por el whatsapp).