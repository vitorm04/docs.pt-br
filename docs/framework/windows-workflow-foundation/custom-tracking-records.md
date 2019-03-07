---
title: Registros de rastreamento personalizadas
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: d4733b4ffc0d866cf90fd5a5e7d649de261c45fb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499115"
---
# <a name="custom-tracking-records"></a>Registros de rastreamento personalizadas

Este tópico demonstra como criar registros personalizados de rastreamento e populá-los com os dados a serem emitidos juntamente com os registros.

## <a name="emitting-custom-tracking-records"></a>Emitindo registros de rastreamento personalizadas

Os registros personalizados de rastreamento podem ser emitidos de uma atividade do código conforme mostrado no exemplo o seguir.

```csharp
protected override void Execute(CodeActivityContext context)
{
…
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");
            customRecord.Data.Add("SendTime", sendTime);
            context.Track(customRecord);
}
```


  <xref:System.Activities.Tracking.CustomTrackingRecord> é emitido em uma atividade de código chamando o método de <xref:System.Activities.NativeActivityContext.Track%2A> em `ActivityContext`.

## <a name="see-also"></a>Consulte também

- [Monitoramento do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201273)
- [Monitoramento de aplicativos com a malha de aplicativos](https://go.microsoft.com/fwlink/?LinkId=201275)
