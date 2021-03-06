---
title: archivo de inclusión
description: archivo de inclusión
services: cosmos-db
author: LuisBosquez
ms.service: cosmos-db
ms.topic: include
ms.date: 04/15/2020
ms.author: lbosq
ms.custom: include file
ms.openlocfilehash: 8d12645bd302a7ea808f13c07e2a72f66846bad7
ms.sourcegitcommit: 23604d54077318f34062099ed1128d447989eea8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/20/2020
ms.locfileid: "85121561"
---
Ahora puede usar la herramienta Explorador de datos en Azure Portal para crear una base de datos y un contenedor de API para MongoDB de Azure Cosmos DB. 

1. Seleccione **Data Explorer** > **Nuevo contenedor**. 
    
    El área **Agregar contenedor** se muestra en el extremo derecho, pero es posible que haya que desplazarse hacia la derecha para verlo.

    :::image type="content" source="./media/cosmos-db-create-collection/azure-cosmosdb-mongodb-data-explorer.png" alt-text="Explorador de datos de Azure Portal, panel Agregar contenedor":::

2. En la página **Agregar contenedor**, especifique la configuración del nuevo contenedor.

    |Configuración|Valor sugerido|Descripción
    |---|---|---|
    |**Identificador de base de datos**|db|Escriba *db* como nombre de la nueva base de datos. Los nombres de base de datos tienen que tener entre 1 y 255 caracteres y no pueden contener `/, \\, #, ?` o espacios finales. Seleccione la opción **Provision database throughput** (Aprovisionar rendimiento de la base de datos) que le permite compartir el rendimiento aprovisionado de la base de datos entre todos los contenedores de esta. Esta opción también le ayudará a reducir los costos. |
    |**Rendimiento**|400|Deje el rendimiento en 400 unidades de solicitud por segundo (RU/s). Si quiere reducir la latencia, puede escalar verticalmente el rendimiento más adelante. También puede elegir el [modo de escalabilidad automática](https://docs.microsoft.com/azure/cosmos-db/provision-throughput-autoscale), lo que le proporcionará un rango de unidades de solicitud que aumentará y disminuirá dinámicamente según sea necesario.| 
    |**Identificador de colección**|coll|Escriba `coll` como nombre del nuevo contenedor. Los identificadores de contenedor tienen los mismos requisitos de caracteres que los nombres de las bases de datos.|
    |**Capacidad de almacenamiento**|Fija (10 GB)|Escriba *Fija (10 GB)* para esta aplicación. Si selecciona *Ilimitada*, tendrá que crear una instancia de `Shard Key`, que todos los elementos que se inserten requerirán.|
    |**Clave de partición**| /_id| El ejemplo que se describe en este artículo no usa una clave de partición, por lo que si se establece en */_id* usará el campo de identificador generado automáticamente como clave de partición. Para más información sobre el particionamiento, que se conoce también como creación de particiones, consulte [Creación de particiones en Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/partitioning-overview)|
        
    Seleccione **Aceptar**. El Explorador de datos muestra la nueva base de datos y el contenedor.
