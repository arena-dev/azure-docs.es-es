---
title: Revisión y publicación de una oferta en el marketplace comercial de Microsoft
description: Use el centro de partners para enviar su oferta a versión preliminar, obtener una versión preliminar de la oferta y, a continuación, publicarla en el marketplace comercial de Microsoft.
ms.reviewer: dannyevers
ms.service: marketplace
ms.subservice: partnercenter-marketplace-publisher
ms.topic: how-to
author: mingshen-ms
ms.author: mingshen
ms.date: 07/05/2020
ms.openlocfilehash: 34e56e5d92526cbf46408c670127e87781e342cd
ms.sourcegitcommit: d7008edadc9993df960817ad4c5521efa69ffa9f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/08/2020
ms.locfileid: "86119742"
---
# <a name="review-and-publish-an-offer-to-commercial-marketplace"></a>Revisión y publicación de una oferta en el marketplace comercial

Este artículo le muestra cómo usar el centro de partners para enviar su oferta a versión preliminar, obtener una versión preliminar de la oferta y, a continuación, publicarla en el marketplace comercial de Microsoft. También se explica cómo comprobar el estado de la publicación a medida que avanza a través de los pasos de publicación. Ya debe haber creado una oferta que quiera publicar.

## <a name="go-to-your-offer-in-commercial-marketplace"></a>Vaya a su oferta en marketplace comercial

1. Inicie sesión en el [Centro de partners](https://partner.microsoft.com/dashboard/home).
1. En el menú de navegación izquierdo, seleccione **Marketplace comercial** > **Información general**.
1. En la pestaña de **Información general**, en **Ofertas**, se muestra uno de los siguientes indicadores de estado en la columna de **Estado** de cada oferta.
 
    | Estado | Descripción |
    | ------------ | ------------- |
    | Borrador | La oferta se ha creado pero no se va a publicar. |
    | Publicación en curso | Se está realizando el proceso de publicación para la oferta. |
    | Atención necesaria | Se ha detectado un problema crítico durante la certificación o durante otra fase de publicación. |
    | Versión preliminar | Nosotros certificamos la oferta, misma que está en espera de la comprobación final del anunciante. Seleccione **Transmitir** para publicar la oferta en vivo. |
    | En vivo | La oferta está activa en Marketplace y los clientes la pueden ver y adquirir. |
    | Detener venta pendiente | El anunciante ha seleccionado "Detener venta" en la oferta o el plan, pero aún no se ha completado la acción. |
    | No disponible en el marketplace | Una oferta publicada anteriormente se ha quitado del Marketplace. |
    |||

4. En la columna de **Alias de la oferta**, seleccione la oferta de la que quiere obtener una versión preliminar y publicarla.

## <a name="submit-your-offer-to-preview"></a>Envío de la oferta para tener una versión preliminar

1. Para enviar la oferta a versión preliminar, seleccione **Revisar y publicar** en la esquina superior derecha del portal. Se abrirá la página **Revisar y publicar**.
1. Asegúrese de que la columna de **Estado** de cada página indica **Completa**. Los tres estados posibles que se muestran son:
   - **No iniciada**: la página no se ha modificado y se debe completar.
   - **Incompleta**: falta información necesaria en la página o hay errores que deben corregirse. Tendrá que volver a la página anterior y actualizarla.
   - **Completa**: la página está completa. Se han proporcionado todos los datos necesarios y no hay ningún error.
1. Si alguna de las páginas tiene un Estado que no sea **Completa**, en la columna de **Página**, seleccione el nombre de la página, corrija el problema, guarde la página y, a continuación, seleccione **Revisar y publicar** de nuevo para volver a esta página.
1. Después de completar todas las páginas, en el cuadro de **Notas para la certificación**, proporcione instrucciones de prueba al equipo de certificación para asegurarse de que la aplicación se ha probado correctamente. Proporcione cualquier nota complementaria que resulte útil para entender la aplicación.
1. Para enviar la oferta para su publicación, seleccione **Publicar**. Aparece la página de **Información general de la oferta** y muestra el estado de la publicación.

## <a name="validation-and-publishing-steps"></a>Pasos de validación y publicación

Después de seleccionar **Publicar**, los procesos de validación y publicación continúan en orden. En esta tabla se muestra el proceso de publicación más común:

| Fase | Qué ocurre | 
| ------------ | ------------- | ------------- |
| Validación automatizada | Procesamos un conjunto de validaciones automatizadas. | 
| Certificación | Llevamos a cabo validaciones manuales. | 
| Creación de versión preliminar | La página del anuncio de la versión preliminar de la oferta está disponible para cualquiera que tenga el vínculo de versión preliminar. Si su oferta se va a vender a través de Microsoft (transactable), solo la audiencia que haya especificado en la página de **Audiencia de versión preliminar** de su oferta puede comprar y obtener acceso a la oferta para realizar pruebas. | 
| Aprobación del publicador | Le enviaremos un correo electrónico con una solicitud para que pueda obtener una versión preliminar y aprobar su oferta. | 
| Publicar | Ejecutamos una serie de pasos para comprobar que la oferta de versión preliminar se publica en directo en el marketplace comercial. | 
|||

## <a name="automated-validation-phase"></a>Fase de validación automatizada

El primer paso del proceso de publicación es realizar un conjunto de validaciones automatizadas. Cada paso de validación corresponde a una característica que eligió al crear la oferta. Cada comprobación de validación se debe completar antes de que la oferta pueda avanzar al siguiente paso del proceso de publicación.

- **Configuración del flujo de compra de la oferta (<10 min)**

   En este paso nos aseguramos de que la oferta se cumple cuando los clientes la compran mediante Azure Portal. Este paso solo es aplicable para las ofertas de venta mediante Microsoft.
- **Validación de los datos de la versión de prueba (~5 min)**

   En este paso validamos los datos que proporcionó en la página de configuración técnica de la oferta. La funcionalidad de la versión de prueba se ha probado y aprobado. Este paso solo es aplicable para las ofertas con una versión de prueba habilitada.

-   **Aprovisionamiento de la versión de prueba (~30 min)**

    En este paso, después de validar los datos y la funcionalidad de la versión de prueba en el paso anterior, implementamos y replicamos las instancias de la versión de prueba para que estén listas para que las usen los clientes. Este paso solo es aplicable para las ofertas con una versión de prueba habilitada.

-   **Registro y validación de la administración de clientes potenciales (<15 min)**

    En este paso confirmamos que su sistema de administración de clientes potenciales puede recibir clientes potenciales en función de los detalles que proporcionó en la página de **Configuración de la oferta**. Este paso solo es aplicable para las ofertas con la administración de clientes potenciales habilitada.

## <a name="certification-phase"></a>Fase de certificación

Antes de que se publiquen, se deben certificar las ofertas enviadas a marketplace comercial. Las ofertas enviadas se someten a pruebas rigurosas, algunas automáticas y otras manuales. Revise las [Directivas de certificación de marketplace comercial](https://aka.ms/commercial-marketplace-certification-policies) para obtener más información.

### <a name="types-of-validation-that-take-place-during-certification"></a>Tipos de validación que se realizan durante la certificación
El proceso de certificación incluye tres niveles de validación para cada oferta enviada.
-   Aptitud de la empresa anunciante
-   Validación del contenido
-   Validación técnica

#### <a name="publisher-business-eligibility"></a>Aptitud de la empresa anunciante
Con cada tipo de oferta se comprueba un conjunto de criterios de aptitud básicos que el anunciante debe cumplir. Estos pueden incluir el estado de MPN del anunciante, las competencias y su grado, y demás.

#### <a name="content-validation"></a>Validación del contenido

Se comprueba la calidad y pertinencia de la información que se introdujo al crear la oferta. Con estas comprobaciones se revisan las entradas de los detalles del anuncio en marketplace, los precios, la disponibilidad, los planes asociados, y demás. Para cumplir los criterios del anuncio de Azure Marketplace y Microsoft AppSource, validamos que la oferta incluya:
-   un título que describa la oferta con precisión
-   descripciones bien escritas que proporcionen información general detallada y una propuesta de valor
-   capturas de pantallas y vídeos de calidad
-   una explicación de cómo la oferta usa las plataformas y las herramientas de Microsoft.

Para más información sobre los criterios de validación del contenido, consulte las [directivas generales de los anuncios](https://aka.ms/commercial-marketplace-certification-policies#100-general).

#### <a name="technical-validation"></a>Validación técnica
Durante la validación técnica, la oferta (paquete o binario) se somete a las siguientes comprobaciones.
-   Examen en busca de malware
-   Monitorización de las llamadas de red
-   Análisis de los paquetes
-   Análisis exhaustivo de la funcionalidad de la oferta

La oferta se prueba en varias plataformas y con distintas versiones para garantizar su solidez.

### <a name="certification-failure-report"></a>Informe de error de certificación

Si se produce algún error en las comprobaciones del anuncio, técnicas o de las directivas, o si no es apto para enviar una oferta de ese tipo, se genera un informe de error de certificación, que se le envía por correo electrónico.

Este informe contiene descripciones de las directivas con error, junto con notas de revisión. Revise el informe del correo electrónico, aborde los problemas mediante la actualización de la oferta como sea necesario y vuelva a enviar esta a través del [Portal de marketplace comercial](https://partner.microsoft.com/dashboard/commercial-marketplace/offers) del centro de partners. Puede volver a enviar las ofertas las veces que sea necesario hasta que se supere la certificación.

## <a name="preview-creation-phase"></a>Fase de versión preliminar

Durante la fase de creación de la versión preliminar, creamos una versión de la oferta que será accesible solo a la audiencia que especificó en la página de **Audiencia de versión preliminar** de su oferta, si la hay. La versión preliminar de la oferta no estará disponible para ningún usuario ajeno a la versión preliminar de la audiencia hasta que publique la oferta en directo.

> [!NOTE]
> No utilice la audiencia de versión preliminar para otorgar visibilidad sobre la oferta a personas ajenas a la organización. Use la opción de Oferta privada en su lugar. En este momento, la oferta no se ha probado y validado por completo y no está lista para distribuirse fuera de la organización. 

## <a name="publisher-signoff-phase"></a>Fase de aprobación del publicador

Cuando la oferta esté lista para su revisión y firma, le enviaremos un correo electrónico para solicitarle que revise y apruebe la versión preliminar de su oferta. También puede actualizar la página de **Información general de la oferta** en el explorador para ver si su oferta ha alcanzado la fase de aprobación del publicador. Si es así, el botón **Transmitir en directo** y los vínculos de versión preliminar estarán disponibles.

En la captura de pantalla siguiente se muestra la página de **Información general de la oferta** para una oferta de SaaS. Los pasos de validación que verá en esta página varían en función del tipo de oferta y de las selecciones realizadas al crear la oferta.

![Muestra la página de Información general de la oferta para una oferta en el Centro de partners. Se muestran los vínculos de versión preliminar y el botón de Transmitir en directo.](./partner-center-portal/media/publish-status-publisher-signoff.png)

**Para obtener una versión preliminar y aprobación de la oferta**
1. Para obtener una versión preliminar de la oferta en la página **Información general de la oferta**, seleccione el vínculo del botón **Transmitir en directo**.
   > [!NOTE]
   > Habrá un vínculo para la versión preliminar de AppSource, la versión preliminar de Azure Marketplace o ambos según las opciones que elija al crear la oferta. Si elige vender la oferta mediante Microsoft, cualquiera que sea agregado a la audiencia de versión preliminar podrá probar la adquisición y la implementación de esta para asegurarse de que cumple sus requisitos durante esta etapa.

1. Si desea realizar cambios después obtener la versión preliminar de la oferta, puede editarla y volver a enviar la publicación para una nueva versión preliminar. Para obtener más información, consulte [Actualización de una oferta existente en el marketplace comercial](./partner-center-portal/update-existing-offer.md).

1. Después de aprobar la versión preliminar, para publicar su oferta en el marketplace comercial, seleccione **Transmitir en directo**.
   > [!TIP]
   > Si la oferta ya está activa y disponible para el público en Marketplace, las actualizaciones que realice no se activarán hasta que seleccione **Transmitir en directo**.

## <a name="publish-phase"></a>Fase de publicación

Ahora que ha decidido transmitir en directo la oferta, de modo que esté disponible en el marketplace comercial, hay una serie de comprobaciones de validación finales que realizamos para garantizar que la oferta activa está configurada igual que en la versión preliminar.

-   **Configuración del flujo de compra de la oferta (>10 min)**

    En este paso nos aseguramos de que la oferta se cumple cuando los clientes la compran mediante Azure Portal. Este paso solo es aplicable para las ofertas de venta mediante Microsoft.
-   **Validación de los datos de la versión de prueba (~5 min)**

    En este paso validamos los datos que proporcionó en la página de configuración técnica de la oferta. La funcionalidad de la versión de prueba se ha probado y aprobado. Este paso solo es aplicable para las ofertas con una versión de prueba habilitada.

-   **Aprovisionamiento de la versión de prueba (~30 min)**

      En este paso implementamos y replicamos instancias de la versión de prueba para que estén listas para que las usen los clientes. Este paso solo es aplicable para las ofertas con una versión de prueba habilitada.
-   **Registro y validación de la administración de clientes potenciales (>15 min)**

    En este paso confirmamos que su sistema de administración de clientes potenciales puede recibir clientes potenciales en función de los detalles proporcionados en la página de **Configuración de la oferta** de la oferta. Este paso solo es aplicable para las ofertas con la administración de clientes potenciales habilitada.

-   **Publicación final (>30 minutos)**

    En este paso nos aseguramos de que la oferta esté públicamente disponible en Marketplace.

Una vez completadas estas comprobaciones de validación, la oferta estará activa en marketplace.

## <a name="next-step"></a>Paso siguiente

[Acceso a los informes de análisis de marketplace comercial en el Centro de partners](./partner-center-portal/analytics.md)