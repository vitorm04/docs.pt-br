---
title: Aviso de SYSLIB0004
description: Saiba mais sobre o obsoletions que gera SYSLIB0004 de aviso de tempo de compilação.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: ba7cd8a890a89000b241d286c9d8069ba1398849
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333210"
---
# <a name="syslib0004-the-constrained-execution-region-cer-feature-is-not-supported"></a><span data-ttu-id="55d72-103">SYSLIB0004: não há suporte para o recurso CER (região de execução restrita)</span><span class="sxs-lookup"><span data-stu-id="55d72-103">SYSLIB0004: The constrained execution region (CER) feature is not supported</span></span>

<span data-ttu-id="55d72-104">Há suporte para o recurso [cer (regiões de execução restrita)](../../framework/performance/constrained-execution-regions.md) somente no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="55d72-104">The [Constrained execution regions (CER)](../../framework/performance/constrained-execution-regions.md) feature is supported only in .NET Framework.</span></span> <span data-ttu-id="55d72-105">Assim, várias APIs relacionadas à CER são marcadas como obsoletas, começando no .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="55d72-105">As such, various CER-related APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="55d72-106">O uso dessas APIs gera aviso `SYSLIB0004` no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="55d72-106">Using these APIs generates warning `SYSLIB0004` at compile time.</span></span>

<span data-ttu-id="55d72-107">As seguintes APIs relacionadas a CER são obsoletas:</span><span class="sxs-lookup"><span data-stu-id="55d72-107">The following CER-related APIs are obsolete:</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup(System.Runtime.CompilerServices.RuntimeHelpers.TryCode,System.Runtime.CompilerServices.RuntimeHelpers.CleanupCode,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegionsNoOP?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareContractedDelegate(System.Delegate)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ProbeForSufficientStack?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Cer?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Consistency?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute?displayProperty=nameWithType>

## <a name="see-also"></a><span data-ttu-id="55d72-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55d72-108">See also</span></span>

- [<span data-ttu-id="55d72-109">Regiões de execução restrita</span><span class="sxs-lookup"><span data-stu-id="55d72-109">Constrained execution regions</span></span>](../../framework/performance/constrained-execution-regions.md)
