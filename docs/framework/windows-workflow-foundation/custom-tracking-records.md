---
title: Registros de rastreamento personalizadas
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: 986f0350c24414d0ff960474445adf6ac3f39734
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802616"
---
# <a name="custom-tracking-records"></a><span data-ttu-id="a426d-102">Registros de rastreamento personalizadas</span><span class="sxs-lookup"><span data-stu-id="a426d-102">Custom Tracking Records</span></span>

<span data-ttu-id="a426d-103">Este tópico demonstra como criar registros personalizados de rastreamento e populá-los com os dados a serem emitidos juntamente com os registros.</span><span class="sxs-lookup"><span data-stu-id="a426d-103">This topic demonstrates how to create custom tracking records and populate them with data to be emitted along with the records.</span></span>

## <a name="emitting-custom-tracking-records"></a><span data-ttu-id="a426d-104">Emitindo registros de rastreamento personalizadas</span><span class="sxs-lookup"><span data-stu-id="a426d-104">Emitting Custom Tracking Records</span></span>

<span data-ttu-id="a426d-105">Os registros personalizados de rastreamento podem ser emitidos de uma atividade do código conforme mostrado no exemplo o seguir.</span><span class="sxs-lookup"><span data-stu-id="a426d-105">Custom tracking records can be emitted from a code activity as shown in the following example.</span></span>

```csharp
protected override void Execute(CodeActivityContext context)
{
…
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");
            customRecord.Data.Add("SendTime", sendTime);
            context.Track(customRecord);
}
```

<span data-ttu-id="a426d-106"><xref:System.Activities.Tracking.CustomTrackingRecord> é emitido em uma atividade de código chamando o método de <xref:System.Activities.NativeActivityContext.Track%2A> em `ActivityContext`.</span><span class="sxs-lookup"><span data-stu-id="a426d-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted in a code activity by invoking the <xref:System.Activities.NativeActivityContext.Track%2A> method on the `ActivityContext`.</span></span>

## <a name="see-also"></a><span data-ttu-id="a426d-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a426d-107">See also</span></span>

- <span data-ttu-id="a426d-108">[Monitoramento do Windows Server app Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a426d-108">[Windows Server App Fabric Monitoring](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="a426d-109">[Monitorando aplicativos com o app Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a426d-109">[Monitoring Applications with App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
