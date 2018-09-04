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
 [Monitoramento do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitoramento de aplicativos com a malha de aplicativos](https://go.microsoft.com/fwlink/?LinkId=201275)
