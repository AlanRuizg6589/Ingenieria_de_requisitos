Problema actual presentado por nosotros (Sobre este problema vamos a presentar en la disertacion para la siguiente "prueba"):

***Una biblioteca presenta dificultades para organizar y administrar sus libros debido a que actualmente registra la información de manera manual (En cuadernos personales).***
***A su vez, no saben exactamente donde se encuentra cada libro, porque no tienen divisiones predefinidas en la biblioteca.***

***Esto provoca que sea difícil saber qué libros están disponibles, cuáles están prestados y cuándo deben ser devueltos, y cual es el estudiante respnasable. Además, los usuarios tienen problemas para encontrar que secciónes de estudio estan disponibles y los bibliotecarios deben revisar constantemente los registros personales para conocer el estado de cada sección.*** 

***También existen dificultades para controlar los préstamos atrasados y para mantener actualizada la información de los usuarios. Por esta razón, la biblioteca necesita un sistema que permita gestionar los libros, usuarios y préstamos de manera más rápida y organizada.***
👥
Actores del problema:

1. Bibliotecario → Registra libros, gestiona préstamos y controla devoluciones.

2. Usuario/Alumno → Busca libros y solicita préstamos.

3. Administrador → Administra la información del sistema y de los usuarios.

4. Proveedor de libros → Entrega nuevos libros a la biblioteca y proporciona información sobre ellos.

Entidades (Pueden aumentar en el futuro):

-Libro

-Ejemplar

-Alumno

-Prestamo

-Bibliotecario

-Admnistrador

-Proovedor

Problema 1:

**"Una biblioteca presenta dificultades para organizar y administrar sus libros debido a que actualmente registra la información de manera manual (En cuadernos personales). "**

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

Problema 2:

**A su vez, no saben exactamente donde se encuentra cada libro, porque no tienen divisiones predefinidas en la biblioteca.**

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

Con estas entidades creadas, podemos organizar mejor la biblioteca de la siguiente forma:

*Varios libros (Incluyendo su Stock completo) se registraran como perteneciente a una estanteria en especifico. El ISBN del libro no se tiene que encontrar en mas de una estanteria distinta a la inicial; Relación 1:N.*

*Cada estanteria va a pertenecer a una sola sección en especifico (O talvez, una sección no tiene ninguna estanteria. Se pueden usar para zonas de estudio.); Relación 1:N*

Con esta distribución, se podra dividir varias estanterias distintas en secciones especificas (Matemáticas, Ciencias, Biología, o lo que el bibliotecario decida) facilitando la busqueda de cada libro mucho más.

Problema 3:

*Esto provoca que sea difícil saber qué libros están disponibles, cuáles están prestados, cuándo deben ser devueltos y cual es el alumno responsable.*

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

Con estas 3 entidades creadas (Se incluye la entidad Libro) se puede crear un sistema de base de datos funcional que registre al usuario cuando hace una arriendo. Las conexiones serian de la siguiente forma:

*La entidad Arriendo_libro tendra una Relación 1:1 con el Libro registrado (Que el usuario desee)*

*El usuario podra tener varios Arriendo_libro distintos, pero cada uno solo pertenecera a un Usuario en especifico (Relación 1:N).*

Con esto se podra mantener a raya a cualquier usuario que desee arrendar un libro (o varios libros).

(Todo esta escrito a mano).