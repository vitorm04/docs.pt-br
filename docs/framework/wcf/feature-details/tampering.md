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
ms.openlocfilehash: 96ab38de1fb2a932fefd4e37cbfab3d9bfbea616
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
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
 [Ataques de repetição](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
