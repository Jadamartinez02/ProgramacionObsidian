
| Título del Documento                       | Conceptos Clave Cubiertos                                                                                                                                                                                                                                                                                                                                       |
| ------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Object Oriented Programming Intro...**   | Introduce los pilares de la POO: Abstracción, Encapsulamiento, Herencia y Polimorfismo. Detalla qué es un Objeto, una Clase, Atributos y Métodos. Incluye una comparación entre la programación Procedural y la POO, y explica los Modificadores de Acceso (`public`, `private`).                                                                               |
| **Inheritance Abstraction Polymorphis...** | Profundiza en Herencia, incluyendo el uso de la palabra clave `super` para constructores y acceso a miembros. Explica el Polimorfismo a través de la Sobreescritura de Métodos (`@Override`) y las Clases y Métodos Abstractos. También toca el tema de la Sobrecarga de Métodos.                                                                               |
| **Exceptions.pptx**                        | Cubre el manejo de Errores y Condiciones Excepcionales en Java. Explica las palabras clave `try`, `catch`, `throw`, `throws`, y `finally`. Clasifica los tipos de Excepciones (Checked vs. Unchecked/Runtime vs. Error) y cómo crear y encadenar excepciones propias.                                                                                           |
| **Interfaces Generics Collections API...** | Abarca cuatro temas avanzados: **Interfaces** (qué especifican sin implementar), **Principios SOLID** (Responsabilidad Única, Abierto/Cerrado, Sustitución de Liskov, Segregación de Interfaces, Inversión de Dependencia), **Genéricos** (tipos parametrizados para seguridad de tipos y colecciones), y la **Collections API** (interfaces List, Set, y Map). |
| **Relations Between Objects.pptx**         | Se centra en cómo representar las relaciones entre objetos en un diseño POO, más allá de la herencia. Define y compara: **Dependencia**, **Asociación**, **Agregación** (la parte puede existir sin el todo) y **Composición** (el ciclo de vida de la parte está ligado al del todo).                                                                          |
| **Design Patterns.pptx**                   | Introduce los Patrones de Diseño, su clasificación (Creacionales, Estructurales, de Comportamiento) y la importancia de aprenderlos. Detalla dos patrones específicos: **Builder** (Creacional) y **Strategy** (Comportamiento).                                                                                                                                |
| **Static keyword.pptx**                    | Explica el uso de la palabra clave `static` para atributos y métodos que pertenecen a la clase y no a la instancia. También cubre los Bloques Estáticos, las Clases Anidadas Estáticas y cómo el patrón Singleton se relaciona con `static`.                                                                                                                    |

### Dependencia:
La dependencia es una relacion debil, en la cual la parte dependiente puede exisitir sin la dependencia, ajustandose a los cambios 

## Asociacion 
Es una relacion mas fuerte que dependencia, estas pueden existir independiente de la otra 

### Agregacion 
En la agregacion es una relacion mas fuerte que la asociacion, donde el todo tiene referencias de las partes. Las partes pueden existir sin necesidad del todo 

### Composicion 
La composicion es una relacion mas fuerte que la agregacion, donde el todo tiene referencias de las partes, y controla la exitencia de las partes. Las partes no pueden vivir sin el todo.

* Diferencia entre una clase y un objeto
	* Una clase es un molde, un objeto es el uso o instancia de ese molde 
* Para que se usa la herencia y cuando se usa  es-un
	* Una herencia es la forma de adoptar metodos, atributos y demas, se usa cuando estas clases comparten una relacion ES-UN
* Que es una interfaz
	* Una interfaz es un contrato que determina que se utuliza  
* Que es una clase abstracta 
	* Una clase abstracta es parecida a una interfaz, compartiendo la caracteristica que usan contratos para definir en clases hijas, esta no puede ser instanciada.
* Que otra forma de heredar hay que no sea herencia
	* Interfaces y composicion 
* Puedes una clase tener mas de una clase padre
	* No, no existe la herencia multiple en Java
* Que es agregacion y que es composicion 
	* agregacion es una relacion mas debil que la composicion, donde el todo tiene referencia de las partes, y las partes pueden exisitir sin el todo.
	* composicion es una relacion mucho mas fuerte que la agregacion, donde el todo contiene refrencias de las partes. Donde el todo controla la exitencia de las partes y las partes sin el todo no puede existir.
* Dos principios SOLID
	* S sigle responsabilty, principio de responsabilidad unica. Dice que un modulos deben tener una unica razon para  cambiar. Responsabilidad unica 
	* I interface segregation, dice que no debemos utiiizar interfaces que no se usan. 
* Que es polimofrismo y sus dos tipo
	* El polimorfismo es la manera para que una operacion se comporte de diferentes maneras
		* Overriding
		* Overloading 
* Para que se usan los modificadores de acceso 
	* Los modificadores de acceso se utilizan para controlar el acceso y encapsulamiento 
* Patrones de diseño, y explicarlo 
* Pilares de la POO
	* Abstraccion
	* Encapsulamiento
	* Herencia
	* Polimorfismo
* Java generics 
	* Java generics, se utilizan para poder reutulizar metos, y no tener que asigarles directamente el tipo de dato, donde estos se suminstran mediante diamantes 

---
* Que es un atributo estatico 
	* Es un atributo que tiene el comportamiento de la keyword static, donde se puede acceder a este mediante la clase, sin la necesidad de instanciarla
* Checked and Unchecked 
	* Checked: Son la excepeciones que debemos manejar por obligacion para no interrumpir el flujo del programa 
	* Unchecked son los tipos de excepciones que tenemos la opcion de manejarlas o no
* Dos atributos de la clase Exception 
	* atrubuto mensage y causa 
* Encadenamiento de excepciones
	* El encadenamiento de excepciones en cuando se atrapa una excepcion y esta excpecion es utilizada en otra excepcion como causa, se encadena entre estas  
* Como llamo un construtor desde otro constructor 
	* Con la keyword this(atributo) se llama un constructor dentro de otro constructor
