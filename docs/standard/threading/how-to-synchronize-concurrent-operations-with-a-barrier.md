---
title: Como sincronizar operações simultâneas com uma barreira
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16dc60fa9cd8782efbe1b6028413138b5991839e
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45624834"
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a><span data-ttu-id="cdb92-102">Como sincronizar operações simultâneas com uma barreira</span><span class="sxs-lookup"><span data-stu-id="cdb92-102">How to: Synchronize Concurrent Operations with a Barrier</span></span>
<span data-ttu-id="cdb92-103">O exemplo a seguir mostra como sincronizar tarefas simultâneas com uma <xref:System.Threading.Barrier>.</span><span class="sxs-lookup"><span data-stu-id="cdb92-103">The following example shows how to synchronize concurrent tasks with a <xref:System.Threading.Barrier>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdb92-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cdb92-104">Example</span></span>  
 <span data-ttu-id="cdb92-105">O objetivo do programa a seguir é contar quantas iterações (ou fases) são necessárias para dois threads para que cada um localize sua metade da solução na mesma fase usando um algoritmo aleatório para reorganizar as palavras.</span><span class="sxs-lookup"><span data-stu-id="cdb92-105">The purpose of the following program is to count how many iterations (or phases) are required for two threads to each find their half of the solution on the same phase by using a randomizing algorithm to reshuffle the words.</span></span> <span data-ttu-id="cdb92-106">Após cada thread ter misturado suas palavras, a operação de pós-fase de barreira comparará os dois resultados para ver se a frase completa foi renderizada na ordem de palavras correta.</span><span class="sxs-lookup"><span data-stu-id="cdb92-106">After each thread has shuffled its words, the barrier post-phase operation compares the two results to see if the complete sentence has been rendered in correct word order.</span></span>  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 <span data-ttu-id="cdb92-107">Uma <xref:System.Threading.Barrier> é um objeto que impede que as tarefas individuais em uma operação paralela continuem até que todas as tarefas atinjam a barreira.</span><span class="sxs-lookup"><span data-stu-id="cdb92-107">A <xref:System.Threading.Barrier> is an object that prevents individual tasks in a parallel operation from continuing until all tasks reach the barrier.</span></span> <span data-ttu-id="cdb92-108">É útil quando uma operação paralela ocorre em fases e cada fase requer a sincronização entre as tarefas.</span><span class="sxs-lookup"><span data-stu-id="cdb92-108">It is useful when a parallel operation occurs in phases, and each phase requires synchronization between tasks.</span></span> <span data-ttu-id="cdb92-109">Neste exemplo, há duas fases para a operação.</span><span class="sxs-lookup"><span data-stu-id="cdb92-109">In this example, there are two phases to the operation.</span></span> <span data-ttu-id="cdb92-110">Na primeira fase, cada tarefa preenche sua seção do buffer com dados.</span><span class="sxs-lookup"><span data-stu-id="cdb92-110">In the first phase, each task fills its section of the buffer with data.</span></span> <span data-ttu-id="cdb92-111">Quando cada tarefa termina de preencher sua seção, a tarefa sinaliza a barreira que ela está pronta para continuar e, em seguida, aguarda.</span><span class="sxs-lookup"><span data-stu-id="cdb92-111">When each task finishes filling its section, the task signals the barrier that it is ready to continue, and then waits.</span></span> <span data-ttu-id="cdb92-112">Quando todas as tarefas sinalizarem a barreira, elas serão desbloqueadas e a segunda fase começará.</span><span class="sxs-lookup"><span data-stu-id="cdb92-112">When all tasks have signaled the barrier, they are unblocked and the second phase starts.</span></span> <span data-ttu-id="cdb92-113">A barreira é necessária porque a segunda fase requer que cada tarefa tenha acesso a todos os dados que foram gerados até este ponto.</span><span class="sxs-lookup"><span data-stu-id="cdb92-113">The barrier is necessary because the second phase requires that each task have access to all the data that has been generated to this point.</span></span> <span data-ttu-id="cdb92-114">Sem a barreira, as primeiras tarefas a serem concluídas podem tentar ler de buffers que ainda não foram preenchidos por outras tarefas.</span><span class="sxs-lookup"><span data-stu-id="cdb92-114">Without the barrier, the first tasks to complete might try to read from buffers that have not been filled in yet by other tasks.</span></span> <span data-ttu-id="cdb92-115">Você pode sincronizar qualquer número das fases dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="cdb92-115">You can synchronize any number of phases in this manner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdb92-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cdb92-116">See also</span></span>

- [<span data-ttu-id="cdb92-117">Estruturas de dados para programação paralela</span><span class="sxs-lookup"><span data-stu-id="cdb92-117">Data Structures for Parallel Programming</span></span>](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
