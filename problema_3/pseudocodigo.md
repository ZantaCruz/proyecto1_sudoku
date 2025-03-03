# Problema 3: Sudoku 🔢
```
Diseñe e implemente un juego de Sudoku en Python, donde el usuario debe completar un tablero de nivel fácil escogido aleatoriamente.
```

# Descripción
```
El programa selecciona un tablero de Sudoku entre cinco opciones disponibles. El usuario ingresa valores en coordenadas seleccionadas. Al final, se verifica si el tablero fue completado correctamente.
```

# Pseudocódigo Inical
```
Inicio
    Cargar cinco tableros de Sudoku de nivel fácil
    Seleccionar uno de forma aleatoria
    
    Repetir hasta que el tablero esté completo:
        Mostrar el tablero
        Pedir al usuario una coordenada y un número
        Verificar si la casilla está ocupada
        Si está vacía, colocar el número
        
        Si el tablero está lleno, verificar si es correcto
    
    Si el tablero es correcto
        Escribir "¡Felicidades, completaste el Sudoku!"
    Sino
        Escribir "Hay errores en el tablero. Sigue intentando."
Fin
```


# Pseudocódigo Final
```
INICIO

    PROCEDIMIENTO limpiar_pantalla()
        SI el sistema operativo es Windows
            EJECUTAR el comando "cls" para limpiar la pantalla
        SI NO
            EJECUTAR el comando "clear" para limpiar la pantalla en otros sistemas
    FIN PROCEDIMIENTO

    PROCEDIMIENTO mostrar_titulo()
        IMPRIMIR "=== ESTAMOS JUGANDO SUDOKU ==="
    FIN PROCEDIMIENTO

    PROCEDIMIENTO mostrar_reglas_sudoku()
        IMPRIMIR "\n=== REGLAS DEL SUDOKU ==="
        IMPRIMIR "1. Se genera un tablero de Sudoku 9x9 con algunos espacios vacíos."
        IMPRIMIR "2. Debes rellenar los espacios vacíos con números del 1 al 9."
        IMPRIMIR "3. No puedes repetir números en la misma fila ni en la misma columna."
        IMPRIMIR "4. Ganas cuando completas el tablero correctamente."
        IMPRIMIR "==========================\n"
    FIN PROCEDIMIENTO

    FUNCIÓN generar_tablero_sudoku() -> TABLERO
        CREAR un tablero de 9x9 lleno de espacios vacíos
        PARA cada fila en el tablero HACER
            PARA cada columna en la fila HACER
                GENERAR un número aleatorio entre 1 y 9
                MIENTRAS el número ya esté en la fila o en la columna
                    GENERAR otro número aleatorio
                SI se cumple una probabilidad del 50%
                    COLOCAR el número en la celda correspondiente
        RETORNAR el tablero generado
    FIN FUNCIÓN

    PROCEDIMIENTO imprimir_tablero_sudoku(TABLERO)
        IMPRIMIR encabezado con los números de las columnas
        IMPRIMIR línea divisoria
        PARA cada fila en el tablero HACER
            IMPRIMIR número de la fila seguido de las celdas separadas por "|"
            IMPRIMIR línea divisoria
    FIN PROCEDIMIENTO

    FUNCIÓN verificar_sudoku(TABLERO) -> VERDADERO O FALSO
        PARA cada fila en el tablero HACER
            SI hay una celda vacía
                RETORNAR FALSO (el tablero no está completo)
        RETORNAR VERDADERO (el tablero está completo)
    FIN FUNCIÓN

    FUNCIÓN obtener_entrada_usuario() -> (FILA, COLUMNA, NUMERO)
        MIENTRAS el usuario no ingrese datos correctos HACER
            INTENTAR
                PEDIR al usuario que ingrese la fila, la columna y el número
                SI los valores ingresados están dentro del rango permitido
                    RETORNAR la fila, la columna y el número
                SI NO
                    MOSTRAR un mensaje de error indicando los rangos permitidos
            SI la entrada es inválida
                MOSTRAR "Error: Ingresa solo números válidos."
            SI el usuario interrumpe el programa
                MOSTRAR "Has salido del juego."
                TERMINAR el programa
    FIN FUNCIÓN

    PROCEDIMIENTO jugar_sudoku()
        mostrar_reglas_sudoku()
        CREAR un tablero de Sudoku con algunos números prellenados
        MIENTRAS el tablero no esté completo HACER
            limpiar_pantalla()
            mostrar_titulo()
            mostrar_reglas_sudoku()
            imprimir_tablero_sudoku(TABLERO)
            MIENTRAS el usuario no haga una jugada válida HACER
                INTENTAR
                    PEDIR al usuario que elija una fila, una columna y un número
                    SI la celda seleccionada está vacía Y el número no se repite en la fila ni la columna
                        COLOCAR el número en la celda
                        SALIR del bucle
                    SI NO
                        MOSTRAR un mensaje de error explicando la restricción
                SI ocurre un error inesperado
                    MOSTRAR el mensaje de error
        limpiar_pantalla()
        mostrar_titulo()
        imprimir_tablero_sudoku(TABLERO)
        MOSTRAR "¡Felicidades, completaste el Sudoku!"
    FIN PROCEDIMIENTO

    SI el programa se está ejecutando directamente ENTONCES
        INTENTAR
            jugar_sudoku()
        SI el usuario interrumpe la ejecución
            MOSTRAR "Has salido del juego."
    FIN SI
FIN
```