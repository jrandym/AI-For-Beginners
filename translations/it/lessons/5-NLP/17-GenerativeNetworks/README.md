# Redes Generativas

## [Cuestionario previo a la clase](https://red-field-0a6ddfd03.1.azurestaticapps.net/quiz/117)

Las Redes Neuronales Recurrentes (RNN) y sus variantes con celdas de compuerta, como las Celdas de Memoria a Largo Plazo (LSTM) y las Unidades Recurrentes con Compuerta (GRU), proporcionan un mecanismo para el modelado del lenguaje, ya que pueden aprender el orden de las palabras y ofrecer predicciones para la siguiente palabra en una secuencia. Esto nos permite utilizar RNN para **tareas generativas**, como la generación de texto ordinario, la traducción automática e incluso la creación de subtítulos para imágenes.

> ✅ Piensa en todas las veces que te has beneficiado de tareas generativas, como la finalización de texto mientras escribes. Investiga en tus aplicaciones favoritas para ver si han aprovechado las RNN.

En la arquitectura de RNN que discutimos en la unidad anterior, cada unidad RNN producía el siguiente estado oculto como salida. Sin embargo, también podemos agregar otra salida a cada unidad recurrente, lo que nos permitiría generar una **secuencia** (que tiene la misma longitud que la secuencia original). Además, podemos utilizar unidades RNN que no aceptan una entrada en cada paso, y solo toman un vector de estado inicial, para luego producir una secuencia de salidas.

Esto permite diferentes arquitecturas neuronales que se muestran en la imagen a continuación:

![Imagen que muestra patrones comunes de redes neuronales recurrentes.](../../../../../translated_images/unreasonable-effectiveness-of-rnn.541ead816778f42dce6c42d8a56c184729aa2378d059b851be4ce12b993033df.it.jpg)

> Imagen del artículo [Efectividad Irrazonable de las Redes Neuronales Recurrentes](http://karpathy.github.io/2015/05/21/rnn-effectiveness/) de [Andrej Karpaty](http://karpathy.github.io/)

* **Uno a uno** es una red neuronal tradicional con una entrada y una salida.
* **Uno a muchos** es una arquitectura generativa que acepta un valor de entrada y genera una secuencia de valores de salida. Por ejemplo, si queremos entrenar una red de **subtitulación de imágenes** que produzca una descripción textual de una imagen, podemos usar una imagen como entrada, pasarla a través de una CNN para obtener su estado oculto, y luego tener una cadena recurrente que genere el subtítulo palabra por palabra.
* **Muchos a uno** corresponde a las arquitecturas RNN que describimos en la unidad anterior, como la clasificación de texto.
* **Muchos a muchos**, o **secuencia a secuencia**, corresponde a tareas como la **traducción automática**, donde una primera RNN recopila toda la información de la secuencia de entrada en el estado oculto, y otra cadena RNN despliega este estado en la secuencia de salida.

En esta unidad, nos enfocaremos en modelos generativos simples que nos ayuden a generar texto. Para simplificar, utilizaremos la tokenización a nivel de caracteres.

Entrenaremos esta RNN para generar texto paso a paso. En cada paso, tomaremos una secuencia de caracteres de longitud `nchars` y pediremos a la red que genere el siguiente carácter de salida para cada carácter de entrada:

![Imagen que muestra un ejemplo de generación de la palabra 'HELLO' por una RNN.](../../../../../translated_images/rnn-generate.56c54afb52f9781d63a7c16ea9c1b86cb70e6e1eae6a742b56b7b37468576b17.it.png)

Al generar texto (durante la inferencia), comenzamos con algún **prompter**, que se pasa a través de las celdas RNN para generar su estado intermedio, y luego desde este estado comienza la generación. Generamos un carácter a la vez y pasamos el estado y el carácter generado a otra celda RNN para generar el siguiente, hasta que generemos suficientes caracteres.

<img src="images/rnn-generate-inf.png" width="60%"/>

> Imagen del autor

## ✍️ Ejercicios: Redes Generativas

Continúa tu aprendizaje en los siguientes cuadernos:

* [Redes Generativas con PyTorch](../../../../../lessons/5-NLP/17-GenerativeNetworks/GenerativePyTorch.ipynb)
* [Redes Generativas con TensorFlow](../../../../../lessons/5-NLP/17-GenerativeNetworks/GenerativeTF.ipynb)

## Generación de texto suave y temperatura

La salida de cada celda RNN es una distribución de probabilidad de caracteres. Si siempre tomamos el carácter con la probabilidad más alta como el siguiente carácter en el texto generado, el texto a menudo puede volverse "cíclico" entre las mismas secuencias de caracteres una y otra vez, como en este ejemplo:

```
today of the second the company and a second the company ...
```

Sin embargo, si miramos la distribución de probabilidad para el siguiente carácter, podría ser que la diferencia entre algunas de las probabilidades más altas no sea enorme, por ejemplo, un carácter puede tener una probabilidad de 0.2, otro - 0.19, etc. Por ejemplo, al buscar el siguiente carácter en la secuencia '*play*', el siguiente carácter podría ser igualmente un espacio o **e** (como en la palabra *player*).

Esto nos lleva a la conclusión de que no siempre es "justo" seleccionar el carácter con una probabilidad más alta, porque elegir el segundo más alto podría aún llevarnos a un texto significativo. Es más sabio **muestrear** caracteres de la distribución de probabilidad dada por la salida de la red. También podemos utilizar un parámetro, **temperatura**, que aplanará la distribución de probabilidad, en caso de que queramos añadir más aleatoriedad, o hacerla más pronunciada, si queremos ceñirnos más a los caracteres de mayor probabilidad.

Explora cómo se implementa esta generación de texto suave en los cuadernos enlazados anteriormente.

## Conclusión

Aunque la generación de texto puede ser útil por sí misma, los principales beneficios provienen de la capacidad de generar texto utilizando RNN a partir de algún vector de características inicial. Por ejemplo, la generación de texto se utiliza como parte de la traducción automática (secuencia a secuencia, en este caso el vector de estado del *encoder* se utiliza para generar o *decodificar* el mensaje traducido), o para generar una descripción textual de una imagen (en cuyo caso el vector de características provendría de un extractor CNN).

## 🚀 Desafío

Toma algunas lecciones en Microsoft Learn sobre este tema.

* Generación de Texto con [PyTorch](https://docs.microsoft.com/learn/modules/intro-natural-language-processing-pytorch/6-generative-networks/?WT.mc_id=academic-77998-cacaste)/[TensorFlow](https://docs.microsoft.com/learn/modules/intro-natural-language-processing-tensorflow/5-generative-networks/?WT.mc_id=academic-77998-cacaste)

## [Cuestionario posterior a la clase](https://red-field-0a6ddfd03.1.azurestaticapps.net/quiz/217)

## Revisión y Autoestudio

Aquí hay algunos artículos para ampliar tus conocimientos:

* Diferentes enfoques para la generación de texto con Cadenas de Markov, LSTM y GPT-2: [artículo del blog](https://towardsdatascience.com/text-generation-gpt-2-lstm-markov-chain-9ea371820e1e)
* Ejemplo de generación de texto en la [documentación de Keras](https://keras.io/examples/generative/lstm_character_level_text_generation/)

## [Asignación](lab/README.md)

Hemos visto cómo generar texto carácter por carácter. En el laboratorio, explorarás la generación de texto a nivel de palabras.

**Disclaimer**:  
This document has been translated using machine-based AI translation services. While we strive for accuracy, please be aware that automated translations may contain errors or inaccuracies. The original document in its native language should be considered the authoritative source. For critical information, professional human translation is recommended. We are not liable for any misunderstandings or misinterpretations arising from the use of this translation.