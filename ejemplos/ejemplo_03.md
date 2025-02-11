# Ejemplo 03: Refactorización de un Contador de Palabras en Java

### 1. Código Sin Refactorizar
```java
  public class ContadorDePalabras {
      public static void main(String[] args) {
          String texto = "Hola, este es un ejemplo de cómo contar palabras en un texto.";
  
          int contador = 0;
          boolean enPalabra = false;
  
          for (int i = 0; i < texto.length(); i++) {
              char c = texto.charAt(i);
              if (Character.isLetterOrDigit(c)) {
                  if (!enPalabra) {
                      enPalabra = true;
                      contador++;
                  }
              } else {
                  enPalabra = false;
              }
          }
  
          System.out.println("Cantidad de palabras: " + contador);
      }
  }
```
### 2. Código Refactorizado
```java
  public class ContadorDePalabras {
      public static void main(String[] args) {
          String texto = "Hola, este es un ejemplo de cómo contar palabras en un texto.";
          int cantidadPalabras = contarPalabras(texto);
          System.out.println("Cantidad de palabras: " + cantidadPalabras);
      }
  
      private static int contarPalabras(String texto) {
          String[] palabras = texto.split("\\W+");
          return palabras.length;
      }
  }
```
### 3. Explicación de los Cambios

- **Extracción de Método `contarPalabras`**: La lógica de contar palabras se extrajo a un método separado. Esto hace que el código sea más modular y reutilizable, y facilita su mantenimiento.

- **Uso del Método `split`**: En lugar de recorrer el texto carácter por carácter, se utiliza el método `split` con una expresión regular `\\W+` que divide el texto en palabras utilizando cualquier delimitador no alfanumérico. Esto hace que el código sea más conciso y fácil de entender.

- **Código Más Limpio y Legible**: Al separar la funcionalidad de contar palabras en un método y aprovechar las funciones integradas de Java, el código se vuelve mucho más claro y fácil de leer. Además, el código es ahora más flexible, ya que se puede cambiar fácilmente la forma de contar las palabras sin tener que modificar toda la lógica del programa.

- **Facilidad para Modificaciones Futuras**: Si se necesitara cambiar la forma en que se cuentan las palabras (por ejemplo, si se requiere contar palabras que estén entre comillas o que tengan ciertos caracteres especiales), el cambio se haría únicamente en el método `contarPalabras`, sin necesidad de tocar el flujo principal.

