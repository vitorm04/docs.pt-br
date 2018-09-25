---
title: Sessões seguras e conversas seguras
ms.date: 03/30/2017
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
author: BrucePerlerMS
ms.openlocfilehash: 077f21f11fae9e91abe281778351954c80d9603b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47156241"
---
# <a name="secure-conversations-and-secure-sessions"></a>Sessões seguras e conversas seguras
Um recurso do Windows Communication Foundation (WCF) é a capacidade de estabelecer sessões seguras entre dois pontos de extremidade que se autenticam e concordem com um processo de criptografia e assinatura digital. Por exemplo, o ponto de extremidade de serviço pode exigir um ponto de extremidade do cliente para enviar um token de segurança com base em um certificado X.509 para autenticação. Quando o cliente é autenticado, o ponto de extremidade de serviço retorna um token de contexto de segurança (SCT) volta ao cliente que é usado para proteger todas as mensagens subsequentes dentro da sessão. Estabelecer essa sessão segura permite que o conjunto de mensagens trocadas entre os dois pontos de extremidade a ser mais eficiente, porque o SCT tem uma chave simétrica. Chaves assimétricas, quais certificados x. 509 se baseiam, exigem significativamente mais capacidade de computação do que as chaves simétricas quando gerar uma assinatura digital ou criptografar um conjunto de dados.  
  
 A política de bootstrap (definido na seção 6.2.7 a [WS-SecurityPolicy](https://go.microsoft.com/fwlink/?LinkId=99817) standard) contém as declarações de segurança de mensagem usadas para proteger o canal e autenticar o cliente antes da troca SCT/RST e RSTR/SCT. Determinadas associações padrão do WCF têm um `Security.Message.EstablishSecurityContext` propriedade que controla se proteger de conversa é usada. Ao usar associações personalizadas o bootstrap é indicado pelo aninhamento elementos de associação de segurança, por meio [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) no arquivo de configuração, ou chamando <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> no código.  
  
 Para obter mais informações sobre as sessões, consulte [sessões usando](../../../../docs/framework/wcf/using-sessions.md).  
  
## <a name="see-also"></a>Consulte também  
 [Sessões, instanciação e simultaneidade](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [Como criar um serviço que requer sessões](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
