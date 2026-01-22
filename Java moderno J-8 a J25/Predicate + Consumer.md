# Predicate + Consumer
Podemos utilizar instancias del Predicate en un consumer o bisconsumer para determinar el filtro o las condicionales como vemos a continuacion: 
```java

    static Predicate<Student> p1 = (s) -> s.getGradeLevel()>=3;

    static Predicate<Student> p2 = (s) -> s.getGpa()>=3.9;

    BiConsumer<String, List<String>> studentBiConsumer = (name, activities) -> System.out.println(name + " : " + activities);

    Consumer<Student> studentConsumer = (student) -> {

        if(p1.and(p2).test(student)){
            studentBiConsumer.accept(student.getName(),student.getActivities());
        }
    };

```