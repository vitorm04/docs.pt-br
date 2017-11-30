---
title: Como habilitar o modo de controle de thread em SpinLock
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
helpviewer_keywords: SpinLock, how to enable thread-tracking
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca5f1b6eace7a24a6bbb7fd541858246828fa757
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a><span data-ttu-id="5142f-102">Como habilitar o modo de controle de thread em SpinLock</span><span class="sxs-lookup"><span data-stu-id="5142f-102">How to: Enable Thread-Tracking Mode in SpinLock</span></span>
<span data-ttu-id="5142f-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType>é um bloqueio de exclusão mútua de baixo nível que você pode usar para cenários que têm tempos de espera muito curto.</span><span class="sxs-lookup"><span data-stu-id="5142f-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType> is a low-level mutual exclusion lock that you can use for scenarios that have very short wait times.</span></span> <span data-ttu-id="5142f-104"><xref:System.Threading.SpinLock>não é de reinserção.</span><span class="sxs-lookup"><span data-stu-id="5142f-104"><xref:System.Threading.SpinLock> is not re-entrant.</span></span> <span data-ttu-id="5142f-105">Depois que um thread entra no bloqueio, ele deve fechar o bloqueio corretamente antes de ela pode entrar novamente.</span><span class="sxs-lookup"><span data-stu-id="5142f-105">After a thread enters the lock, it must exit the lock correctly before it can enter again.</span></span> <span data-ttu-id="5142f-106">Em geral, qualquer tentativa de inserir novamente o bloqueio poderia causar bloqueio e deadlocks podem ser muito difícil de depurar.</span><span class="sxs-lookup"><span data-stu-id="5142f-106">Typically, any attempt to re-enter the lock would cause deadlock, and deadlocks can be very difficult to debug.</span></span> <span data-ttu-id="5142f-107">Como um auxílio para desenvolvimento e <xref:System.Threading.SpinLock?displayProperty=nameWithType> oferece suporte a um modo de controle de thread que gera uma exceção seja lançada quando um thread tenta inserir novamente um bloqueio que ela já contém.</span><span class="sxs-lookup"><span data-stu-id="5142f-107">As an aid to development, <xref:System.Threading.SpinLock?displayProperty=nameWithType> supports a thread-tracking mode that causes an exception to be thrown when a thread attempts to re-enter a lock that it already holds.</span></span> <span data-ttu-id="5142f-108">Isso permite que mais fácil localizam o ponto em que o bloqueio não foi encerrado corretamente.</span><span class="sxs-lookup"><span data-stu-id="5142f-108">This lets you more easily locate the point at which the lock was not exited correctly.</span></span> <span data-ttu-id="5142f-109">Você pode ativar o modo de controle de thread usando o <xref:System.Threading.SpinLock> construtor que usa um valor booleano de entrada e passando um argumento de `true`.</span><span class="sxs-lookup"><span data-stu-id="5142f-109">You can turn on thread-tracking mode by using the <xref:System.Threading.SpinLock> constructor that takes a Boolean input parameter, and passing in an argument of `true`.</span></span> <span data-ttu-id="5142f-110">Depois de concluir as fases de desenvolvimento e teste, desative o modo de controle de thread para melhorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="5142f-110">After you complete the development and testing phases, turn off thread-tracking mode for better performance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5142f-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5142f-111">Example</span></span>  
 <span data-ttu-id="5142f-112">O exemplo a seguir demonstra o modo de controle de thread.</span><span class="sxs-lookup"><span data-stu-id="5142f-112">The following example demonstrates thread-tracking mode.</span></span> <span data-ttu-id="5142f-113">As linhas que sair corretamente o bloqueio são comentadas para simular um erro de código que faz com que um dos seguintes resultados:</span><span class="sxs-lookup"><span data-stu-id="5142f-113">The lines that correctly exit the lock are commented out to simulate a coding error that causes one of the following results:</span></span>  
  
-   <span data-ttu-id="5142f-114">Uma exceção será lançada se o <xref:System.Threading.SpinLock> foi criado usando um argumento de `true` (`True` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="5142f-114">An exception is thrown if the <xref:System.Threading.SpinLock> was created by using an argument of `true` (`True` in Visual Basic).</span></span>  
  
-   <span data-ttu-id="5142f-115">Se um deadlock de <xref:System.Threading.SpinLock> foi criado usando um argumento de `false` (`False` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="5142f-115">Deadlock if the <xref:System.Threading.SpinLock> was created by using an argument of `false` (`False` in Visual Basic).</span></span>  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="5142f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5142f-116">See Also</span></span>  
 [<span data-ttu-id="5142f-117">SpinLock</span><span class="sxs-lookup"><span data-stu-id="5142f-117">SpinLock</span></span>](../../../docs/standard/threading/spinlock.md)
