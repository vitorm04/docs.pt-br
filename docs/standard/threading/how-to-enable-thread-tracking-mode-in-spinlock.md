---
title: Como habilitar o modo de controle de thread em SpinLock
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to enable thread-tracking
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3b9671c10889287bc22d64df1fb5c3a2984bd55
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44195274"
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a><span data-ttu-id="dca91-102">Como habilitar o modo de controle de thread em SpinLock</span><span class="sxs-lookup"><span data-stu-id="dca91-102">How to: Enable Thread-Tracking Mode in SpinLock</span></span>
<span data-ttu-id="dca91-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType> é um bloqueio de exclusão mútua de baixo nível que você pode usar para cenários com tempos de espera muito curtos.</span><span class="sxs-lookup"><span data-stu-id="dca91-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType> is a low-level mutual exclusion lock that you can use for scenarios that have very short wait times.</span></span> <span data-ttu-id="dca91-104">O <xref:System.Threading.SpinLock> não oferece reinserção.</span><span class="sxs-lookup"><span data-stu-id="dca91-104"><xref:System.Threading.SpinLock> is not re-entrant.</span></span> <span data-ttu-id="dca91-105">Depois que um thread entra no bloqueio, ele deve sair do bloqueio corretamente antes de poder entrar novamente.</span><span class="sxs-lookup"><span data-stu-id="dca91-105">After a thread enters the lock, it must exit the lock correctly before it can enter again.</span></span> <span data-ttu-id="dca91-106">Normalmente, qualquer tentativa de reintroduzir o bloqueio causaria um deadlock, e os deadlocks podem ser muito difíceis de depurar.</span><span class="sxs-lookup"><span data-stu-id="dca91-106">Typically, any attempt to re-enter the lock would cause deadlock, and deadlocks can be very difficult to debug.</span></span> <span data-ttu-id="dca91-107">Como um auxílio ao desenvolvimento, o <xref:System.Threading.SpinLock?displayProperty=nameWithType> suporta um modo de controle de thread que faz com que uma exceção seja acionada quando um thread tenta reintroduzir um bloqueio que ele já possui.</span><span class="sxs-lookup"><span data-stu-id="dca91-107">As an aid to development, <xref:System.Threading.SpinLock?displayProperty=nameWithType> supports a thread-tracking mode that causes an exception to be thrown when a thread attempts to re-enter a lock that it already holds.</span></span> <span data-ttu-id="dca91-108">Isso permite que você localize mais facilmente o ponto em que o bloqueio não foi encerrado corretamente.</span><span class="sxs-lookup"><span data-stu-id="dca91-108">This lets you more easily locate the point at which the lock was not exited correctly.</span></span> <span data-ttu-id="dca91-109">Você pode ativar o modo de controle de thread usando o construtor <xref:System.Threading.SpinLock> que leva um parâmetro de entrada booleano e passando um argumento de `true`.</span><span class="sxs-lookup"><span data-stu-id="dca91-109">You can turn on thread-tracking mode by using the <xref:System.Threading.SpinLock> constructor that takes a Boolean input parameter, and passing in an argument of `true`.</span></span> <span data-ttu-id="dca91-110">Depois de concluir as fases de desenvolvimento e teste, desative o modo de controle de thread para um melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="dca91-110">After you complete the development and testing phases, turn off thread-tracking mode for better performance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dca91-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dca91-111">Example</span></span>  
 <span data-ttu-id="dca91-112">O exemplo a seguir demonstra o modo de controle de thread.</span><span class="sxs-lookup"><span data-stu-id="dca91-112">The following example demonstrates thread-tracking mode.</span></span> <span data-ttu-id="dca91-113">As linhas que saem corretamente do bloqueio são comentadas para simular um erro de codificação que causa um dos seguintes resultados:</span><span class="sxs-lookup"><span data-stu-id="dca91-113">The lines that correctly exit the lock are commented out to simulate a coding error that causes one of the following results:</span></span>  
  
-   <span data-ttu-id="dca91-114">Uma exceção será lançada se o <xref:System.Threading.SpinLock> foi criado usando um argumento de `true` (`True` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="dca91-114">An exception is thrown if the <xref:System.Threading.SpinLock> was created by using an argument of `true` (`True` in Visual Basic).</span></span>  
  
-   <span data-ttu-id="dca91-115">Um deadlock se o <xref:System.Threading.SpinLock> foi criado usando um argumento de `false` (`False` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="dca91-115">Deadlock if the <xref:System.Threading.SpinLock> was created by using an argument of `false` (`False` in Visual Basic).</span></span>  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="dca91-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dca91-116">See also</span></span>

- [<span data-ttu-id="dca91-117">SpinLock</span><span class="sxs-lookup"><span data-stu-id="dca91-117">SpinLock</span></span>](../../../docs/standard/threading/spinlock.md)
