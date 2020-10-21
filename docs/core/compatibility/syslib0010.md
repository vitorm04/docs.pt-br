---
title: Aviso de SYSLIB0010
description: Saiba mais sobre o obsoletions que gera SYSLIB0010 de aviso de tempo de compilação.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: dcd331aa5c68381ea29848bc54ee4b1a5e75330d
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333201"
---
# <a name="syslib0010-unsupported-remoting-apis"></a><span data-ttu-id="837f4-103">SYSLIB0010: APIs de comunicação remota sem suporte</span><span class="sxs-lookup"><span data-stu-id="837f4-103">SYSLIB0010: Unsupported remoting APIs</span></span>

<span data-ttu-id="837f4-104">A [comunicação remota do .net](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) é uma tecnologia herdada, e a infraestrutura existe somente no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="837f4-104">[.NET remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) is a legacy technology, and the infrastructure exists only in .NET Framework.</span></span> <span data-ttu-id="837f4-105">As seguintes APIs relacionadas a comunicação remota são marcadas como obsoletas, a partir do .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="837f4-105">The following remoting-related APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="837f4-106">Usá-los no código gera aviso `SYSLIB0010` no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="837f4-106">Using them in code generates warning `SYSLIB0010` at compile time.</span></span>

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType>

## <a name="workaround"></a><span data-ttu-id="837f4-107">Solução alternativa</span><span class="sxs-lookup"><span data-stu-id="837f4-107">Workaround</span></span>

<span data-ttu-id="837f4-108">Considere usar o WCF ou serviços REST baseados em HTTP para se comunicar com objetos em outros aplicativos ou entre computadores.</span><span class="sxs-lookup"><span data-stu-id="837f4-108">Consider using WCF or HTTP-based REST services to communicate with objects in other applications or across machines.</span></span> <span data-ttu-id="837f4-109">Para obter mais informações, consulte [.NET Framework Technologies indisponíveis no .NET Core](../porting/net-framework-tech-unavailable.md).</span><span class="sxs-lookup"><span data-stu-id="837f4-109">For more information, see [.NET Framework technologies unavailable on .NET Core](../porting/net-framework-tech-unavailable.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="837f4-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="837f4-110">See also</span></span>

- <span data-ttu-id="837f4-111">[Comunicação remota do .NET](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))</span><span class="sxs-lookup"><span data-stu-id="837f4-111">[.NET remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))</span></span>
