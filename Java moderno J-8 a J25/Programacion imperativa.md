Se dice que este estilo de programación se centra en cómo obtener el resultado que queremos este estilo de programación implica cambiar el estado del objeto para lograr un objetivo que no es nada pero mutar un objeto y obtener el resultado deseado. Digamos que quieres lograr un objetivo, define la lista de pasos para lograr un objetivo usted codifica lo que debe hacerse en cada paso. La programación imperativa es un concepto utilizado detrás del estilo clásico de programación orientada a objetos.


``` java

// sum of integers for the range from 0 to 100  
/**  
 * Imperative Style - how style of programming */int sum=0;  
for(int i=0;i<=100;i++){  
        sum+=i; // shared mutable state and its sequential anf it will go step by step  
            // and it will have issues if we try to run the code in multithreaded environment}  
System.out.println("Sum is : "+sum);
```

``` java
  
List<Integer> integerList =Arrays.asList(1,2,3,4,4,5,5,6,7,7,8,9,9);  
  
//Remove the duplicates from the list.  
  
/**  
 * Imperative Style */
List<Integer> uniqueList = new ArrayList<>();  
for(Integer i :integerList)  
    if(!uniqueList.contains(i)){  //El metodo constains verifica que ese valor pertenezca a la lista
    uniqueList.add(i);  
    }  
System.out.println("unique List : " + uniqueList);
```

