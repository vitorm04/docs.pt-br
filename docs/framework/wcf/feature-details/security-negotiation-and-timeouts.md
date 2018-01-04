---
title: "Negociação de segurança e tempo limite"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 6fbee18d31cb1774300c14587b0f7d973a4996ed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="security-negotiation-and-timeouts"></a><span data-ttu-id="49f7a-102">Negociação de segurança e tempo limite</span><span class="sxs-lookup"><span data-stu-id="49f7a-102">Security Negotiation and Timeouts</span></span>
<span data-ttu-id="49f7a-103">Quando os clientes e serviços de autenticação, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] suporta o modo em que a credencial de serviço é negociada como parte da autenticação.</span><span class="sxs-lookup"><span data-stu-id="49f7a-103">When clients and services authenticate, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] supports a mode where the service credential is negotiated as part of authentication.</span></span> <span data-ttu-id="49f7a-104">Nesses cenários, uma troca potencialmente vários trecho ocorre entre o cliente e o serviço para propagar as credenciais do serviço ao cliente.</span><span class="sxs-lookup"><span data-stu-id="49f7a-104">In such scenarios, a potentially multi-leg exchange occurs between the client and the service to propagate the service credential to the client.</span></span> <span data-ttu-id="49f7a-105">O <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> propriedade controla quanto tempo a troca de multi-segmento de pode demorar para ser concluída.</span><span class="sxs-lookup"><span data-stu-id="49f7a-105">The <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property controls how long the multi-leg exchange can take to complete.</span></span> <span data-ttu-id="49f7a-106">No entanto, esse tempo limite se aplica somente se o exchange leva mais que uma única solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="49f7a-106">However, this timeout only applies if the exchange actually takes more that a single request-response.</span></span> <span data-ttu-id="49f7a-107">Em casos onde a negociação é realizada em uma única viagem de ida e, o tempo limite não se aplica.</span><span class="sxs-lookup"><span data-stu-id="49f7a-107">In cases where the negotiation completes in a single round trip, the timeout does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49f7a-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49f7a-108">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [<span data-ttu-id="49f7a-109">Como definir uma distorção máxima do relógio</span><span class="sxs-lookup"><span data-stu-id="49f7a-109">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
