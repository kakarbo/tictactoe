# Tic-Tac-Toe

Utilizando Minimax, implemente una IA para jugar al tres en raya de forma óptima.

![Alt text](image.png)

## Primeros pasos
* Descarga el código de distribución de https://cdn.cs50.net/ai/2023/x/projects/0/tictactoe.zip y descomprímelo.
* Una vez en el directorio del proyecto, ejecute ```pip3 install -r requirements.txt``` para instalar el paquete Python necesario (```pygame```) para este proyecto.

## Comprender
Hay dos archivos principales en este proyecto: ```runner.py``` y ```tictactoe.py```. ```tictactoe.py``` contiene toda la lógica para jugar el juego, y para hacer movimientos óptimos. ```runner.py``` ha sido implementado para ti, y contiene todo el código para ejecutar la interfaz gráfica del juego. Una vez que hayas completado todas las funciones requeridas en ```tictactoe.py```, ¡deberías ser capaz de ejecutar runner.py para jugar contra tu IA!

Abramos ```tictactoe.py``` para entender lo que se proporciona. Primero, definimos tres variables: ```X```, ```O```, y ```EMPTY```, para representar posibles movimientos del tablero.

La función ```initial_state``` devuelve el estado inicial del tablero. Para este problema, hemos elegido representar el tablero como una lista de tres listas (que representan las tres filas del tablero), donde cada lista interna contiene tres valores que son ```X```, ```O``` o ```EMPTY```. Lo que sigue son funciones que te hemos dejado a ti para que las implementes.

## Especificación
Complete las implementaciones de ```player```, ```actions```, ```result```, ```winner```, ```terminal```, ```utility``` y ```minimax```.
* La función de ```player``` debe tomar un estado del tablero como entrada, y devolver qué jugador es el turno (```X``` u ```O```).
    * En el estado inicial del juego, ```X``` obtiene el primer movimiento. Posteriormente, el jugador se alterna con cada movimiento adicional.
    * Cualquier valor de retorno es aceptable si se proporciona un tablero terminal como entrada (es decir, el juego ya ha terminado).
* La función ```actions``` debe devolver un ```set``` de todas las acciones posibles que se pueden realizar en un tablero dado.
    * Cada acción debe representarse como una tupla (```i```, ```j```) donde ```i``` corresponde a la fila del movimiento (```0```, ```1``` o ```2```) y ```j``` corresponde a qué celda de la fila corresponde el movimiento (también ```0```, ```1``` o ```2```).
    * Los movimientos posibles son todas las casillas del tablero que no tengan ya una ```X``` o una ```O```.
    * Cualquier valor de retorno es aceptable si se proporciona una placa de bornes como entrada.
* La función de ```result``` toma un ```board``` y una ```action``` como entrada, y debe devolver un nuevo estado del tablero, sin modificar el tablero original.
    * Si ```action``` no es una acción válida para la tabla, su programa debería lanzar una excepción.
    * El estado del tablero devuelto debería ser el tablero que resultaría de tomar el tablero de entrada original, y dejar que el jugador cuyo turno es haga su movimiento en la casilla indicada por la acción de entrada.
    * Es importante que el tablero original no se modifique, ya que Minimax requerirá en última instancia considerar muchos estados diferentes del tablero durante su cálculo. Esto significa que la simple actualización de una celda en el propio tablero no es una implementación correcta de la función ```result```. Probablemente querrá hacer una ```deep copy``` del tablero antes de hacer cualquier cambio.
* La función de ```winner``` debe aceptar un ```board``` como entrada, y devolver el ganador del tablero si lo hay.
    * Si el jugador X ha ganado la partida, tu función debe devolver ```X```. Si el jugador O ha ganado la partida, tu función debe devolver ```O```.
    * Se puede ganar la partida con tres de sus movimientos seguidos en horizontal, vertical o diagonal.
    * Puede asumir que habrá como máximo un ganador (es decir, ningún tablero tendrá nunca a ambos jugadores con tres en raya, ya que sería un estado de tablero inválido).
    * Si no hay ganador de la partida (ya sea porque la partida está en curso o porque terminó en empate), la función debe devolver ```None```.
* La función ```terminal``` debe aceptar un ```board``` como entrada, y devolver un valor booleano indicando si el juego ha terminado.
    * Si el juego ha terminado, ya sea porque alguien ha ganado la partida o porque se han llenado todas las casillas sin que nadie haya ganado, la función debe devolver ```True```.
    * En caso contrario, la función debe devolver ```False``` si el juego sigue en curso.
* La función de ```utility``` debe aceptar una ```board``` terminal  como entrada y dar como salida la utilidad de la board.
    * Si X ha ganado la partida, la utilidad es ```1```. Si O ha ganado la partida, la utilidad es ```-1```. Si la partida ha terminado en empate, la utilidad es ```0```.
    * Puede asumir que la ```utility``` sólo será llamada en una ```board``` si terminal(```board```) es True.
* La función ```minimax``` debe tomar un ```board``` como entrada, y devolver el movimiento óptimo para que el jugador se mueva en ese board.
    * La jugada devuelta debe ser la acción óptima (```i```, ```j```) que sea una de las acciones permitidas en el tablero. Si varios movimientos son igualmente óptimos, cualquiera de ellos es aceptable.
    * Si la ```board``` es una board terminal, la función minimax debe devolver None.

Para todas las funciones que aceptan una ```board``` como entrada, puede asumir que es una tabla válida (es decir, que es una lista que contiene tres filas, cada una con tres valores de ```X```, ```O``` o ```EMPTY```). No debe modificar las declaraciones de función (el orden o el número de argumentos de cada función) proporcionadas.

Una vez que todas las funciones estén implementadas correctamente, deberías poder ejecutar ```python runner.py``` y jugar contra tu IA. Y, puesto que el tres en raya es un empate dado el juego óptimo de ambas partes, nunca deberías poder ganar a la IA (aunque si no juegas también de forma óptima, ¡puede que te gane!).

## Sugerencias
* Si quieres probar tus funciones en un archivo Python diferente, puedes importarlas con líneas como ```from tictactoe import initial_state```.
* Puedes añadir funciones de ayuda adicionales a tictactoe.py, siempre que sus nombres no coincidan con nombres de funciones o variables que ya estén en el módulo.
* La poda alfa-beta es opcional, pero puede hacer que tu IA funcione de forma más eficiente.


