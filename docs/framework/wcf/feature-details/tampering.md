---
title: Violação
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: 519881a0813ac0b9f9218db42a42723a19a3089c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498625"
---
# <a name="tampering"></a><span data-ttu-id="b2289-102">Violação</span><span class="sxs-lookup"><span data-stu-id="b2289-102">Tampering</span></span>
<span data-ttu-id="b2289-103">*Violação* é o ato de alteração de uma mensagem ou a entrega de uma mensagem e usando a mensagem alterada para uma finalidade que não seja o que ele estivesse destinado.</span><span class="sxs-lookup"><span data-stu-id="b2289-103">*Tampering* is the act of altering a message, or the delivery of a message, and using the altered message for a purpose other than what it was intended for.</span></span>  
  
## <a name="do-not-disable-ws-addressing"></a><span data-ttu-id="b2289-104">Não desabilite o WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="b2289-104">Do Not Disable WS-Addressing</span></span>  
 <span data-ttu-id="b2289-105">A especificação WS-Addressing fornece cabeçalhos de endereço em cada mensagem, permitindo que um destinatário de mensagem verificar o remetente da mensagem.</span><span class="sxs-lookup"><span data-stu-id="b2289-105">The WS-Addressing specification provides address headers on each message, allowing a message recipient to verify the sender of the message.</span></span> <span data-ttu-id="b2289-106">Você pode desativar esse recurso, definindo a <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> propriedade <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="b2289-106">You can disable this feature by setting the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="b2289-107">Quando o modo de segurança é definido como mensagem e WS-Addressing é desabilitada, um invasor pode levar a uma solicitação de um cliente e enviá-lo para outro serviço, e o segundo serviço dispõe de nenhuma forma de detectar que a mensagem foi enviada do cliente original.</span><span class="sxs-lookup"><span data-stu-id="b2289-107">When the security mode is set to Message, and if WS-Addressing is disabled, an attacker could take a request from a client and send it to another service, and the second service has no way of detecting that the message came from the original client.</span></span> <span data-ttu-id="b2289-108">Na verdade, o primeiro serviço pode fingir que se trata de um cliente ao conversar com o segundo serviço.</span><span class="sxs-lookup"><span data-stu-id="b2289-108">In effect, the first service can pretend that it is a client when talking to the second service.</span></span>  
  
 <span data-ttu-id="b2289-109">Para atenuar isso, nunca defina o <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> propriedade <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>e evitar o uso de <xref:System.ServiceModel.Channels.MessageVersion>, como estático <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> propriedade, que define o <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> propriedade <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="b2289-109">To mitigate this, never set the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>, and avoid the use of <xref:System.ServiceModel.Channels.MessageVersion>, such as the static <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> property, which sets the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2289-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2289-110">See Also</span></span>  
 [<span data-ttu-id="b2289-111">Considerações sobre segurança</span><span class="sxs-lookup"><span data-stu-id="b2289-111">Security Considerations</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [<span data-ttu-id="b2289-112">Divulgação de informações</span><span class="sxs-lookup"><span data-stu-id="b2289-112">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [<span data-ttu-id="b2289-113">Elevação de privilégio</span><span class="sxs-lookup"><span data-stu-id="b2289-113">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [<span data-ttu-id="b2289-114">Negação de serviço</span><span class="sxs-lookup"><span data-stu-id="b2289-114">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [<span data-ttu-id="b2289-115">Cenários sem suporte</span><span class="sxs-lookup"><span data-stu-id="b2289-115">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 [<span data-ttu-id="b2289-116">Ataques de reprodução</span><span class="sxs-lookup"><span data-stu-id="b2289-116">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
