---
title: Caracterización en experimentos de AutoML
titleSuffix: Azure Machine Learning
description: Obtenga información sobre los valores de caracterización que Azure Machine Learning ofrece y cómo se admite la ingeniería de características en experimentos de ML automatizado.
author: nibaccam
ms.author: nibaccam
ms.reviewer: nibaccam
services: machine-learning
ms.service: machine-learning
ms.subservice: core
ms.topic: how-to
ms.date: 05/28/2020
ms.custom: seodec18
ms.openlocfilehash: 11bb692027d8a2e5033c7bdaf8eb2c565d1562b0
ms.sourcegitcommit: 3541c9cae8a12bdf457f1383e3557eb85a9b3187
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2020
ms.locfileid: "86205694"
---
# <a name="featurization-in-automated-machine-learning"></a>Caracterización en aprendizaje automático automatizado

[!INCLUDE [applies-to-skus](../../includes/aml-applies-to-basic-enterprise-sku.md)]

En esta guía, obtendrá información sobre lo siguiente:

- Valores de caracterización que ofrece Azure Machine Learning.
- Procedimientos para personalizar esas características para los [experimentos de aprendizaje automático automatizado](concept-automated-ml.md).

La *ingeniería de características* es el proceso de usar el conocimiento de dominio de los datos para crear características que permitan mejorar los algoritmos de aprendizaje automático (ML). En Azure Machine Learning, se aplican técnicas de escalado de datos y normalización para facilitar la ingeniería de características. El conjunto de estas técnicas y la ingeniería de características se conoce como *caracterización* en el área de aprendizaje automático automatizado o *AutoML*, y experimentos.

En este artículo se da por supuesto que ya sabe cómo configurar un experimento de AutoML. Para obtener información sobre la configuración, vea los artículos siguientes:

- Para obtener una experiencia de codificar por primera vez: [Configuración de experimentos de ML automatizado con el SDK de Azure Machine Learning para Python](how-to-configure-auto-train.md).
- Para obtener una experiencia sin código o con poco código: [Creación, revisión e implementación de modelos de aprendizaje automático automatizado con Azure Machine Learning Studio](how-to-use-automated-ml-for-ml-models.md).

## <a name="configure-featurization"></a>Configuración de la caracterización

En todos los experimentos de aprendizaje automático automatizado se aplican [técnicas de escalado automático y normalización](#featurization) a los datos de forma predeterminada. Estas técnicas son tipos de caracterización que ayudan a *ciertos* algoritmos que son sensibles a las características a diferentes escalas. Sin embargo, también puede habilitar una caracterización adicional, como la *atribución de los valores que faltan*, la *codificación* y las *transformaciones*.

> [!NOTE]
> Los pasos de la caracterización del aprendizaje automático automatizado (tales como la normalización de características, el control de los datos que faltan o la conversión de valores de texto a numéricos) se convierten en parte del modelo subyacente. Cuando se usa el modelo para realizar predicciones, se aplican automáticamente a los datos de entrada los mismos pasos de caracterización que se aplican durante el entrenamiento.

En el caso de los experimentos configurados con el SDK de Python, se puede habilitar o deshabilitar el valor de caracterización y especificar con más detalle los pasos de caracterización que se van a usar para el experimento. Si usa Azure Machine Learning Studio, vea los [pasos para habilitar la caracterización](how-to-use-automated-ml-for-ml-models.md#customize-featurization).

En la tabla siguiente se muestran los valores aceptados para `featurization` en la [clase AutoMLConfig](/python/api/azureml-train-automl-client/azureml.train.automl.automlconfig.automlconfig):

|Configuración de la caracterización | Descripción|
------------- | ------------- |
|`"featurization": 'auto'`| Especifica que, como parte del preprocesamiento, los [pasos de caracterización y de límite de protección de datos](#featurization) se van a realizar automáticamente. Esta es la configuración predeterminada.|
|`"featurization": 'off'`| Especifica que los pasos de caracterización no se van a realizar automáticamente.|
|`"featurization":`&nbsp;`'FeaturizationConfig'`| Especifica que se van a usar los pasos de caracterización personalizados. [Aprenda a personalizar la caracterización](#customize-featurization).|

<a name="featurization"></a>

## <a name="automatic-featurization"></a>Características automáticas

En la tabla siguiente se resumen las técnicas que se aplican automáticamente a los datos. Estas técnicas se aplican para los experimentos que se configuran mediante el SDK o Studio. Para deshabilitar este comportamiento, establezca `"featurization": 'off'` en el objeto `AutoMLConfig`.

> [!NOTE]
> Si tiene previsto exportar los modelos creados mediante AutoML a un [modelo de ONNX](concept-onnx.md), solo se admiten las opciones de caracterización indicadas con un asterisco ("*") en el formato ONNX. Más información sobre la [conversión de modelos a ONNX](concept-automated-ml.md#use-with-onnx).

|Pasos de caracterización&nbsp;| Descripción |
| ------------- | ------------- |
|**Eliminación de las características de cardinalidad alta o sin variación*** |Permite eliminar estas características de los conjuntos de entrenamiento y validación. Se aplican a características en las que faltan todos los valores, que tienen el mismo valor en todas las filas o que tienen una cardinalidad alta (por ejemplo, hashes, id. o GUID).|
|**Atribución de los valores que faltan*** |Para las características numéricas, se atribuyen con el promedio de los valores de la columna.<br/><br/>Para las características de categorías, se atribuyen con el valor más frecuente.|
|**Generación de características adicionales*** |Para las características de fecha y hora: año, mes, día, día de la semana, día del año, trimestre, semana del año, hora, minuto, segundo.<br/><br/>Para las características de texto: Frecuencia de término basada en unigramas, bigramas y trigramas.|
|**Transformación y codificación***|Permite transformar las características numéricas con pocos valores únicos en características de categorías.<br/><br/>La codificación "one-hot" se utiliza para las características de categoría de cardinalidad baja. La codificación "one-hot-hash" se utiliza para las características de categorías de cardinalidad alta.|
|**Inserciones de palabras**|Caracterizador de texto que convierte los vectores de tokens de texto en vectores de oración mediante un modelo previamente entrenado. El vector de inserción de cada palabra en un documento se agrega con el resto para producir un vector de característica de documento.|
|**Codificaciones de destino**|En el caso de las características de categorías, este paso se asigna a cada categoría con un valor de destino promedio para los problemas de regresión, y a la probabilidad de clase para cada clase para problemas de clasificación. La ponderación basada en la frecuencia y la validación cruzada de k iteraciones se aplican para reducir el ajuste excesivo de la asignación y el ruido que provocan las categorías de datos dispersos.|
|**Codificación de destino de texto**|Para la entrada de texto, se usa un modelo lineal apilado con bolsa de palabras para generar la probabilidad de cada clase.|
|**Ponderación de la evidencia (WoE)**|Calcula WoE como una medida de la correlación de las columnas de categorías para la columna de destino. Se calcula como el registro de la relación de las probabilidades dentro de la clase frente a las probabilidades fuera de la clase. Este paso genera una columna de característica numérica por clase y quita la necesidad de atribuir de forma explícita los valores que faltan y el tratamiento de valores atípicos.|
|**Distancia del clúster**|Entrena un modelo de agrupación en clústeres k-means en todas las columnas numéricas. Genera *k* nuevas características (una característica numérica nueva por grupo), que contienen la distancia de cada muestra hasta el centroide de cada clúster.|

## <a name="data-guardrails"></a>Límites de protección de datos

Los *límites de protección de datos* permiten identificar posibles incidencias con los datos (por ejemplo, valores que faltan o [desequilibrio de clases](concept-manage-ml-pitfalls.md#identify-models-with-imbalanced-data)). También ayudan a tomar acciones correctivas para mejorar los resultados.

Se aplican límites de protección de datos:

- **En el caso de los experimentos de SDK**: cuando se especifican los parámetros `"featurization": 'auto'` o `validation=auto` en el objeto `AutoMLConfig`.
- **En el caso de experimentos de Studio**: cuando se habilita la caracterización automática.

Puede revisar los límites de protección de datos del experimento:

- Mediante el establecimiento de `show_output=True` cuando se envía un experimento con el SDK.

- En Studio, en la pestaña **Límites de protección de datos** de la ejecución del ML automatizado.

### <a name="data-guardrail-states"></a>Estados de límites de protección de datos

Los límites de protección de datos muestran uno de los tres estados siguientes:

|State| Descripción |
|----|---- |
|**Superado**| No se ha detectado ningún problema con los datos y no se requiere ninguna acción por su parte. |
|**Listo**| Los cambios se han aplicado a los datos. Se recomienda revisar las acciones correctivas que ha realizado ML automatizado para asegurarse de que los cambios se alineen con los resultados esperados. |
|**Con alertas**| Se ha detectado una incidencia con los datos, pero no se ha podido resolver. Se recomienda revisar y solucionar la incidencia.|

### <a name="supported-data-guardrails"></a>Límites de protección de datos admitidos

En la tabla siguiente se describen los límites de protección de datos admitidos actualmente, así como los estados asociados que podría ver al enviar el experimento:

Límite de protección|Estado|Condición&nbsp;para&nbsp;el desencadenador
---|---|---
**Atribución de los valores de características que faltan** |Superado <br><br><br> ¡Listo!| No se ha detectado que falten valores de característica en los datos de entrenamiento. Obtenga más información sobre la [imputación de valores que faltan](https://docs.microsoft.com/azure/machine-learning/how-to-use-automated-ml-for-ml-models#advanced-featurization-options). <br><br> Se han detectado valores de característica que faltan en los datos de entrenamiento y se han imputado.
**Control de características de cardinalidad alta** |Superado <br><br><br> ¡Listo!| Se han analizado las entradas y no se han detectado características de cardinalidad alta. <br><br> Se han detectado características de cardinalidad alta en las entradas y se han controlado.
**Control de división de validación** |¡Listo!| La configuración de validación se ha establecido en `'auto'` y los datos de entrenamiento contenían *menos de 20 000 filas*. <br> Todas las iteraciones del modelo entrenado se han validado mediante validación cruzada. Obtenga más información sobre la [validación de datos](https://docs.microsoft.com/azure/machine-learning/how-to-configure-auto-train#train-and-validation-data). <br><br> La configuración de validación se ha establecido en `'auto'` y los datos de entrenamiento contenían *más de 20 000 filas*. <br> Los datos de entrada se han dividido en un conjunto de datos de entrenamiento y un conjunto de datos de validación para comprobar el modelo.
**Detección de equilibrio de clases** |Superado <br><br><br><br><br> Con alertas | Se analizaron las entradas y todas las clases están equilibradas en los datos de entrenamiento. Se considera que un conjunto de datos está equilibrado si todas las clases tienen una representación adecuada en el conjunto de datos según el número y proporción de las muestras. <br><br><br> Se han detectado clases desequilibradas en las entradas. Para corregir el sesgo del modelo, corrija el problema de equilibrio. Obtenga más información sobre [datos desequilibrados](https://docs.microsoft.com/azure/machine-learning/concept-manage-ml-pitfalls#identify-models-with-imbalanced-data).
**Detección de problemas de memoria** |Superado <br><br><br><br> ¡Listo! |<br> Se han analizado los valores seleccionados (horizonte, retardo y ventana con desplazamiento) sin que se hayan detectado incidencias potenciales de memoria insuficiente. Obtenga más información sobre las [configuraciones de previsión](https://docs.microsoft.com/azure/machine-learning/how-to-auto-train-forecast#configure-and-run-experiment) de series temporales. <br><br><br>Se han analizado los valores seleccionados (horizonte, retardo y ventana con desplazamiento) y pueden provocar que el experimento se quede sin memoria. Se han desactivado las configuraciones de ventana con desplazamiento o retardo.
**Detección de frecuencias** |Superado <br><br><br><br> ¡Listo! |<br> Se ha analizado la serie temporal y todos los puntos de datos están alineados con la frecuencia detectada. <br> <br> Se ha analizado la serie temporal y se han detectado puntos de datos que no están alineados con la frecuencia detectada. Estos puntos de datos se quitaron del conjunto de datos. Obtenga más información sobre la [preparación de datos para las previsiones de serie temporal](https://docs.microsoft.com/azure/machine-learning/how-to-auto-train-forecast#preparing-data).

## <a name="customize-featurization"></a>Personalización de la caracterización

Se pueden personalizar los valores de la caracterización para asegurarse de que los datos y las características que se usan a fin de entrenar el modelo de Machine Learning generen predicciones pertinentes.

Para personalizar las caracterizaciones, especifique `"featurization": FeaturizationConfig` en el objeto `AutoMLConfig`. Si usa Azure Machine Learning Studio para el experimento, vea el [artículo de procedimiento](how-to-use-automated-ml-for-ml-models.md#customize-featurization).

Las personalizaciones compatibles incluyen:

|Personalización|Definición|
|--|--|
|**Actualización del propósito de la columna**|Reemplazar el tipo de característica para la columna especificada.|
|**Actualización de parámetros del transformador** |Actualizar los parámetros para el transformador especificado. Actualmente admite *Imputer* (media, más frecuente y mediana) y *HashOneHotEncoder*.|
|**Quitar columnas** |Especifica las columnas que se van a eliminar de la caracterización.|
|**Transformadores de bloque**| Especifica los transformadores de bloque que se van a usar en el proceso de características.|

Cree el objeto `FeaturizationConfig` mediante llamadas API:

```python
featurization_config = FeaturizationConfig()
featurization_config.blocked_transformers = ['LabelEncoder']
featurization_config.drop_columns = ['aspiration', 'stroke']
featurization_config.add_column_purpose('engine-size', 'Numeric')
featurization_config.add_column_purpose('body-style', 'CategoricalHash')
#default strategy mean, add transformer param for for 3 columns
featurization_config.add_transformer_params('Imputer', ['engine-size'], {"strategy": "median"})
featurization_config.add_transformer_params('Imputer', ['city-mpg'], {"strategy": "median"})
featurization_config.add_transformer_params('Imputer', ['bore'], {"strategy": "most_frequent"})
featurization_config.add_transformer_params('HashOneHotEncoder', [], {"number_of_bits": 3})
```

## <a name="next-steps"></a>Pasos siguientes

* Obtenga información sobre cómo configurar los experimentos de ML automatizado:

    * Para obtener una experiencia de codificar por primera vez: [Configuración de experimentos de ML automatizado con el SDK de Azure Machine Learning](how-to-configure-auto-train.md).
    * Para obtener una experiencia sin código o con poco código: [Creación de experimentos de aprendizaje automático automatizado en Azure Machine Learning Studio](how-to-use-automated-ml-for-ml-models.md).

* Obtenga más información sobre [cómo y dónde implementar un modelo](how-to-deploy-and-where.md).

* Obtenga más información sobre los [procedimientos para entrenar un modelo de regresión con aprendizaje automático automatizado](tutorial-auto-train-models.md) o los [procedimientos pata entrenar con aprendizaje automático automatizado en un recurso remoto](how-to-auto-train-remote.md).
