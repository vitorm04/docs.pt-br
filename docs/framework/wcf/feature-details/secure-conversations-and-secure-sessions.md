---
title: Sessões seguras e conversas seguras
ms.date: 03/30/2017
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: c87f53bcaa167dd7b3b039c70129efca43742c1c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="secure-conversations-and-secure-sessions"></a>Sessões seguras e conversas seguras
Um recurso do Windows Communication Foundation (WCF) é a capacidade de estabelecer sessões seguras entre dois pontos de extremidade que autentiquem uns aos outros e concordem com um processo de criptografia e assinatura digital. Por exemplo, o ponto de extremidade de serviço pode exigir um ponto de extremidade do cliente para enviar um token de segurança com base em um certificado x. 509 para autenticação. Depois que o cliente é autenticado, o ponto de extremidade de serviço retorna um token de contexto de segurança (SCT) para o cliente que é usado para proteger todas as mensagens subsequentes na sessão. Estabelecer essa sessão segura permite que o conjunto de mensagens trocadas entre os dois pontos de extremidade para ser mais eficiente, porque o SCT tem uma chave simétrica. Chaves assimétricas, os certificados x. 509 se baseiam, exigem mais potência computacional que as chaves simétricas quando gerar uma assinatura digital ou criptografar um conjunto de dados.  
  
 A política de inicialização (definidos na seção 6.2.7 o [WS-SecurityPolicy](http://go.microsoft.com/fwlink/?LinkId=99817) padrão) contém as declarações de segurança de mensagem usadas para proteger o canal e autenticar o cliente antes da primeira/SCT e RSTR/SCT troca. Determinadas associações padrão do WCF tem um `Security.Message.EstablishSecurityContext` propriedade que controla se proteger a conversa é usada. Ao usar associações personalizadas a inicialização é indicada pelo aninhamento elementos de associação de segurança, por meio de [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) no arquivo de configuração, ou chamando <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> no código.  
  
 Para obter mais informações sobre as sessões, consulte [sessões usando](../../../../docs/framework/wcf/using-sessions.md).  
  
## <a name="see-also"></a>Consulte também  
 [Sessões, instanciação e simultaneidade](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [Como criar um serviço que requer sessões](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
