---
title: Protegendo aplicativos de canal par
ms.date: 03/30/2017
ms.assetid: d4a0311d-3f78-4525-9c4b-5c93c4492f28
ms.openlocfilehash: a747923f81f4773eb58a4b7500cf4fc1c006f889
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59146231"
---
# <a name="securing-peer-channel-applications"></a>Protegendo aplicativos de canal par
Como outras associações sob o [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], `NetPeerTcpBinding` tem segurança habilitada por padrão e oferece tanto a segurança baseada em mensagem e transporte (ou ambos). Este tópico discute esses dois tipos de segurança. O tipo de segurança é especificado pela marca de modo de segurança na especificação de vinculação (<xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>`Mode`).  
  
## <a name="transport-based-security"></a>Segurança baseada no transporte  
 Canal par dá suporte a dois tipos de credenciais de autenticação para a proteção de transporte, que exigem configuração fora de `ClientCredentialSettings.Peer` propriedade associado `ChannelFactory`:  
  
-   Senha. Clientes usam o conhecimento de uma senha secreta para autenticar conexões. Quando esse tipo de credencial é usado, `ClientCredentialSettings.Peer.MeshPassword` necessário realizar uma senha válida e, opcionalmente, um `X509Certificate2` instância.  
  
-   Certificado. Autenticação de aplicativo específico é usada. Quando esse tipo de credencial é usado, você deve usar uma implementação concreta da <xref:System.IdentityModel.Selectors.X509CertificateValidator> em `ClientCredentialSettings.Peer.PeerAuthentication`.  
  
## <a name="message-based-security"></a>Segurança baseada em mensagens  
 Usando a segurança de mensagem, um aplicativo pode assinar as mensagens de saída para que todas as partes de recebimento podem verificar se que a mensagem é enviada por um terceiro confiável e que a mensagem não foi violado. Atualmente, Peer Channel dá suporte a assinatura de mensagens de credencial de x. 509 única.  
  
## <a name="best-practices"></a>Práticas recomendadas  
  
-   Esta seção discute as práticas recomendadas para proteger os aplicativos de canal par.  
  
### <a name="enable-security-with-peer-channel-applications"></a>Habilitar a segurança com aplicativos de canal par  
 Devido à natureza distribuída dos protocolos Peer Channel, é difícil para impor a associação de malha, confidencialidade e privacidade em uma malha não segura. Também é importante lembrar-se de proteger a comunicação entre clientes e o serviço de resolvedor. Em resolução de protocolo PNRP (Peer Name), use nomes seguros para evitar a falsificação e outros ataques comuns. Proteger um serviço de resolvedor personalizado, permitindo a segurança sobre o uso de clientes de conexão entre em contato com o serviço de resolvedor, incluindo os dois segurança com base em mensagem e transporte.  
  
### <a name="use-the-strongest-possible-security-model"></a>Usar o modelo de segurança mais forte  
 Por exemplo, se cada membro da malha precisa ser identificada individualmente, use o modelo de autenticação baseada em certificado. Se isso não for possível, use a autenticação baseada em senha seguindo as recomendações atuais para mantê-los seguros. Isso inclui o compartilhamento de senhas somente com partes confiáveis, transmitir senhas usando um meio seguro, alteração de senhas com frequência e garantindo que as senhas sejam fortes (pelo menos oito caracteres de comprimento, inclua pelo menos uma letra de ambos os casos, um dígito e um caractere especial).  
  
### <a name="never-accept-self-signed-certificates"></a>Nunca aceitar certificados autoassinados  
 Nunca aceite uma credencial de certificado com base em nomes de assunto. Observe que qualquer pessoa pode criar um certificado, e qualquer pessoa pode escolher um nome que você está validando. Para evitar a possibilidade de falsificação, valide certificados com base na emissão de credenciais de autoridade (um emissor confiável ou uma autoridade de certificação raiz).  
  
### <a name="use-message-authentication"></a>Usar a autenticação de mensagem  
 Use a autenticação de mensagem para verificar que uma mensagem proveniente de uma fonte confiável e que ninguém tenha violado a mensagem durante a transmissão. Sem a autenticação de mensagem, é mais fácil para um cliente mal-intencionado falsificar ou mensagens da malha.  
  
## <a name="peer-channel-code-examples"></a>Exemplos de código de canal par  
 [Cenários de canal par](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md)  
  
## <a name="see-also"></a>Consulte também

- [Segurança de canal par](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)
- [Compilando um aplicativo de canal par](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
