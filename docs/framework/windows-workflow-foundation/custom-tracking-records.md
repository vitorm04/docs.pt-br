---
title: Registros de rastreamento personalizadas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9a459e6df0e030f4e17bb73461d8fa790a61787e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="custom-tracking-records"></a><span data-ttu-id="b35ab-102">Registros de rastreamento personalizadas</span><span class="sxs-lookup"><span data-stu-id="b35ab-102">Custom Tracking Records</span></span>
<span data-ttu-id="b35ab-103">Este tópico demonstra como criar registros personalizados de rastreamento e populá-los com os dados a serem emitidos juntamente com os registros.</span><span class="sxs-lookup"><span data-stu-id="b35ab-103">This topic demonstrates how to create custom tracking records and populate them with data to be emitted along with the records.</span></span>  
  
## <a name="emitting-custom-tracking-records"></a><span data-ttu-id="b35ab-104">Emitindo registros de rastreamento personalizadas</span><span class="sxs-lookup"><span data-stu-id="b35ab-104">Emitting Custom Tracking Records</span></span>  
 <span data-ttu-id="b35ab-105">Os registros personalizados de rastreamento podem ser emitidos de uma atividade do código conforme mostrado no exemplo o seguir.</span><span class="sxs-lookup"><span data-stu-id="b35ab-105">Custom tracking records can be emitted from a code activity as shown in the following example.</span></span>  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
…  
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");  
            customRecord.Data.Add("SendTime", sendTime);  
            context.Track(customRecord);  
}  
```  
  
 <span data-ttu-id="b35ab-106"><xref:System.Activities.Tracking.CustomTrackingRecord> é emitido em uma atividade de código chamando o método de <xref:System.Activities.NativeActivityContext.Track%2A> em `ActvityContext`.</span><span class="sxs-lookup"><span data-stu-id="b35ab-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted in a code activity by invoking the <xref:System.Activities.NativeActivityContext.Track%2A> method on the `ActvityContext`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b35ab-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b35ab-107">See Also</span></span>  
 [<span data-ttu-id="b35ab-108">Monitoramento do Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="b35ab-108">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="b35ab-109">Monitoramento de aplicativos com App Fabric</span><span class="sxs-lookup"><span data-stu-id="b35ab-109">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
