La interfaz funcional Consumer, consume un atributo y no tiene retorno, es tipo void

Usada comun mente para recorrer arreglos u objetos 

```java

        Consumer<String> c1 = (s) -> System.out.println(s.toUpperCase());

        c1.accept("java8");
```