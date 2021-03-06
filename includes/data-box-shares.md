---
author: alkohli
ms.service: databox
ms.subservice: pod
ms.topic: include
ms.date: 06/05/2020
ms.author: alkohli
ms.openlocfilehash: 7b8ebd085edfdb130f44c477d7697807d349e4e5
ms.sourcegitcommit: 3541c9cae8a12bdf457f1383e3557eb85a9b3187
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2020
ms.locfileid: "86208903"
---
En función de la cuenta de almacenamiento seleccionada, Data Box crea hasta:

* Tres recursos compartidos para cada cuenta de almacenamiento asociada (GPv1 y GPv2).
* Un recurso compartido para Premium Storage.
* Un recurso compartido para una cuenta de Blob Storage.

En los recursos compartidos de blob en bloques y en páginas, las entidades de primer nivel son contenedores y las entidades de segundo nivel son blobs. En los recursos compartidos de Azure Files, las entidades de primer nivel son los recursos compartidos y las entidades de segundo nivel son los archivos.

En la tabla siguiente se muestra la ruta de acceso UNC a los recursos compartidos en la dirección URL de la ruta de acceso de Data Box y Azure Storage donde se cargan los datos. La dirección URL final de la ruta de acceso de Azure Storage se puede derivar a partir de la ruta de acceso UNC al recurso compartido.
 
|                   |                                                            |
|-------------------|--------------------------------------------------------------------------------|
| Blobs en bloques de Azure | <li>Ruta de acceso UNC a recursos compartidos: `\\<DeviceIPAddress>\<StorageAccountName_BlockBlob>\<ContainerName>\files\a.txt`</li><li>Dirección URL de Azure Storage: `https://<StorageAccountName>.blob.core.windows.net/<ContainerName>/files/a.txt`</li> |  
| Blobs en páginas de Azure  | <li>Ruta de acceso UNC a recursos compartidos: `\\<DeviceIPAddres>\<StorageAccountName_PageBlob>\<ContainerName>\files\a.txt`</li><li>Dirección URL de Azure Storage: `https://<StorageAccountName>.blob.core.windows.net/<ContainerName>/files/a.txt`</li>   |  
| Azure Files       |<li>Ruta de acceso UNC a recursos compartidos: `\\<DeviceIPAddres>\<StorageAccountName_AzFile>\<ShareName>\files\a.txt`</li><li>Dirección URL de Azure Storage: `https://<StorageAccountName>.file.core.windows.net/<ShareName>/files/a.txt`</li>        |      

