---
title: Negociação de segurança e tempo limite
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 508d648acf148f13076327bb312d0a0b08471ac1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497458"
---
# <a name="security-negotiation-and-timeouts"></a><span data-ttu-id="531fa-102">Negociação de segurança e tempo limite</span><span class="sxs-lookup"><span data-stu-id="531fa-102">Security Negotiation and Timeouts</span></span>
<span data-ttu-id="531fa-103">Ao autenticam clientes e serviços, Windows Communication Foundation (WCF) suporta o modo em que a credencial de serviço é negociada como parte da autenticação.</span><span class="sxs-lookup"><span data-stu-id="531fa-103">When clients and services authenticate, Windows Communication Foundation (WCF) supports a mode where the service credential is negotiated as part of authentication.</span></span> <span data-ttu-id="531fa-104">Nesses cenários, uma troca potencialmente vários trecho ocorre entre o cliente e o serviço para propagar as credenciais do serviço ao cliente.</span><span class="sxs-lookup"><span data-stu-id="531fa-104">In such scenarios, a potentially multi-leg exchange occurs between the client and the service to propagate the service credential to the client.</span></span> <span data-ttu-id="531fa-105">O <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> propriedade controla quanto tempo a troca de multi-segmento de pode demorar para ser concluída.</span><span class="sxs-lookup"><span data-stu-id="531fa-105">The <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property controls how long the multi-leg exchange can take to complete.</span></span> <span data-ttu-id="531fa-106">No entanto, esse tempo limite se aplica somente se o exchange leva mais que uma única solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="531fa-106">However, this timeout only applies if the exchange actually takes more that a single request-response.</span></span> <span data-ttu-id="531fa-107">Em casos onde a negociação é realizada em uma única viagem de ida e, o tempo limite não se aplica.</span><span class="sxs-lookup"><span data-stu-id="531fa-107">In cases where the negotiation completes in a single round trip, the timeout does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="531fa-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="531fa-108">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [<span data-ttu-id="531fa-109">Como definir uma distorção máxima do relógio</span><span class="sxs-lookup"><span data-stu-id="531fa-109">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
