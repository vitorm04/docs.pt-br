---
title: Violação
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: 519881a0813ac0b9f9218db42a42723a19a3089c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="tampering"></a>Violação
*Violação* é o ato de alteração de uma mensagem ou a entrega de uma mensagem e usando a mensagem alterada para uma finalidade que não seja o que ele estivesse destinado.  
  
## <a name="do-not-disable-ws-addressing"></a>Não desabilite o WS-Addressing.  
 A especificação WS-Addressing fornece cabeçalhos de endereço em cada mensagem, permitindo que um destinatário de mensagem verificar o remetente da mensagem. Você pode desativar esse recurso, definindo a <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> propriedade <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.  
  
 Quando o modo de segurança é definido como mensagem e WS-Addressing é desabilitada, um invasor pode levar a uma solicitação de um cliente e enviá-lo para outro serviço, e o segundo serviço dispõe de nenhuma forma de detectar que a mensagem foi enviada do cliente original. Na verdade, o primeiro serviço pode fingir que se trata de um cliente ao conversar com o segundo serviço.  
  
 Para atenuar isso, nunca defina o <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> propriedade <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>e evitar o uso de <xref:System.ServiceModel.Channels.MessageVersion>, como estático <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> propriedade, que define o <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> propriedade <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.  
  
## <a name="see-also"></a>Consulte também  
 [Considerações sobre segurança](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Divulgação de informações](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [Elevação de privilégio](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [Negação de serviço](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [Cenários sem suporte](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 [Ataques de reprodução](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
