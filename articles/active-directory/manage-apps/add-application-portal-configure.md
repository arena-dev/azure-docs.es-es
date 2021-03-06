---
title: 'Inicio rápido: Configuración de las propiedades de una aplicación en el inquilino de Azure Active Directory (Azure AD)'
description: Este inicio rápido usa Azure Portal para configurar una aplicación que se ha registrado con su inquilino de Azure Active Directory (Azure AD).
services: active-directory
author: kenwith
manager: celestedg
ms.service: active-directory
ms.subservice: app-mgmt
ms.topic: quickstart
ms.workload: identity
ms.date: 10/29/2019
ms.author: kenwith
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8418a45c9eba596339999c2bddf937a516d3e2d9
ms.sourcegitcommit: f844603f2f7900a64291c2253f79b6d65fcbbb0c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2020
ms.locfileid: "86223353"
---
# <a name="quickstart-configure-properties-for-an-application-in-your-azure-active-directory-azure-ad-tenant"></a>Inicio rápido: Configuración de las propiedades de una aplicación en el inquilino de Azure Active Directory (Azure AD)

En el inicio rápido anterior, agregó una aplicación a su inquilino de Azure Active Directory (Azure AD). Cuando se agrega una aplicación, se permite que el inquilino de Azure AD sepa que es el proveedor de identidades de la aplicación. Ahora configurará algunas de las propiedades de la aplicación.
 
## <a name="prerequisites"></a>Requisitos previos

Para configurar las propiedades de una aplicación en el inquilino de Azure AD, necesita:

- Una cuenta de Azure con una suscripción activa. [Cree una cuenta gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F).
- Uno de los siguientes roles: Administrador global, Administrador de aplicaciones en la nube, Administrador de aplicaciones o Propietario de la entidad de servicio.
- Opcional: Haber finalizado el inicio rápido de [Visualización de las aplicaciones](view-applications-portal.md).
- Opcional: Haber finalizado el inicio rápido de [Incorporación de una aplicación](add-application-portal.md).

>[!IMPORTANT]
>Para probar los pasos de este inicio rápido, use un entorno que no sea de producción.

## <a name="configure-app-properties"></a>Configuración de las propiedades de una aplicación

Cuando termine de agregar una aplicación al inquilino de Azure AD, aparecerá la página de información general. Si está configurando una aplicación que ya se había agregado, consulte el primer inicio rápido. Este le guía a través de la visualización de las aplicaciones agregadas a su inquilino. 

Para editar las propiedades de la aplicación:

1. En el portal de Azure AD, seleccione **Aplicaciones empresariales**. Después, busque y seleccione la aplicación que desea configurar.
1. En la sección **Administrar**, seleccione **Propiedades** para abrir el panel **Propiedades** para editarlo.

    ![Captura de la pantalla Propiedades que muestra las propiedades de la aplicación editables.](media/add-application-portal/edit-properties.png)

1. Dedique un momento a comprender las opciones disponibles para su configuración:
    - La opción **¿Habilitado para que los usuarios inicien sesión?** determina si los usuarios asignados a la aplicación pueden iniciar sesión.
    - La opción **¿Asignación de usuarios?** determina si los usuarios que no están asignados a la aplicación pueden iniciar sesión.
    - La opción **¿Es visible para los usuarios?** determina si los usuarios asignados a una aplicación pueden verla en el [panel de acceso](https://myapps.microsoft.com) y en el iniciador de Office 365. (Vea el menú de gofres en la esquina superior izquierda de un sitio web de Office 365 o Microsoft 365).
1. Use las siguientes tablas para ayudarle a elegir las opciones que más se ajusten a sus necesidades.

   - Comportamiento para los usuarios *asignados*:

       | Propiedad de la aplicación | Propiedad de la aplicación | Propiedad de la aplicación | Experiencia del usuario asignado | Experiencia del usuario asignado |
       |---|---|---|---|---|
       | ¿Está habilitado para que los usuarios inicien sesión? | ¿Se requiere la asignación de usuarios? | ¿Es visible para los usuarios? | ¿Pueden los usuarios asignados iniciar sesión? | ¿Pueden ver los usuarios asignados la aplicación?* |
       | Sí | Sí | Sí | Sí | Sí  |
       | Sí | Sí | No  | Sí | No   |
       | Sí | No  | Sí | Sí | Sí  |
       | Sí | No  | No  | Sí | No   |
       | No  | Sí | Sí | No  | No   |
       | No  | Sí | No  | No  | No   |
       | No  | No  | Sí | No  | No   |
       | No  | No  | No  | No  | No   |

   - Comportamiento para los usuarios *no asignados*:

       | Propiedad de la aplicación | Propiedad de la aplicación | Propiedad de la aplicación | Experiencia del usuario no asignado | Experiencia del usuario no asignado |
       |---|---|---|---|---|
       | ¿Está habilitado para que los usuarios inicien sesión? | ¿Se requiere la asignación de usuarios? | ¿Es visible para los usuarios? | ¿Pueden iniciar sesión los usuarios no asignados? | ¿Pueden ver la aplicación los usuarios no asignados?* |
       | Sí | Sí | Sí | No  | No   |
       | Sí | Sí | No  | No  | No   |
       | Sí | No  | Sí | Sí | No   |
       | Sí | No  | No  | Sí | No   |
       | No  | Sí | Sí | No  | No   |
       | No  | Sí | No  | No  | No   |
       | No  | No  | Sí | No  | No   |
       | No  | No  | No  | No  | No   |

     ¿*Puede el usuario ver la aplicación en el panel de acceso y el iniciador de aplicaciones de Office 365?

## <a name="use-a-custom-logo"></a>Uso de un logotipo personalizado

Para usar un logotipo personalizado:

1. Cree un logotipo de 215 por 215 píxeles y guárdelo en formato .png.
1. En el portal de Azure AD, seleccione **Aplicaciones empresariales**. Después, busque y seleccione la aplicación que desea configurar.
1. En la sección **Administrar**, seleccione **Propiedades** para abrir el panel **Propiedades** para editarlo. 
1. Seleccione el icono para cargar el logotipo.
1. Cuando haya terminado, seleccione **Guardar**.

    ![Captura de la pantalla Propiedades que muestra cómo cambiar el logotipo.](media/add-application-portal/change-logo.png)

   > [!NOTE]
   > La miniatura que se muestra en este panel de **Propiedades** no se actualiza inmediatamente. Puede cerrar y volver a abrir el panel **Propiedades** para ver el icono actualizado.

## <a name="next-steps"></a>Pasos siguientes

Ahora que ha configurado las propiedades de una aplicación puede continuar con la configuración del inicio de sesión único.

- [Configuración del inicio de sesión único](add-application-portal-setup-sso.md)
- [Eliminación de una aplicación](delete-application-portal.md)