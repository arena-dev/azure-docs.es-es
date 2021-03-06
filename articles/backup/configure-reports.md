---
title: Configuración de informes de Azure Backup
description: Configure y vea informes para Azure Backup mediante Log Analytics y libros de Azure
ms.topic: conceptual
ms.date: 02/10/2020
ms.openlocfilehash: 20dcf7f3f9bbc5626c4a05ef064203b3ae5020cd
ms.sourcegitcommit: 877491bd46921c11dd478bd25fc718ceee2dcc08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "84484977"
---
# <a name="configure-azure-backup-reports"></a>Configuración de informes de Azure Backup

Un requisito común para los administradores de copias de seguridad es obtener conclusiones sobre las copias de seguridad, en función de datos que abarcan un largo período de tiempo. Entre los casos de uso de esta solución se incluyen:

- Asignación y previsión del almacenamiento en la nube consumido.
- Auditoría de copias de seguridad y restauraciones.
- Identificación de las tendencias clave con diferentes niveles de granularidad.

En la actualidad, Azure Backup proporciona una solución de informes que usa [registros de Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/log-query/get-started-portal) y [libros de Azure](https://docs.microsoft.com/azure/azure-monitor/platform/workbooks-overview). Estos recursos le ayudan a obtener mejores conclusiones sobre las copias de seguridad en todo el conjunto de copias de seguridad. En este artículo se explica cómo configurar y ver informes de Azure Backup.

## <a name="supported-scenarios"></a>Escenarios admitidos

- Los informes de Backup se admiten en máquinas virtuales de Azure, SQL en máquinas virtuales de Azure, SAP HANA en máquinas virtuales de Azure, el agente de Microsoft Azure Recovery Services (MARS), Microsoft Azure Backup Server (MABS) y System Center Data Protection Manager (DPM). Para la copia de seguridad de recursos compartidos de Azure, se muestran los datos de todos los registros creados el 1 de junio de 2020 o después de esa fecha.
- En las cargas de trabajo de DPM, se admiten los informes de Backup para la versión 5.1.363.0 de DPM y posteriores, y la versión 2.0.9127.0 del agente y posteriores.
- En las cargas de trabajo de MABS, se admiten los informes de Backup para la versión 13.0.415.0 de MABS y posteriores, y la versión 2.0.9170.0 del agente y posteriores.
- Los informes de Backup se pueden ver en todos los elementos de copia de seguridad, almacenes, suscripciones y regiones, siempre y cuando sus datos se envíen a un área de trabajo de Log Analytics a la que el usuario tenga acceso. Para ver los informes de un conjunto de almacenes, solo necesita tener acceso de lectura al área de trabajo de Log Analytics a la que los almacenes envían sus datos. No es necesario que tenga acceso a los almacenes individuales.
- Si es usuario de [Azure Lighthouse](https://docs.microsoft.com/azure/lighthouse/) con acceso delegado a las suscripciones de los clientes, puede usar estos informes con Azure Lighthouse para ver los informes de todos los inquilinos.
- Actualmente, los datos se pueden ver en Informes de Backup en un máximo de 100 áreas de trabajo de Log Analytics (entre inquilinos).
- Los datos de los trabajos de copia de seguridad de registros no se muestran actualmente en los informes.

## <a name="get-started"></a>Introducción

Siga estos pasos para empezar a usar los informes.

### <a name="1-create-a-log-analytics-workspace-or-use-an-existing-one"></a>1. Creación de un área de trabajo de Log Analytics o uso de una existente

Configure una o varias áreas de trabajo de Log Analytics para almacenar los datos de los informes de Backup. La ubicación y la suscripción donde se puede crear esta área de trabajo de Log Analytics es independiente de la ubicación y la suscripción donde existen los almacenes.

Para configurar un área de trabajo de Log Analytics, consulte [Creación de un área de trabajo de Log Analytics en Azure Portal](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace).

De forma predeterminada, los datos de un área de trabajo de Log Analytics se conservan durante 30 días. Para ver los datos de un horizonte temporal más largo, cambie el período de retención del área de trabajo de Log Analytics. Para cambiar el período de retención, consulte [Administración del uso y los costos con los registros de Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/platform/manage-cost-storage).

### <a name="2-configure-diagnostics-settings-for-your-vaults"></a>2. Configuración de los valores de diagnóstico para los almacenes

Los recursos de Azure Resource Manager como, por ejemplo, el almacén de Recovery Services, registran información acerca de las operaciones programadas y las operaciones desencadenadas por el usuario como datos de diagnóstico.

En la sección de supervisión del almacén de Recovery Services, seleccione **Configuración de diagnóstico** y especifique el destino de los datos de diagnóstico del almacén de Recovery Services. Para obtener más información sobre el uso de eventos de diagnóstico, consulte [Uso de la configuración de diagnósticos para almacenes de Recovery Services](https://docs.microsoft.com/azure/backup/backup-azure-diagnostic-events).

![Panel Configuración de diagnóstico](./media/backup-azure-configure-backup-reports/resource-specific-blade.png)

Azure Backup también proporciona una definición de Azure Policy integrada que automatiza la configuración de diagnóstico para todos los almacenes de un ámbito determinado. Para obtener información sobre cómo usar esta directiva, consulte [Configuración de los valores de diagnóstico del almacén a gran escala](https://docs.microsoft.com/azure/backup/azure-policy-configure-diagnostics).

> [!NOTE]
> Después de haber configurado el diagnóstico, las inserciones de datos iniciales pueden tardar hasta 24 horas en completarse. Después de que los datos comiencen a fluir al área de trabajo de Log Analytics, es posible que no pueda ver los datos en los informes inmediatamente, ya que los datos para el día parcial actual no se muestran en los informes. Para obtener más información, consulte [Convenciones usadas en los informes de copia de seguridad](https://docs.microsoft.com/azure/backup/configure-reports#conventions-used-in-backup-reports). Se recomienda empezar a ver los informes dos días después de configurar los almacenes para enviar datos a Log Analytics.

#### <a name="3-view-reports-in-the-azure-portal"></a>3. Visualización de los informes en Azure Portal

Después de haber configurado los almacenes para enviar datos a Log Analytics, consulte los informes de Backup en el panel de cualquier almacén y seleccione **Informes de Backup**.

![Panel del almacén](./media/backup-azure-configure-backup-reports/vault-dashboard.png)

Seleccione este vínculo para abrir el libro del informe de Backup.

> [!NOTE]
>
> - Actualmente, la carga inicial del informe puede tardar hasta 1 minuto.
> - El almacén de Recovery Services es simplemente un punto de entrada para los informes de Backup. Después de que el libro del informe de Backup se abra en el panel de un almacén, seleccione el conjunto adecuado de áreas de trabajo de Log Analytics para ver los datos agregados entre todos sus almacenes.

El informe contiene varias pestañas:

- **Resumen**: Use esta pestaña para obtener información general sobre el conjunto de copias de seguridad. Puede obtener una vista rápida del número total de elementos de copia de seguridad, el almacenamiento en la nube total consumido, el número de instancias protegidas y la tasa de éxito de los trabajos por tipo de carga de trabajo. Para obtener información más detallada sobre un tipo de artefacto de copia de seguridad específico, vaya a las pestañas correspondientes.

   ![Pestaña Resumen](./media/backup-azure-configure-backup-reports/summary.png)

- **Elementos de copia de seguridad**: Use esta pestaña para ver información y tendencias sobre el almacenamiento en la nube consumido en el nivel de elemento de Backup. Por ejemplo, si usa la copia de seguridad de SQL en VM de Azure, puede ver el almacenamiento en la nube consumido por cada base de datos SQL de la que se realiza una copia de seguridad. También puede ver los datos de los elementos de copia de seguridad de un estado de protección determinado. Por ejemplo, al seleccionar el icono **Protección detenida** en la parte superior de la pestaña, se filtran todos los widgets debajo para mostrar solo los datos de los elementos de Backup en estado de Protección detenida.

   ![Pestaña Elementos de copia de seguridad](./media/backup-azure-configure-backup-reports/backup-items.png)

- **Uso** Use esta pestaña para ver los parámetros de facturación principales de las copias de seguridad. La información que se muestra en esta pestaña corresponde al nivel de entidad de facturación (contenedor protegido). Por ejemplo, en el caso de que se realice una copia de seguridad de un servidor de DPM en Azure, puede ver la tendencia de las instancias protegidas y el almacenamiento en la nube consumido para el servidor de DPM. Del mismo modo, si usa SQL en Azure Backup o SAP HANA en Azure Backup, esta pestaña proporciona información relacionada con el uso en el nivel de la máquina virtual en la que se encuentran estas bases de datos.

   ![Pestaña Uso](./media/backup-azure-configure-backup-reports/usage.png)

> [!NOTE]
> En el caso de las cargas de trabajo de DPM, los usuarios pueden ver una pequeña diferencia (del orden de 20 MB por servidor DPM) entre los valores de uso mostrados en los informes en comparación con el valor de uso agregado, tal como se muestra en la pestaña Información general del almacén de Recovery Services. Esta diferencia se tiene en cuenta por el hecho de que cada servidor DPM que se está registrando para la copia de seguridad tiene un origen de datos "Metadata" asociado que no aparece como un artefacto para la creación de informes.

- **Trabajos**: Use esta pestaña para ver tendencias de ejecución prolongada de los trabajos, como el número de trabajos con errores por día y las causas principales de los errores de los trabajos. Puede ver esta información en un nivel agregado y en el nivel de elemento de Backup. Seleccione un elemento de Backup determinado en una cuadrícula para ver información detallada sobre cada trabajo que se desencadenó en ese elemento de Backup en el intervalo de tiempo seleccionado.

   ![Pestaña Trabajos](./media/backup-azure-configure-backup-reports/jobs.png)

- **Directivas**: Use esta pestaña para ver información sobre todas las directivas activas, como el número de elementos asociados y el almacenamiento en la nube total consumido por los elementos de los que se ha realizado una copia de seguridad por una directiva determinada. Seleccione una directiva determinada para ver información sobre cada uno de los elementos de Backup asociados.

   ![Pestaña Directivas](./media/backup-azure-configure-backup-reports/policies.png)

## <a name="export-to-excel"></a>Exportación a Excel

Seleccione el botón de flecha abajo situado en la parte superior derecha de cualquier widget, como una tabla o un gráfico, para exportar el contenido de ese widget como hoja de Excel, tal cual, con los filtros existentes aplicados. Para exportar más filas de una tabla a Excel, puede aumentar el número de filas que se muestran en la página mediante la flecha desplegable **Filas por página** en la parte superior de cada cuadrícula.

## <a name="pin-to-dashboard"></a>Anclar al panel

Haga clic en el botón de anclaje en la parte superior de cada widget para anclar el widget al panel de Azure Portal. Esta característica le ayudará a crear paneles personalizados adaptados para mostrar la información más importante que necesita.

## <a name="cross-tenant-reports"></a>Informes entre inquilinos

Si usa [Azure Lighthouse](https://docs.microsoft.com/azure/lighthouse/) con acceso delegado a las suscripciones en varios entornos de inquilinos, puede usar el filtro de suscripción predeterminado. Seleccione el botón de filtro situado en la esquina superior derecha de Azure Portal para elegir todas las suscripciones para las que desea ver datos. Esto le permite seleccionar áreas de trabajo de Log Analytics de los inquilinos para ver informes multiinquilino.

## <a name="conventions-used-in-backup-reports"></a>Convenciones usadas en los informes de Backup

- Los filtros se aplican de izquierda a derecha y de arriba abajo en cada pestaña. Es decir, cualquier filtro solo se aplica a todos aquellos widgets que se colocan a la derecha del filtro o debajo de ese filtro.
- Al seleccionar un icono coloreado, se filtran los widgets situados debajo del icono para los registros que pertenecen al valor de ese icono. Por ejemplo, al seleccionar el icono **Protección detenida** en la pestaña **Elementos de copia de seguridad**, se filtran las cuadrículas y los gráficos siguientes para mostrar solo los datos de los elementos de copia de seguridad en estado de Protección detenida.
- No es posible hacer clic en los iconos que no están coloreados.
- Los datos del día parcial actual no aparecen en los informes. Por lo tanto, cuando el valor seleccionado de **Intervalo de tiempo** es **Últimos 7 días**, el informe muestra los registros de los últimos siete días completados. No se incluye el día actual.
- El informe muestra los detalles de los trabajos (aparte de los trabajos de registro) que se *desencadenaron* en el intervalo de tiempo seleccionado.
- Los valores que se muestran para el **Almacenamiento en la nube** y las **Instancias protegidas** corresponden al *final* del intervalo de tiempo seleccionado.
- Los elementos de Backup que se muestran en los informes son los que existen al *final* del intervalo de tiempo seleccionado. No se muestran los elementos de Backup que se eliminaron en medio del intervalo de tiempo seleccionado. Se aplica la misma convención para las directivas de Backup.

## <a name="query-load-times"></a>Tiempos de carga de las consultas

Los widgets del informe de Backup se basan en consultas de Kusto, que se ejecutan en las áreas de trabajo de Log Analytics del usuario. Normalmente, estas consultas implican el procesamiento de grandes cantidades de datos, con varias combinaciones, para proporcionar información más completa. Como resultado, los widgets podrían no cargarse de forma instantánea cuando el usuario vea informes de un gran conjunto de copias de seguridad. En esta tabla se proporciona una estimación aproximada del tiempo que pueden tardar en cargarse los distintos widgets, en función del número de elementos de Backup y el intervalo de tiempo para el que se visualiza el informe.

| **N.º de orígenes de datos**                         | **Horizonte temporal** | **Tiempos de carga aproximados**                                              |
| --------------------------------- | ------------- | ------------------------------------------------------------ |
| ~5 K                       | 1 mes          | Iconos: 5 a 10 segundos <br> Cuadrículas: 5 a 10 segundos <br> Gráficos: 5 a 10 segundos <br> Filtros de nivel de informe: 5 a 10 segundos|
| ~5 K                       | 3 meses          | Iconos: 5 a 10 segundos <br> Cuadrículas: 5 a 10 segundos <br> Gráficos: 5 a 10 segundos <br> Filtros de nivel de informe: 5 a 10 segundos|
| ~10 K                       | 3 meses          | Iconos: 15 a 20 segundos <br> Cuadrículas: 15 a 20 segundos <br> Gráficos: 1 a 2 minutos <br> Filtros de nivel de informe: 25 a 30 segundos|
| ~15 K                       | 1 mes          | Iconos: 15 a 20 segundos <br> Cuadrículas: 15 a 20 segundos <br> Gráficos: 50 a 60 segundos <br> Filtros de nivel de informe: 20 a 25 segundos|
| ~15 K                       | 3 meses          | Iconos: 20 a 30 segundos <br> Cuadrículas: 20 a 30 segundos <br> Gráficos: 2 a 3 minutos <br> Filtros de nivel de informe: 50 a 60 segundos |

## <a name="what-happened-to-the-power-bi-reports"></a>¿Qué ha ocurrido con los informes de Power BI?

- La versión anterior de la plantilla de Power BI para la creación de informes, que tiene como origen de los datos una cuenta de Azure Storage, está en una ruta de desuso. Se recomienda comenzar a enviar los datos de diagnóstico del almacén a Log Analytics para ver los informes.

- Además, el [esquema V1](https://docs.microsoft.com/azure/backup/backup-azure-diagnostics-mode-data-model#v1-schema-vs-v2-schema) de envío de datos de diagnóstico a una cuenta de almacenamiento o a un área de trabajo de LA también se encuentra en una ruta de degradación. Esto significa que, si ha escrito consultas personalizadas o automatizaciones basadas en el esquema v1, se recomienda actualizar estas consultas para usar el esquema V2 actualmente admitido.

## <a name="next-steps"></a>Pasos siguientes

[Más información sobre la supervisión y la generación de informes con Azure Backup](https://docs.microsoft.com/azure/backup/backup-azure-monitor-alert-faq)
