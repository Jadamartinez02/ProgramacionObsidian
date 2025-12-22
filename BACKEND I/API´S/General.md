	FrameWorks 

* Java - Spring boot
* C# - .Net
* Python - Django, Fast API
* PHP - Laravel 
[[Glosario]]


API + SERVDIDORES:
=
								Librerias esenciales
=> levantar servidores                   Spring web 1)
=> leer peticiones HTTP                Spring web
=> Enviar respuestas HTTP            Spring web
=> Logica negocio                         
=> Desplegar SIN                          
                                JPA SQL herramienta para persistencia de datos (traductor de java a sql, ORM) 2)
                                 mysql ( crear la conexion de la base de datos A DB (jdbc-Java Data Base Conection)) 3)
                                 H2 (base de datos embebida o virtualizada) 4)
                                 DevTools(Herramientas para facilitar la programacion) 5)

Persistencia de datos
=

Las anotaciones para operar contexto
@Anotacion, arriba de las clases en spring boot

Manipular transformar tabla en Spting Boot
anotacion @Table("") Cambiar modificar, definir la tabla 
@GeneratedValue() definir la estrategia de generacion de la llave primaria 
@Column() Cambiar nombre de columnas 

TAREA COLE, TAREA
=

Todas las anotaciones haciendo las 3 tables y las configuraciones de las tablas 



El servidor envia
Respuestas 
El clliente envia
Peticiones (request)

¿Porque un cliente quiere comunicarse con la db? 
### Peticiones
* Headers(Cabeceras)-Por fuera
		 - Endpoins y datos
* Body(Datos)-Por dentro
		-

### Servidor

Uri = url/ep/

Para programar API´s se utilizan arquitecturas
La mas comun que se utiliza es MVC "Modelo Vista Controlador"
En el que contiene

Arquitectura de capas:
Desventaja aplicacion acoplada(Si una muere las otras tambien)

