# BiPredicate

El BiPredicate básicamente va a aceptar dos parámetros y realizar algún tipo de operación, sobre la entrada, cualquiera que sea la que se esté pasando mediante la instancia de predicado.

Y devolverá un valor booleano como resultado.

```Java

    BiPredicate<Integer, Double> biPredicate = (gradeLevel, gpa) -> gradeLevel>=3 && gpa>=3.9;
    
    Consumer<Student> studConsumer = (student) -> {
        if (biPredicate.test(student.getGradeLevel(),student.getGpa())) {
            studentBiConsumer.accept(student.getName(), student.getActivities());
        }
    }; //Aplicando BiPredicate 
```