---
title: "Como usar SpinWait para implementar uma operação bifásica de espera"
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
helpviewer_keywords: SpinWait, how to synchronize two-phase wait
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2717ba2d63e4ecf40638c369b66f2c696e396a5e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a>Como usar SpinWait para implementar uma operação bifásica de espera
O exemplo a seguir mostra como usar um <xref:System.Threading.SpinWait?displayProperty=nameWithType> objeto para implementar uma operação de espera de duas fases. Na primeira fase, o objeto de sincronização, um `Latch`, gira para alguns ciclos enquanto ele verifica se o bloqueio se tornou disponível. Na segunda fase, se o bloqueio esteja disponível, em seguida, o `Wait` método retorna sem usar o <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> para executar sua espera; caso contrário, `Wait` executa a espera.  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra uma implementação muito básica de uma sincronização de trava primitivo. Você pode usar essa estrutura de dados quando os tempos de espera devem ser muito curto. Este exemplo tem fins apenas demonstrativos. Se você precisar de funcionalidade do tipo de trava em seu programa, considere o uso de <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 A trava usa o <xref:System.Threading.SpinWait> objeto para executar em vigor somente até a próxima chamada para `SpinOnce` faz com que o <xref:System.Threading.SpinWait> para produzir a fração de tempo do thread. Nesse ponto, a trava faz com que o seu próprio alternância de contexto chamando <xref:System.Threading.WaitHandle.WaitOne%2A> no <xref:System.Threading.ManualResetEvent> e passando o restante do valor de tempo limite.  
  
 A saída de log mostra quantas vezes a trava foi capaz de aumentar o desempenho ao adquirir o bloqueio sem usar o <xref:System.Threading.ManualResetEvent>.  
  
## <a name="see-also"></a>Consulte também  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 [Objetos e recursos de threading](../../../docs/standard/threading/threading-objects-and-features.md)
