# Lógica de negocio

Como se indica en la [solución propuesta](https://github.com/Mil4n0r/WhatToPlay/blob/main/docs/solution.md) se optará por un sistema de recomendación que emplea *Collaborative Filtering*, basado en la búsqueda de usuarios similares de cara a ofrecer recomendaciones adecuadas.

Para ello emplearemos dos algoritmos principalmente.

## Algoritmos

### Detección de gustos similares

Para encontrar usuarios con gustos similares se empleará el cálculo de la ["Similitud coseno"](https://en.wikipedia.org/wiki/Cosine_similarity), una métrica que define como de similares son 2 vectores, donde el valor estará entre 0 y 1, significando 1 que ambos son idénticos mientras que 0 significa que no hay ningún tipo de similitud. 

![Cálculo de la similitud coseno](https://github.com/Mil4n0r/WhatToPlay/blob/main/img/cosine_similarity.png)

En nuestro caso estos vectores vendrán definidos por tantas dimensiones como *items* existan en el sistema, siendo su medida la correspondiente a la valoración otorgada por cada usuario a ese *item*.

De esta manera, lograremos determinar si 2 usuarios tienen gustos similares en base a la cercanía al número 0.

### Predicción de valoraciones

Una vez tenemos la similitud de nuestro usuario respecto al resto, podremos obtener una valoración media ponderada en base a las valoraciones del resto de usuarios y su correlación con el usuario que ha solicitado la recomendación.

La fórmula empleada es la siguiente:

![Cálculo de la valoración media ponderada](https://github.com/Mil4n0r/WhatToPlay/blob/main/img/average_weighted_rating.png)

Donde **Ru** representa la valoración de cada usuario y **Su** representa el factor de similitud (entre 0 y 1) con el usuario actual.

Obteniendo la valoración esperada por parte del usuario para cada juego, estos se ordenarán de manera descendente y se mostrarán como recomendaciones al usuario.

## Detalles

Las funcionalidades del sistema ofrecidas a cada uno de los usuarios serán las siguientes:

1. En caso de que no se tengan valoraciones de ningún juego por parte del usuario, se le solicitarán **20 valoraciones iniciales**, buscando así tener un punto de partida para recomendar. Las valoraciones se podrán hacer de las siguientes formas:
	1. Realizando una búsqueda en el **buscador** de videojuegos.
	2. Solicitando juegos de manera **aleatoria** (pudiendo especificar un género en concreto).
2. Una vez se tienen un mínimo de 20 valoraciones por parte del usuario se cuenta con las siguientes opciones:
	1. Obtener recomendaciones: Se le ofrecerán recomendaciones al usuario, teniendo este 3 opciones:
		1. Agregar el juego a una **lista de "deseados"**.
		2. Otorgar una **valoración** del juego en caso de ya conocerlo o haberlo jugado.
		3. **Ignorar** y pasar a la siguiente recomendación.
	2. Realizar valoraciones. De igual manera a como hemos visto anteriormente:
		1. Realizando una búsqueda en el **buscador** de videojuegos.
		2. Solicitando juegos de manera **aleatoria** (pudiendo especificar un género en concreto).