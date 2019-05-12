# Chest X-Ray Image classifier to detect pneumonia
CNN model to detect pneumonia with Chest X-Ray Images

Dataset:
> Kermany, Daniel; Zhang, Kang; Goldbaum, Michael (2018), “Labeled Optical Coherence Tomography (OCT) and Chest X-Ray Images for Classification”, Mendeley Data, v2
> http://dx.doi.org/10.17632/rscbjbr9sj.2

---

Spanish report:

Se ha creado una red neuronal convolutiva que clasifica radiografías de pecho diferenciando pacientes con neumonía o sin neumonía. Para ello, se ha realizado el siguiente proceso:	

Primero, se ha procedido a la aumentación de los datos. Con el uso de la clase de Keras ImageDataGenerator y sus métodos, hemos creado dos generadores de imágenes (uno para validación y otro para entrenamiento) con imágenes en escala de grises normalizadas de tamaño 224x224.

Lo siguiente ha sido la creación del modelo. Se trata de un modelo secuencial, una red neuronal convolutiva pequeña. Este mismo se ha entrado haciendo uso de callbacks, en específico, checkpoints y early stopping.

Cabe destacar que los datos del dataset se encuentran desbalanceados (existen 3 veces más fotos de pacientes con neumonía que de pacientes sanos). Sin embargo, el equilibrio de pesos de clase no nos es de interés, ya que la misma naturaleza de los datos nos permite reducir el número de falsos negativos que existen.

Se ha validado el entrenamiento de nuestro modelo, a través de la curva ROC, la comparación Precisión/Exhaustividad y la matriz de confusión.

Luego, a partir del concepto de Transfer Learning, se ha creado un nuevo modelo basado en las Capas Convolutivas de Xception con los pesos predefinidos del dataset Imagenet. Incluyendo una salida personalizada a nuestro dataset (la naturaleza de nuestro clasificador es binaria, no categórica). 

Finalmente se ha realizado una última validación, y se ha analizado el resultado obtenido. 

Por lo general, para ambos modelos, el número de falsos negativos es menor que el de falsos positivos lo que nos es interesante. Aunque la precisión detectando pacientes sanos es mejor, la exhaustividad es mucho mejor para las muestras con neumonía.
