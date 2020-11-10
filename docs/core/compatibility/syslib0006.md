---
title: Aviso de SYSLIB0006
description: Saiba mais sobre o obsoletions que gera SYSLIB0006 de aviso de tempo de compilação.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 222b669a8a0260713e85721e6031144bb7bda5cc
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440654"
---
# <a name="syslib0006-threadabort-is-not-supported"></a>SYSLIB0006: não há suporte para thread. Abort

As seguintes APIs estão marcadas como obsoletas, a partir do .NET 5,0. O uso dessas APIs gera aviso `SYSLIB0006` no momento da compilação.

- <xref:System.Threading.Thread.Abort?displayProperty=nameWithType>
- <xref:System.Threading.Thread.Abort(System.Object)?displayProperty=nameWithType>

## <a name="workarounds"></a>Soluções Alternativas

Use um <xref:System.Threading.CancellationToken> para anular o processamento de uma unidade de trabalho em vez de chamar <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> . O exemplo a seguir ilustra o uso de <xref:System.Threading.CancellationToken> .

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

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a>Confira também

- [Thread. Abort é uma alteração de interrupção obsoleta](3.1-5.0.md#threadabort-is-obsolete)
- [Cancelamento em threads gerenciados](../../standard/threading/cancellation-in-managed-threads.md)
