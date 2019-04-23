---
title: Violação
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: 7a4265c30a6713f9557de2b3d1e99c87b7dd3e58
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107881"
---
# <a name="tampering"></a>Violação
*Violação* é o ato de alteração de uma mensagem ou a entrega de uma mensagem e usando a mensagem alterada para uma finalidade que não seja o que ele foi destinado.  
  
## <a name="do-not-disable-ws-addressing"></a>Não desabilite o WS-Addressing.  
 A especificação WS-Addressing fornece os cabeçalhos de endereço em cada mensagem, permitindo que um destinatário de mensagem verificar o remetente da mensagem. Você pode desabilitar esse recurso definindo a <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> propriedade para <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.  
  
 Quando o modo de segurança é definido como mensagem e WS-Addressing é desabilitada, um invasor pode levar a uma solicitação de um cliente e enviá-lo para outro serviço, e o segundo serviço não tem nenhuma maneira de detectar que a mensagem foi enviada do cliente original. Na verdade, o primeiro serviço poderá fingir que se trata de um cliente ao conversar com o segundo serviço.  
  
 Para atenuar isso, nunca defina o <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> propriedade para <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>e evite o uso de <xref:System.ServiceModel.Channels.MessageVersion>, como estático <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> propriedade, que define o <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> propriedade <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.  
  
## <a name="see-also"></a>Consulte também

- [Considerações sobre segurança](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Divulgação de informações](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [Elevação de privilégio](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [Negação de serviço](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Cenários sem suporte](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
- [Ataques de reprodução](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
