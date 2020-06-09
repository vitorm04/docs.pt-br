---
title: Adulteração
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: e618ab369a46d403aa8db26c4b472e2be3634785
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600705"
---
# <a name="tampering"></a><span data-ttu-id="ff579-102">Adulteração</span><span class="sxs-lookup"><span data-stu-id="ff579-102">Tampering</span></span>
<span data-ttu-id="ff579-103">A *violação* é o ato de alterar uma mensagem ou a entrega de uma mensagem, e usar a mensagem alterada para uma finalidade diferente da que foi pretendida.</span><span class="sxs-lookup"><span data-stu-id="ff579-103">*Tampering* is the act of altering a message, or the delivery of a message, and using the altered message for a purpose other than what it was intended for.</span></span>  
  
## <a name="do-not-disable-ws-addressing"></a><span data-ttu-id="ff579-104">Não desabilitar o WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="ff579-104">Do Not Disable WS-Addressing</span></span>  
 <span data-ttu-id="ff579-105">A especificação WS-Addressing fornece cabeçalhos de endereço em cada mensagem, permitindo que um destinatário da mensagem Verifique o remetente da mensagem.</span><span class="sxs-lookup"><span data-stu-id="ff579-105">The WS-Addressing specification provides address headers on each message, allowing a message recipient to verify the sender of the message.</span></span> <span data-ttu-id="ff579-106">Você pode desabilitar esse recurso definindo a <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> propriedade como <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> .</span><span class="sxs-lookup"><span data-stu-id="ff579-106">You can disable this feature by setting the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="ff579-107">Quando o modo de segurança é definido como mensagem e, se o WS-Addressing estiver desabilitado, um invasor poderá fazer uma solicitação de um cliente e enviá-lo para outro serviço, e o segundo serviço não terá como detectar se a mensagem veio do cliente original.</span><span class="sxs-lookup"><span data-stu-id="ff579-107">When the security mode is set to Message, and if WS-Addressing is disabled, an attacker could take a request from a client and send it to another service, and the second service has no way of detecting that the message came from the original client.</span></span> <span data-ttu-id="ff579-108">Na verdade, o primeiro serviço pode fingir que é um cliente ao conversar com o segundo serviço.</span><span class="sxs-lookup"><span data-stu-id="ff579-108">In effect, the first service can pretend that it is a client when talking to the second service.</span></span>  
  
 <span data-ttu-id="ff579-109">Para atenuar isso, nunca defina a <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> propriedade como <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> e evite o uso de <xref:System.ServiceModel.Channels.MessageVersion> , como a <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> propriedade estática, que define a <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> propriedade como <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> .</span><span class="sxs-lookup"><span data-stu-id="ff579-109">To mitigate this, never set the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>, and avoid the use of <xref:System.ServiceModel.Channels.MessageVersion>, such as the static <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> property, which sets the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff579-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff579-110">See also</span></span>

- [<span data-ttu-id="ff579-111">Considerações sobre segurança</span><span class="sxs-lookup"><span data-stu-id="ff579-111">Security Considerations</span></span>](security-considerations-in-wcf.md)
- [<span data-ttu-id="ff579-112">Divulgação de informações</span><span class="sxs-lookup"><span data-stu-id="ff579-112">Information Disclosure</span></span>](information-disclosure.md)
- [<span data-ttu-id="ff579-113">Elevação de privilégio</span><span class="sxs-lookup"><span data-stu-id="ff579-113">Elevation of Privilege</span></span>](elevation-of-privilege.md)
- [<span data-ttu-id="ff579-114">Negação de serviço</span><span class="sxs-lookup"><span data-stu-id="ff579-114">Denial of Service</span></span>](denial-of-service.md)
- [<span data-ttu-id="ff579-115">Cenários sem suporte</span><span class="sxs-lookup"><span data-stu-id="ff579-115">Unsupported Scenarios</span></span>](unsupported-scenarios.md)
- [<span data-ttu-id="ff579-116">Ataques por repetição</span><span class="sxs-lookup"><span data-stu-id="ff579-116">Replay Attacks</span></span>](replay-attacks.md)
