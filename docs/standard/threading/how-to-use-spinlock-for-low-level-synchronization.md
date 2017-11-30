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
helpviewer_keywords: SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 30ddc7d340b210aaad4a04ea43e89555d2701f20
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a><span data-ttu-id="cecc9-102">Como usar SpinLock para sincronização de baixo nível</span><span class="sxs-lookup"><span data-stu-id="cecc9-102">How to: Use SpinLock for Low-Level Synchronization</span></span>
<span data-ttu-id="cecc9-103">O exemplo a seguir demonstra como usar um <xref:System.Threading.SpinLock>.</span><span class="sxs-lookup"><span data-stu-id="cecc9-103">The following example demonstrates how to use a <xref:System.Threading.SpinLock>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cecc9-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cecc9-104">Example</span></span>  
 <span data-ttu-id="cecc9-105">Neste exemplo, a seção crítica executa uma quantidade mínima de trabalho, o que torna um bom candidato para um <xref:System.Threading.SpinLock>.</span><span class="sxs-lookup"><span data-stu-id="cecc9-105">In this example, the critical section performs a minimal amount of work, which makes it a good candidate for a <xref:System.Threading.SpinLock>.</span></span> <span data-ttu-id="cecc9-106">Aumentar o trabalho uma pequena quantidade aumenta o desempenho do <xref:System.Threading.SpinLock> em comparação com um bloqueio padrão.</span><span class="sxs-lookup"><span data-stu-id="cecc9-106">Increasing the work a small amount increases the performance of the <xref:System.Threading.SpinLock> compared to a standard lock.</span></span> <span data-ttu-id="cecc9-107">No entanto, há um ponto em que um SpinLock se torna mais caro do que um bloqueio padrão.</span><span class="sxs-lookup"><span data-stu-id="cecc9-107">However, there is a point at which a SpinLock becomes more expensive than a standard lock.</span></span> <span data-ttu-id="cecc9-108">Você pode usar a criação de perfil de funcionalidade nas ferramentas de criação de perfil de simultaneidade para ver qual tipo de bloqueio fornece melhor desempenho em seu programa.</span><span class="sxs-lookup"><span data-stu-id="cecc9-108">You can use the concurrency profiling functionality in the profiling tools to see which type of lock provides better performance in your program.</span></span> <span data-ttu-id="cecc9-109">Para obter mais informações, consulte [Visualizador de simultaneidade](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="cecc9-109">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <span data-ttu-id="cecc9-110"><xref:System.Threading.SpinLock>pode ser útil quando um bloqueio em um recurso compartilhado não vai ser mantidos por muito tempo.</span><span class="sxs-lookup"><span data-stu-id="cecc9-110"><xref:System.Threading.SpinLock> might be useful when a lock on a shared resource is not going to be held for very long.</span></span> <span data-ttu-id="cecc9-111">Nesses casos, em computadores com vários núcleos pode ser eficiente para o thread bloqueado gire para alguns ciclos até que o bloqueio seja liberado.</span><span class="sxs-lookup"><span data-stu-id="cecc9-111">In such cases, on multi-core computers it can be efficient for the blocked thread to spin for a few cycles until the lock is released.</span></span> <span data-ttu-id="cecc9-112">Por rotação, o thread não ser bloqueado, que é um processo intensivo de CPU.</span><span class="sxs-lookup"><span data-stu-id="cecc9-112">By spinning, the thread does not become blocked, which is a CPU-intensive process.</span></span> <span data-ttu-id="cecc9-113"><xref:System.Threading.SpinLock>irá parar giratório sob determinadas condições para evitar privação de processadores lógicos ou inversão de prioridade em sistemas com o Hyper-Threading.</span><span class="sxs-lookup"><span data-stu-id="cecc9-113"><xref:System.Threading.SpinLock> will stop spinning under certain conditions to prevent starvation of logical processors or priority inversion on systems with Hyper-Threading.</span></span>  
  
 <span data-ttu-id="cecc9-114">Este exemplo usa o <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> classe, que requer sincronização de usuário para acesso de vários segmentos.</span><span class="sxs-lookup"><span data-stu-id="cecc9-114">This example uses the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class, which requires user synchronization for multi-threaded access.</span></span> <span data-ttu-id="cecc9-115">Em aplicativos direcionam ao .NET Framework versão 4, outra opção é usar o <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, que não exige nenhum bloqueio de usuário.</span><span class="sxs-lookup"><span data-stu-id="cecc9-115">In applications that target the .NET Framework version 4, another option is to use the <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, which does not require any user locks.</span></span>  
  
 <span data-ttu-id="cecc9-116">Observe o uso de `false` (`False` no Visual Basic) na chamada para <xref:System.Threading.SpinLock.Exit%2A>.</span><span class="sxs-lookup"><span data-stu-id="cecc9-116">Note the use of `false` (`False` in Visual Basic) in the call to <xref:System.Threading.SpinLock.Exit%2A>.</span></span> <span data-ttu-id="cecc9-117">Isso fornece o melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="cecc9-117">This provides the best performance.</span></span> <span data-ttu-id="cecc9-118">Especifique `true` (`True`) em arquiteturas de IA64 para usar o limite de memória, que libera os buffers de gravação para garantir que o bloqueio agora está disponível para outros threads sair.</span><span class="sxs-lookup"><span data-stu-id="cecc9-118">Specify `true` (`True`)on IA64 architectures to use the memory fence, which flushes the write buffers to ensure that the lock is now available for other threads to exit.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cecc9-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cecc9-119">See Also</span></span>  
 [<span data-ttu-id="cecc9-120">Objetos e recursos de threading</span><span class="sxs-lookup"><span data-stu-id="cecc9-120">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
