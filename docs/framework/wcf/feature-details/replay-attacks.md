---
title: Ataques por repetição
ms.date: 03/30/2017
ms.assetid: 7a17e040-93cd-4432-81b9-9f62fec78c8f
ms.openlocfilehash: bceaa1bb723144ee4e3b534aa1537acdc7f65fc3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712071"
---
# <a name="replay-attacks"></a>Ataques por repetição
Um *ataque de reprodução* ocorre quando um invasor copia um fluxo de mensagens entre duas partes e repete o fluxo a um ou mais das partes. A menos que atenuado, os computadores sujeita a ataque processam o fluxo como mensagens legítimas, resultando em um intervalo de consequências incorretas, como com redundância de pedidos de um item.  
  
## <a name="bindings-may-be-subject-to-reflection-attacks"></a>Associações podem estar sujeito a ataques de reflexão  
 *Ataques de reflexão* são repetições de mensagens de volta para um remetente como se eles vieram o destinatário, como a resposta. O padrão *detecção de reprodução* no Windows Communication Foundation (WCF) mecanismo não lidam automaticamente com isso.  
  
 Ataques de reflexão são atenuados por padrão porque o modelo de serviço do WCF adiciona uma ID de mensagem assinadas para mensagens de solicitação e espera-se com um sinal `relates-to` cabeçalho nas mensagens de resposta. Consequentemente, a mensagem de solicitação não pode ser reproduzida como uma resposta. Em cenários de mensagens confiável e segura de (RM), ataques de reflexão são atenuados porque:  
  
-   A sequência de criação e criar esquemas de mensagens de resposta de sequência são diferentes.  
  
-   Para as sequências de simples, mensagens de sequência, que o cliente envia não podem ser repetidas volta para ele, porque o cliente não é possível entender essas mensagens.  
  
-   Para as sequências de duplex, a sequência de duas IDs deve ser exclusivos. Portanto, uma mensagem de sequência de saída não pode ser reproduzida volta como uma mensagem de sequência de entrada (todos os cabeçalhos de sequência e corpos são assinados, muito).  
  
 As apenas associações que são suscetíveis a ataques de reflexão são aqueles sem WS-Addressing: ligações personalizadas que têm o WS-Addressing desabilitado e usam a segurança de baseada em chave simétrica. O <xref:System.ServiceModel.BasicHttpBinding> não usa WS-Addressing por padrão, mas não usa segurança baseada em chave simétrica de uma maneira que permite que ele seja vulnerável a esse ataque.  
  
 A mitigação para associações personalizadas é não estabelecer o contexto de segurança ou para solicitar que os cabeçalhos de WS-Addressing.  
  
## <a name="web-farm-attacker-replays-request-to-multiple-nodes"></a>Web Farm: Solicitação de repetições do invasor para vários nós  
 Um cliente usa um serviço que é implementado em uma Web farm. Um invasor repetirá uma solicitação enviada a um nó no farm para outro nó no farm. Além disso, se um serviço for reiniciado, o cache de reprodução é liberado, permitindo que um invasor repetir a solicitação. (O cache contém valores de assinatura de mensagem usado, Vista anteriormente e impede a repetição para que essas assinaturas podem ser usadas apenas uma vez. Reprodução caches não são compartilhados entre um Web farm.)  
  
 Atenuantes incluem:  
  
-   Use a segurança de modo de mensagem com tokens de contexto de segurança com monitoração de estado (com ou sem conversa segura habilitada). Para obter mais informações, confira [Como: Criar um contexto de segurança para uma sessão segura Token](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
-   Configure o serviço para usar a segurança de nível de transporte.  
  
## <a name="see-also"></a>Consulte também
- [Considerações sobre segurança](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Divulgação de informações](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [Elevação de privilégio](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [Negação de serviço](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Violação](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Cenários sem suporte](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
