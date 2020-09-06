# TetraMasterJS
Juego de cartas de Final Fantasy IX TetraMaster

https://steamcommunity.com/sharedfiles/filedetails/?id=665845408
http://www.lacapitalolvidada.com/foro/tetra-master-t6643.html
Diseño de la carta
 Nombre
 Imagen
 Tipo: Carta o pared
 Fechas
o Sup-Izq
o Sup
o Sup-Der
o Lat-Der
o Inf-Der
o Inf
o Inf-Izq
o Lat-Izq
 Poder de ataque
 Tipo de ataque
o P o F: ataque Físico (Physic), La carta ataca a la defensa física en la carta rival
o M: ataque Mágico, La carta ataca a la defensa mágica en la carta rival
o X: flexible, La carta ataca a la defensa más baja en la carta rival
o A: asalto, La carta ataca con el valor más alto al valor más bajo
En el Asalto la carta que ataca no necesariamente debe usar el valor de ataque; si el valor de defensa es más alto
que el de ataque, entonces lo puede utilizar. Igualmente la carta que se defiende, solo puede usar el valor más
bajo, no importa que no sea el valor de defensa.
 Defensa física
 Defensa mágica
Diseño de la mesa
 Lista de Lugares[n,n]
o Carta o Pared
o Carta
o Color: el jugador al que pertenece la carta
o Arriba-Izq
o Arriba
o Abajo-Der
o Lado-Der
o Abajo-Der
o Abajo
o Abajo-Izq
o Lado-Izq
 Poner Carta En Mesa ()

 Preparar Mesa Inicial ()
Diseño de una partida
 Descripción de la partida
 Fecha
 Resultado
 Lista de Jugadores []
o Jugador
o Mazo
 Mesa
 Generador de turnos
 Lista de Jugadas []
o Jugador
o Carta
o Estado

Jugador
 Nombre
 Mazo Central
o Lista de Cartas []
 Lista de mazos preparados
o Descripción
o Lista de Cartas []

Tabla de valores de ataque y defensa
Valor Dígito
mínimo
Dígito
máximo
0 0 15
1 16 31
2 32 47
3 48 63
4 64 79
5 80 95
6 96 111
7 112 127
8 128 143
9 144 159
A 160 175
B 176 191
C 192 207
D 208 223
E 224 239
F 240 255

Las 3 etapas para resolver un encuentro de cartas
Etapa A

 Con la carta que ataca, se verifica el tipo de ataque para determinar a qué defensa atacará
 A1 = Con la carta que ataca, el poder de ataque se sortea entre el mínimo y el máximo de la tabla
 A2 = Con la carta que se defiende, el poder de defensa se sortea entre el mínimo y el máximo de la tabla
Etapa B
 B1 = Se sortea un entero entre cero y A1
 B2 = Se sortea un entero entre cero y A2
Etapa C
 C1 = A1 – B1
 C2 = A2 – B2
 Si C1 &gt; C2 entonces gana la carta atacante
Resumen de fórmulas para resolver el ataque
Sean:
: El tipo de ataque: P es ataque físico, M es ataque mágico, X es ataque a la defensa más baja, A
: El indicador de ataque
: El indicador de defensa contra un ataque físico
: El indicador de defensa contra un ataque físico
: Función que retorna el valor mínimo y máximo permitido para el valor de ataque correspondiente
: Función randómica que sortea un número entero entre y
Por lo tanto, el algoritmo se puede expresar de la siguiente forma:
Caso ataque físico:
 : La carta atacante usa su índice de ataque
 : La carta atacada usa su índice de defensa contra el ataque físico
Caso ataque mágico:
 : La carta atacante usa su índice de ataque
 : La carta atacada usa su índice de defensa contra el ataque mágico
Caso ataque flexible:
 : La carta atacante usa su índice de ataque
 : El índice es el menor de los índices de ataque y defensa
Caso ataque por asalto:
 : El índice de ataque es el mayor de todos los índices de la carta atacante
 : El índice de defensa es el menor de todos los índices de la carta atacada
En cualquiera de los casos el cálculo es:
 : El valor neto de ataque
 : El valor neto de defensa
 Si entonces la carta atacante gana, caso contrario pierde.

Reglas:

El juego de cartas de FFIX no tiene ninguna recompensa. Sólo está como entretenimiento.
Las cartas están compuestas por flechas (de 0 a 8) que indican direcciones (arriba, abajo, derecha, izquierda y las 4
diagonales) y por 4 números (o letras).

El juego consiste en colocar las cartas (5 cada uno) en una cuadrícula de 4x4 que puede tener algunas casillas ocupadas.
Cuando colocas una carta sus flechas apuntarán a algunas casillas, si una casilla está ocupada por una carta del rival
pueden pasar 2 cosas:

1-La carta no tiene una flecha apuntando hacia la tuya. En este caso la carta del rival pasa a ser tuya.
2-La carta del rival también tiene una flecha que apunta hacia la tuya. En este caso hay un combate y el ganador se
queda la carta del rival.
Cuando una carta cambia de propietario cuenta como si ésta hubiese sido colocada de nuevo y “luchará” contra las
cartas rivales que apunten sus flechas.

Cuando finalice la partida gana aquel con más cartas volcadas.

¿Cómo saber si puedo ganar un combate?

Los combates se realizan con los valores de los 4 números (o letras) que aparecen en la carta. Dichos dígitos significan lo
siguiente (de izquierda a derecha):
Ataque: La fuerza con la que ataca.
Tipo de ataque: Puede ser F (físico), M (mágico), X (especial), A (Avanzado).
Defensa física: Indica la capacidad defensiva frente a ataques físicos.
Defensa mágica: Indica la capacidad defensiva frente a ataques mágicos.

Tipos de ataque:
F y M atacan respectivamente a la defensa física (3º número) y a la mágica (4º número) del rival.

X ataca la defensa más baja (mínimo entre el 3º y 4º números).

A: ataca al valor más bajo del rival (mínimo entre el 1º,3º y 4º números).

Los dígitos de ataque y defensa (1º,3º,4º) varían entre 0 y 15 en escala hexadecimal:
0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A (=10), B (=11), C (=12), D (=13), E (=14), F (=15).

Siendo 0 el mínimo y F el máximo

La fuerza del ataque se determina siguiendo la fórmula siguiente:
Sea X el número de ataque (1º dígito):
Se escoge un número aleatorio, Y, entre 15*(X-1) y 15*(X). Es decir:
15(X-1) &lt;= Y &lt;= 15*X

(El * indica multiplicación y “&lt;=” se lee “más pequeño o igual que” .
Después se escoge un valor aleatorio entre 0 e Y, llamémosle Z:
0 &lt;= Z &lt;= Y.
Z será nuestro ataque.

El número de defensa se calcula igual usando como X el número que marque el tipo de ataque de la carta atacante:

El atacante tiene una Fà 3º dígito

El atacante tiene una Mà 4º dígito

El atacante tiene una Xà mínimo entre 3º y 4º.

El atacante tiene una Aà mínimo entre 1º, 3º y 4º.

Normalmente tener un número de ataque superior a la defensa correspondiente es suficiente para ganar, pero no
siempreTenemos la carta 5X31 vs 2M32, atacante 5X31, defensora 2M32.
Ataque = 5, por tanto X=5. El juego calcula un numero aleatorio entre 15*4 y 15*5 [4 y 5, en la formula, son X-
1 y X], es decir, 60 y 75, supongamos que escoge 63. Y=63.
El juego calcula un valor aleatorio entre 0 y 63, por ejemplo, 41. Z=41.
Tenemos un ataque de 41.
La defensa:

El ataque es Tipo X (defensa ams debil), hay defensa fisica 3 y magica 2, la ams debil es la magica, es decir, 2.
Este sera el valor en la defensa, X=2.
Numero aleatorio entre 15*1 y 15*2, es decir, 15 y 30, por ejemplo, 29. Y=29.
Ahora uno aleatorio entre 0 y 29, pogamos 10. Z=10.
Atacante vs defensor = 41 vs 10, gana 41---&gt; gana la carta atacante 5X31.
Ahora bien, normalmente pasara esto, gana 5X31, pero sit ienes mala suerte:
X=5, escogemos un numero aleatorio entre 60 y 75, sale 61.
Y=61, escogemos numero aleatorio entre 0 y 61, sale 1.
Z=1 es el ataque final.
SI la defensa sale como ante, 41, ganaria la carta 2M32.

Lo has entendido ahora? Sino, di que paso no entiendes.
Consejo: Como la parte aleatoria no depende de ti, para aumentar las probabilidades de gaanr, simplemente ten
ams ataque que defensa tu rival, es decir, miras el TIPOD E ATAQUE (P,M,X,A), el digito de defensa del rival
que corresponde (fisica, magica, ams debil...) y cuando tengas la defensa, mira tu ataque, sie s mas alto, mas
posibilidades de ganar