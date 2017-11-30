---
title: CountdownEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: synchronization primitives, CountdownEvent
ms.assetid: eec3812a-e20f-4ecd-bfef-6921d508b708
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9f953f6477abf1f4e0d6aaf79e67005172ff1144
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="countdownevent"></a>CountdownEvent
<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>é um primitivo de sincronização que desbloqueia seus threads de espera, depois de ser sinalizado um determinado número de vezes. <xref:System.Threading.CountdownEvent>foi projetado para cenários em que caso contrário, seria necessário usar um <xref:System.Threading.ManualResetEvent> ou <xref:System.Threading.ManualResetEventSlim> e diminuir manualmente uma variável antes de sinalizar o evento. Por exemplo, em um cenário de bifurcação/junção, você pode simplesmente criar um <xref:System.Threading.CountdownEvent> que tem uma contagem de sinal de 5 e, em seguida, iniciar cinco itens de trabalho no thread de pool e tem cada chamada de item de trabalho <xref:System.Threading.CountdownEvent.Signal%2A> quando ele for concluído. Cada chamada para <xref:System.Threading.CountdownEvent.Signal%2A> diminui o sinal de contagem em 1. No thread principal, a chamada para <xref:System.Threading.CountdownEvent.Wait%2A> será bloqueado até que a contagem de sinal é zero.  
  
> [!NOTE]
>  Para o código que não têm para interagir com a sincronização do .NET Framework herdada APIs, considere o uso de <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objetos ou o <xref:System.Threading.Tasks.Parallel.Invoke%2A> método para uma abordagem mais fácil para expressar o paralelismo bifurcado.  
  
 <xref:System.Threading.CountdownEvent>tem estes recursos adicionais:  
  
-   A operação de espera pode ser cancelada usando tokens de cancelamento.  
  
-   Sua contagem de sinal pode ser incrementada depois que a instância é criada.  
  
-   Instâncias podem ser reutilizadas após <xref:System.Threading.CountdownEvent.Wait%2A> foi retornado ao chamar o <xref:System.Threading.CountdownEvent.Reset%2A> método.  
  
-   Instâncias de expõem um <xref:System.Threading.WaitHandle> para integração com outra APIs de sincronização do .NET Framework, como <xref:System.Threading.WaitHandle.WaitAll%2A>.  
  
## <a name="basic-usage"></a>Uso básico  
 O exemplo a seguir demonstra como usar um <xref:System.Threading.CountdownEvent> com <xref:System.Threading.ThreadPool> itens de trabalho.  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a>CountdownEvent com cancelamento  
 O exemplo a seguir mostra como cancelar a operação de espera em <xref:System.Threading.CountdownEvent> usando um token de cancelamento. O padrão básico segue o modelo para cancelamento unificado, introduzida no [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Para obter mais informações, consulte [cancelamento em Threads gerenciados](../../../docs/standard/threading/cancellation-in-managed-threads.md).  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 Observe que a operação de espera não cancelar os threads que são a sinalização. Normalmente, o cancelamento é aplicado a uma operação lógica e que pode incluir a aguardar o evento, bem como todos os itens de trabalho que a espera está sincronizando. Neste exemplo, cada item de trabalho é passado uma cópia do mesmo token de cancelamento de forma que ele pode responder à solicitação de cancelamento.  
  
## <a name="see-also"></a>Consulte também  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
