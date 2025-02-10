# Refactorización de Condicionales Anidados en Java

## Ejemplo 01: Refactorización de Condicionales Anidados

### 1. Código Sin Refactorizar

```java
public class RefactorizacionEjemplo {
    public static void main(String[] args) {
        int edad = 25;
        boolean tieneLicencia = true;

        if (edad >= 18) {
            if (tieneLicencia) {
                System.out.println("Puedes conducir");
            } else {
                System.out.println("No puedes conducir, necesitas una licencia");
            }
        } else {
            System.out.println("No puedes conducir, eres menor de edad");
        }
    }
}
