---
title: Aviso de SYSLIB0005
description: Saiba mais sobre o obsoletion que gera SYSLIB0005 de aviso de tempo de compilação.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 8a9893d81c781335014c8b970c460b5a4241ed18
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333209"
---
# <a name="syslib0005-the-global-assembly-cache-gac-is-not-supported"></a><span data-ttu-id="51fef-103">SYSLIB0005: não há suporte para o GAC (cache de assembly global)</span><span class="sxs-lookup"><span data-stu-id="51fef-103">SYSLIB0005: The global assembly cache (GAC) is not supported</span></span>

<span data-ttu-id="51fef-104">O .NET Core e o .NET 5,0 e versões posteriores eliminam o conceito do GAC (cache de assembly global) que estava presente no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="51fef-104">.NET Core and .NET 5.0 and later versions eliminate the concept of the global assembly cache (GAC) that was present in .NET Framework.</span></span> <span data-ttu-id="51fef-105">Para ajudar os desenvolvedores a se afastar dessas APIs, algumas APIs relacionadas ao GAC são marcadas como obsoletas, a partir do .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="51fef-105">To help steer developers away from these APIs, some GAC-related APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="51fef-106">O uso dessas APIs gera aviso `SYSLIB0005` no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="51fef-106">Using these APIs generates warning `SYSLIB0005` at compile time.</span></span>

<span data-ttu-id="51fef-107">As seguintes APIs relacionadas ao GAC estão marcadas como obsoletas:</span><span class="sxs-lookup"><span data-stu-id="51fef-107">The following GAC-related APIs are marked obsolete:</span></span>

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType>

  <span data-ttu-id="51fef-108">Bibliotecas e aplicativos não devem usar a <xref:System.Reflection.Assembly.GlobalAssemblyCache> API para fazer determinações sobre o comportamento de tempo de execução, como sempre retorna `false` no .NET Core e no .NET 5 +.</span><span class="sxs-lookup"><span data-stu-id="51fef-108">Libraries and apps should not use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> API to make determinations about run-time behavior, as it always returns `false` in .NET Core and .NET 5+.</span></span>

## <a name="workaround"></a><span data-ttu-id="51fef-109">Solução alternativa</span><span class="sxs-lookup"><span data-stu-id="51fef-109">Workaround</span></span>

<span data-ttu-id="51fef-110">Se seu aplicativo consulta a <xref:System.Reflection.Assembly.GlobalAssemblyCache> propriedade, considere remover a chamada.</span><span class="sxs-lookup"><span data-stu-id="51fef-110">If your application queries the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property, consider removing the call.</span></span> <span data-ttu-id="51fef-111">Se você usar o <xref:System.Reflection.Assembly.GlobalAssemblyCache> valor para escolher entre um "assembly no GAC"-Flow versus um "assembly que não está no GAC"-Flow em tempo de execução, reconsidere se o fluxo ainda faz sentido para um aplicativo .NET 5 +.</span><span class="sxs-lookup"><span data-stu-id="51fef-111">If you use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> value to choose between an "assembly in the GAC"-flow vs. an "assembly not in the GAC"-flow at run time, reconsider whether the flow still makes sense for a .NET 5+ application.</span></span>

## <a name="see-also"></a><span data-ttu-id="51fef-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51fef-112">See also</span></span>

- [<span data-ttu-id="51fef-113">Cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="51fef-113">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
