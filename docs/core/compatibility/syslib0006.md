---
title: Aviso de SYSLIB0006
description: Saiba mais sobre o obsoletions que gera SYSLIB0006 de aviso de tempo de compilação.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 45d2d8ec6ad99996f8b8f46d0c2e0ac2e02cf450
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333219"
---
# <a name="syslib0006-threadabort-is-not-supported"></a><span data-ttu-id="7023a-103">SYSLIB0006: não há suporte para thread. Abort</span><span class="sxs-lookup"><span data-stu-id="7023a-103">SYSLIB0006: Thread.Abort is not supported</span></span>

<span data-ttu-id="7023a-104">As seguintes APIs estão marcadas como obsoletas, a partir do .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="7023a-104">The following APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="7023a-105">O uso dessas APIs gera aviso `SYSLIB0006` no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="7023a-105">Use of these APIs generates warning `SYSLIB0006` at compile time.</span></span>

- <xref:System.Threading.Thread.Abort?displayProperty=nameWithType>
- <xref:System.Threading.Thread.Abort(System.Object)?displayProperty=nameWithType>

## <a name="workaround"></a><span data-ttu-id="7023a-106">Solução alternativa</span><span class="sxs-lookup"><span data-stu-id="7023a-106">Workaround</span></span>

<span data-ttu-id="7023a-107">Use um <xref:System.Threading.CancellationToken> para anular o processamento de uma unidade de trabalho em vez de chamar <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7023a-107">Use a <xref:System.Threading.CancellationToken> to abort processing of a unit of work instead of calling <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7023a-108">O exemplo a seguir ilustra o uso de <xref:System.Threading.CancellationToken> .</span><span class="sxs-lookup"><span data-stu-id="7023a-108">The following example illustrates the use of <xref:System.Threading.CancellationToken>.</span></span>

```csharp
void ProcessPendingWorkItemsNew(CancellationToken cancellationToken)
{
    if (QueryIsMoreWorkPending())
    {
        // If the CancellationToken is marked as "needs to cancel",
        // this will throw the appropriate exception.
        cancellationToken.ThrowIfCancellationRequested();

        WorkItem work = DequeueWorkItem();
        ProcessWorkItem(work);
    }
}
```

## <a name="see-also"></a><span data-ttu-id="7023a-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7023a-109">See also</span></span>

- [<span data-ttu-id="7023a-110">Thread. Abort é uma alteração de interrupção obsoleta</span><span class="sxs-lookup"><span data-stu-id="7023a-110">Thread.Abort is obsolete - breaking change</span></span>](3.1-5.0.md#threadabort-is-obsolete)
- [<span data-ttu-id="7023a-111">Cancelamento em threads gerenciados</span><span class="sxs-lookup"><span data-stu-id="7023a-111">Cancellation in managed threads</span></span>](../../standard/threading/cancellation-in-managed-threads.md)
