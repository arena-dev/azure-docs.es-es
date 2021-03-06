---
title: 'Conectividad SSL/TLS: Azure Database for MariaDB'
description: Información para configurar Azure Database for MariaDB y las aplicaciones asociadas, a fin de usar correctamente las conexiones SSL
author: ajlam
ms.author: andrela
ms.service: mariadb
ms.topic: conceptual
ms.date: 07/08/2020
ms.openlocfilehash: d207c318a76ec9c75f7c64d25153d1aa415e4f2b
ms.sourcegitcommit: 5cace04239f5efef4c1eed78144191a8b7d7fee8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/08/2020
ms.locfileid: "86143040"
---
# <a name="ssltls-connectivity-in-azure-database-for-mariadb"></a>Conectividad SSL/TLS en Azure Database for MariaDB
Azure Database for MariaDB permite conectar el servidor de bases de datos a las aplicaciones cliente con la Capa de sockets seguros (SSL). Aplicar conexiones SSL entre el servidor de base de datos y las aplicaciones cliente ayuda a proteger contra los ataques de tipo "man in the middle" mediante el cifrado del flujo de datos entre el servidor y la aplicación.

## <a name="default-settings"></a>Configuración predeterminada
De forma predeterminada, el servicio de base de datos debe configurarse para requerir conexiones SSL al conectar con MariaDB.  Se recomienda evitar la desactivación de la opción SSL siempre que sea posible.

Al aprovisionar un nuevo servidor de Azure Database for MariaDB en Azure Portal o con la CLI de Azure, el establecimiento de conexiones SSL está habilitado de forma predeterminada.

Las cadenas de conexión para distintos lenguajes de programación se muestran en Azure Portal. Estas cadenas de conexión incluyen los parámetros SSL que se requieren para conectarse a la base de datos. En Azure Portal, seleccione el servidor. En el encabezado **Configuración**, seleccione las **cadenas de conexión**. El parámetro SSL varía según el conector, por ejemplo, "ssl = true" o "sslmode = require" o "sslmode = required" y otras variaciones.

Para información sobre cómo habilitar o deshabilitar la conexión SSL al desarrollar la aplicación, consulte [Configuración de SSL](howto-configure-ssl.md).

## <a name="tls-enforcement-in-azure-database-for-mariadb"></a>Aplicación de TLS en Azure Database for MariaDB

Azure Database for MariaDB admite el cifrado de los clientes que se conectan al servidor de bases de datos mediante la Seguridad de la capa de transporte (TLS). TLS es un protocolo estándar del sector que garantiza conexiones de red seguras entre el servidor de bases de datos y las aplicaciones cliente, lo que le permite ajustarse a los requisitos de cumplimiento.

### <a name="tls-settings"></a>Configuración de TLS

Azure Database for MariaDB proporciona la capacidad de aplicar la versión de TLS para las conexiones cliente. Para aplicar la versión de TLS, use el valor de la opción **Versión de TLS mínima**. Se permiten los siguientes valores para esta configuración de opción:

|  Versión de TLS mínima             | Versión de TLS compatible con el cliente                |
|:---------------------------------|-------------------------------------:|
| TLSEnforcementDisabled (valor predeterminado) | No se requiere TLS                      |
| TLS1_0                           | TLS 1.0, TLS 1.1, TLS 1.2 y versiones posteriores         |
| TLS1_1                           | TLS 1.1, TLS 1.2 y versiones posteriores              |
| TLS1_2                           | TLS versión 1.2 y posteriores                  |


Por ejemplo, si se establece el valor de la versión de TLS mínima en TLS 1.0, significa que el servidor permitirá conexiones de los clientes que usen TLS 1.0, 1.1 y 1.2 y versiones posteriores. Como alternativa, si se establece en 1.2 significa que solo se permiten conexiones de los clientes que usan TLS 1.2 o versión posterior y se rechazan todas las conexiones con TLS 1.0 y TLS 1.1.

> [!Note] 
> De forma predeterminada, Azure Database for MariaDB no aplica una versión de TLS mínima (opción de configuración `TLSEnforcementDisabled`).
>
> Una vez que se aplica una versión de TLS mínima, esta no se puede deshabilitar posteriormente.

Para obtener información sobre cómo establecer la configuración de TLS para Azure Database for MariaDB, consulte [Configuración de los valores de TLS](howto-tls-configurations.md).

## <a name="next-steps"></a>Pasos siguientes
- Obtenga más información sobre [las reglas de firewall del servidor](concepts-firewall-rules.md)
- Obtenga más información sobre cómo [configurar SSL](howto-configure-ssl.md).
- Obtenga más información sobre [cómo configurar TLS](howto-tls-configurations.md).
