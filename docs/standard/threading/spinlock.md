---
title: SpinLock
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: efe9b3126b3c952ab156f9ca40752ad8d3fddcd1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="spinlock"></a><span data-ttu-id="59e4a-102">SpinLock</span><span class="sxs-lookup"><span data-stu-id="59e4a-102">SpinLock</span></span>
<span data-ttu-id="59e4a-103">O <xref:System.Threading.SpinLock> estrutura é um nível inferior, exclusão mútua primitivo de sincronização que gira enquanto ele espera para adquirir um bloqueio.</span><span class="sxs-lookup"><span data-stu-id="59e4a-103">The <xref:System.Threading.SpinLock> structure is a low-level, mutual-exclusion synchronization primitive that spins while it waits to acquire a lock.</span></span> <span data-ttu-id="59e4a-104">Em computadores com vários núcleos, quando os tempos de espera são deve ser curto e quando é mínima, a contenção <xref:System.Threading.SpinLock> podem executar melhor do que outros tipos de bloqueios.</span><span class="sxs-lookup"><span data-stu-id="59e4a-104">On multicore computers, when wait times are expected to be short and when contention is minimal, <xref:System.Threading.SpinLock> can perform better than other kinds of locks.</span></span> <span data-ttu-id="59e4a-105">No entanto, recomendamos que você use <xref:System.Threading.SpinLock> somente quando você determinar pela criação de perfil que o <xref:System.Threading.Monitor?displayProperty=nameWithType> método ou o <xref:System.Threading.Interlocked> métodos são significativamente mais lento o desempenho do seu programa.</span><span class="sxs-lookup"><span data-stu-id="59e4a-105">However, we recommend that you use <xref:System.Threading.SpinLock> only when you determine by profiling that the <xref:System.Threading.Monitor?displayProperty=nameWithType> method or the <xref:System.Threading.Interlocked> methods are significantly slowing the performance of your program.</span></span>  
  
 <span data-ttu-id="59e4a-106"><xref:System.Threading.SpinLock>pode resultar em fração de tempo do thread mesmo se ele ainda não tenha adquirido o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="59e4a-106"><xref:System.Threading.SpinLock> may yield the time slice of the thread even if it has not yet acquired the lock.</span></span> <span data-ttu-id="59e4a-107">Isso é feito para evitar inversão de prioridade de thread e para habilitar o coletor de lixo tornar o progresso.</span><span class="sxs-lookup"><span data-stu-id="59e4a-107">It does this to avoid thread-priority inversion, and to enable the garbage collector to make progress.</span></span> <span data-ttu-id="59e4a-108">Quando você usa um <xref:System.Threading.SpinLock>, certifique-se de que nenhum thread pode manter o bloqueio por mais de um período de tempo muito breve, e que nenhum thread pode bloquear enquanto ele mantém o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="59e4a-108">When you use a <xref:System.Threading.SpinLock>, ensure that no thread can hold the lock for more than a very brief time span, and that no thread can block while it holds the lock.</span></span>  
  
 <span data-ttu-id="59e4a-109">Como SpinLock é um tipo de valor, você deve explicitamente passar por referência se quiser que as duas cópias para se referir ao mesmo bloqueio.</span><span class="sxs-lookup"><span data-stu-id="59e4a-109">Because SpinLock is a value type, you must explicitly pass it by reference if you intend the two copies to refer to the same lock.</span></span>  
  
 <span data-ttu-id="59e4a-110">Para obter mais informações sobre como usar esse tipo, consulte <xref:System.Threading.SpinLock?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="59e4a-110">For more information about how to use this type, see <xref:System.Threading.SpinLock?displayProperty=nameWithType>.</span></span> <span data-ttu-id="59e4a-111">Para obter um exemplo, consulte [como: usar SpinLock para sincronização de baixo nível](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="59e4a-111">For an example, see [How to: Use SpinLock for Low-Level Synchronization](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).</span></span>  
  
 <span data-ttu-id="59e4a-112"><xref:System.Threading.SpinLock>oferece suporte a um *thread*-*controle* modo que você pode usar durante a fase de desenvolvimento para ajudar a controlar o thread que está mantendo o bloqueio em um momento específico.</span><span class="sxs-lookup"><span data-stu-id="59e4a-112"><xref:System.Threading.SpinLock> supports a *thread*-*tracking* mode that you can use during the development phase to help track the thread that is holding the lock at a specific time.</span></span> <span data-ttu-id="59e4a-113">Modo de controle de thread é muito útil para depuração, mas é recomendável que você desativá-lo na versão de lançamento do seu programa porque ele pode diminuir o desempenho.</span><span class="sxs-lookup"><span data-stu-id="59e4a-113">Thread-tracking mode is very useful for debugging, but we recommend that you turn it off in the release version of your program because it may slow performance.</span></span> <span data-ttu-id="59e4a-114">Para obter mais informações, consulte [como: modo de controle de habilitar o Thread em SpinLock](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).</span><span class="sxs-lookup"><span data-stu-id="59e4a-114">For more information, see [How to: Enable Thread-Tracking Mode in SpinLock](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59e4a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59e4a-115">See Also</span></span>  
 [<span data-ttu-id="59e4a-116">Objetos e recursos de threading</span><span class="sxs-lookup"><span data-stu-id="59e4a-116">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
