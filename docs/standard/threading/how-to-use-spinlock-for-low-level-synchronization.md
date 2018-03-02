---
title: "Como usar SpinLock para sincronização de baixo nível"
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
helpviewer_keywords:
- SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 11d41a1fd04039fd08d945a72a37a479f79449a5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a><span data-ttu-id="209af-102">Como usar SpinLock para sincronização de baixo nível</span><span class="sxs-lookup"><span data-stu-id="209af-102">How to: Use SpinLock for Low-Level Synchronization</span></span>
<span data-ttu-id="209af-103">O exemplo a seguir demonstra como usar o <xref:System.Threading.SpinLock>.</span><span class="sxs-lookup"><span data-stu-id="209af-103">The following example demonstrates how to use a <xref:System.Threading.SpinLock>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="209af-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="209af-104">Example</span></span>  
 <span data-ttu-id="209af-105">No exemplo, a seção crítica executa uma quantidade mínima de trabalho, o que a torna uma boa candidata para o <xref:System.Threading.SpinLock>.</span><span class="sxs-lookup"><span data-stu-id="209af-105">In this example, the critical section performs a minimal amount of work, which makes it a good candidate for a <xref:System.Threading.SpinLock>.</span></span> <span data-ttu-id="209af-106">Aumentar um pouco o trabalho aumenta o desempenho do <xref:System.Threading.SpinLock> em comparação com um bloqueio padrão.</span><span class="sxs-lookup"><span data-stu-id="209af-106">Increasing the work a small amount increases the performance of the <xref:System.Threading.SpinLock> compared to a standard lock.</span></span> <span data-ttu-id="209af-107">No entanto, há um ponto em que um SpinLock se torna mais caro do que um bloqueio padrão.</span><span class="sxs-lookup"><span data-stu-id="209af-107">However, there is a point at which a SpinLock becomes more expensive than a standard lock.</span></span> <span data-ttu-id="209af-108">Use a funcionalidade de Criação de Perfil de Simultaneidade nas ferramentas de criação de perfil para ver qual tipo de bloqueio oferece o melhor desempenho no seu programa.</span><span class="sxs-lookup"><span data-stu-id="209af-108">You can use the concurrency profiling functionality in the profiling tools to see which type of lock provides better performance in your program.</span></span> <span data-ttu-id="209af-109">Para saber mais, confira [Visualização Simultânea](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="209af-109">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <span data-ttu-id="209af-110">O <xref:System.Threading.SpinLock> poderá ser útil quando um bloqueio em um recurso compartilhado não será mantido por muito tempo.</span><span class="sxs-lookup"><span data-stu-id="209af-110"><xref:System.Threading.SpinLock> might be useful when a lock on a shared resource is not going to be held for very long.</span></span> <span data-ttu-id="209af-111">Nesses casos, em computadores com vários núcleos, pode ser eficiente para o thread bloqueado girar por alguns ciclos até que o bloqueio seja liberado.</span><span class="sxs-lookup"><span data-stu-id="209af-111">In such cases, on multi-core computers it can be efficient for the blocked thread to spin for a few cycles until the lock is released.</span></span> <span data-ttu-id="209af-112">Ao girar, o thread não fica bloqueado, que é um processo de uso intenso da CPU.</span><span class="sxs-lookup"><span data-stu-id="209af-112">By spinning, the thread does not become blocked, which is a CPU-intensive process.</span></span> <span data-ttu-id="209af-113">O <xref:System.Threading.SpinLock> cessará de girar sob determinadas condições para evitar a privação dos processadores lógicos ou a inversão de prioridades em sistemas com o Hyper-Threading.</span><span class="sxs-lookup"><span data-stu-id="209af-113"><xref:System.Threading.SpinLock> will stop spinning under certain conditions to prevent starvation of logical processors or priority inversion on systems with Hyper-Threading.</span></span>  
  
 <span data-ttu-id="209af-114">Este exemplo usa a classe <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>, que requer a sincronização de usuário para o acesso de threads múltiplos.</span><span class="sxs-lookup"><span data-stu-id="209af-114">This example uses the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class, which requires user synchronization for multi-threaded access.</span></span> <span data-ttu-id="209af-115">Outra opção nos aplicativos que direcionam para a versão 4 do .NET Framework é usar o <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, que não exige bloqueio de usuário.</span><span class="sxs-lookup"><span data-stu-id="209af-115">In applications that target the .NET Framework version 4, another option is to use the <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, which does not require any user locks.</span></span>  
  
 <span data-ttu-id="209af-116">Observe o uso do `false` (`False` no Visual Basic) na chamada do <xref:System.Threading.SpinLock.Exit%2A>.</span><span class="sxs-lookup"><span data-stu-id="209af-116">Note the use of `false` (`False` in Visual Basic) in the call to <xref:System.Threading.SpinLock.Exit%2A>.</span></span> <span data-ttu-id="209af-117">Isso oferece o melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="209af-117">This provides the best performance.</span></span> <span data-ttu-id="209af-118">Especifique `true` (`True`) em arquiteturas de IA64 para usar o limite de memória, que libera os buffers de gravação para garantir que o bloqueio esteja disponível para outros threads saírem.</span><span class="sxs-lookup"><span data-stu-id="209af-118">Specify `true` (`True`)on IA64 architectures to use the memory fence, which flushes the write buffers to ensure that the lock is now available for other threads to exit.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="209af-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="209af-119">See Also</span></span>  
 [<span data-ttu-id="209af-120">Objetos e recursos de threading</span><span class="sxs-lookup"><span data-stu-id="209af-120">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
