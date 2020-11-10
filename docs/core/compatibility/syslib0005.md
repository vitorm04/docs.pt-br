---
title: Aviso de SYSLIB0005
description: Saiba mais sobre o obsoletion que gera SYSLIB0005 de aviso de tempo de compilação.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 8e5420b5cfaa9515ed7a3ac4472dc5d4e49f5bcb
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94439996"
---
# <a name="syslib0005-the-global-assembly-cache-gac-is-not-supported"></a><span data-ttu-id="c8209-103">SYSLIB0005: não há suporte para o GAC (cache de assembly global)</span><span class="sxs-lookup"><span data-stu-id="c8209-103">SYSLIB0005: The global assembly cache (GAC) is not supported</span></span>

<span data-ttu-id="c8209-104">O .NET Core e o .NET 5,0 e versões posteriores eliminam o conceito do GAC (cache de assembly global) que estava presente no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c8209-104">.NET Core and .NET 5.0 and later versions eliminate the concept of the global assembly cache (GAC) that was present in .NET Framework.</span></span> <span data-ttu-id="c8209-105">Para ajudar os desenvolvedores a se afastar dessas APIs, algumas APIs relacionadas ao GAC são marcadas como obsoletas, a partir do .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="c8209-105">To help steer developers away from these APIs, some GAC-related APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="c8209-106">O uso dessas APIs gera aviso `SYSLIB0005` no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="c8209-106">Using these APIs generates warning `SYSLIB0005` at compile time.</span></span>

<span data-ttu-id="c8209-107">As seguintes APIs relacionadas ao GAC estão marcadas como obsoletas:</span><span class="sxs-lookup"><span data-stu-id="c8209-107">The following GAC-related APIs are marked obsolete:</span></span>

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType>

  <span data-ttu-id="c8209-108">Bibliotecas e aplicativos não devem usar a <xref:System.Reflection.Assembly.GlobalAssemblyCache> API para fazer determinações sobre o comportamento de tempo de execução, como sempre retorna `false` no .NET Core e no .NET 5 +.</span><span class="sxs-lookup"><span data-stu-id="c8209-108">Libraries and apps should not use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> API to make determinations about run-time behavior, as it always returns `false` in .NET Core and .NET 5+.</span></span>

## <a name="workarounds"></a><span data-ttu-id="c8209-109">Soluções Alternativas</span><span class="sxs-lookup"><span data-stu-id="c8209-109">Workarounds</span></span>

<span data-ttu-id="c8209-110">Se seu aplicativo consulta a <xref:System.Reflection.Assembly.GlobalAssemblyCache> propriedade, considere remover a chamada.</span><span class="sxs-lookup"><span data-stu-id="c8209-110">If your application queries the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property, consider removing the call.</span></span> <span data-ttu-id="c8209-111">Se você usar o <xref:System.Reflection.Assembly.GlobalAssemblyCache> valor para escolher entre um "assembly no GAC"-Flow versus um "assembly que não está no GAC"-Flow em tempo de execução, reconsidere se o fluxo ainda faz sentido para um aplicativo .NET 5 +.</span><span class="sxs-lookup"><span data-stu-id="c8209-111">If you use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> value to choose between an "assembly in the GAC"-flow vs. an "assembly not in the GAC"-flow at run time, reconsider whether the flow still makes sense for a .NET 5+ application.</span></span>

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="c8209-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="c8209-112">See also</span></span>

- [<span data-ttu-id="c8209-113">Cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="c8209-113">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
