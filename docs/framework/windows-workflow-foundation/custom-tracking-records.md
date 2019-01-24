---
title: Registros de rastreamento personalizadas
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: 7f866713b5d6f6c82dff80864f2eccb5d2f6cb30
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54529824"
---
# <a name="custom-tracking-records"></a>Registros de rastreamento personalizadas
Este tópico demonstra como criar registros personalizados de rastreamento e populá-los com os dados a serem emitidos juntamente com os registros.  
  
## <a name="emitting-custom-tracking-records"></a>Emitindo registros de rastreamento personalizadas  
 Os registros personalizados de rastreamento podem ser emitidos de uma atividade do código conforme mostrado no exemplo o seguir.  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
…  
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");  
            customRecord.Data.Add("SendTime", sendTime);  
            context.Track(customRecord);  
}  
```  
  
 <xref:System.Activities.Tracking.CustomTrackingRecord> é emitido em uma atividade de código chamando o método de <xref:System.Activities.NativeActivityContext.Track%2A> em `ActvityContext`.  
  
## <a name="see-also"></a>Consulte também
- [Monitoramento do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201273)
- [Monitoramento de aplicativos com a malha de aplicativos](https://go.microsoft.com/fwlink/?LinkId=201275)
