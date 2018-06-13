---
title: Ataques por repetição
ms.date: 03/30/2017
ms.assetid: 7a17e040-93cd-4432-81b9-9f62fec78c8f
ms.openlocfilehash: 3139e0ea094f1f7483261ffd10026815e5d12f31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494072"
---
# <a name="replay-attacks"></a>Ataques por repetição
Um *reproduzir ataque* ocorre quando um invasor copia um fluxo de mensagens entre duas partes e repete o fluxo para um ou mais das partes. A menos que atenuado, os computadores sujeitos a ataque processam o fluxo como mensagens legítimas, resultando em um intervalo de consequências incorretas, como pedidos de redundância de um item.  
  
## <a name="bindings-may-be-subject-to-reflection-attacks"></a>Associações podem estar sujeitos a ataques de reflexão  
 *Ataques de reflexão* são reproduções de mensagens para um remetente como se eles vieram o destinatário, como a resposta. O padrão *detecção de repetição* no Windows Communication Foundation (WCF) mecanismo não lidam automaticamente com isso.  
  
 Ataques de reflexão sejam atenuados por padrão porque o modelo de serviço WCF adiciona uma ID de mensagem assinada para mensagens de solicitação e espera entrou `relates-to` cabeçalho em mensagens de resposta. Consequentemente, a mensagem de solicitação não pode ser reproduzida como uma resposta. Em cenários de mensagens confiável e seguro de (RM), ataques de reflexão são reduzidos porque:  
  
-   A sequência de criação e criar esquemas de mensagem de resposta de sequência são diferentes.  
  
-   Para sequências simples, o cliente envia mensagens na sequência não podem ser repetidas-lo porque o cliente não é possível entender essas mensagens.  
  
-   Para as sequências de duplex, a sequência de dois IDs deve ser exclusivos. Assim, uma mensagem de sequência de saída não pode ser reproduzida como uma mensagem de sequência de entrada (todos os cabeçalhos de sequência e corpos esteja conectados, muito).  
  
 As associações só são suscetíveis a ataques de reflexão são aqueles sem WS-Addressing: associações personalizadas que têm o WS-Addressing desabilitado e usam a segurança de baseada em chave simétrica. O <xref:System.ServiceModel.BasicHttpBinding> não usa WS-Addressing por padrão, mas não usa segurança baseada em chave simétrica de forma que permite que ele ficar vulnerável a esse ataque.  
  
 A atenuação para associações personalizadas é para não estabelecer o contexto de segurança ou para solicitar cabeçalhos de WS-Addressing.  
  
## <a name="web-farm-attacker-replays-request-to-multiple-nodes"></a>Web Farm: Solicitação de repetições invasor a vários nós  
 Um cliente usa um serviço que é implementado em um Web farm. Um invasor repete uma solicitação enviada para um nó no farm para outro nó no farm. Além disso, se um serviço for reiniciado, o cache de reprodução é liberado, permitindo que um invasor repetir a solicitação. (O cache contém valores de assinatura de mensagem usado, Vista anteriormente e impede a repetição para que as assinaturas podem ser usadas apenas uma vez. Os caches de reprodução não são compartilhados entre uma Web farm.)  
  
 Atenuantes incluem:  
  
-   Use a segurança de modo de mensagem com tokens de contexto de segurança com monitoração de estado (com ou sem conversa segura habilitada). Para obter mais informações, consulte [como: criar um Token de contexto de segurança para uma sessão segura](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
-   Configure o serviço para usar a segurança em nível de transporte.  
  
## <a name="see-also"></a>Consulte também  
 [Considerações sobre segurança](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Divulgação de informações](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [Elevação de privilégio](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [Negação de serviço](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [Violação](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [Cenários sem suporte](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
