---
title: Registros de rastreamento personalizadas
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: 6c68c08e5beacee30b517bf0c2bad3e83785409b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511329"
---
# <a name="custom-tracking-records"></a><span data-ttu-id="f7eab-102">Registros de rastreamento personalizadas</span><span class="sxs-lookup"><span data-stu-id="f7eab-102">Custom Tracking Records</span></span>
<span data-ttu-id="f7eab-103">Este tópico demonstra como criar registros personalizados de rastreamento e populá-los com os dados a serem emitidos juntamente com os registros.</span><span class="sxs-lookup"><span data-stu-id="f7eab-103">This topic demonstrates how to create custom tracking records and populate them with data to be emitted along with the records.</span></span>  
  
## <a name="emitting-custom-tracking-records"></a><span data-ttu-id="f7eab-104">Emitindo registros de rastreamento personalizadas</span><span class="sxs-lookup"><span data-stu-id="f7eab-104">Emitting Custom Tracking Records</span></span>  
 <span data-ttu-id="f7eab-105">Os registros personalizados de rastreamento podem ser emitidos de uma atividade do código conforme mostrado no exemplo o seguir.</span><span class="sxs-lookup"><span data-stu-id="f7eab-105">Custom tracking records can be emitted from a code activity as shown in the following example.</span></span>  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
…  
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");  
            customRecord.Data.Add("SendTime", sendTime);  
            context.Track(customRecord);  
}  
```  
  
 <span data-ttu-id="f7eab-106"><xref:System.Activities.Tracking.CustomTrackingRecord> é emitido em uma atividade de código chamando o método de <xref:System.Activities.NativeActivityContext.Track%2A> em `ActvityContext`.</span><span class="sxs-lookup"><span data-stu-id="f7eab-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted in a code activity by invoking the <xref:System.Activities.NativeActivityContext.Track%2A> method on the `ActvityContext`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7eab-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7eab-107">See Also</span></span>  
 [<span data-ttu-id="f7eab-108">Monitoramento do Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="f7eab-108">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="f7eab-109">Monitoramento de aplicativos com App Fabric</span><span class="sxs-lookup"><span data-stu-id="f7eab-109">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
