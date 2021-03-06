---
title: Novedades de Text Analytics API
titleSuffix: Text Analytics - Azure Cognitive Services
description: En este artículo se proporciona información sobre las versiones y características nuevas de Text Analytics de Azure Cognitive Services.
services: cognitive-services
author: aahill
manager: nitinme
ms.service: cognitive-services
ms.subservice: text-analytics
ms.topic: conceptual
ms.date: 07/07/2020
ms.author: aahi
ms.openlocfilehash: 3d9fb7f3fa01c06cc778e4062dd1d136e9c6e342
ms.sourcegitcommit: d7008edadc9993df960817ad4c5521efa69ffa9f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/08/2020
ms.locfileid: "86103405"
---
# <a name="whats-new-in-the-text-analytics-api"></a>Novedades de Text Analytics API

Text Analytics API se actualiza constantemente. Para mantenerse al día con los avances recientes, en este artículo se proporciona información sobre las nuevas versiones y características.

## <a name="july-2020"></a>Julio de 2020

### <a name="text-analytics-for-health-container-public-gated-preview"></a>Text Analytics para la versión preliminar pública de contenedor de estado

Text Analytics para el contenedor de estado está ahora en versión preliminar pública, lo que le permite extraer información de texto en inglés no estructurado en documentos clínicos como los formularios de ingesta de pacientes, las notas del doctor, los documentos de investigación y los resúmenes de descarga. Actualmente, no se le facturará el uso de Text Analytics para el contenedor de estado. 

El contenedor ofrece las siguientes características:

* Reconocimiento de entidades con nombre
* Extracción de relaciones
* Vinculación de entidad
* Negación


> [!div class="nextstepaction"]
> [Más información sobre la versión preliminar de Text Analytics para el contenedor de estado](how-tos/text-analytics-for-health.md)

## <a name="may-2020"></a>Mayo de 2020

### <a name="text-analytics-api-v3-general-availability"></a>Disponibilidad general de Text Analytics API v3

Text Analytics API v3 ahora está disponible con carácter general con las siguientes actualizaciones:

* Versión del modelo `2020-04-01`
* Nuevos [límites de datos](concepts/data-limits.md) para cada característica
* [Compatibilidad de idiomas](language-support.md) actualizada para [Análisis de sentimiento (SA) v3](how-tos/text-analytics-how-to-sentiment-analysis.md)
* Punto de conexión independiente para la vinculación de entidad 
* Nueva categoría de entidad "Dirección" en [Reconocimiento de entidades con nombre (NER) v3](how-tos/text-analytics-how-to-entity-linking.md).
* Nuevas subcategorías en NER v3:
   * Ubicación: geográfica
   * Ubicación: estructural
   * Organización: bolsa
   * Organización: médica
   * Organización: deportes
   * Evento: cultural
   * Evento: natural
   * Evento: deportes

Se han agregado las siguientes propiedades en la respuesta JSON:
   * `SentenceText` en Análisis de sentimiento
   * `Warnings` para cada documento 

Se han cambiado los nombres de las siguientes propiedades en la respuesta JSON, donde procedía:

* El nombre de `score` ha cambiado a `confidenceScore`
    * `confidenceScore` tiene dos espacios decimales de precisión. 
* El nombre de `type` ha cambiado a `category`
* El nombre de `subtype` ha cambiado a `subcategory`

[!INCLUDE [v3 region availability](includes/v3-region-availability.md)]

> [!div class="nextstepaction"]
> [Más información sobre Text Analytics API v3](https://westus2.dev.cognitive.microsoft.com/docs/services/TextAnalytics-v3-0/operations/Languages)

### <a name="text-analytics-api-v31-public-preview"></a>Versión preliminar pública de Text Analytics API v3.1
   * Nueva característica de Análisis de sentimiento: [minería de opiniones](how-tos/text-analytics-how-to-sentiment-analysis.md#opinion-mining)
   * Nuevo [filtro de dominio personal (`PII`)](how-tos/text-analytics-how-to-entity-linking.md#named-entity-recognition-versions-and-features) para obtener información de salud protegida (`PHI`).

> [!div class="nextstepaction"]
> [Más información sobre la versión preliminar de Text Analytics API v3.1](https://westcentralus.dev.cognitive.microsoft.com/docs/services/TextAnalytics-v3-1-preview-1/operations/Languages)

## <a name="february-2020"></a>Febrero de 2020

### <a name="sdk-support-for-text-analytics-api-v3-public-preview"></a>Compatibilidad del SDK con la versión preliminar pública de Text Analytics API v3

Como parte de la [versión unificada de Azure SDK](https://techcommunity.microsoft.com/t5/azure-sdk/january-2020-unified-azure-sdk-release/ba-p/1097290), el SDK de Text Analytics API v3 ahora está disponible como versión preliminar pública para los siguientes lenguajes de programación:
   * [C#](https://docs.microsoft.com/azure/cognitive-services/text-analytics/quickstarts/text-analytics-sdk?tabs=version-3&pivots=programming-language-csharp)
   * [Python](https://docs.microsoft.com/azure/cognitive-services/text-analytics/quickstarts/text-analytics-sdk?tabs=version-3&pivots=programming-language-python)
   * [JavaScript (Node.js)](https://docs.microsoft.com/azure/cognitive-services/text-analytics/quickstarts/text-analytics-sdk?tabs=version-3&pivots=programming-language-javascript)
   * [Java](https://docs.microsoft.com/azure/cognitive-services/text-analytics/quickstarts/text-analytics-sdk?tabs=version-3&pivots=programming-language-java)
   
   > [!div class="nextstepaction"]
> [Más información sobre el SDK de Text Analytics API v3](https://docs.microsoft.com/azure/cognitive-services/text-analytics/quickstarts/text-analytics-sdk?tabs=version-3)

### <a name="named-entity-recognition-v3-public-preview"></a>Versión preliminar pública de reconocimiento de entidades con nombre v3

Los tipos de entidad adicionales ahora están disponibles en el servicio de versión preliminar pública de Reconocimiento de entidades con nombre (NER) v3 a medida que se expande la detección de entidades de información general y personal detectada en el texto. Esta actualización presenta [versión de modelo](concepts/model-versioning.md) `2020-02-01`, que incluye:

* Reconocimiento de los siguientes tipos de entidad generales (solo inglés):
    * PersonType
    * Producto
    * Evento
    * Entidad geopolítica (GPE) como subtipo de Ubicación
    * Habilidad

* Reconocimiento de los tipos de entidad de información personal siguientes (solo inglés):
    * Person
    * Organización
    * Edad como subtipo de Cantidad
    * Fecha como subtipo de DateTime
    * Email 
    * Número de teléfono (solo EE. UU.)
    * URL
    * Dirección IP

> [!div class="nextstepaction"]
> [Más información sobre el Reconocimiento de entidades con nombre v3](how-tos/text-analytics-how-to-entity-linking.md#named-entity-recognition-versions-and-features)

### <a name="october-2019"></a>Octubre de 2019

#### <a name="named-entity-recognition-ner"></a>Reconocimiento de entidades con nombre (NER)

* Un [punto de conexión nuevo](https://westus.dev.cognitive.microsoft.com/docs/services/TextAnalytics-v3-0-Preview-1/operations/EntitiesRecognitionPii) para reconocer los tipos de entidad de información personal (solo en inglés).

* Puntos de conexión independientes para el [reconocimiento de entidades](https://westus.dev.cognitive.microsoft.com/docs/services/TextAnalytics-v3-0-Preview-1/operations/EntitiesRecognitionGeneral) y la [vinculación de entidades](https://westus.dev.cognitive.microsoft.com/docs/services/TextAnalytics-v3-0-Preview-1/operations/EntitiesLinking).

* [Versión de modelo](concepts/model-versioning.md) `2019-10-01`, que incluye:
    * Detección expandida y categorización de entidades detectadas en el texto. 
    * Reconocimiento de los siguientes tipos de entidad nuevos:
        * Número de teléfono
        * Dirección IP

La vinculación de entidades admite el inglés y el español. La compatibilidad de idiomas de NER varía según el tipo de entidad.

#### <a name="sentiment-analysis-v3-public-preview"></a>Versión preliminar pública de la versión 3 de Análisis de sentimiento

* Un [nuevo punto de conexión](https://westus.dev.cognitive.microsoft.com/docs/services/TextAnalytics-v3-0-Preview-1/operations/Sentiment) para analizar la opinión.
* [Versión de modelo](concepts/model-versioning.md) `2019-10-01`, que incluye:

    * Importantes mejoras respecto a la precisión y el detalle de la categorización del texto y la puntuación de la API.
    * Etiquetado automático para los distintos sentimientos en el texto.
    * Análisis de sentimiento y salida a nivel de documento y oración. 

Admite inglés (`en`), japonés (`ja`), chino simplificado (`zh-Hans`), chino tradicional (`zh-Hant`), francés (`fr`), italiano (`it`), español (`es`), neerlandés (`nl`), portugués (`pt`) y alemán (`de`) y está disponible en las siguientes regiones: `Australia East`, `Central Canada`, `Central US`, `East Asia`, `East US`, `East US 2`, `North Europe`, `Southeast Asia`, `South Central US`, `UK South`, `West Europe` y `West US 2`. 

> [!div class="nextstepaction"]
> [Más información sobre Análisis de sentimiento v3](how-tos/text-analytics-how-to-sentiment-analysis.md#sentiment-analysis-versions-and-features)

## <a name="next-steps"></a>Pasos siguientes

* [¿Qué es Text Analytics API?](overview.md)  
* [Ejemplos de escenarios de usuario](text-analytics-user-scenarios.md)
* [Análisis de opiniones](how-tos/text-analytics-how-to-sentiment-analysis.md)
* [Detección de idioma](how-tos/text-analytics-how-to-language-detection.md)
* [Reconocimiento de entidades](how-tos/text-analytics-how-to-entity-linking.md)
* [Extracción de frases clave](how-tos/text-analytics-how-to-keyword-extraction.md)
