
## 📚 HERENCIA EN JAVA

### ¿Qué es?

La herencia permite que una clase (hija) **herede** atributos y métodos de otra clase (padre), promoviendo la reutilización de código.

### Sintaxis básica

java

```java
// Clase padre (superclase)
class Animal {
    String nombre;
    
    void comer() {
        System.out.println("El animal está comiendo");
    }
}

// Clase hija (subclase) - usa 'extends'
class Perro extends Animal {
    void ladrar() {
        System.out.println("Guau guau!");
    }
}

// Uso
Perro miPerro = new Perro();
miPerro.nombre = "Rex";  // Heredado de Animal
miPerro.comer();         // Heredado de Animal
miPerro.ladrar();        // Propio de Perro
```

### Conceptos clave

**1. `super` - Acceder a la clase padre**

java

```java
class Vehiculo {
    String marca;
    
    Vehiculo(String marca) {
        this.marca = marca;
    }
}

class Carro extends Vehiculo {
    int puertas;
    
    Carro(String marca, int puertas) {
        super(marca);  // Llama al constructor del padre
        this.puertas = puertas;
    }
}
```

**2. `@Override` - Sobrescribir métodos**

java

```java
class Animal {
    void hacerSonido() {
        System.out.println("Sonido genérico");
    }
}

class Gato extends Animal {
    @Override
    void hacerSonido() {
        System.out.println("Miau!");
    }
}
```

**3. Polimorfismo - Un objeto puede tomar muchas formas**

java

```java
Animal a1 = new Perro();  // Polimorfismo
Animal a2 = new Gato();

a1.hacerSonido();  // "Guau guau!"
a2.hacerSonido();  // "Miau!"
```

### Modificadores de acceso (importante para herencia)

- `public` → Accesible desde cualquier lugar
- `protected` → Accesible en la misma clase, subclases y mismo paquete
- `private` → Solo accesible en la misma clase (NO heredable directamente)
- `default` (sin modificador) → Solo en el mismo paquete
## 📝 EJERCICIO 1: Sistema de Empleados (BÁSICO)

### Clase `Empleado` (Clase Padre)

**Atributos:**

- `String nombre`
- `String id`
- `double salarioBase`

**Constructor:**

- `Empleado(String nombre, String id, double salarioBase)`

**Métodos:**

- `double calcularPago()` → Retorna `salarioBase`
- `void mostrarInfo()` → Imprime: "Empleado: [nombre], ID: [id], Pago: $[pago]"
- Getters y setters para todos los atributos

---

### Clase `EmpleadoTiempoCompleto` (Hereda de Empleado)

**Atributos adicionales:**

- `double bonoAnual`

**Constructor:**

- `EmpleadoTiempoCompleto(String nombre, String id, double salarioBase, double bonoAnual)`
    - Debe llamar al constructor del padre con `super()`

**Métodos a sobrescribir:**

- `@Override double calcularPago()` → Retorna `salarioBase + (bonoAnual / 12)`
    - El bono se divide entre 12 meses

---

### Clase `EmpleadoMedioTiempo` (Hereda de Empleado)

**Atributos adicionales:**

- `int horasTrabajadas`
- `double pagoPorHora`

**Constructor:**

- `EmpleadoMedioTiempo(String nombre, String id, int horasTrabajadas, double pagoPorHora)`
    - NO debe recibir `salarioBase` porque se calcula automáticamente
    - Llama al padre con `super(nombre, id, 0)` (salarioBase = 0)

**Métodos a sobrescribir:**

- `@Override double calcularPago()` → Retorna `horasTrabajadas * pagoPorHora`

---

### Clase `Main` para probar

java

````java
public class Main {
    public static void main(String[] args) {
        // Crear empleados
        Empleado emp1 = new EmpleadoTiempoCompleto("Ana López", "E001", 3000, 12000);
        Empleado emp2 = new EmpleadoMedioTiempo("Carlos Ruiz", "E002", 80, 15);
        
        // Mostrar información (polimorfismo)
        emp1.mostrarInfo();
        emp2.mostrarInfo();
        
        // Calcular pagos
        System.out.println("Pago Ana: $" + emp1.calcularPago());
        System.out.println("Pago Carlos: $" + emp2.calcularPago());
    }
}
```

**Resultado esperado:**
```
Empleado: Ana López, ID: E001, Pago: $4000.0
Empleado: Carlos Ruiz, ID: E002, Pago: $1200.0
Pago Ana: $4000.0
Pago Carlos: $1200.0
````

---

## 📐 EJERCICIO 2: Figuras Geométricas (INTERMEDIO)

### Clase abstracta `Figura` (Clase Padre)

**Atributos:**

- `String color`
- `String nombre`

**Constructor:**

- `Figura(String color, String nombre)`

**Métodos abstractos** (sin implementación):

- `abstract double calcularArea()`
- `abstract double calcularPerimetro()`

**Métodos concretos:**

- `void mostrarInfo()` → Imprime: "[nombre] de color [color] - Área: [area], Perímetro: [perimetro]"
    - Este método usa `calcularArea()` y `calcularPerimetro()` que implementarán las clases hijas
- `String getColor()` y `setColor(String color)`

---

### Clase `Circulo` (Hereda de Figura)

**Atributos adicionales:**

- `double radio`

**Constructor:**

- `Circulo(String color, double radio)`
    - Llama a `super(color, "Círculo")`

**Métodos a implementar:**

- `@Override double calcularArea()` → `Math.PI * radio * radio`
- `@Override double calcularPerimetro()` → `2 * Math.PI * radio`

---

### Clase `Rectangulo` (Hereda de Figura)

**Atributos adicionales:**

- `double base`
- `double altura`

**Constructor:**

- `Rectangulo(String color, double base, double altura)`
    - Llama a `super(color, "Rectángulo")`

**Métodos a implementar:**

- `@Override double calcularArea()` → `base * altura`
- `@Override double calcularPerimetro()` → `2 * (base + altura)`

---

### Clase `Triangulo` (Hereda de Figura)

**Atributos adicionales:**

- `double base`
- `double altura`
- `double lado1, lado2, lado3` (para calcular perímetro)

**Constructor:**

- `Triangulo(String color, double base, double altura, double lado1, double lado2, double lado3)`
    - Llama a `super(color, "Triángulo")`

**Métodos a implementar:**

- `@Override double calcularArea()` → `(base * altura) / 2`
- `@Override double calcularPerimetro()` → `lado1 + lado2 + lado3`

---

### Clase `Main` para probar

java

````java
public class Main {
    public static void main(String[] args) {
        // Polimorfismo: todas son tipo Figura
        Figura[] figuras = {
            new Circulo("Rojo", 5),
            new Rectangulo("Azul", 4, 6),
            new Triangulo("Verde", 4, 3, 3, 4, 5)
        };
        
        // Recorrer y mostrar información
        for (Figura figura : figuras) {
            figura.mostrarInfo();
            System.out.println("---");
        }
    }
}
```

**Resultado esperado:**
```
Círculo de color Rojo - Área: 78.54, Perímetro: 31.42
---
Rectángulo de color Azul - Área: 24.0, Perímetro: 20.0
---
Triángulo de color Verde - Área: 6.0, Perímetro: 12.0
---
````

---

## 💳 EJERCICIO 3: Sistema de Pagos (AVANZADO)

### Interface `Pagable`

**Métodos:**

- `boolean procesarPago(double monto)` → Retorna `true` si el pago fue exitoso
- `String obtenerTipoPago()` → Retorna el nombre del método de pago
- `double obtenerSaldoDisponible()` → Retorna el saldo/crédito disponible

---

### Clase `TarjetaCredito` (Implementa Pagable)

**Atributos:**

- `String numeroTarjeta`
- `String titular`
- `double limiteCredito`
- `double creditoUsado`

**Constructor:**

- `TarjetaCredito(String numeroTarjeta, String titular, double limiteCredito)`
    - `creditoUsado` inicia en 0

**Métodos a implementar:**

- `@Override boolean procesarPago(double monto)`
    - Si `(creditoUsado + monto) <= limiteCredito`:
        - Suma `monto` a `creditoUsado`
        - Imprime: "Pago de $[monto] aprobado con Tarjeta de Crédito"
        - Retorna `true`
    - Si no:
        - Imprime: "Pago rechazado: Límite de crédito insuficiente"
        - Retorna `false`
- `@Override String obtenerTipoPago()` → `"Tarjeta de Crédito"`
- `@Override double obtenerSaldoDisponible()` → `limiteCredito - creditoUsado`

---

### Clase `PayPal` (Implementa Pagable)

**Atributos:**

- `String email`
- `double saldo`

**Constructor:**

- `PayPal(String email, double saldoInicial)`

**Métodos a implementar:**

- `@Override boolean procesarPago(double monto)`
    - Si `saldo >= monto`:
        - Resta `monto` de `saldo`
        - Imprime: "Pago de $[monto] procesado con PayPal"
        - Retorna `true`
    - Si no:
        - Imprime: "Pago rechazado: Saldo insuficiente en PayPal"
        - Retorna `false`
- `@Override String obtenerTipoPago()` → `"PayPal"`
- `@Override double obtenerSaldoDisponible()` → `saldo`
- Método adicional: `void recargarSaldo(double monto)` → Suma `monto` al `saldo`

---

### Clase `Efectivo` (Implementa Pagable)

**Atributos:**

- `double montoDisponible`

**Constructor:**

- `Efectivo(double montoDisponible)`

**Métodos a implementar:**

- `@Override boolean procesarPago(double monto)`
    - Si `montoDisponible >= monto`:
        - Resta `monto` de `montoDisponible`
        - Imprime: "Pago de $[monto] realizado en Efectivo"
        - Retorna `true`
    - Si no:
        - Imprime: "Efectivo insuficiente"
        - Retorna `false`
- `@Override String obtenerTipoPago()` → `"Efectivo"`
- `@Override double obtenerSaldoDisponible()` → `montoDisponible`

---

### Clase `ProcesadorPagos`

**Método estático:**

java

```java
public static void procesarListaPagos(List<Pagable> metodosPago, double montoPorPago) {
    System.out.println("=== Procesando pagos de $" + montoPorPago + " ===\n");
    
    for (Pagable metodo : metodosPago) {
        System.out.println("Método: " + metodo.obtenerTipoPago());
        System.out.println("Saldo disponible: $" + metodo.obtenerSaldoDisponible());
        
        boolean exitoso = metodo.procesarPago(montoPorPago);
        
        if (exitoso) {
            System.out.println("Saldo restante: $" + metodo.obtenerSaldoDisponible());
        }
        System.out.println("---\n");
    }
}
```

---

### Clase `Main` para probar

java

````java
import java.util.ArrayList;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        // Crear métodos de pago
        List<Pagable> metodosPago = new ArrayList<>();
        
        metodosPago.add(new TarjetaCredito("1234-5678-9012-3456", "Juan Pérez", 5000));
        metodosPago.add(new PayPal("juan@email.com", 300));
        metodosPago.add(new Efectivo(150));
        
        // Procesar pagos de $200 en cada método
        ProcesadorPagos.procesarListaPagos(metodosPago, 200);
        
        // Intentar otro pago de $500 (algunos fallarán)
        System.out.println("\n========== SEGUNDO INTENTO ==========\n");
        ProcesadorPagos.procesarListaPagos(metodosPago, 500);
    }
}
```

**Resultado esperado (parcial):**
```
=== Procesando pagos de $200.0 ===

Método: Tarjeta de Crédito
Saldo disponible: $5000.0
Pago de $200.0 aprobado con Tarjeta de Crédito
Saldo restante: $4800.0
---

Método: PayPal
Saldo disponible: $300.0
Pago de $200.0 procesado con PayPal
Saldo restante: $100.0
---

Método: Efectivo
Saldo disponible: $150.0
Efectivo insuficiente
---
````

---

## ✅ CHECKLIST DE LO QUE DEBES INCLUIR

Para cada ejercicio asegúrate de:

- ✅ Usar `extends` o `implements` según corresponda
- ✅ Llamar a `super()` en constructores de clases hijas
- ✅ Usar `@Override` cuando sobrescribas métodos
- ✅ Usar modificadores de acceso apropiados (`private`, `public`, `protected`)
- ✅ Probar con el `Main` que te proporcioné