---
title: Configuración de imágenes de Azure Marketplace en Azure DevTest Labs
description: Configuración de las imágenes de Azure Marketplace que se pueden usar al crear una máquina virtual en Azure DevTest Labs
ms.topic: article
ms.date: 06/26/2020
ms.openlocfilehash: 9fdb4e3a888e876f91b8af2e4854a9c101eea45c
ms.sourcegitcommit: 877491bd46921c11dd478bd25fc718ceee2dcc08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85482724"
---
# <a name="configure-azure-marketplace-image-settings-in-azure-devtest-labs"></a>Configuración de imágenes de Azure Marketplace en Azure DevTest Labs
DevTest Labs admite la creación de máquinas virtuales basadas en imágenes de Azure Marketplace, en función de cómo se hayan configurado las imágenes de Azure Marketplace para usarlas en el laboratorio. En este artículo se muestra cómo especificar qué imágenes de Azure Marketplace se pueden utilizar al crear máquinas virtuales en un laboratorio, si se puede usar alguna. Esto garantiza que el equipo solo tiene acceso a las imágenes de Marketplace que necesitan. 

## <a name="select-which-azure-marketplace-images-are-allowed-when-creating-a-vm"></a>Elección de las imágenes de Azure Marketplace que se permiten al crear una máquina virtual
1. Inicie sesión en [Azure Portal](https://go.microsoft.com/fwlink/p/?LinkID=525040).
2. Seleccione **Todos los servicios** y, luego, **DevTest Labs** en la lista.
3. En la lista de laboratorios, seleccione el laboratorio que desee. 
4. En la hoja del laboratorio, seleccione **Directivas y configuración**.
5. En la hoja **Configuration and policies** (Directivas y configuración) de **Virtual Machine Bases** (Bases de datos de las máquinas virtuales), seleccione **Marketplace images** (Imágenes de Marketplace).
6. Especifique si desea que todas las imágenes cualificadas de Azure Marketplace estén disponibles para su uso como base de una nueva máquina virtual. Si selecciona **Sí**, se permitirán en el laboratorio todas las imágenes de Azure Marketplace que cumplan los criterios siguientes:
   
   * La imagen crea una única máquina virtual **y**
   * La imagen utiliza Azure Resource Manager para aprovisionar máquinas virtuales **y**
   * La imagen no requiere la compra de un plan de licencias adicional.
     
     Si desea que no se permitan imágenes o desea especificar las imágenes que se pueden utilizar, seleccione **No**.
     
     ![Opción para permitir que todas las imágenes de Marketplace se usen como imágenes base para las máquinas virtuales](./media/devtest-lab-configure-marketplace-images/allow-all-marketplace-images.png)
7. Si ha seleccionado **No** en el paso anterior, se habilita la casilla **Allowed images/Select all** (Imágenes permitidas/seleccionar todas). 
   Puede utilizar esta opción junto con el cuadro de búsqueda para seleccionar o anular la selección de todos los elementos que se muestran en la lista rápidamente.
   * Seleccione individualmente las imágenes de Azure Marketplace que desea permitir para la creación de máquinas virtuales. Para ello, active la casilla correspondiente a cada imagen.
   * No seleccione nada en la lista si no desea permitir que las imágenes de Azure Marketplace se usen en el laboratorio.
   
     ![Puede especificar qué imágenes de Azure Marketplace se pueden usar como imágenes base para las máquinas virtuales](./media/devtest-lab-configure-marketplace-images/select-marketplace-images.png)

[!INCLUDE [devtest-lab-try-it-out](../../includes/devtest-lab-try-it-out.md)]

## <a name="next-steps"></a>Pasos siguientes
Una vez que haya configurado cómo se permiten las imágenes de Azure Marketplace al crear una máquina virtual, el siguiente paso es [agregar una máquina virtual al laboratorio](devtest-lab-add-vm.md).

