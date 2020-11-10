---
title: Aviso de SYSLIB0010
description: Saiba mais sobre o obsoletions que gera SYSLIB0010 de aviso de tempo de compilação.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 824423d58802d4a286bfed98422341097985990f
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440602"
---
# <a name="syslib0010-unsupported-remoting-apis"></a><span data-ttu-id="84d0f-103">SYSLIB0010: APIs de comunicação remota sem suporte</span><span class="sxs-lookup"><span data-stu-id="84d0f-103">SYSLIB0010: Unsupported remoting APIs</span></span>

<span data-ttu-id="84d0f-104">A [comunicação remota do .net](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) é uma tecnologia herdada, e a infraestrutura existe somente no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="84d0f-104">[.NET remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) is a legacy technology, and the infrastructure exists only in .NET Framework.</span></span> <span data-ttu-id="84d0f-105">As seguintes APIs relacionadas a comunicação remota são marcadas como obsoletas, a partir do .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="84d0f-105">The following remoting-related APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="84d0f-106">Usá-los no código gera aviso `SYSLIB0010` no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="84d0f-106">Using them in code generates warning `SYSLIB0010` at compile time.</span></span>

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="84d0f-107">Soluções Alternativas</span><span class="sxs-lookup"><span data-stu-id="84d0f-107">Workarounds</span></span>

<span data-ttu-id="84d0f-108">Considere usar o WCF ou serviços REST baseados em HTTP para se comunicar com objetos em outros aplicativos ou entre computadores.</span><span class="sxs-lookup"><span data-stu-id="84d0f-108">Consider using WCF or HTTP-based REST services to communicate with objects in other applications or across machines.</span></span> <span data-ttu-id="84d0f-109">Para obter mais informações, consulte [.NET Framework Technologies indisponíveis no .NET Core](../porting/net-framework-tech-unavailable.md).</span><span class="sxs-lookup"><span data-stu-id="84d0f-109">For more information, see [.NET Framework technologies unavailable on .NET Core](../porting/net-framework-tech-unavailable.md).</span></span>

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="84d0f-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="84d0f-110">See also</span></span>

- <span data-ttu-id="84d0f-111">[Comunicação remota do .NET](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))</span><span class="sxs-lookup"><span data-stu-id="84d0f-111">[.NET remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))</span></span>
