---
title: 'Detalles de la política de pago: Azure Marketplace'
description: Detalles relativos a las políticas de pago, incluidas las programaciones y la recuperación.
ms.service: marketplace
ms.subservice: partnercenter-marketplace-publisher
ms.topic: conceptual
author: mingshen
ms.author: mingshen
ms.date: 04/24/2020
ms.openlocfilehash: f26e006998b0818ba84fa23ee1941a1033ef205b
ms.sourcegitcommit: d7008edadc9993df960817ad4c5521efa69ffa9f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/08/2020
ms.locfileid: "86118297"
---
# <a name="payout-policy-details"></a>Detalles de la política de pago

En este artículo se describe el proceso de pago de Microsoft, la programación de pago, dónde encontrar el estado de un pago y la política de recuperación.

## <a name="where-to-find-upcoming-payouts"></a>Dónde encontrar los pagos futuros

En el Centro de partners, seleccione **Pago** en la parte superior derecha del portal:

![Se muestra el icono de Pago en la parte superior derecha del portal del Centro de partners.](./media/payout-overview.png)

> [!TIP]
> No todos los roles de cuenta tienen acceso a la información de pago. Para más información, consulte [Roles y permisos para acceder al informe de pago](./payout-summary-overview.md#roles-and-permissions).

## <a name="payment-schedules"></a>Programaciones de pago

En las secciones siguientes se describe nuestro proceso de pago.

### <a name="enterprise-agreement-transactions-after-may-1-2020"></a>Transacciones del Contrato Enterprise después del 1 de mayo de 2020

#### <a name="update-to-our-commercial-marketplace-publisher-payout-model"></a>Actualización a nuestro modelo de pago de anunciantes de Marketplace comercial

A partir del 1 de mayo de 2020, vamos a actualizar nuestra política de pago relacionada con los productos que los clientes con un Contrato Enterprise de Microsoft han adquirido en Azure Marketplace o AppSource. Si un cliente compra un producto en Azure Marketplace o AppSource con su Contrato Enterprise de Microsoft actual con posterioridad al 1 de mayo de 2020, los pagos comenzarán a emitirse en el siguiente ciclo de pago, 30 días después de la factura del cliente. Las transacciones realizadas mediante tarjeta de crédito no experimentarán cambios y seguirán teniendo un período de retención de 30 días antes del pago. En esta tabla se muestran los detalles de la programación de pago.

> [!NOTE]
> Consulte a continuación [Proceso para impagos de los clientes](#process-for-customer-non-payment) para conocer qué acciones emprender si un cliente no paga, pero a usted ya se la ha emitido un pago.

| Evento  | Date  | Visibilidad de los asociados: Informe de pago del Centro de partners  |  Visibilidad de los asociados: Análisis del Centro de partners\* |
| --- | --- | --- | --- |
| Transacción o mes de uso | 1/8/2020 – 31/8/2020 | N/D | **Informe de uso**: se muestra el nuevo consumo (actualizado cada cuatro horas).<br>**Informe de pedidos**: N/D |
| Final del período (mes) | 31/8/2020 | N/D | **Informe de uso**: se muestra el consumo de fin de mes.<br>**Informe de pedidos**: N/D |
| Pedido generado | 3/9/2020 – 7/9/2020 | N/D | **Informe de uso**: se muestra el consumo con OrderID/OrderLineItemID.<br>**Informe de pedidos**: los pedidos de cliente se muestran como activos. |
| Cálculo de la ganancia de pago | 4/9/2020 – 10/9/2020 | Se marca como **No procesado** en el historial de transacciones del panel de pago | **Informe de uso**: se muestra el consumo con OrderID/OrderLineItemID.<br>**Informe de pedidos**: los pedidos de cliente se muestran como activos. |
| Pago mensual | 5/10/2020 | Se marca como **Próximo** en el historial de transacciones del panel de pago. | **Informe de uso**: se muestra el consumo con OrderID/OrderLineItemID.<br>**Informe de pedidos**: los pedidos de cliente se muestran como activos. |
| Fecha de pago | 15/10/2020 | Se marca como **Enviado** en el historial de transacciones y en la sección de pagos del panel de pago. | **Informe de uso**: se muestra el consumo con OrderID/OrderLineItemID.<br>**Informe de pedidos**: los pedidos de cliente se muestran como activos. |
| Factura de cliente cobrada | 1/12/2020 | Se marca como **Enviado** en el historial de transacciones y en la sección de pagos del panel de pago. | **Informe de uso**: se muestra el consumo con OrderID/OrderLineItemID.<br>**Informe de pedidos**: los pedidos de cliente se muestran como activos.  |
|  |  |  |  |

\* Se puede acceder a los informes de uso y de pedidos en la sección Analizar del Centro de partners.

### <a name="customers-who-pay-using-credit-card-or-invoice"></a>Clientes que pagan mediante tarjeta de crédito o factura

Todas las compras con una tarjeta de crédito o una factura mensual tienen un período de retención de 30 días para garantizar que los fondos se borran y no hay contracargos ni fraudes sospechosos.

| Evento  | Date  | Visibilidad de los asociados: Informe de pago del Centro de partners  |  Visibilidad de los asociados: Análisis del Centro de partners\*  |
| --- | --- | --- | --- |
| Transacción o mes de uso | 1/8/2019 - 31/8/2019 | N/D | **Informe de uso**: se muestra el nuevo consumo (actualizado cada cuatro horas).<br>**Informe de pedidos**: N/D |
| Final del período (mes) | 31/8/2019 | N/D | **Informe de uso**: se muestra el consumo de fin de mes.<br>**Informe de pedidos**: N/D |
| Pedido generado | 3/9/2019 – 7/9/2019 | N/D | **Informe de uso**: se muestra el consumo con OrderID/OrderLineItemID.<br>**Informe de pedidos**: los pedidos de cliente se muestran como activos. |
| Factura de cliente cobrada | 7/9/2019 – 10/9/2019 | N/D | **Informe de uso**: se muestra el consumo con OrderID/OrderLineItemID.<br>**Informe de pedidos**: los pedidos de cliente se muestran como activos. |
| Cálculo del pago | 8/9/2019 –12/9/2019 | Se marca como **No procesado** en el historial de transacciones del panel de pago | **Informe de uso**: se muestra el consumo con OrderID/OrderLineItemID.<br>**Informe de pedidos**: los pedidos de cliente se muestran como activos. |
| Pago mensual | 5/11/2019\* | Se marca como **Próximo** en el historial de transacciones del panel de pago. | **Informe de uso**: se muestra el consumo con OrderID/OrderLineItemID.<br>**Informe de pedidos**: los pedidos de cliente se muestran como activos. |
| Fecha de pago | 15/11/2019 | Se marca como **Enviado** en el historial de transacciones y en la sección de pagos del panel de pago. | **Informe de uso**: se muestra el consumo con OrderID/OrderLineItemID.<br>**Informe de pedidos**: los pedidos de cliente se muestran como activos. |
|  |  |  |  |

\* Se puede acceder a los informes de uso y de pedidos en la sección Analizar del Centro de partners.

### <a name="enterprise-agreement-transactions-prior-to-may-1-2020"></a>Transacciones del Contrato Enterprise anteriores al 1 de mayo de 2020

Todas las compras realizadas antes de esta fecha se procesan y pagan según la programación siguiente después de que Microsoft haya cobrado el pago a los clientes y procesado la cuota de Marketplace.

| Evento  | Date  | Visibilidad de los asociados: Informe de pago del Centro de partners  |  Visibilidad de los asociados: Análisis del Centro de partners\*  |
| --- | --- | --- | --- |
| Transacción o mes de uso | 1/8/2019 – 31/8/2019 | N/D | **Informe de uso**: se muestra el nuevo consumo (actualizado cada cuatro horas).<br>**Informe de pedidos**: N/D |
| Final del período (mes) | 31/8/2019 | N/D | **Informe de uso**: se muestra el consumo de fin de mes.<br>**Informe de pedidos**: N/D |
| Pedido generado | 3/9/2019 – 7/9/2019 | N/D | **Informe de uso**: se muestra el consumo con OrderID/OrderLineItemID.<br>**Informe de pedidos**: los pedidos de cliente se muestran como activos. |
| Factura de cliente cobrada | 1/12/2019 | N/D | **Informe de uso**: se muestra el consumo con OrderID/OrderLineItemID.<br>**Informe de pedidos**: los pedidos de cliente se muestran como activos. |
| Cálculo del pago | 5/12/2019 –7/12/2019 | Se marca como **No procesado** en el historial de transacciones del panel de pago | **Informe de uso**: se muestra el consumo con OrderID/OrderLineItemID.<br>**Informe de pedidos**: los pedidos de cliente se muestran como activos. |
| Pago mensual | 5/1/2019 | Se marca como **Próximo** en el historial de transacciones del panel de pago. | **Informe de uso**: se muestra el consumo con OrderID/OrderLineItemID.<br>**Informe de pedidos**: los pedidos de cliente se muestran como activos. |
| Fecha de pago | 15/1/2019 | Se marca como **Enviado** en el historial de transacciones y en la sección de pagos del panel de pago. | **Informe de uso**: se muestra el consumo con OrderID/OrderLineItemID.<br>**Informe de pedidos**: los pedidos de cliente se muestran como activos. |
|  |  |  |  |

\* Se puede acceder a los informes de uso y de pedidos en la sección Analizar del Centro de partners.

## <a name="process-for-customer-non-payment"></a>Proceso en caso de impago de los clientes

En raras ocasiones, Microsoft no puede cobrar los pagos a los clientes por sus compras en Marketplace comercial. Cuando un cliente no puede pagar a Microsoft según su programación de facturación, comienza el proceso de cobro. Este proceso tarda aproximadamente cuatro meses e implica una comunicación continua con Microsoft. Si al final de este proceso no se recibe el pago, Microsoft cancela los fondos y los considera no cobrados.

Según el proceso de pago articulado aquí, es posible que Microsoft ya haya pagado fondos a los anunciantes (usted) que finalmente no se podrán cobrar. Por lo tanto, tenemos un proceso para conciliar estos importes. Para asegurarse de que tiene la advertencia de que su pago (ya recibido) se puede conciliar, se le avisará cuando un cliente se encuentre en el proceso de cobro y es probable que se cancelen las compras.

Microsoft recuperará los pagos que ya se le hayan pagado a usted con uno de los siguientes métodos: (1) Microsoft puede restar los importes no pagados de los pagos futuros; por ejemplo, si se considera que 1000 dólares USA de los pagos no se pueden cobrar ni cancelar, se retienen los pagos futuros hasta que se recupere este importe; o bien, (2) Microsoft puede solicitar un reembolso o los importes no cobrados a los anunciantes de la factura.

A continuación, se muestra una programación de ejemplo:

| Evento | Fecha aproximada | Visibilidad de los asociados |
| --- | --- | --- |
| Ejemplo de fecha de pago | 15/10/2020 | Se marca como **Enviado** en el historial de transacciones y en la sección de pagos del panel de pago. |
| <font color="red">Si el cliente no paga a Microsoft</font> | 2/12/2020 – 5/12/2020 | Sin cambios, igual que antes. |
| El cliente recibe el primer correo electrónico de pago atrasado. | 12/6/2020 | None |
| El cliente recibe mensajes de correo electrónico periódicos cada vez más urgentes. | 07/12/2020 – 31/01/2021 | None |
| Es probable que el anunciante reciba una notificación de una probable cancelación. | 07/01/2021 | Notificación por correo electrónico enviada al anunciante de que su cliente aún no ha enviado el pago. Se incluyen el identificador de la transacción y el importe en dólares. |
| El cliente recibe el aviso de cancelación. | 01/02/2021 | None |
| El proceso de cobro finaliza o los fondos se cancelan. | 15/02/2021 | Notificación por correo electrónico enviada al anunciante de que los fondos se han cancelado. Se incluyen el identificador de la transacción y el importe en dólares. |
| El pago se deduce. | 01/03/2021 | El anunciante verá una transacción negativa en la declaración de pago del Centro de partners. |
| El pago se retiene. | 15/03/2021 | Los pagos futuros se mostrarán en la declaración de pago del Centro de partners. El anunciante no recibirá ningún pago hasta que el saldo deje de ser negativo.  |
|||

## <a name="next-step"></a>siguiente paso

- [Datos fiscales](./tax-details-paid-transactions.md)
