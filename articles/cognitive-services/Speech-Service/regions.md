---
title: 'Regiones: servicio de voz'
titleSuffix: Azure Cognitive Services
description: Una lista de regiones y puntos de conexión disponibles para el servicio de voz, como la conversión de voz a texto, la conversión de texto a voz y la traducción de voz.
services: cognitive-services
author: mahilleb-msft
manager: nitinme
ms.service: cognitive-services
ms.subservice: speech-service
ms.topic: conceptual
ms.date: 11/05/2019
ms.author: panosper
ms.custom: seodec18
ms.openlocfilehash: 27e26bb37b444b49797d46dd4e12b61f8fe11b16
ms.sourcegitcommit: 52d2f06ecec82977a1463d54a9000a68ff26b572
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2020
ms.locfileid: "84782541"
---
# <a name="speech-service-supported-regions"></a>Regiones admitidas del servicio de voz

El servicio Voz permite que la aplicación convierta audio en texto, lleve a cabo la traducción de voz y convertir texto a voz. Este servicio está disponible en varias regiones con puntos de conexión únicos para SDK de Voz y API REST.

El portal de Voz para realizar configuraciones personalizadas a su experiencia de voz para todas las regiones está disponible aquí: https://speech.microsoft.com

En el caso de las invocaciones del servicio de voz, asegúrese de que la llamada coincide con la región de la suscripción.

## <a name="speech-sdk"></a>SDK de voz

En las regiones de [SDK de Voz](speech-sdk.md), las regiones se especifican como una cadena (por ejemplo, como un parámetro `SpeechConfig.FromSubscription` en el SDK de Voz para C#).

### <a name="speech-to-text-text-to-speech-and-translation"></a>Voz a texto, texto a voz y traducción

El portal de personalización de voz está disponible aquí: https://speech.microsoft.com

El servicio de voz está disponible en estas regiones para el **reconocimiento de voz**, la **conversión de texto a voz** y la **traducción**:

[!INCLUDE [](../../../includes/cognitive-services-speech-service-region-identifier.md)]

Si usa el [SDK de Voz](speech-sdk.md), las regiones se especifican mediante el **identificador de región** (por ejemplo, como un parámetro de `SpeechConfig.FromSubscription`). Asegúrese de que la región coincide con la región de la suscripción.

### <a name="intent-recognition"></a>Reconocimiento de la intención

Las regiones disponibles para el **reconocimiento de la intención** mediante el SDK de Voz son las siguientes:

| Región global | Region           | Identificador de región |
| ------------- | ---------------- | -------------------- |
| Asia          | Este de Asia        | `eastasia`           |
| Asia          | Sudeste de Asia   | `southeastasia`      |
| Australia     | Este de Australia   | `australiaeast`      |
| Europa        | Norte de Europa     | `northeurope`        |
| Europa        | Oeste de Europa      | `westeurope`         |
| Norteamérica | Este de EE. UU.          | `eastus`             |
| Norteamérica | Este de EE. UU. 2        | `eastus2`            |
| Norteamérica | Centro-sur de EE. UU. | `southcentralus`     |
| Norteamérica | Centro-Oeste de EE. UU.  | `westcentralus`      |
| Norteamérica | Oeste de EE. UU.          | `westus`             |
| Norteamérica | Oeste de EE. UU. 2        | `westus2`            |
| Sudamérica | Sur de Brasil     | `brazilsouth`        |

Se trata de un subconjunto de las regiones de publicación compatibles con el [servicio Language Understanding (LUIS)](/azure/cognitive-services/luis/luis-reference-regions).

### <a name="voice-assistants"></a>Asistentes de voz

El [SDK de Voz](speech-sdk.md) admite funcionalidades de **asistente de voz** en estas regiones:

| Region         | Identificador de región |
| -------------- | -------------------- |
| Oeste de EE. UU.        | `westus`             |
| Oeste de EE. UU. 2      | `westus2`            |
| Este de EE. UU.        | `eastus`             |
| Este de EE. UU. 2      | `eastus2`            |
| Oeste de Europa    | `westeurope`         |
| Norte de Europa   | `northeurope`        |
| Sudeste de Asia | `southeastasia`      |

### <a name="speaker-recognition"></a>Speaker Recognition

Speaker Recognition actualmente solo está disponible en la región `westus`.

## <a name="rest-apis"></a>API de REST

El servicio Voz también expone puntos de conexión REST para las solicitudes de voz a texto y texto a voz.

### <a name="speech-to-text"></a>Voz a texto

Para obtener la documentación de referencia sobre la opción de voz a texto, consulte las [API de REST de voz a texto](rest-speech-to-text.md).

El punto de conexión de la API REST tiene este formato:

```
https://<REGION_IDENTIFIER>.stt.speech.microsoft.com/speech/recognition/conversation/cognitiveservices/v1
```

Reemplace `<REGION_IDENTIFIER>` por el identificador que coincida con la región de la suscripción en la siguiente tabla:

[!INCLUDE [](../../../includes/cognitive-services-speech-service-region-identifier.md)]

> [!NOTE]
> El parámetro de idioma debe anexarse a la dirección URL para evitar la recepción de errores HTTP 4xx. Por ejemplo, el idioma definido a inglés de Estados Unidos con el punto de conexión del Oeste de EE. UU. es: `https://westus.stt.speech.microsoft.com/speech/recognition/conversation/cognitiveservices/v1?language=en-US`.

### <a name="text-to-speech"></a>Texto a voz

Para obtener documentación de referencia sobre la opción de texto a voz, consulte las [API de REST de texto a voz](rest-text-to-speech.md).

[!INCLUDE [](../../../includes/cognitive-services-speech-service-endpoints-text-to-speech.md)]
