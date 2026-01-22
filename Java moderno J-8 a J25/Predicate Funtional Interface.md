# Predicate

El Predicate es una Interfaz funcional que devuelve un Booleano 

Tiene tres metodos, que son and, para concatenar mas instancias de la intefaz, or para admitir una condicional tipo ||, negate tipo !, isEqueal tipo comparacion ==, and tipo && y test que recibe los parametros a evaluar.

```java
    static Predicate<Integer> p = (i) -> {return  i%2 ==0;};

    static Predicate<Integer> p1 = (i) -> i%2 ==0;
    static Predicate<Integer> p2 = (i) -> i%5 ==0;


    public static void predicateAnd(){

        System.out.println("Result in predicateAnd : " + p1.and(p2).test(10));
    }
    

    public static void predicateNegate(){

        System.out.println("Result in predicateNegate : " + p1.and(p2).negate().test(4)); //equivalent to reversing the result
    }

```

