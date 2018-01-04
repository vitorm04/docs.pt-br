---
title: "Violação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ee041de1a9e009ca68ecc8bba8bc2fa06ba6ca3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="tampering"></a><span data-ttu-id="db07e-102">Violação</span><span class="sxs-lookup"><span data-stu-id="db07e-102">Tampering</span></span>
<span data-ttu-id="db07e-103">*Violação* é o ato de alteração de uma mensagem ou a entrega de uma mensagem e usando a mensagem alterada para uma finalidade que não seja o que ele estivesse destinado.</span><span class="sxs-lookup"><span data-stu-id="db07e-103">*Tampering* is the act of altering a message, or the delivery of a message, and using the altered message for a purpose other than what it was intended for.</span></span>  
  
## <a name="do-not-disable-ws-addressing"></a><span data-ttu-id="db07e-104">Não desabilite o WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="db07e-104">Do Not Disable WS-Addressing</span></span>  
 <span data-ttu-id="db07e-105">A especificação WS-Addressing fornece cabeçalhos de endereço em cada mensagem, permitindo que um destinatário de mensagem verificar o remetente da mensagem.</span><span class="sxs-lookup"><span data-stu-id="db07e-105">The WS-Addressing specification provides address headers on each message, allowing a message recipient to verify the sender of the message.</span></span> <span data-ttu-id="db07e-106">Você pode desativar esse recurso, definindo a <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> propriedade <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="db07e-106">You can disable this feature by setting the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="db07e-107">Quando o modo de segurança é definido como mensagem e WS-Addressing é desabilitada, um invasor pode levar a uma solicitação de um cliente e enviá-lo para outro serviço, e o segundo serviço dispõe de nenhuma forma de detectar que a mensagem foi enviada do cliente original.</span><span class="sxs-lookup"><span data-stu-id="db07e-107">When the security mode is set to Message, and if WS-Addressing is disabled, an attacker could take a request from a client and send it to another service, and the second service has no way of detecting that the message came from the original client.</span></span> <span data-ttu-id="db07e-108">Na verdade, o primeiro serviço pode fingir que se trata de um cliente ao conversar com o segundo serviço.</span><span class="sxs-lookup"><span data-stu-id="db07e-108">In effect, the first service can pretend that it is a client when talking to the second service.</span></span>  
  
 <span data-ttu-id="db07e-109">Para atenuar isso, nunca defina o <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> propriedade <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>e evitar o uso de <xref:System.ServiceModel.Channels.MessageVersion>, como estático <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> propriedade, que define o <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> propriedade <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="db07e-109">To mitigate this, never set the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>, and avoid the use of <xref:System.ServiceModel.Channels.MessageVersion>, such as the static <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> property, which sets the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db07e-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db07e-110">See Also</span></span>  
 [<span data-ttu-id="db07e-111">Considerações sobre segurança</span><span class="sxs-lookup"><span data-stu-id="db07e-111">Security Considerations</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [<span data-ttu-id="db07e-112">Divulgação de informações</span><span class="sxs-lookup"><span data-stu-id="db07e-112">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [<span data-ttu-id="db07e-113">Elevação de privilégio</span><span class="sxs-lookup"><span data-stu-id="db07e-113">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [<span data-ttu-id="db07e-114">Negação de serviço</span><span class="sxs-lookup"><span data-stu-id="db07e-114">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [<span data-ttu-id="db07e-115">Cenários sem suporte</span><span class="sxs-lookup"><span data-stu-id="db07e-115">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 [<span data-ttu-id="db07e-116">Ataques de reprodução</span><span class="sxs-lookup"><span data-stu-id="db07e-116">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
