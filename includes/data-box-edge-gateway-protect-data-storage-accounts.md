---
author: alkohli
ms.service: databox
ms.topic: include
ms.date: 04/16/2019
ms.author: alkohli
ms.openlocfilehash: 9ac9865afe37916f1777d92eab8637884eba0c08
ms.sourcegitcommit: 856db17a4209927812bcbf30a66b14ee7c1ac777
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2020
ms.locfileid: "82562138"
---
Su dispositivo está asociado a una cuenta de almacenamiento que se utiliza como destino para los datos en Azure. El acceso a la cuenta de almacenamiento se controla mediante la suscripción y las dos claves de acceso de almacenamiento de 512 bits asociadas a esa cuenta de almacenamiento.

Una de las claves se utiliza para la autenticación cuando el dispositivo Azure Stack Edge accede a la cuenta de almacenamiento. La otra clave se mantiene en reserva, por lo que puede rotar periódicamente las claves.

Por motivos de seguridad, muchos centros de datos requieren que las claves se roten. Se recomienda seguir estos procedimientos recomendados para la rotación de claves:

- La clave de la cuenta de almacenamiento es similar a la contraseña raíz de la cuenta de almacenamiento. Proteja cuidadosamente la clave de cuenta. No distribuya la contraseña a otros usuarios, no la codifique ni la guarde en cualquier lugar en texto sin formato que sea accesible para otros.
- Vuelva a generar la clave de cuenta mediante Azure Portal si cree que podría encontrarse en peligro. Para obtener más información, consulte [Administración de las claves de acceso de la cuenta de almacenamiento](../articles/storage/common/storage-account-keys-manage.md).
- Periódicamente, el administrador de Azure debe cambiar o volver a generar la clave principal o secundaria mediante la sección Storage de Azure Portal para acceder directamente a la cuenta de almacenamiento.