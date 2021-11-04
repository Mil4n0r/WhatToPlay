# Solución propuesta

Se propone la creación de una aplicación llamada **WhatToPlay** capaz de ofrecer recomendaciones personalizadas para cada usuario.

Para ello, requeriremos un listado de videojuegos y un conjunto de valoraciones por parte de los usuarios.

El listado de videojuegos será obtenido por medio de *web scraping* de una de las plataformas más grandes y populares dentro del mundo de los videojuegos, Steam.

La estrategia empleada para el sistema de recomendación será *Collaborative Filtering*. Este método consiste en una matriz cuyas filas se corresponden con los usuarios del sistema y cuyas columnas se corresponden con los *items* (en este caso, los videojuegos). En las celdas contaremos con la valoración aportada por cada usuario a cada juego. El objetivo del sistema será "rellenar" las celdas vacías con las valoraciones esperadas por el usuario de cara a ofrecer recomendaciones adecuadas para él. 

Concretamente, el método utilizado para recomendar será el que se conoce como *User-based*, en el cual se identifican usuarios con gustos similares y se dan recomendaciones de nuevos *items* basándose en la valoración dada por estos usuarios.