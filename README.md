# Redes_Mammography_Classification_Mass-Calc
CNN network for Mass and Calcification mammography classification

El dataset que se utilzó es el 'Curated Breast Imaging Subset of  Digital Database for Screening Mammography' el cual posee 3103 imágenes. Se trabajó con un archivo .zip dado que el espacio de almacenamiento que ocupaba el archivo era de 95.5 GB. El dataset de mamografías tienen dos subgrupos, mamografías con calcificaciones y con masas que a su vez cada uno ya esta previamente dividido en test y train.

* mass_test -->  361 mamografias
* mass_train --> 1231 mamografias
* calc_test --> 284 mamografias
* calc_train --> 1227 mamografias

Se realiza un remap donde
* 0 --> mamografías con masas
* 1 --> mamografías con calcificaciones

En Check images se pueden observar 8 imágenes los cuales son ejemplos de estos dos casos (Label 0: mass, Label 1: calc) para que se pueda observar lo similares que son las imágenes entre estos dos subgrupos.

Se preprocesan las imágenes y se realiza un generador de imágenes debido a la poca cantidad que nos brinda el dataset.

#Model 0
En el primer modelo se obtuvo una accuracy para el set de validación de 77.38% y para el de test 72.92%. Se pueden observar oscilaciones en los gráficos de la accuracy y la loss lo que indica que el modelo no esta generalizando correctamente (overfitting alert!). Por lo tanto se probará con métodos de regularización o más cantidad de capas.

#Modelo 1
Se agrega una capa de Dropout para reducir el overfitting. Se obtuvo una accuracy para el set de validación de 84.11% y para el de test 78.27%. Aunque mejoró la accuracy todavía quedan rastros de overfitting.

#Modelo 2
En este modelo se probó data argumentation para que pueda entrenar con más data y pueda generalizar mejor. Se obtuvo una accuracy para el set de validación de 82.24% y para el de test 81.55%. Se ven que los valores de accuracy estan más cerca y que se logró bajar aún más el overfitting. Esto también se refleja en menos oscilaciones en los gráficos de accuracy y loss.

#Modelo 3
* Se agregó Conv2D con 128 filtros
* Dense(48, activation='relu')
* Early stopping
* Batch_size=128
* RMSprop(learning_rate=0.001, decay=1e-3)
Se obtuvo una accuracy para el set de validación de 87.48% y para el de test 83.04%. Mejoró la accuracy pero podemos seguir viendo picos en los gráficos de accuracy y loss.

#Model 4
Extra Conv2D con 256 filtros. Se obtuvo una accuracy para el set de validación de 87.48% y para el de test 82.74%. Vemos como se sigue reduciendo el overfitting.

#Model 5
A las capas Conv2D se les agrego un regularizador kernel_regularizer=l2(0.00005). Se obtuvo una accuracy para el set de validación de 88.79% y para el de test 84.23%.

Se toman los últimos tres modelos y se analiza la clasificación que realizaron.
Se tomo como mala clasificación (wrong classification) aquellas que se clasificaron mal con un error mayor al 50% y como peor clasificación (worst classification) aquellas que lo hicieron por mas del 80%. Graficamos aquellas imágenes que tuvieron un error de clasificación por mas del 80%. 

Modelo 3
* Cantidad de imaágenes de Test: 336
* Mala clasificación: 57
* Peor clasificación: 22

En la matriz de confusión se logra ver como el modelo 3 es el que mejor clasifica masas. Tiene un porcentaje de una buena clasificación general de 83%.

Modelo 4
* Cantidad de imaágenes de Test: 336
* Mala clasificación: 58
* Peor clasificación: 21

Tiene un porcentaje de una buena clasificación general de 82.7%.

Modelo 5 
* Number of test images: 336
* Mala clasificación: 53
* Peor clasificación: 12

En la matriz de confusión se logra ver como el modelo 5 es el que mejor clasifica calcificaciones. Tiene un porcentaje de una buena clasificación general de 84%.

Aunque las tres tienen un comportamiento de clasificación distintos el porcentaje de clasificación es bastante similar.


