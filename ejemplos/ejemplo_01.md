# Ejemplo 01: Refactorización de Condicionales Anidados en Java

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
```

### 2. Código Refactorizado
```java
    public class RefactorizacionEjemplo {
        public static void main(String[] args) {
            int edad = 25;
            boolean tieneLicencia = true;
    
            if (edad < 18) {
                System.out.println("No puedes conducir, eres menor de edad");
                return;
            }
    
            if (!tieneLicencia) {
                System.out.println("No puedes conducir, necesitas una licencia");
                return;
            }
    
            System.out.println("Puedes conducir");
        }
    }
```
   
### 3. Explicación de los Cambios


- **Eliminación de Condicionales Anidados**: Se evitó el anidamiento de `if` para que el flujo sea más claro. Ahora, cada condición se maneja por separado y se sale del método de inmediato si no se cumple.

- **Mayor Claridad**: El código es más fácil de leer, ya que las condiciones son más simples y no dependen unas de otras.

- **Código Más Simple**: Al reducir el anidamiento, el código se vuelve más limpio y fácil de entender. Las modificaciones futuras serán más fáciles de implementar sin complicar la lógica.

 
