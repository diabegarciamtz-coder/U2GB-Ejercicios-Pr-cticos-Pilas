# U2GB-Ejercicios-Practicos-Pilas

### Lista Invertida
```
package ejPracticosPilas;

/**
 * Este programa invierte el orden de una lista de números utilizando una pila.
 * Apila cada elemento y luego los desapila para mostrarlos en orden inverso.
 *
 * @author Diana Mabel Garcia Martinez
 *         1224100672
 *         diabegarciamtz@gmail.com
 *         01/11/25
 */

// Implementación personalizada de una pila usando lista enlazada
class Pila<T> {
    private Nodo<T> tope;
    private int tamaño;
    
    private static class Nodo<T> {
        T dato;
        Nodo<T> siguiente;
        
        Nodo(T dato) {
            this.dato = dato;
            this.siguiente = null;
        }
    }
    
    public Pila() {
        this.tope = null;
        this.tamaño = 0;
    }
    
    public void push(T elemento) {
        Nodo<T> nuevoNodo = new Nodo<>(elemento);
        nuevoNodo.siguiente = tope;
        tope = nuevoNodo;
        tamaño++;
    }
    
    public T pop() {
        if (isEmpty()) {
            return null;
        }
        T dato = tope.dato;
        tope = tope.siguiente;
        tamaño--;
        return dato;
    }
    
    public T peek() {
        return isEmpty() ? null : tope.dato;
    }
    
    public int size() {
        return tamaño;
    }
    
    public boolean isEmpty() {
        return tope == null;
    }
}

public class InversorLista {
    public static void main(String[] args) {
        // Se define una lista de enteros
        int[] lista = {1, 2, 3, 4};

        // Se crea una pila para almacenar los elementos de la lista
        Pila<Integer> pila = new Pila<>();

        // Mensaje de encabezado del programa
        System.out.println("=== INVERSOR DE LISTA ===");

        //  Mostrar la lista original
        System.out.print("Lista original: ");
        for (int n : lista) {
            System.out.print(n + " "); // Imprime cada número en orden
        }
        System.out.println(); // Salto de línea

        //  Apilar los elementos de la lista
        for (int n : lista) {
            pila.push(n); // Inserta cada número en la pila
        }

        //  Mostrar la lista invertida
        System.out.print("Lista invertida: ");
        while (!pila.isEmpty()) {
            System.out.print(pila.pop() + " "); // Extrae y muestra el último número insertado
        }
    }
}
```

### Palabras Invertidas
```
package ejPracticosPilas;

/**
 * Este programa invierte una palabra utilizando una pila (estructura LIFO).
 * Cada letra se apila y luego se desapila para mostrar la palabra en orden inverso.
 *
 * @author Diana Mabel Garcia Martinez
 *         1224100672
 *         diabegarciamtz@gmail.com
 *         01/11/25
 */

import java.util.Scanner;

public class PalabraInversa {
    public static void main(String[] args) {
        // Se crea un objeto Scanner para leer entrada del usuario
        Scanner sc = new Scanner(System.in);

        // Se crea una pila de caracteres para almacenar las letras de la palabra
        Pila<Character> pila = new Pila<>();

        // Mensaje de bienvenida al usuario
        System.out.println("=== INVERSOR DE PALABRAS ===");

        // Solicita al usuario que ingrese una palabra
        System.out.print("Ingrese una palabra: ");
        String palabra = sc.nextLine();

        //  Apilar cada letra de la palabra
        // Se convierte la palabra en un arreglo de caracteres y se apilan uno por uno
        for (char c : palabra.toCharArray()) {
            pila.push(c); // Inserta el carácter en la pila
        }

        //  Mostrar la palabra invertida
        // Se desapilan los caracteres uno por uno y se imprimen
        System.out.print("Palabra invertida: ");
        while (!pila.isEmpty()) {
            System.out.print(pila.pop()); // Extrae el último carácter insertado
        }

        // Se cierra el Scanner para liberar recursos
        sc.close();
    }
}
```

### Palindromos
```
package ejPracticosPilas;

/**
 * Este programa verifica si una palabra ingresada por el usuario es un palíndromo.
 * Utiliza una pila para invertir la palabra y luego compara ambas versiones.
 *
 * Un palíndromo es una palabra que se lee igual de izquierda a derecha que de derecha a izquierda.
 *
 * Ejemplos: "oso", "reconocer", "anita lava la tina"
 *
 * @author Diana Mabel Garcia Martinez
 *         1224100672
 *         diabegarciamtz@gmail.com
 *         01/11/25
 */

import java.util.Stack;
import java.util.Scanner;

public class Palindromo {
    public static void main(String[] args) {
        // Se crea un objeto Scanner para leer la entrada del usuario
        Scanner sc = new Scanner(System.in);

        // Se crea una pila de caracteres para almacenar las letras de la palabra
        Stack<Character> pila = new Stack<>();

        // Mensaje de bienvenida
        System.out.println("=== DETECTOR DE PALÍNDROMOS ===");

        // Solicita al usuario que ingrese una palabra
        System.out.print("Ingrese palabra: ");
        String palabra = sc.nextLine();

        //  Apilar cada carácter de la palabra
        // Se convierte la palabra en un arreglo de caracteres y se apilan uno por uno
        for (char c : palabra.toCharArray()) {
            pila.push(c); // Inserta el carácter en la pila
        }

        //  Construir la palabra invertida desapilando los caracteres
        String invertida = "";
        while (!pila.isEmpty()) {
            invertida += pila.pop(); // Extrae el último carácter insertado
        }

        //  Mostrar la palabra original y la invertida
        System.out.println("Palabra original: " + palabra);
        System.out.println("Palabra invertida: " + invertida);

        // Verificar si es palíndromo (ignorando mayúsculas/minúsculas)
        if (palabra.equalsIgnoreCase(invertida)) {
            System.out.println("Resultado: ES PALÍNDROMO");
        } else {
            System.out.println("Resultado: NO ES PALÍNDROMO");
        }

        // Cerrar el Scanner para liberar recursos
        sc.close();
    }
}
```

### Pila basica
```
package ejPracticosPilas;

/**
 * Simulador básico de operaciones con una pila utilizando la clase Stack de Java.
 *
 * @author Diana Mabel Garcia Martinez
 *         1224100672
 *         diabegarciamtz@gmail.com
 *         01/11/25
 */

import java.util.Stack;

public class SimuladorPilaBasica {
    public static void main(String[] args) {
        // Se crea una pila de enteros utilizando la clase Stack
        Stack<Integer> pila = new Stack<>();

        // Mensaje de bienvenida al simulador
        System.out.println("=== SIMULADOR DE PILA BÁSICA ===");

        //  Inserción de elementos en la pila (operación push)
        pila.push(5);   // Se inserta el número 5
        pila.push(10);  // Se inserta el número 10
        pila.push(15);  // Se inserta el número 15
        pila.push(20);  // Se inserta el número 20

        // Se muestra el contenido actual de la pila después de las inserciones
        System.out.println("Pila después de inserts: " + pila);

        //  Eliminación de elementos de la pila (operación pop)
        pila.pop(); // Se elimina el último elemento insertado (20)
        pila.pop(); // Se elimina el siguiente elemento (15)

        // Se muestra el contenido final de la pila después de las eliminaciones
        System.out.println("Contenido actual: " + pila);
    }
}
```

### Verificador de pila
```
package ejPracticosPilas;

/**
 * Este programa simula la verificación del estado de una pila utilizando la clase Stack de Java.
 * Permite comprobar si la pila está vacía antes y después de insertar un elemento.
 *
 * @author Diana Mabel Garcia Martinez
 *         1224100672
 *         diabegarciamtz@gmail.com
 *         01/11/25
 */

import java.util.Stack;

public class VerificadorPilaVacia {
    public static void main(String[] args) {
        // Se crea una pila de enteros utilizando la clase Stack
        Stack<Integer> pila = new Stack<>();

        // Mensaje de encabezado del simulador
        System.out.println("=== VERIFICADOR DE PILA VACÍA ===");

        //  Verificación inicial: la pila está recién creada, debe estar vacía
        System.out.println("Pila recién creada - ¿Está vacía? " + pila.isEmpty());

        // Se agrega un elemento a la pila
        pila.push(1);
        System.out.println("Elemento agregado: 1");

        //  Verificación después de agregar un elemento
        System.out.println("Después de agregar elemento - ¿Está vacía? " + pila.isEmpty());

        //  Se muestra el contenido actual de la pila
        System.out.println("Elementos en pila: " + pila);
    }
}
```

