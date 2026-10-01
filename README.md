# professional-js-sudoku

Aplicación web de Sudoku generada dinámicamente mediante algoritmos de Backtracking. Construida enteramente con HTML, CSS (Tailwind) y JavaScript (ES6+).

Este proyecto no utiliza tableros predefinidos o estáticos. Cada partida genera una solución matemática válida en tiempo real y remueve dinámicamente los valores basándose en el nivel de dificultad seleccionado por el usuario, asegurando un número casi infinito de variaciones de juego.

## Tabla de Contenidos

- [Demostración](#demostración)
- [Capturas de Pantalla](#capturas-de-pantalla)
- [Características Principales](#características-principales)
- [Tecnologías Utilizadas](#tecnologías-utilizadas)
- [Arquitectura y Algoritmos](#arquitectura-y-algoritmos)
- [Instalación y Uso Local](#instalación-y-uso-local)
- [Contribución](#contribución)
- [Licencia](#licencia)

## Demostración

El proyecto se encuentra desplegado para su uso inmediato a través de GitHub Pages:

[Enlace al Sudoku en vivo] (Reemplazar con enlace real)

## Capturas de Pantalla

[Para documentar la interfaz, se sugiere agregar capturas de la aplicación en funcionamiento en la carpeta correspondiente y actualizar las rutas a continuación]

**Interfaz Principal y Tablero Inicial:**
![Tablero de Sudoku - Vista Principal](https://i.ibb.co/ycz1d3H3/image.png)

## Características Principales

*   **Generación Procedural:** Algoritmo determinista que asegura que cada juego sea único, construyendo un tablero válido desde cero en menos de un segundo.
*   **Selector de Dificultad:** Escala variable que ajusta la cantidad de celdas removidas del tablero solucionado (Fácil, Medio, Difícil, Experto).
*   **Validación en Tiempo Real:** Motor de verificación que compara el estado actual del DOM del usuario contra la matriz de solución generada en memoria, resaltando las entradas incorrectas.
*   **Diseño Responsivo:** Interfaz gráfica optimizada con CSS Grid que mantiene el formato simétrico de 9x9 con separadores de sección de 3x3 en cualquier tamaño de pantalla.
*   **Validación de Inputs UX:** Restricción de caracteres a nivel de DOM y lógica JS para impedir el ingreso de caracteres no numéricos o cadenas de múltiples dígitos.

## Tecnologías Utilizadas

*   **HTML5:** Para el marcado de la estructura base.
*   **Tailwind CSS (CDN):** Framework de utilidades para estilar la interfaz, manejar tipografías, estados de validación (colores de error/éxito) y el diseño adaptable.
*   **JavaScript (ES6):** Toda la lógica de negocio, manipulación del DOM y evaluación algorítmica.

## Arquitectura y Algoritmos

El núcleo de la aplicación reside en la clase `SudokuGame`, la cual separa la lógica de estado de la presentación (DOM):

1.  **Backtracking Algorithm (Vuelta atrás):**
    Para la generación del tablero, se emplea una función recursiva de búsqueda en profundidad (DFS). El algoritmo intenta colocar un dígito del 1 al 9 en la primera celda vacía. Si el número respeta las reglas del Sudoku (no se repite en fila, columna, ni subcuadrícula de 3x3), el algoritmo avanza. Si alcanza un callejón sin salida (ningún número es válido), retrocede (backtracks) a la celda anterior y prueba con el siguiente número disponible.

2.  **Aleatorización de Generación:**
    Para evitar que el Backtracking genere siempre el mismo tablero, el arreglo de números probados `[1,2,3,4,5,6,7,8,9]` es mezclado aleatoriamente (mediante una función `shuffle`) antes de ser evaluado en cada recursión.

3.  **Gestión de Memoria y Estado:**
    Se mantienen matrices bidimensionales separadas:
    *   `this.board`: Representa el estado actual del tablero en juego.
    *   `this.solution`: Almacena la matriz resuelta y se usa de forma inmutable como fuente de la verdad durante las verificaciones.

## Instalación y Uso Local

Al ser un proyecto Vanilla JS, no se requieren manejadores de paquetes ni dependencias de construcción.

1. Clona el repositorio:
   ```bash
   git clone [https://github.com/TU_USUARIO/professional-js-sudoku.git](https://github.com/TU_USUARIO/professional-js-sudoku.git)
