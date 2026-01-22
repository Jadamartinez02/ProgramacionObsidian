# BiConsumer

Lo que hace el Bi consumer es funciona igual que el consumer, con la diferencia que admite dos tipos de datos en los diamantes 
```java
BiConsumer<a,b>


        BiConsumer<String, String> biConsumer = (a,b) -> {
            System.out.println(" a : "  +  a + " b : " + b );
        };
        biConsumer.accept("java7" , "java8");

```

