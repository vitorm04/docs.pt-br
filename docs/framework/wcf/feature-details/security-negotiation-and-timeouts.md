---
title: Negociação de segurança e tempo limite
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
ms.openlocfilehash: 1b5fb15b4ea00ba33b741c96bcb423aefe9890fa
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600991"
---
# <a name="security-negotiation-and-timeouts"></a><span data-ttu-id="4b0b5-102">Negociação de segurança e tempo limite</span><span class="sxs-lookup"><span data-stu-id="4b0b5-102">Security Negotiation and Timeouts</span></span>
<span data-ttu-id="4b0b5-103">Quando os clientes e serviços são autenticados, Windows Communication Foundation (WCF) dá suporte a um modo em que a credencial de serviço é negociada como parte da autenticação.</span><span class="sxs-lookup"><span data-stu-id="4b0b5-103">When clients and services authenticate, Windows Communication Foundation (WCF) supports a mode where the service credential is negotiated as part of authentication.</span></span> <span data-ttu-id="4b0b5-104">Nesses cenários, uma troca potencialmente de vários trechos ocorre entre o cliente e o serviço para propagar a credencial de serviço para o cliente.</span><span class="sxs-lookup"><span data-stu-id="4b0b5-104">In such scenarios, a potentially multi-leg exchange occurs between the client and the service to propagate the service credential to the client.</span></span> <span data-ttu-id="4b0b5-105">A <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> propriedade controla por quanto tempo a troca de vários trechos pode levar para ser concluída.</span><span class="sxs-lookup"><span data-stu-id="4b0b5-105">The <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property controls how long the multi-leg exchange can take to complete.</span></span> <span data-ttu-id="4b0b5-106">No entanto, esse tempo limite só se aplica se o Exchange realmente demorar mais que uma única solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="4b0b5-106">However, this timeout only applies if the exchange actually takes more that a single request-response.</span></span> <span data-ttu-id="4b0b5-107">Nos casos em que a negociação é concluída em uma única viagem de ida e volta, o tempo limite não se aplica.</span><span class="sxs-lookup"><span data-stu-id="4b0b5-107">In cases where the negotiation completes in a single round trip, the timeout does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b0b5-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b0b5-108">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="4b0b5-109">Como definir a precisão máxima do relógio</span><span class="sxs-lookup"><span data-stu-id="4b0b5-109">How to: Set a Max Clock Skew</span></span>](how-to-set-a-max-clock-skew.md)
