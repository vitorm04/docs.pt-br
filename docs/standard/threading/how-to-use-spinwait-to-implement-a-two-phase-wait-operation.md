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
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a><span data-ttu-id="fd745-102">Como usar SpinWait para implementar uma operação bifásica de espera</span><span class="sxs-lookup"><span data-stu-id="fd745-102">How to: Use SpinWait to Implement a Two-Phase Wait Operation</span></span>
<span data-ttu-id="fd745-103">O exemplo a seguir mostra como usar um <xref:System.Threading.SpinWait?displayProperty=nameWithType> objeto para implementar uma operação de espera de duas fases.</span><span class="sxs-lookup"><span data-stu-id="fd745-103">The following example shows how to use a <xref:System.Threading.SpinWait?displayProperty=nameWithType> object to implement a two-phase wait operation.</span></span> <span data-ttu-id="fd745-104">Na primeira fase, o objeto de sincronização, um `Latch`, gira para alguns ciclos enquanto ele verifica se o bloqueio se tornou disponível.</span><span class="sxs-lookup"><span data-stu-id="fd745-104">In the first phase, the synchronization object, a `Latch`, spins for a few cycles while it checks whether the lock has become available.</span></span> <span data-ttu-id="fd745-105">Na segunda fase, se o bloqueio esteja disponível, em seguida, o `Wait` método retorna sem usar o <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> para executar sua espera; caso contrário, `Wait` executa a espera.</span><span class="sxs-lookup"><span data-stu-id="fd745-105">In the second phase, if the lock becomes available, then the `Wait` method returns without using the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> to perform its wait; otherwise, `Wait` performs the wait.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd745-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fd745-106">Example</span></span>  
 <span data-ttu-id="fd745-107">Este exemplo mostra uma implementação muito básica de uma sincronização de trava primitivo.</span><span class="sxs-lookup"><span data-stu-id="fd745-107">This example shows a very basic implementation of a Latch synchronization primitive.</span></span> <span data-ttu-id="fd745-108">Você pode usar essa estrutura de dados quando os tempos de espera devem ser muito curto.</span><span class="sxs-lookup"><span data-stu-id="fd745-108">You can use this data structure when wait times are expected to be very short.</span></span> <span data-ttu-id="fd745-109">Este exemplo tem fins apenas demonstrativos.</span><span class="sxs-lookup"><span data-stu-id="fd745-109">This example is for demonstration purposes only.</span></span> <span data-ttu-id="fd745-110">Se você precisar de funcionalidade do tipo de trava em seu programa, considere o uso de <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fd745-110">If you require latch-type functionality in your program, consider using <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 <span data-ttu-id="fd745-111">A trava usa o <xref:System.Threading.SpinWait> objeto para executar em vigor somente até a próxima chamada para `SpinOnce` faz com que o <xref:System.Threading.SpinWait> para produzir a fração de tempo do thread.</span><span class="sxs-lookup"><span data-stu-id="fd745-111">The latch uses the <xref:System.Threading.SpinWait> object to spin in place only until the next call to `SpinOnce` causes the <xref:System.Threading.SpinWait> to yield the time slice of the thread.</span></span> <span data-ttu-id="fd745-112">Nesse ponto, a trava faz com que o seu próprio alternância de contexto chamando <xref:System.Threading.WaitHandle.WaitOne%2A> no <xref:System.Threading.ManualResetEvent> e passando o restante do valor de tempo limite.</span><span class="sxs-lookup"><span data-stu-id="fd745-112">At that point, the latch causes its own context switch by calling <xref:System.Threading.WaitHandle.WaitOne%2A> on the <xref:System.Threading.ManualResetEvent> and passing in the remainder of the time-out value.</span></span>  
  
 <span data-ttu-id="fd745-113">A saída de log mostra quantas vezes a trava foi capaz de aumentar o desempenho ao adquirir o bloqueio sem usar o <xref:System.Threading.ManualResetEvent>.</span><span class="sxs-lookup"><span data-stu-id="fd745-113">The logging output shows how often the Latch was able to increase performance by acquiring the lock without using the <xref:System.Threading.ManualResetEvent>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd745-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fd745-114">See Also</span></span>  
 [<span data-ttu-id="fd745-115">SpinWait</span><span class="sxs-lookup"><span data-stu-id="fd745-115">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
 [<span data-ttu-id="fd745-116">Objetos e recursos de threading</span><span class="sxs-lookup"><span data-stu-id="fd745-116">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
