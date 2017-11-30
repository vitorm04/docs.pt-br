---
title: "Como sincronizar operações simultâneas com uma barreira"
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
helpviewer_keywords: Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0b2e32fe3cec30a4da7467447aee625dfe7e379b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a><span data-ttu-id="73e34-102">Como sincronizar operações simultâneas com uma barreira</span><span class="sxs-lookup"><span data-stu-id="73e34-102">How to: Synchronize Concurrent Operations with a Barrier</span></span>
<span data-ttu-id="73e34-103">O exemplo a seguir mostra como sincronizar tarefas simultâneas com uma <xref:System.Threading.Barrier>.</span><span class="sxs-lookup"><span data-stu-id="73e34-103">The following example shows how to synchronize concurrent tasks with a <xref:System.Threading.Barrier>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73e34-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="73e34-104">Example</span></span>  
 <span data-ttu-id="73e34-105">A finalidade do programa a seguir é para contar o número de iterações (ou fases) são necessários dois threads para cada localização sua metade da solução na mesma fase usando um algoritmo aleatório para rearranjas essas palavras.</span><span class="sxs-lookup"><span data-stu-id="73e34-105">The purpose of the following program is to count how many iterations (or phases) are required for two threads to each find their half of the solution on the same phase by using a randomizing algorithm to reshuffle the words.</span></span> <span data-ttu-id="73e34-106">Após cada thread tem embaralhado seus palavras, a operação de pós-fase de barreira compara os dois resultados para ver se a frase completa foi renderizado na ordem correta do word.</span><span class="sxs-lookup"><span data-stu-id="73e34-106">After each thread has shuffled its words, the barrier post-phase operation compares the two results to see if the complete sentence has been rendered in correct word order.</span></span>  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 <span data-ttu-id="73e34-107">Um <xref:System.Threading.Barrier> é um objeto que impede que as tarefas individuais em uma operação paralela continue até que todas as tarefas a barreira de alcance.</span><span class="sxs-lookup"><span data-stu-id="73e34-107">A <xref:System.Threading.Barrier> is an object that prevents individual tasks in a parallel operation from continuing until all tasks reach the barrier.</span></span> <span data-ttu-id="73e34-108">É útil quando ocorre uma operação paralela em fases, e cada fase requer sincronização entre tarefas.</span><span class="sxs-lookup"><span data-stu-id="73e34-108">It is useful when a parallel operation occurs in phases, and each phase requires synchronization between tasks.</span></span> <span data-ttu-id="73e34-109">Neste exemplo, há duas fases para a operação.</span><span class="sxs-lookup"><span data-stu-id="73e34-109">In this example, there are two phases to the operation.</span></span> <span data-ttu-id="73e34-110">A primeira fase, cada tarefa preenche sua seção de buffer com dados.</span><span class="sxs-lookup"><span data-stu-id="73e34-110">In the first phase, each task fills its section of the buffer with data.</span></span> <span data-ttu-id="73e34-111">Quando cada tarefa termina de preencher sua seção, a tarefa sinaliza a barreira que ele está pronto para continuar e, em seguida, aguarda.</span><span class="sxs-lookup"><span data-stu-id="73e34-111">When each task finishes filling its section, the task signals the barrier that it is ready to continue, and then waits.</span></span> <span data-ttu-id="73e34-112">Quando todas as tarefas têm sinalizado a barreira, elas são desbloqueadas e inicia a segunda fase.</span><span class="sxs-lookup"><span data-stu-id="73e34-112">When all tasks have signaled the barrier, they are unblocked and the second phase starts.</span></span> <span data-ttu-id="73e34-113">A barreira é necessária porque a segunda fase requer que cada tarefa tem acesso a todos os dados que foram gerado para esse ponto.</span><span class="sxs-lookup"><span data-stu-id="73e34-113">The barrier is necessary because the second phase requires that each task have access to all the data that has been generated to this point.</span></span> <span data-ttu-id="73e34-114">Sem a barreira, as conclusão de tarefas primeiro tente ler de buffers que não tem sido preenchidos ainda por outras tarefas.</span><span class="sxs-lookup"><span data-stu-id="73e34-114">Without the barrier, the first tasks to complete might try to read from buffers that have not been filled in yet by other tasks.</span></span> <span data-ttu-id="73e34-115">Você pode sincronizar qualquer número das fases dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="73e34-115">You can synchronize any number of phases in this manner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73e34-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73e34-116">See Also</span></span>  
 [<span data-ttu-id="73e34-117">Estruturas de dados para programação paralela</span><span class="sxs-lookup"><span data-stu-id="73e34-117">Data Structures for Parallel Programming</span></span>](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
