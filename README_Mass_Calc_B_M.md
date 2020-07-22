# Redes_Mammography_Classification_Mass-Calc
CNN network for Mass benign, Mass malignant, Calcification benign, Calcification malignant mammography classification

Se uso la misma base de datos que en el anterior pero en este caso el remap se hizo para todas las clases
* 0 -> mass benign ([1. 0. 0. 0.])
* 1 -> mass malignant ([0. 1. 0. 0.])
* 2 -> calcification benign ([0. 0. 1. 0.])
* 3 -> calcification malignant ([0. 0. 0. 1.])

En la sección de 'Load data and process', la segunda celda de código muestra dos ejemplos de cada grupo de imágenes 
para analizar cuán distintas eran las imágenes a simple vista. En mi humilde opinión si los médicos pueden identificar y clasificar 
estos casos probablemente la red convolucional también.

#Model 1 -->
Se utilizó el mismo modelo que en la notebook anterior pero con una capa Densa: Dense(4, activation='softmax')) ya que son 4 las clases 
que se quieren obtener.
Se obtuvo una accuracy para el set de validación de 59.63% y para el set de test 60.12%.

En la matriz de confusión se puede observar que 42 imágenes fueron mal clasificadas según su tipo (mass/calc), con un total de 336 
imágenes representa el 12.5%. También se puede observar como se pudo clasificar sin tanto error entre masas y calcificaciones. Pero es
curioso observar que esta facilidad de clasificacion se ve solo en los casos de masas y calcificaciones benignas y no tanto
para las malignas. Globalmente, 202 imágenes fueron correctamente clasificadas obteniendo un 60% de resultados correctos.


