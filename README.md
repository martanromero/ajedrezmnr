# ajedrezmnr
def partida_ajedrez(nombre_fichero):
# Representamos un tablero como una cadema separando las separando las filas por cambios de línea y las columnas por tabuladores. Empleamos además caracteres para las piezas.
    tablero_inicial = '♜\t♞\t♝\t♛\t♚\t♝\t♞\t♜\n♟\t♟\t♟\t♟\t♟\t♟\t♟\t♟\n\t\t\t\t\t\t\t\n\t\t\t\t\t\t\t\n\t\t\t\t\t\t\t\n\t\t\t\t\t\t\t\n♙\t♙\t♙\t♙\t♙\t♙\t♙\t♙\n♖\t♘\t♗\t♕\t♔\t♗\t♘\t♖'
# Convertir la representación del tablero enuna lista de listas.
    tablero = []
    for i in tablero_inicial.split('\n'):
        tablero.append(i.split('\t'))
# Abrir el archivo en modo escritura ('w') con codificación utf-8 (empleo la codificación utf-8 puesto que sino me da error, lo uso por ser una codificación de caracteres que es capaz de manejar una amplia gama de caracteres Unicode, es decir, lo empleo para representar los dibujos que representan las piezas)
    f = open(nombre_fichero, 'w', encoding = 'utf-8')
    for i in tablero:
        f.write('\t'.join(i) + '\n')
    f.close()
# Inicializar el contador de movimientos
    movimiento = 0
# Bucle principal para permitir movimientos en el tablero
    while True:
# Solicitar entrada al usuario para decidir si realizar otro movimiento, si la respuesta no es s, se sale del bucle
        continuar = input('Deseas hacer otro movimiento (s/n):')
# Salir del bucle si el usuario no desea continuar
        if continuar != 's':
            break
        else:
# Solicitar información sobre el movimiento al usuario
            fila_origen = int(input('Introduce la fila de la pieza a mover:'))
            columna_origen = int(input('Introduce la columna de la pieza a mover:'))
            fila_destino = int(input('Introduce la fila de destino:'))
            columna_destino = int(input('Introduce la columna de destino:'))
# Actualizar el tablero con el nuevo movimiento
            tablero[fila_destino-1][columna_destino-1] = tablero[fila_origen-1][columna_origen-1]
            tablero[fila_origen-1][columna_origen-1] = ''
# Incrementar el contador de movimientos
            movimiento += 1
# Abrir el archivo en modo anexar ('a') con codificación utf-8 y se escribe información sobre el movimiento en el archivo
            f = open(nombre_fichero, 'a', encoding = 'utf-8')
# Escribir información sobre el movimiento en el archivo
            f.write('Movimiento' + str(movimiento) + '\n')
            for i in tablero:
                f.write('\t'.join(i) + '\n')
            f.close()
# Fin de la funcion
    return
partida_ajedrez('partida1.txt')
