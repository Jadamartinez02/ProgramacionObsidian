[[POO]]
## POO
#poo es un paradigma de programación, en el cual se basa en Clases y Objetos, que son capaces de representar entidades, objetos y conceptos mediante estas.

---

## Clases 

### <span style="color: blue;">Como lo entiendo:  </span>
Las #clases son moldes especificos que definen directamente el comportamiento de un Objeto 

---
# Teoría de Clases en Java y en General

La programación orientada a objetos (POO) es un paradigma que utiliza "clases" y "objetos" para organizar el código y facilitar su mantenimiento y reutilización. En Java, las clases son uno de los conceptos fundamentales de este paradigma. A continuación, se presenta una explicación sobre las clases en Java y en general.

## ¿Qué es una Clase?

Una **clase** es una plantilla o un modelo que define las características y comportamientos de un tipo de objeto. En términos más técnicos, una clase es una estructura que encapsula datos (atributos) y métodos (funciones) que operan sobre esos datos.

### Componentes de una Clase

1. **Atributos (o Propiedades)**: Son las variables que definen el estado de un objeto. Por ejemplo, en una clase `Coche`, los atributos podrían ser `color`, `marca`, `modelo`, etc.

2. **Métodos**: Son las funciones que definen el comportamiento de los objetos de la clase. Por ejemplo, en la clase `Coche`, podrías tener métodos como `acelerar()`, `frenar()`, `tocarBocina()`, etc.

3. **Constructores**: Son métodos especiales que se utilizan para crear instancias de la clase. Un constructor tiene el mismo nombre que la clase y no tiene un tipo de retorno. Se puede sobrecargar, lo que significa que puedes tener múltiples constructores con diferentes parámetros.


---
## Objetos
### <span style="color: blue;">Como lo entiendo:  </span>
Los #objetos son la instanciacion de la clase mediante el contructor.


list.of(metodo estatico de la intefaz lista)


---
# Teoría de Objetos en Java y en General

En la programación orientada a objetos (POO), un **objeto** es una instancia de una clase. Los objetos son fundamentales para este paradigma, ya que representan entidades del mundo real y encapsulan tanto datos como comportamientos. A continuación, se presenta una explicación sobre los objetos en Java y en general.

## ¿Qué es un Objeto?

Un **objeto** es una unidad que combina estado (atributos) y comportamiento (métodos). Cada objeto tiene su propia identidad y puede interactuar con otros objetos a través de sus métodos. Los objetos son instancias concretas de una clase, lo que significa que se crean a partir de la definición de una clase.

### Características de los Objetos

1. **Atributo(Estado)**: Representado por los atributos del objeto. Por ejemplo, un objeto `Coche` puede tener atributos como `color`, `marca` y `modelo`.

2. **Metodos(Comportamiento)**: Representado por los métodos del objeto. Por ejemplo, un objeto `Coche` puede tener métodos como `acelerar()`, `frenar()`, y `tocarBocina()`.

3. **Referencia(Identidad)**: Cada objeto tiene una identidad única, que lo distingue de otros objetos, incluso si tienen el mismo estado.


 


---
## Herencia ( cuantas clases pueden ser heredadas ) (estudiar referencia circular y como lo evito)
	
### <span style="color: blue;">Como lo entiendo:  </span>
La #herencia es la forma de acceder de una clase a otra, compartir sus metodos y sus atributos en mejores palabras heredaralas.

---
# Resumen de Herencia en Programación Orientada a Objetos

La **herencia** es uno de los conceptos fundamentales de la programación orientada a objetos (POO) que permite crear una nueva clase basada en una clase existente. La clase que se hereda se llama **clase base** o **clase padre**, y la nueva clase se llama **clase derivada** o **clase hija**. La herencia promueve la reutilización del código y establece una relación jerárquica entre las clases.

## Características de la Herencia

1. **Reutilización de Código**: La herencia permite que la clase hija herede atributos y métodos de la clase padre, lo que evita la duplicación de código. Esto facilita el mantenimiento y la extensión del software.

2. **Relación "Es-Un"**: La herencia establece una relación "es-un" entre la clase hija y la clase padre. Por ejemplo, si tienes una clase `Animal` y una clase `Perro` que hereda de `Animal`, puedes decir que un `Perro` es un `Animal`.

3. **Sobreescritura de Métodos**: La clase hija puede modificar el comportamiento de los métodos heredados de la clase padre mediante la **sobreescritura** (overriding). Esto permite que la clase hija implemente su propia versión de un método #overriding.

4. **Constructores**: Los constructores de la clase padre no se heredan, pero la clase hija puede llamar al constructor de la clase padre utilizando la palabra clave `super`.

## Ejemplo de Herencia en Java

Aquí tienes un ejemplo simple que ilustra la herencia en Java:

```java
// Clase padre
public class Animal {
    public void hacerSonido() {
        System.out.println("El animal hace un sonido.");
    }
}

// Clase hija
public class Perro extends Animal {
    @Override
    public void hacerSonido() {
        System.out.println("El perro ladra.");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal miAnimal = new Animal();
        miAnimal.hacerSonido(); // Salida: El animal hace un sonido.

        Perro miPerro = new Perro();
        miPerro.hacerSonido(); // Salida: El perro ladra.
    }
}
```

## Tasks herencia
#DiamonProblem #ReferenciaCircular
* ¿cuantas clases pueden ser heredadas?
No se permite herencias multiples, solo se puede heredar una clase **pero** puede implementar multuples interfaces
* ¿Que es el diamond problem y como evitarla?
La referencia circular es un problema que se causa en Java no explicitamente con las multiples herencias como en caso de lenguajes que acepten esta, sino mas que todo en el caso de las interfaces.
¿Como se soluciona?
La solucion puede ser un Override en la clase que implementa las interfaces, para modificar el metodo dependiendo de la clase o interface que se este utilizando. O siendo explicito en la implementacion del metodo ejemplo:
```java
//Sintaxis 
##InterfaceName.super.methodName().
// Llamar a la implementación de B 
B.super.metodo(); // Salida: Método de B 
// Llamar a la implementación de C 
C.super.metodo(); // Salida: Método de C
```
* ¿Que es referencia circular y como solucionarlo?
La referencia circular se ve cuando dos clases se referencian entre si creando un ciclo mediante atributos de tipo Clase, al momento de crear la instancia de alguna de las dos clases, de esta manera se produce el problema de la referencia circular.
```java
class Persona {
    private String nombre;
    private Direccion direccion;

    public Persona(String nombre, Direccion direccion) {
        this.nombre = nombre;
        this.direccion = direccion;
    }
}

class Direccion {
    private String calle;
    private Persona persona;

    public Direccion(String calle, Persona persona) {
        this.calle = calle;
        this.persona = persona;
    }
}

```
La solucion es eliminar al menos una de las dos referencias.

---
## Polimorfismo 
### <span style="color: blue;">Como lo entiendo:  </span> (~~Parcialmente correcto~~)
El #polimorfismo es la el cambio o la mutacion de los metodos de una clase a un Objeto instanciado por una clase diferente. 

---
# Resumen de Polimorfismo en Programación Orientada a Objetos

El **polimorfismo** es uno de los conceptos fundamentales de la programación orientada a objetos (POO) que permite que una misma operación se comporte de diferentes maneras según el objeto que la invoque. El término "polimorfismo" proviene del griego y significa "muchas formas". Este concepto es esencial para lograr flexibilidad y extensibilidad en el diseño de software.

## Tipos de Polimorfismo
#tiposDePolimorfismo
1. **Polimorfismo de Tiempo de Compilación (o Estático)**:
   - Se refiere a la capacidad de un lenguaje para resolver la llamada a un método en tiempo de compilación. 
   - Se logra principalmente a través de la **sobrecarga de métodos** (method overloading) y la **sobrecarga de operadores**.
   - Ejemplo de sobrecarga de métodos:

     ```java
     public class Calculadora {
         public int sumar(int a, int b) {
             return a + b;
         }

         public double sumar(double a, double b) {
             return a + b;
         }
     }

     public class Main {
         public static void main(String[] args) {
             Calculadora calc = new Calculadora();
             System.out.println(calc.sumar(5, 10)); // Salida: 15
             System.out.println(calc.sumar(5.5, 10.5)); // Salida: 16.0
         }
     }
     ```

2. **Polimorfismo de Tiempo de Ejecución (o Dinámico)**:
   - Se refiere a la capacidad de un lenguaje para resolver la llamada a un método en tiempo de ejecución.
   - Se logra a través de la **sobreescritura de métodos** (method overriding) y se basa en la herencia.
   - Ejemplo de sobreescritura de métodos:

     ```java
     // Clase padre
     public class Animal {
         public void hacerSonido() {
             System.out.println("El animal hace un sonido.");
         }
     }

     // Clase hija
     public class Perro extends Animal {
         @Override
         public void hacerSonido() {
             System.out.println("El perro ladra.");
         }
     }

     // Clase hija
     public class Gato extends Animal {
         @Override
         public void hacerSonido() {
             System.out.println("El gato maulla.");
         }
     }

     public class Main {
         public static void main(String[] args) {
             Animal miAnimal;

             miAnimal = new Perro();
             miAnimal.hacerSonido(); // Salida: El perro ladra.

             miAnimal = new Gato();
             miAnimal.hacerSonido(); // Salida: El gato maulla.
         }
     }
     ```


- **Polimorfismo Estático (Tiempo de Compilación)**: Se resuelve en tiempo de compilación y se logra a través de la sobrecarga de métodos y operadores.
    
- **Polimorfismo Dinámico (Tiempo de Ejecución)**: Se resuelve en tiempo de ejecución y se logra a través de la sobreescritura de métodos en el contexto de la herencia.
## Ventajas del Polimorfismo

1. **Flexibilidad**: Permite que las funciones y métodos trabajen con diferentes tipos de objetos, lo que facilita la extensión del código sin modificar las clases existentes.

2. **Mantenibilidad**: Al utilizar polimorfismo, el código se vuelve más fácil de mantener y entender, ya que se pueden utilizar interfaces y clases abstractas para definir comportamientos comunes.

3. **Reutilización de Código**: Facilita la reutilización de código, ya que se pueden utilizar métodos genéricos que operan sobre diferentes tipos de objetos.

## Conclusión
El polimorfismo es un concepto clave en la programación orientada a objetos que permite que una misma operación se ejecute de diferentes maneras según el contexto. Al aprovechar el polimorfismo, los desarrolladores pueden crear aplicaciones más flexibles, mantenibles y reutilizables, lo que mejora la calidad del software y reduce el tiempo de desarrollo.

---

## Encapsulamiento
### <span style="color: blue;">Como lo entiendo:  </span>
 El #encapsulamiento es la forma de proteger metodos, parametros y atributos, que no sean accesibles para todos los packcage dependiendo la situacion, donde encontramos public, private y protected 

---
# Resumen de Encapsulamiento en Programación Orientada a Objetos

El **encapsulamiento** es uno de los principios fundamentales de la programación orientada a objetos que se refiere a la práctica de restringir el acceso a ciertos componentes de un objeto y proteger su estado interno. Este concepto ayuda a mantener la integridad de los datos y a ocultar la complejidad del sistema.

## Características del Encapsulamiento

1. **Ocultamiento de Datos**: El encapsulamiento permite ocultar los detalles internos de un objeto, exponiendo solo lo necesario a través de una interfaz pública. Esto significa que los atributos de un objeto no son accesibles directamente desde fuera de la clase.

2. **Control de Acceso**: Se utilizan modificadores de acceso (como `private`, `protected` y `public`) para controlar qué partes del código pueden acceder a los atributos y métodos de una clase. Esto ayuda a prevenir modificaciones no deseadas y a mantener la integridad del objeto.

3. **Interfaz Pública**: A través de métodos públicos (también conocidos como **métodos de acceso** o **getters y setters**), se puede interactuar con los atributos de un objeto de manera controlada. Esto permite validar o modificar datos antes de que se almacenen.

## Ejemplo de Encapsulamiento en Java

Aquí tienes un ejemplo que ilustra el encapsulamiento en Java:

```java
public class CuentaBancaria {
    // Atributos privados
    private String titular;
    private double saldo;

    // Constructor
    public CuentaBancaria(String titular, double saldoInicial) {
        this.titular = titular;
        this.saldo = saldoInicial;
    }

    // Método público para obtener el saldo
    public double getSaldo() {
        return saldo;
    }

    // Método público para depositar dinero
    public void depositar(double cantidad) {
        if (cantidad > 0) {
            saldo += cantidad;
        }
    }

    // Método público para retirar dinero
    public boolean retirar(double cantidad) {
        if (cantidad > 0 && cantidad <= saldo) {
            saldo -= cantidad;
            return true;
        }
        return false;
    }
}

public class Main {
    public static void main(String[] args) {
        CuentaBancaria cuenta = new CuentaBancaria("Juan", 1000.0);
        cuenta.depositar(500.0);
        System.out.println("Saldo: " + cuenta.getSaldo()); // Salida: Saldo: 1500.0

        if (cuenta.retirar(200.0)) {
            System.out.println("Retiro exitoso.");
        } else {
            System.out.println("Fondos insuficientes.");
        }

        System.out.println("Saldo: " + cuenta.getSaldo()); // Salida: Saldo: 1300.0
    }
}
```
# Modificadores de Acceso en Programación Orientada a Objetos

Los **modificadores de acceso** son palabras clave que se utilizan para especificar el nivel de acceso que tienen los atributos y métodos de una clase. Estos modificadores son fundamentales para implementar el principio de **encapsulamiento**, ya que controlan cómo y desde dónde se puede acceder a los miembros de una clase.

## Tipos de Modificadores de Acceso

En Java, hay cuatro modificadores de acceso principales:

1. **public**:
   - Los miembros (atributos o métodos) declarados como `public` son accesibles desde cualquier otra clase en cualquier paquete.
   - Esto significa que no hay restricciones sobre su acceso.

   ```java
   public class EjemploPublico {
       public int atributoPublico;

       public void metodoPublico() {
           // Código
       }
   }````
2. **private**:

- Los miembros declarados como `private` son accesibles solo dentro de la misma clase en la que se definen.
    
- No pueden ser accedidos desde otras clases, ni siquiera desde clases que heredan de la clase padre.
````java
public class EjemploPrivado {
    private int atributoPrivado;

    private void metodoPrivado() {
        // Código
    }
}
````
3. **protected**:

- Los miembros declarados como `protected` son accesibles dentro de la misma clase, en clases del mismo paquete y en clases que heredan de la clase padre, incluso si están en paquetes diferentes.
    
- Esto permite un mayor nivel de acceso que `private`, pero menos que `public`.
```java
public class EjemploProtegido {
    protected int atributoProtegido;

    protected void metodoProtegido() {
        // Código
    }
}
```

---
### <span style="color: blue;">Segundo fragmento </span>

## Task 
* interfaz(cuantas clases pueden implementar una interfaz, como puedo definir una implementacion en especifico si estas tienen varias) 
* clases abstractas 
* cuando interfaz cuando clase abstracta

## Interfaces: 
### <span style="color: blue;">Como lo entiendo </span> 
Las #interfaces son parecidas a las #clases estas se diferencia en que normalmente contienen metodos uno o mas , es posible crear constantes y lo recomendado es no utilizar variables, por defecto cuando se crean estas siempre vienen implicitamente con public, static y final incluso si se omiten en la declaracion de variables.


---
# Resumen del Artículo "Java Interfaces"

## Introducción a las Interfaces en Java

Las interfaces en Java son un tipo de referencia que permite definir un contrato que las clases deben seguir. Una interfaz puede contener métodos abstractos (sin implementación) y métodos por defecto (con implementación). Las interfaces son fundamentales para la programación orientada a objetos, ya que permiten la creación de código más flexible y reutilizable.

## Características de las Interfaces

1. **Métodos Abstractos**:
   - Las interfaces pueden contener métodos abstractos, que son métodos sin cuerpo. Las clases que implementan la interfaz deben proporcionar una implementación para estos métodos.
   - Ejemplo:
     ```java
     interface Animal {
         void hacerSonido(); // Método abstracto
     }
     
     ### Implementación de la Interfaz en Clases
     
     class Perro implements Animal {
    @Override
    public void hacerSonido() {
        System.out.println("Guau"); // Implementación del método para Perro
    }
}

class Gato implements Animal {
    @Override
    public void hacerSonido() {
        System.out.println("Miau"); // Implementación del método para Gato
    }
}
	### Uso de las Clases

 public class Main {
    public static void main(String[] args) {
        Animal miPerro = new Perro(); // Crear un objeto de tipo Perro
        Animal miGato = new Gato(); // Crear un objeto de tipo Gato

        miPerro.hacerSonido(); // Salida: Guau
        miGato.hacerSonido(); // Salida: Miau
    }
}    
     ```

2. **Métodos por Defecto**:
   - Desde Java 8, las interfaces pueden incluir métodos por defecto, que tienen una implementación. Esto permite agregar nuevos métodos a las interfaces sin romper las clases existentes que ya las implementan.
   - Ejemplo:
     ```java
     interface Animal {
         void hacerSonido(); // Método abstracto

         default void dormir() {
             System.out.println("El animal está durmiendo.");
         }
     }
     
     ### Implementación de la Interfaz en Clases
     class Perro implements Animal {
    @Override
    public void hacerSonido() {
        System.out.println("Guau"); // Implementación del método para Perro
    }
}

class Gato implements Animal {
    @Override
    public void hacerSonido() {
        System.out.println("Miau"); // Implementación del método para Gato
    }
}
### Uso de las Clases

public class Main {
    public static void main(String[] args) {
        Animal miPerro = new Perro(); // Crear un objeto de tipo Perro
        Animal miGato = new Gato(); // Crear un objeto de tipo Gato

        miPerro.hacerSonido(); // Salida: Guau
        miGato.hacerSonido(); // Salida: Miau

        miPerro.dormir(); // Salida: El animal está durmiendo.
        miGato.dormir(); // Salida: El animal está durmiendo.
    }
}
     ```

3. **Métodos Estáticos**:
   - Las interfaces pueden contener métodos estáticos que se pueden llamar sin necesidad de instanciar la interfaz. Estos métodos son útiles para proporcionar utilidades relacionadas con la interfaz.
   - Ejemplo:
     ```java
     interface Utilidades {
         static void imprimirMensaje(String mensaje) {
             System.out.println(mensaje);
         }
     }
     
     #### Uso del Método Estático en la Interfaz
     public class Main {
    public static void main(String[] args) {
        // Llamar al método estático directamente desde la interfaz
        Utilidades.imprimirMensaje("Hola, este es un mensaje desde un método estático en una interfaz.");
    }
}
     ```

4. **Herencia de Interfaces**:
   - Las interfaces pueden extender otras interfaces, lo que permite crear jerarquías de interfaces. Una clase puede implementar múltiples interfaces, lo que permite la herencia múltiple de comportamientos.
   - Ejemplo:
     ```java
		// Interfaz base
interface Animal {
    void hacerSonido(); // Método abstracto
}

// Interfaz que hereda de Animal
interface Volador extends Animal {
    void volar(); // Método abstracto adicional
}
#### Implementación de la Herencia de Interfaces en una Clase
class Pajaro implements Volador {
    @Override
    public void hacerSonido() {
        System.out.println("El pájaro canta."); // Implementación del método de Animal
    }

    @Override
    public void volar() {
        System.out.println("El pájaro está volando."); // Implementación del método de Volador
    }
}
#### Uso de la Clase que Implementa la Herencia de Interfaces
public class Main {
    public static void main(String[] args) {
        Volador miPajaro = new Pajaro(); // Crear un objeto de tipo Pajaro
        miPajaro.hacerSonido(); // Salida: El pájaro canta.
        miPajaro.volar(); // Salida: El pájaro está volando.
    }
}

     ```

5. **No se Pueden Instanciar**:
   - Las interfaces no pueden ser instanciadas directamente. En su lugar, las clases que implementan la interfaz son las que se instancian.
   - Ejemplo:
     ```java
     // Animal animal = new Animal(); // Esto no es válido
     ```

## Ejemplo de Uso

El artículo proporciona ejemplos de cómo definir y utilizar interfaces en Java. Se muestra cómo una clase puede implementar múltiples interfaces y cómo se pueden utilizar métodos por defecto.

```java
interface Vehiculo {
    void conducir(); // Método abstracto

    default void encender() {
        System.out.println("El vehículo está encendido.");
    }
}

class Coche implements Vehiculo {
    @Override
    public void conducir() {
        System.out.println("Conduciendo un coche.");
    }
}

public class Main {
    public static void main(String[] args) {
        Coche miCoche = new Coche();
        miCoche.encender(); // Salida: El vehículo está encendido.
        miCoche.conducir(); // Salida: Conduciendo un coche.
    }
}
````


### Tasks: 
* ¿Cuantas clases pueden implementar una interfaz?
En Java, una interfaz puede ser implementada por múltiples clases. No hay un límite en la cantidad de clases que pueden implementar una misma interfaz. Esto permite que diferentes clases compartan un contrato común, lo que facilita la programación orientada a objetos y la reutilización de código.
* ¿Como puedo definir una implementacion en especifico si estas tienen varias?
Si la interfaz cuenta con mupltiples implementaciones la opcion para implementarla en especifico es utilizando la anotacion #ovrride @Override oara modificar el metodo implementado.

# Clases Abstractas en Java
#ClasesAbstractas
## Introducción

Una **clase abstracta** en Java es una clase que no se puede instanciar directamente y que puede contener métodos abstractos (sin implementación) y métodos concretos (con implementación). Las clases abstractas se utilizan como base para otras clases, permitiendo definir un comportamiento común que las subclases deben seguir.

## Características de las Clases Abstractas

1. **No se Pueden Instanciar**: No puedes crear objetos de una clase abstracta directamente. Debes crear una subclase que implemente los métodos abstractos.

2. **Métodos Abstractos**: Una clase abstracta puede contener métodos abstractos, que son métodos sin cuerpo. Las subclases deben proporcionar una implementación para estos métodos.

3. **Métodos Concretos**: Además de métodos abstractos, una clase abstracta puede tener métodos concretos que tienen una implementación. Las subclases pueden usar estos métodos tal como están o sobreescribirlos.

4. **Constructores**: Las clases abstractas pueden tener constructores, que se utilizan para inicializar atributos comunes en las subclases.

5. **Herencia**: Las clases abstractas pueden ser extendidas por otras clases, permitiendo la herencia de comportamiento y atributos.

## Ejemplo de Clase Abstracta

### Definición de la Clase Abstracta

```java
abstract class Animal {
    String nombre;

    // Constructor
    public Animal(String nombre) {
        this.nombre = nombre;
    }

    // Método abstracto
    public abstract void hacerSonido();

    // Método concreto
    public void dormir() {
        System.out.println(nombre + " está durmiendo.");
    }
}

### Implementación de la Clase Abstracta en Subclases
class Perro extends Animal {
    public Perro(String nombre) {
        super(nombre); // Llamar al constructor de la clase base
    }

    @Override
    public void hacerSonido() {
        System.out.println("Guau"); // Implementación del método abstracto
    }
}

class Gato extends Animal {
    public Gato(String nombre) {
        super(nombre); // Llamar al constructor de la clase base
    }

    @Override
    public void hacerSonido() {
        System.out.println("Miau"); // Implementación del método abstracto
    }
}
### Uso de las Clases Abstractas y Subclases
public class Main {
    public static void main(String[] args) {
        Animal miPerro = new Perro("Rex"); // Crear un objeto de tipo Perro
        Animal miGato = new Gato("Miau"); // Crear un objeto de tipo Gato

        miPerro.hacerSonido(); // Salida: Guau
        miGato.hacerSonido(); // Salida: Miau

        miPerro.dormir(); // Salida: Rex está durmiendo.
        miGato.dormir(); // Salida: Miau está durmiendo.
    }
}

```


---

# Cuando usar clases abstractas y cuando usar interfaz

# Clases Abstractas vs. Interfaces en Java

## Cuándo Utilizar una Clase Abstracta

1. **Comportamiento Común**:
   - Utiliza una clase abstracta cuando varias clases comparten un comportamiento común y deseas proporcionar una implementación base que las subclases pueden heredar.
   - **Ejemplo**: Si tienes una clase `Animal` que tiene un método `dormir()` que es común a todas las subclases, puedes definirlo en una clase abstracta.

2. **Métodos Abstractos y Concretos**:
   - Si necesitas definir métodos abstractos (sin implementación) y también proporcionar algunos métodos concretos (con implementación) que las subclases pueden usar o sobreescribir, una clase abstracta es adecuada.
   - **Ejemplo**: La clase `Animal` puede tener un método abstracto `hacerSonido()` y un método concreto `dormir()`.

3. **Estado Compartido**:
   - Si las clases que heredan de la clase abstracta necesitan compartir atributos (estado), es apropiado utilizar una clase abstracta. Las clases abstractas pueden tener campos (atributos) que se pueden inicializar en el constructor.
   - **Ejemplo**: La clase `Animal` puede tener un atributo `nombre` que todas las subclases deben tener.

4. **Relación "Es-Un"**:
   - Utiliza una clase abstracta cuando existe una relación "es-un" clara entre la clase abstracta y las subclases. Por ejemplo, un `Perro` es un `Animal`.

## Cuándo Utilizar una Interfaz

1. **Contratos de Comportamiento**:
   - Utiliza una interfaz cuando deseas definir un contrato que varias clases pueden implementar, sin importar su relación jerárquica. Las interfaces son ideales para definir comportamientos que pueden ser compartidos por clases no relacionadas.
   - **Ejemplo**: Una interfaz `Volador` puede ser implementada por `Pájaro`, `Avión`, y `Murciélago`, que no tienen una relación directa entre sí.

2. **Múltiples Implementaciones**:
   - Si una clase necesita implementar múltiples comportamientos, las interfaces son la mejor opción, ya que Java permite que una clase implemente múltiples interfaces.
   - **Ejemplo**: Una clase `Pájaro` puede implementar tanto la interfaz `Volador` como la interfaz `Animal`.

3. **Métodos por Defecto**:
   - Desde Java 8, las interfaces pueden tener métodos por defecto, lo que permite proporcionar implementaciones comunes sin romper las clases existentes. Si necesitas agregar funcionalidad a una interfaz sin afectar a las implementaciones existentes, utiliza métodos por defecto.
   - **Ejemplo**: Una interfaz `Animal` puede tener un método por defecto `dormir()`.

4. **Desacoplamiento**:
   - Utiliza interfaces para promover el desacoplamiento en tu diseño. Esto permite que las clases interactúen a través de interfaces, lo que facilita la prueba y el mantenimiento del código.
   - **Ejemplo**: Una clase `ControlRemoto` puede interactuar con cualquier clase que implemente la interfaz `Dispositivo`, sin necesidad de conocer la implementación específica.

## Resumen

- **Clases Abstractas**:
  - Se utilizan cuando hay un comportamiento común que se puede compartir.
  - Permiten métodos abstractos y concretos.
  - Pueden tener estado (atributos) y constructores.
  - Se utilizan para establecer una relación "es-un".

- **Interfaces**:
  - Se utilizan para definir contratos de comportamiento que pueden ser implementados por clases no relacionadas.
  - Permiten la implementación de múltiples interfaces.
  - Pueden tener métodos por defecto (desde Java 8).
  - Promueven el desacoplamiento y la flexibilidad en el diseño.

## Ejemplo Comparativo

**Clase Abstracta**:
```java
abstract class Animal {
    String nombre;

    public Animal(String nombre) {
        this.nombre = nombre;
    }

    public abstract void hacerSonido();
    
    public void dormir() {
        System.out.println(nombre + " está durmiendo.");
    }
}

```

---
### <span style="color: blue;">Tercer fragmento </span>

* Java casting (tipos casting) 
* Java Genericos (que son y que solucionan) estos nacen en Java 5.

# ¿Qué es Java Casting y qué tipos hay?

Java Casting se refiere al proceso de convertir un tipo de dato en otro. Es una práctica común en programación, especialmente en Java, donde se trabaja con diferentes tipos de datos y objetos.

## Tipos de Casting en Java

Existen dos tipos principales de casting en Java:

### 1. **Casting Implícito (Widening Casting)**

- **Descripción**: Ocurre automáticamente cuando se convierte un tipo de dato más pequeño a uno más grande. No se pierde información.
- **Ejemplo**: Convertir un `int` a `double`.
  
  ```java
  int numero = 10;
  double decimal = numero; // Casting implícito
  ````
  ```
### 2. **Casting Explícito (Narrowing Casting)**

- **Descripción**: Requiere una conversión explícita y puede implicar la pérdida de información. Se utiliza cuando se convierte un tipo de dato más grande a uno más pequeño.
    
- **Ejemplo**: Convertir un `double` a `int`.
    
    java
    
    `double decimal = 10.5; int numero = (int) decimal; // Casting explícito`
    

## Casting de Objetos

En Java, el casting también se aplica a objetos, especialmente en el contexto de la herencia:

- **Casting hacia abajo (Downcasting)**: Convertir un objeto de una clase padre a una clase hija. Puede causar `ClassCastException` si el objeto no es realmente una instancia de la clase hija.
    
    ``` java
    
    
    Animal animal = new Perro(); Perro perro = (Perro) animal; // Downcasting
  ```  
- **Casting hacia arriba (Upcasting)**: Convertir un objeto de una clase hija a una clase padre. Este tipo de casting es seguro y no requiere conversión explícita.
    
    ```java
    
    Perro perro = new Perro(); Animal animal = perro; // Upcasting
    ```

## Conclusión

Java Casting es esencial para trabajar con diferentes tipos de datos y objetos. Comprender los tipos de casting y cuándo utilizarlos es fundamental para evitar errores y garantizar un código eficiente y seguro.


---
## ***EXTRA***
***PARA VER EN CLASE (patrones de diseño)


---
## Checklist de Tareas

### Clases
- [x] Clases
- [x] Objetos
- [x] Herencia (cuántas clases pueden ser heredadas) (estudiar referencia circular y cómo evitarla)
- [x] Polimorfismo
- [x] Encapsulamiento

---

### Interfaz
- [x] Interfaz (cuántas clases pueden implementar una interfaz, cómo puedo definir una implementación en específico si estas tienen varias)
- [x] Clases abstractas
- [x] Cuándo usar interfaz y cuándo usar clase abstracta

---

### Java
- [x] Java casting (tipos de casting)
- [ ] Java genéricos (qué son y qué solucionan; estos nacen en Java 5)

---

### Para ver en clase
- [ ] Patrones de diseño
---
* Interfaces funcionales y tipos de interfaces funcionales 
