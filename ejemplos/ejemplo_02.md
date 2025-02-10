# Ejemplo 02: Refactorización de un Ciclo en Java
###  1. Código Sin Refactorizar
```java
  public class RefactorizacionCiclo {
      public static void main(String[] args) {
          int[] numeros = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
  
          for (int i = 0; i < numeros.length; i++) {
              if (numeros[i] % 2 == 0) {
                  System.out.println("Número par: " + numeros[i]);
              } else {
                  System.out.println("Número impar: " + numeros[i]);
              }
          }
      }
  }
```
### 2. Código Refactorizado
```java

  public class RefactorizacionCiclo {
      public static void main(String[] args) {
          int[] numeros = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
  
          for (int numero : numeros) {
              imprimirTipoNumero(numero);
          }
      }
  
      private static void imprimirTipoNumero(int numero) {
          if (esPar(numero)) {
              System.out.println("Número par: " + numero);
          } else {
              System.out.println("Número impar: " + numero);
          }
      }
  
      private static boolean esPar(int numero) {
          return numero % 2 == 0;
      }
  }
```

### 3. Explicación de los Cambios

- **Uso de `for-each`**: Se reemplazó el ciclo `for` tradicional con un ciclo `for-each`, lo que hace que el código sea más legible y menos propenso a errores de índice.

- **Extracción de Métodos**:
    - La lógica para determinar si un número es par o impar se extrajo a un método separado (`esPar`), lo que mejora la claridad y facilita la reutilización.
    - La lógica para imprimir el tipo de número se extrajo a otro método (`imprimirTipoNumero`), lo que hace que el código sea más modular y fácil de mantener.

- **Código Más Limpio y Legible**: Al dividir la lógica en métodos más pequeños, el código se vuelve más fácil de entender y mantener. Además, el uso de nombres descriptivos para los métodos mejora la claridad.

- **Facilidad para Modificaciones Futuras**: Si en el futuro se necesita cambiar la lógica para determinar si un número es par o impar, solo se necesitará modificar el método `esPar`, sin afectar el resto del código.
