---
title: Considerações de segurança para sessões seguras
ms.date: 03/30/2017
ms.assetid: 0d5be591-9a7b-4a6f-a906-95d3abafe8db
ms.openlocfilehash: d2244ba42b1cf95f77424d32a19ebe11dd3a2a45
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148701"
---
# <a name="security-considerations-for-secure-sessions"></a>Considerações de segurança para sessões seguras
Você deve considerar os seguintes itens que afetam a segurança ao implementar sessões seguras. Para obter mais informações sobre considerações de segurança, consulte [considerações de segurança](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md) e [práticas recomendadas de segurança](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).  
  
## <a name="secure-sessions-and-metadata"></a>Sessões seguras e metadados  
 Quando uma sessão segura é estabelecida e o <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> estiver definida como `false`, Windows Communication Foundation (WCF) envia um `mssp:MustNotSendCancel` asserção como parte dos metadados do documento de descrição linguagem WSDL (Web Services) para o ponto de extremidade de serviço. O `mssp:MustNotSendCancel` asserção informa os clientes que o serviço não responde às solicitações para cancelar a sessão segura. Quando o <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> estiver definida como `true`, em seguida, o WCF não emite um `mssp:MustNotSendCancel` asserção no documento WSDL. Os clientes devem enviar uma solicitação de cancelamento para o serviço quando eles não exigem a sessão segura. Quando um cliente é gerado usando o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), o código do cliente reagirá adequadamente para a presença ou ausência do `mssp:MustNotSendCancel` asserção.  
  
## <a name="secure-conversations-and-custom-tokens"></a>Conversas seguras e Tokens personalizados  
 Há alguns problemas com a combinação de tokens personalizados e as chaves derivadas devido à maneira como ele é definido na especificação WS-SecureConversation. A especificação afirma que `wsse:SecurityTokenReference` é um elemento opcional que referencia o token derivada: "`/wsc:DerivedKeyToken/wsse:SecurityTokenReference` Esse elemento opcional é usado para especificar o token de contexto de segurança, o token de segurança ou usado para a derivação de chave/segredo compartilhado. Se não for especificado, presume-se que o destinatário pode determinar a chave compartilhada do contexto da mensagem. Se o contexto não pode ser determinado, em seguida, uma falha, como `wsc:UnknownDerivationSource` deve ser gerado. "  
  
 Isso significa que, se você quiser um token personalizado para ser derivado, você deve encapsular seu tipo de cláusula em uma `SecurityTokenReference` elemento. Há uma opção para desativar a derivação, mas o padrão é derivar de chaves. Se você não conseguir encapsular a chave, serializar o token de chave derivado for bem-sucedida, mas tentar desserializá-lo lança uma exceção.  
  
## <a name="see-also"></a>Consulte também

- [Como: desabilitar sessões seguras em uma WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Considerações sobre segurança](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Melhores práticas de segurança](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md)
