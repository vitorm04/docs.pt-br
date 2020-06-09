---
title: Como determinar a versão de descoberta de uma solicitação de investigação
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 2b7e42714ae1d16a84bcb6f0fc79cf5b376a7a16
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595408"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="9debb-102">Como determinar a versão de descoberta de uma solicitação de investigação</span><span class="sxs-lookup"><span data-stu-id="9debb-102">How to:Determine the Discovery Version of a Probe Request</span></span>

<span data-ttu-id="9debb-103">Um proxy de descoberta pode expor vários pontos de extremidade de descoberta usando diferentes versões de descoberta.</span><span class="sxs-lookup"><span data-stu-id="9debb-103">A discovery proxy may expose multiple discovery endpoints using different discovery versions.</span></span> <span data-ttu-id="9debb-104">Quando uma solicitação de investigação de multicast UDP chega ao proxy, o proxy deve responder com uma mensagem de supressão de multicast.</span><span class="sxs-lookup"><span data-stu-id="9debb-104">When a UDP multicast Probe request arrives at the proxy, the proxy should respond with a multicast suppression message.</span></span> <span data-ttu-id="9debb-105">Para fazer isso, seria necessário saber a versão de descoberta da solicitação.</span><span class="sxs-lookup"><span data-stu-id="9debb-105">In order to do this, it would have to know the discovery version of the request.</span></span>

## <a name="to-determine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="9debb-106">Para determinar a versão de descoberta de uma solicitação de investigação</span><span class="sxs-lookup"><span data-stu-id="9debb-106">To Determine the Discovery Version of a Probe Request</span></span>

<span data-ttu-id="9debb-107">No método que responde a uma solicitação de investigação (por exemplo <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> ), use a <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> propriedade estática para pesquisar por um <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> , conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="9debb-107">In the method that responds to a Probe request (for example <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType>) use the static <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> property to search for a <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension>, as shown in the following code.</span></span>

```csharp
DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();
// Access the discovery version from the DiscoveryOperationContextExtension
doce.DiscoveryVersion;
```

## <a name="see-also"></a><span data-ttu-id="9debb-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9debb-108">See also</span></span>

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>
- [<span data-ttu-id="9debb-109">Implementando um proxy de descoberta</span><span class="sxs-lookup"><span data-stu-id="9debb-109">Implementing a Discovery Proxy</span></span>](implementing-a-discovery-proxy.md)
