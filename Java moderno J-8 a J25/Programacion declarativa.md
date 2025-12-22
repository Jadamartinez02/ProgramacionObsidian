
Ahora hablemos de esa programación declarativa.

Este estilo de programación se centra en el resultado que desea.

No le molesta ni le preocupa cómo obtener el resultado.

Este estilo de programación adopta la inmutabilidad de los objetos. Es análogo a SQL.

En SQL,

Solicitamos datos de las tablas pero no nos importa lo que sea

Algoritmo o cómo se recuperan los datos de la base de datos. ¿Verdad?

El estilo declarativo de programación es similar al mismo concepto. Utilizaremos el

funciones que vienen con el lenguaje.

No tienes que preocuparte por cómo se procesan los datos detrás de escena para obtener el resultado.

``` java
/**  
 * Declarative style. (Functional programming uses the same style) * what style of programming. * You let the system do the job for you and get the result. */int sum1= IntStream.rangeClosed(0,100)  
        //.parallel()  
        .map(Integer::new)  
        .sum();  
  
System.out.println("sum1 : " + sum1);
```

``` java
/**  
 * Declarative Syle */  
List<Integer> uniqueList1 = integerList.stream()  
        .distinct()  
        .collect(toList());  
// El metodo distinct toma el arreglo con valores unicos sin repetir          
System.out.println("uniqueList1 : " + uniqueList1);
```