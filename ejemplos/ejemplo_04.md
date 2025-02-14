# Ejemplo 04: Refactorización de cuenta bancaria

### 1. Código Sin Refactorizar
```java
  public class Banco {
      public static void main(String[] args) {
          String nombre = "Juan Perez";
          double saldo = 1000.0;
          
          // Depósito
          saldo += 500.0;
          
          // Retiro
          if (saldo >= 300.0) {
              saldo -= 300.0;
          } else {
              System.out.println("Saldo insuficiente");
          }
          
          System.out.println("Saldo final de " + nombre + ": " + saldo);
      }
  }
```
### 2. Código Refactorizado
```java
  public class CuentaBancaria {
      private String propietario;
      private double saldo;
  
      public CuentaBancaria(String propietario, double saldoInicial) {
          this.propietario = propietario;
          this.saldo = saldoInicial;
      }
  
      public void depositar(double cantidad) {
          if (cantidad > 0) {
              saldo += cantidad;
          } else {
              System.out.println("La cantidad de depósito debe ser positiva");
          }
      }
  
      public void retirar(double cantidad) {
          if (cantidad > saldo) {
              System.out.println("Saldo insuficiente");
          } else if (cantidad > 0) {
              saldo -= cantidad;
          } else {
              System.out.println("La cantidad de retiro debe ser positiva");
          }
      }
  
      public double obtenerSaldo() {
          return saldo;
      }
  
      public String obtenerPropietario() {
          return propietario;
      } 
      public static void main(String[] args) {
          CuentaBancaria cuenta = new CuentaBancaria("Juan Perez", 1000.0);
          cuenta.depositar(500.0);
          cuenta.retirar(300.0);
          System.out.println("Saldo final de " + cuenta.obtenerPropietario() + ": " + cuenta.obtenerSaldo());
      }
  }
```
## Explicación de los Cambios

- **Clases y Objetos**: Se creó la clase `CuentaBancaria` para representar la cuenta con atributos como `propietario` y `saldo`, aplicando el principio de encapsulamiento en POO.

- **Métodos**: Se añadieron los métodos `depositar()`, `retirar()` y `obtenerSaldo()` para organizar y reutilizar las operaciones sobre la cuenta.

- **Encapsulamiento**: Los atributos `propietario` y `saldo` no se pueden modificar directamente, solo a través de los métodos definidos.

- **Modularidad**: La lógica está organizada, permitiendo manejar múltiples cuentas sin duplicar código.

- **Mantenimiento**: Se facilita agregar nuevas funcionalidades (como intereses o transacciones) sin afectar el flujo principal.


