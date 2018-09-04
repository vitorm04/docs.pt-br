---
title: Registros de rastreamento personalizadas
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: ef3c20890f33f3ffd07a9c88de863e1ebe24851f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520179"
---
# <a name="custom-tracking-records"></a><span data-ttu-id="e7ae7-102">Registros de rastreamento personalizadas</span><span class="sxs-lookup"><span data-stu-id="e7ae7-102">Custom Tracking Records</span></span>
<span data-ttu-id="e7ae7-103">Este tópico demonstra como criar registros personalizados de rastreamento e populá-los com os dados a serem emitidos juntamente com os registros.</span><span class="sxs-lookup"><span data-stu-id="e7ae7-103">This topic demonstrates how to create custom tracking records and populate them with data to be emitted along with the records.</span></span>  
  
## <a name="emitting-custom-tracking-records"></a><span data-ttu-id="e7ae7-104">Emitindo registros de rastreamento personalizadas</span><span class="sxs-lookup"><span data-stu-id="e7ae7-104">Emitting Custom Tracking Records</span></span>  
 <span data-ttu-id="e7ae7-105">Os registros personalizados de rastreamento podem ser emitidos de uma atividade do código conforme mostrado no exemplo o seguir.</span><span class="sxs-lookup"><span data-stu-id="e7ae7-105">Custom tracking records can be emitted from a code activity as shown in the following example.</span></span>  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
…  
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");  
            customRecord.Data.Add("SendTime", sendTime);  
            context.Track(customRecord);  
}  
```  
  
 <span data-ttu-id="e7ae7-106"><xref:System.Activities.Tracking.CustomTrackingRecord> é emitido em uma atividade de código chamando o método de <xref:System.Activities.NativeActivityContext.Track%2A> em `ActvityContext`.</span><span class="sxs-lookup"><span data-stu-id="e7ae7-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted in a code activity by invoking the <xref:System.Activities.NativeActivityContext.Track%2A> method on the `ActvityContext`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7ae7-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7ae7-107">See Also</span></span>  
 [<span data-ttu-id="e7ae7-108">Monitoramento do Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="e7ae7-108">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="e7ae7-109">Monitoramento de aplicativos com a malha de aplicativos</span><span class="sxs-lookup"><span data-stu-id="e7ae7-109">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
