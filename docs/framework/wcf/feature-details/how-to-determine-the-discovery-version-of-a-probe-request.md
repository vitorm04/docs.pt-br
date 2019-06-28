---
title: Como determinar a versão de descoberta de uma solicitação de investigação
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 8fbc3936278a5c6f403f48b59390c69c64378004
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425264"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="1318e-102">Como determinar a versão de descoberta de uma solicitação de investigação</span><span class="sxs-lookup"><span data-stu-id="1318e-102">How to:Determine the Discovery Version of a Probe Request</span></span>

<span data-ttu-id="1318e-103">Um proxy de descoberta pode expor vários pontos de extremidade de descoberta usando versões diferentes de descoberta.</span><span class="sxs-lookup"><span data-stu-id="1318e-103">A discovery proxy may expose multiple discovery endpoints using different discovery versions.</span></span> <span data-ttu-id="1318e-104">Quando um UDP multicast solicitação de investigação chega no proxy, o proxy deve responder com uma mensagem de supressão multicast.</span><span class="sxs-lookup"><span data-stu-id="1318e-104">When a UDP multicast Probe request arrives at the proxy, the proxy should respond with a multicast suppression message.</span></span> <span data-ttu-id="1318e-105">Para fazer isso, ele precisa saber a versão de descoberta da solicitação.</span><span class="sxs-lookup"><span data-stu-id="1318e-105">In order to do this, it would have to know the discovery version of the request.</span></span>

## <a name="to-determine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="1318e-106">Para determinar a versão de uma solicitação de investigação de descoberta</span><span class="sxs-lookup"><span data-stu-id="1318e-106">To Determine the Discovery Version of a Probe Request</span></span>

<span data-ttu-id="1318e-107">No método que responde a uma solicitação de investigação (por exemplo <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType>) use estático <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> propriedade para pesquisar um <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension>, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="1318e-107">In the method that responds to a Probe request (for example <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType>) use the static <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> property to search for a <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension>, as shown in the following code.</span></span>

```csharp
DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();
// Access the discovery version from the DiscoveryOperationContextExtension
doce.DiscoveryVersion;
```

## <a name="see-also"></a><span data-ttu-id="1318e-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1318e-108">See also</span></span>

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>
- [<span data-ttu-id="1318e-109">Implementando um proxy de descoberta</span><span class="sxs-lookup"><span data-stu-id="1318e-109">Implementing a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)
