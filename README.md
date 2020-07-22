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

Se preprocesan las imágenes y se realiza un generador de imágenes debido a la poca cantidad que nos brinda el dataset.

#Model 0
En el primer modelo se obtuvo una accuracy para el set de validación de 77.38% y para el de test 72.92%. Se pueden observar oscilaciones en los gráficos de la accuracy y la loss lo que indica que el modelo no esta generalizando correctamente (overfitting alert!). Por lo tanto se probará con métodos de regularización o más cantidad de capas.

#Modelo 1
Se agrega una capa de Dropout para reducir el overfitting. Se obtuvo una accuracy para el set de validación de 84.11% y para el de test 78.27%. Aunque mejoró la accuracy todavía quedan rastros de overfitting.

#Modelo 2
En este modelo se probó data argumentation para que pueda entrenar con más data y pueda generalizar mejor. Se obtuvo una accuracy para el set de validación de 82.24% y para el de test 81.55%. Se ven que los valores de accuracy estan más cerca y que se logró bajar aún más el overfitting. Esto también se refleja en menos oscilaciones en los gráficos de accuracy y loss.


