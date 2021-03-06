---
title: Aptitud cognitiva para la detección de idiomas
titleSuffix: Azure Cognitive Search
description: Evalúa el texto no estructurado y devuelve para cada registro un identificador de idioma con una puntuación que indica la solidez del análisis en una canalización de enriquecimiento de inteligencia artificial de Azure Cognitive Search.
manager: nitinme
author: luiscabrer
ms.author: luisca
ms.service: cognitive-search
ms.topic: conceptual
ms.date: 06/17/2020
ms.openlocfilehash: bac2f86f4134cc8d22e9f388b46bc76ab2d0e5ff
ms.sourcegitcommit: 877491bd46921c11dd478bd25fc718ceee2dcc08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85080809"
---
#   <a name="language-detection-cognitive-skill"></a>Aptitud cognitiva para la detección de idiomas

La aptitud **Detección de idioma** detecta el idioma del texto de entrada e informa de un único código de idioma para cada documento enviado en la solicitud. El código de idioma se empareja con una puntuación que indica la intensidad del análisis. Esta aptitud utiliza los modelos de aprendizaje automático proporcionados por [Text Analytics](https://docs.microsoft.com/azure/cognitive-services/text-analytics/overview) en Cognitive Services.

Esta funcionalidad es especialmente útil cuando necesita proporcionar el idioma del texto como entrada para otras aptitudes (por ejemplo, la [aptitud de análisis de opiniones](cognitive-search-skill-sentiment.md) o la [aptitud de división de texto](cognitive-search-skill-textsplit.md)).

La detección de idioma aprovecha las bibliotecas de procesamiento de lenguaje natural de Bing, lo que supera el número de [idiomas y regiones admitidos](https://docs.microsoft.com/azure/cognitive-services/text-analytics/language-support) enumerados para Text Analytics. La lista exacta de idiomas no está publicada, pero incluye todos los idiomas ampliamente hablados, además de variantes, dialectos y algunos idiomas regionales y culturales. Si tiene contenido que se expresa en un idioma que se usa con menos frecuencia, puede [probar Language Detection API](https://westus.dev.cognitive.microsoft.com/docs/services/TextAnalytics.V2.0/operations/56f30ceeeda5650db055a3c7) para ver si devuelve un código. La respuesta para los idiomas que no se pueden detectar es `unknown`.

> [!NOTE]
> A medida que expanda el ámbito aumentando la frecuencia de procesamiento, agregando más documentos o agregando más algoritmos de IA, tendrá que [asociar un recurso facturable de Cognitive Services](cognitive-search-attach-cognitive-services.md). Los cargos se acumulan cuando se llama a las API de Cognitive Services y por la extracción de imágenes como parte de la fase de descifrado de documentos de Azure Cognitive Search. No hay ningún cargo por la extracción de texto de documentos.
>
> La ejecución de aptitudes integradas se cobra según los [precios de pago por uso de Cognitive Services](https://azure.microsoft.com/pricing/details/cognitive-services/) existentes. Los precios de la extracción de imágenes se describen en la [página de precios de Búsqueda cognitiva de Azure](https://azure.microsoft.com/pricing/details/search/).


## <a name="odatatype"></a>@odata.type  
Microsoft.Skills.Text.LanguageDetectionSkill

## <a name="data-limits"></a>Límites de datos
El tamaño máximo de un registro debe tener menos de 50 000 caracteres según la medición de [`String.Length`](https://docs.microsoft.com/dotnet/api/system.string.length). Si tiene que dividir los datos antes de enviarlos a la aptitud de detección de idioma, puede usar la [aptitud de división de texto](cognitive-search-skill-textsplit.md).

## <a name="skill-inputs"></a>Entradas de la aptitud

Los parámetros distinguen mayúsculas de minúsculas.

| Entradas     | Descripción |
|--------------------|-------------|
| `text` | Texto que se va a analizar.|

## <a name="skill-outputs"></a>Salidas de la aptitud

| Nombre de salida    | Descripción |
|--------------------|-------------|
| `languageCode` | El código de idioma ISO 6391 para el idioma identificado. Por ejemplo, "en". |
| `languageName` | El nombre del idioma. Por ejemplo, "inglés". |
| `score` | Un valor entre 0 y 1. La probabilidad de que el lenguaje esté correctamente identificado. La puntuación puede ser inferior a 1 si la oración tiene distintos idiomas.  |

##  <a name="sample-definition"></a>Definición de ejemplo

```json
 {
    "@odata.type": "#Microsoft.Skills.Text.LanguageDetectionSkill",
    "inputs": [
      {
        "name": "text",
        "source": "/document/text"
      }
    ],
    "outputs": [
      {
        "name": "languageCode",
        "targetName": "myLanguageCode"
      },
      {
        "name": "languageName",
        "targetName": "myLanguageName"
      },
      {
        "name": "score",
        "targetName": "myLanguageScore"
      }

    ]
  }
```

##  <a name="sample-input"></a>Entrada de ejemplo

```json
{
    "values": [
      {
        "recordId": "1",
        "data":
           {
             "text": "Glaciers are huge rivers of ice that ooze their way over land, powered by gravity and their own sheer weight. "
           }
      },
      {
        "recordId": "2",
        "data":
           {
             "text": "Estamos muy felices de estar con ustedes."
           }
      }
    ]
```


##  <a name="sample-output"></a>Salida de ejemplo

```json
{
    "values": [
      {
        "recordId": "1",
        "data":
            {
              "languageCode": "en",
              "languageName": "English",
              "score": 1,
            }
      },
      {
        "recordId": "2",
        "data":
            {
              "languageCode": "es",
              "languageName": "Spanish",
              "score": 1,
            }
      }
    ]
}
```


## <a name="error-cases"></a>Casos de error
Si el texto está escrito en un idioma no compatible, se genera un error y no se devuelve ningún identificador de idioma.

## <a name="see-also"></a>Consulte también

+ [Aptitudes integradas](cognitive-search-predefined-skills.md)
+ [Definición de un conjunto de aptitudes](cognitive-search-defining-skillset.md)
