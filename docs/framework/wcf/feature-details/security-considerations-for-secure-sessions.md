---
title: "Considerações de segurança para sessões seguras"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d5be591-9a7b-4a6f-a906-95d3abafe8db
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: be460249ed877b2f67f2d153c2aea4a3cc4d2b37
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="security-considerations-for-secure-sessions"></a>Considerações de segurança para sessões seguras
Você deve considerar os itens a seguir que afetam a segurança ao implementar sessões seguras. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Considerações sobre segurança, consulte [considerações de segurança](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md) e [práticas recomendadas de segurança](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).  
  
## <a name="secure-sessions-and-metadata"></a>Sessões seguras e metadados  
 Quando uma sessão segura é estabelecida e o <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> está definida como `false`, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] envia um `mssp:MustNotSendCancel` asserção como parte dos metadados do documento WSDL Web Services Description Language () para o ponto de extremidade de serviço. O `mssp:MustNotSendCancel` asserção informa os clientes que o serviço não responde às solicitações para cancelar a sessão segura. Quando o <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> está definida como `true`, em seguida, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não emite um `mssp:MustNotSendCancel` asserção no documento WSDL. Os clientes devem enviar uma solicitação de cancelamento para o serviço quando eles não exigem a sessão segura. Quando um cliente é gerado usando o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), o código do cliente reage adequadamente a presença ou ausência do `mssp:MustNotSendCancel` asserção.  
  
## <a name="secure-conversations-and-custom-tokens"></a>Conversas seguras e Tokens personalizados  
 Há alguns problemas com a mistura de tokens personalizados e chaves derivadas devido à maneira que ele é definido na especificação WS-SecureConversation. A especificação diz que `wsse:SecurityTokenReference` é um elemento opcional que referencia o token derivada: "`/wsc:DerivedKeyToken/wsse:SecurityTokenReference` esse elemento opcional é usado para especificar o token de contexto de segurança, o token de segurança ou usado para a derivação de chave/segredo compartilhado. Se não for especificado, presume-se que o destinatário pode determinar a chave compartilhada do contexto da mensagem. Se o contexto não pode ser determinado, em seguida, uma falha, como `wsc:UnknownDerivationSource` deve ser gerado. "  
  
 Isso significa que se você quiser um token personalizado derivada, você deve quebrar o seu tipo de cláusula em uma `SecurityTokenReference` elemento. Há uma opção para desativar a derivação, mas o padrão é derivar as chaves. Se você não incluir a chave, serializar o token de chave derivada for bem-sucedida, mas a tentativa de desserializá-lo lança uma exceção.  
  
## <a name="see-also"></a>Consulte também  
 [Como: desabilitar sessões seguras em um WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 [Considerações sobre segurança](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Práticas recomendadas de segurança](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md)
