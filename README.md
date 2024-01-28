# LaEscenciadelcliente
Revelando la Esencia del Cliente


Descripción
La exploración visual de datos permite a los científicos de datos examinar y explorar grandes volúmenes de datos de manera intuitiva y eficiente. Al representar los datos visualmente, se pueden identificar características importantes, como valores atípicos, distribuciones, correlaciones y agrupaciones, que podrían no ser evidentes al examinar solo los números o las tablas de datos.

Se trata de una herramienta poderosa para comprender, analizar y comunicar información clave presente en los conjuntos de datos, brindando una comprensión más profunda y facilitando la toma de decisiones informadas.

1. Haciendo uso de Matplotlib y Seaborn vamos a generar diversos gráficos para entender mejor nuestros datos.

2. Ejemplo: A través de un histograma, podrás observar la distribución de ingresos anuales de los clientes, por ejemplo. (Siéntete libre de escoger las variables que desees visualizar, y genera varios gráficos, según lo consideres pertinente)

3. Es importante que escribas todas tus observaciones e hipótesis en la medida que generes los gráficos. Puedes utilizar una celda de texto de tu notebook para hacerlo.

Tip: Voy a dejar a continuación algunas variables que pueden ser de interés para tenerlas en cuenta en tu análisis visual: Escolaridad, Ocupación, Miembro, Género, Estado Civil, Número de Hijos, Ingresos_anuales, Categoría de alimentos, Tipo, entre otras.

Preprocesamiento
1. En esta fase es importante utilizar una forma de codificar las variables categóricas para que el modelo de clusterización las pueda reconocer. Puedes usar one-hot-encoder, get_dummies, o establecer un valor numérico para las variables de acuerdo con tu percepción; por ejemplo, si queremos categorizar primaria, secundaria y universidad, podríamos decir que el valor numérico para primaria podría ser 1, el valor numérico para secundaria, 2, y así sucesivamente. (Es importante aclarar que en ejemplo citado, asignamos los valores a cada nivel porque sabemos que primaria es menor que secundaria, y secundaria menor que universidad)

2. Tras establecer un método de codificación para tus variables categóricas, debes reemplazar los valores numéricos asignados en el dataset para sustituir las cadenas de texto.

Tip: La pregunta que te debes estar haciendo es: ¿Será que tengo que codificar todas las columnas categóricas del dataset? La respuesta es no; únicamente codifica las columnas que tu consideres que puedan ser relevantes para la clusterización.

3. Teniendo en cuenta el paso anterior, debes en efecto seleccionar las variables que sean más relevantes para el caso de estudio: Se desea agrupar a los clientes en diversos clusters para entender sus características y brindarles el mejor servicio.

4. Con tus atributos seleccionados, al menos 6 y máximo 12, procederemos a estandarizar nuestros datos (que en este punto deben ser todos numéricos) para que todas las variables puedan ser tenidas en cuenta dentro de una misma escala. Varios de los hiperparámetros utilizados en las funciones de un modelo de Machine Learning asumen que todas las características están centradas alrededor de 0 y tienen varianza en el mismo orden. Si uno de los atributos del dataset tiene una varianza con orden de magnitud muy superior al de los demás atributos, puede dominar la función del modelo y hacer que el estimador no aprenda correctamente de los otros atributos como se espera. Vamos a utilizar con el StandardScaler. Puedes almacenar los valores estandarizados en una variable llamada X_std , por ejemplo.

5. Clusterización
1. El algoritmo recomendado para la clusterización es KMeans, sin embargo, eres libre de utilizar cualquier otro algoritmo como Mean Shift o, incluso, DBSCAN. Lo importante es hallar el mejor número de clusters.

Validación
2. Número de clusters: Debes instanciar de 3 a máximo 10 clusters con el(los) algoritmo(s) seleccionado(s), utilizando X_std y obtener cómo mínimo el puntaje de Silhouette, aunque te recomiendo utilizar otras métricas como Davies-Bouldin y Calinski and Harabasz para que puedas decidir cuál es la mejor configuración para el número de clusters.

Restricciones: (El puntaje mínimo de Silhouette debe ser de 0.50; el de Davies-Bouldin máximo de 0.75; y el de CalinskiHarabasz, el número más alto posible.)

3. Estructura: Debes evaluar la estructura de los clusters tomando como referencia una baseline. Para generar la baseline, vamos a generar números aleatorios con el módulo random de numpy con las mismas dimensiones de tu dataset X_std y lo vas a almacenar en una variable llamada random_data y vas a repetir el paso 2. Analiza los puntajes da la(s) métrica(s) utilizada y asegúrate de que tu X_std tiene un desempeño muy superior al de random_data.

4. Estabilidad: Finalmente, debes evaluar la estabilidad de los clusters con el número de clusters seleccionado en el paso 2. Para ello, debes segmentar X_std en 3 o 5 partes iguales, (puedes apoyarte en la función array_split() de numpy, y almacenar cada fragmento del dataset en una variable llamada set_1, set_2, ..., set_n) y repetir los pasos de validación para el número de clusters escogido en cada uno de los sets. Aquí lo verdaderamente importante es que los puntajes no presenten una variación mayor a ±5% entre sí. Esto va a garantizar que hay homogeneidad en la composición de los clusters.

Si has logrado llevar a cabo con éxito los pasos anteriores, puedes avanzar a la próxima fase. En caso contrario, verifica nuevamente las variables: añade, remueve, cambia por otras, y repite de nuevo los pasos de la tarjeta anterior para poder repetir los pasos de esta tarjeta hasta que obtengas los resultados sugeridos.

Instanciando la mejor configuración de clusters
5. Vas a instanciar el algoritmo de clusterización una vez , con la configuración escogida, y vas a crear un nuevo atributo en el dataset datos_raw llamado 'cluster' para almacenar los labels de los clusters.

Nota: Te sugiero que no ejecutes KMeans de nuevo, porque los clusters van a cambiar de label y color con cada ejecución del algoritmo.

6. Vas a realizar varios gráficos de dispersión para comparar las variables añadiendo una tercera dimensión con los clusters en el parámetro hue del gráfico. Trata de describir tus observaciones. Por ejemplo: En el cluster 0, de color rojo, se encuentran agrupados los clientes que gastan más dinero en productos no comestibles.

Repite el paso anterior hasta que puedas obtener varias descripciones de cada uno de los clusters.

1. Debes generar en una celda de texto el resultado consolidado de tu análisis.

Posibles estrategias a implementar
2. Aquí vas a elaborar una serie de recomendaciones de estrategias para personalizar la experiencia de los clientes en cada uno de los clusters; por ejemplo:

En el cluster A, se encuentran reunidos los clientes que gastan más dinero en productos de bebida.

Estrategia sugerida: Elaborar una campaña dirigida a estos clientes para que también compren productos de comida(…)

Aquí puedes usar toda tu creatividad, y la idea es proponer acciones para los clientes según sus características de consumo.

Checklist
