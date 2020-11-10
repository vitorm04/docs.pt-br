---
title: Aviso de SYSLIB0009
description: Saiba mais sobre o obsoletions que gera SYSLIB0009 de aviso de tempo de compilação.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 47b4f595a54800370da90f61d838c665df8b6091
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94439970"
---
# <a name="syslib0009-the-authenticationmanager-authenticate-and-preauthenticate-methods-are-not-supported"></a><span data-ttu-id="58112-103">SYSLIB0009: não há suporte para os métodos de autenticação e de autenticidade do CustomTargetNameDictionary</span><span class="sxs-lookup"><span data-stu-id="58112-103">SYSLIB0009: The AuthenticationManager Authenticate and PreAuthenticate methods are not supported</span></span>

<span data-ttu-id="58112-104">As seguintes APIs estão marcadas como obsoletas, a partir do .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="58112-104">The following APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="58112-105">O uso dessas APIs gera aviso `SYSLIB0009` no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="58112-105">Use of these APIs generates warning `SYSLIB0009` at compile time.</span></span>

- <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType>
- <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType>

## <a name="suppress-the-warning"></a><span data-ttu-id="58112-106">Suprimir o aviso</span><span class="sxs-lookup"><span data-stu-id="58112-106">Suppress the warning</span></span>

<span data-ttu-id="58112-107">Se você não puder alterar seu código, poderá suprimir o aviso por meio de uma `#pragma` diretiva ou `<NoWarn>` configuração de projeto.</span><span class="sxs-lookup"><span data-stu-id="58112-107">If you cannot change your code, you can suppress the warning through a `#pragma` directive or a `<NoWarn>` project setting.</span></span> <span data-ttu-id="58112-108">Para obter exemplos, consulte [suprimir avisos](syslib-obsoletions.md#suppress-warnings).</span><span class="sxs-lookup"><span data-stu-id="58112-108">For examples, see [Suppress warnings](syslib-obsoletions.md#suppress-warnings).</span></span>
