---
title: Aviso de SYSLIB0008
description: Saiba mais sobre o obsoletion que gera SYSLIB0008 de aviso de tempo de compilação.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 22ac5b4c5f57ec3f92585ee8d1f8cf278a15dbb0
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440589"
---
# <a name="syslib0008-createpdbgenerator-is-not-supported"></a><span data-ttu-id="8c3bd-103">SYSLIB0008: não há suporte para CreatePdbGenerator</span><span class="sxs-lookup"><span data-stu-id="8c3bd-103">SYSLIB0008: CreatePdbGenerator is not supported</span></span>

<span data-ttu-id="8c3bd-104">A <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> API está marcada como obsoleta, começando no .net 5,0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-104">The <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> API is marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="8c3bd-105">O uso dessa API gera aviso `SYSLIB0008` no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-105">Using this API generates warning `SYSLIB0008` at compile time.</span></span>

## <a name="suppress-the-warning"></a><span data-ttu-id="8c3bd-106">Suprimir o aviso</span><span class="sxs-lookup"><span data-stu-id="8c3bd-106">Suppress the warning</span></span>

<span data-ttu-id="8c3bd-107">Se você não puder alterar seu código, poderá suprimir o aviso por meio de uma `#pragma` diretiva ou `<NoWarn>` configuração de projeto.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-107">If you cannot change your code, you can suppress the warning through a `#pragma` directive or a `<NoWarn>` project setting.</span></span> <span data-ttu-id="8c3bd-108">Para obter exemplos, consulte [suprimir avisos](syslib-obsoletions.md#suppress-warnings).</span><span class="sxs-lookup"><span data-stu-id="8c3bd-108">For examples, see [Suppress warnings](syslib-obsoletions.md#suppress-warnings).</span></span>
