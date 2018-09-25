---
title: Negociação de segurança e tempo limite
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
author: BrucePerlerMS
ms.openlocfilehash: 6b6c9c6ed44eb3ebefb21f2fbff1e73171262ed7
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47088302"
---
# <a name="security-negotiation-and-timeouts"></a><span data-ttu-id="63757-102">Negociação de segurança e tempo limite</span><span class="sxs-lookup"><span data-stu-id="63757-102">Security Negotiation and Timeouts</span></span>
<span data-ttu-id="63757-103">Quando os clientes e serviços de autenticação, o Windows Communication Foundation (WCF) suporta um modo em que a credencial de serviço é negociada como parte da autenticação.</span><span class="sxs-lookup"><span data-stu-id="63757-103">When clients and services authenticate, Windows Communication Foundation (WCF) supports a mode where the service credential is negotiated as part of authentication.</span></span> <span data-ttu-id="63757-104">Nesses cenários, uma troca potencialmente multi-segmentos ocorre entre o cliente e o serviço para propagar a credencial de serviço ao cliente.</span><span class="sxs-lookup"><span data-stu-id="63757-104">In such scenarios, a potentially multi-leg exchange occurs between the client and the service to propagate the service credential to the client.</span></span> <span data-ttu-id="63757-105">O <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> propriedade controla o quanto o exchange multi-segmentos pode demorar para ser concluída.</span><span class="sxs-lookup"><span data-stu-id="63757-105">The <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property controls how long the multi-leg exchange can take to complete.</span></span> <span data-ttu-id="63757-106">No entanto, esse tempo limite se aplica somente se o exchange, na verdade, demorar mais que uma única solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="63757-106">However, this timeout only applies if the exchange actually takes more that a single request-response.</span></span> <span data-ttu-id="63757-107">Em casos em que a negociação é realizada em uma única ida e volta, o tempo limite não se aplica.</span><span class="sxs-lookup"><span data-stu-id="63757-107">In cases where the negotiation completes in a single round trip, the timeout does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63757-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63757-108">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [<span data-ttu-id="63757-109">Como definir uma distorção máxima do relógio</span><span class="sxs-lookup"><span data-stu-id="63757-109">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
