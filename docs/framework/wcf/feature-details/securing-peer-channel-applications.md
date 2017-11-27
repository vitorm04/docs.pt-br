---
title: Protegendo aplicativos de canal par
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4a0311d-3f78-4525-9c4b-5c93c4492f28
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 02bad6b5c7460655f4d3a5851e4e74d7de12111f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="securing-peer-channel-applications"></a>Protegendo aplicativos de canal par
Como outras associações sob o [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], `NetPeerTcpBinding` tem segurança habilitada por padrão e oferece tanto a segurança baseada em mensagem e transporte (ou ambos). Este tópico discute esses dois tipos de segurança. O tipo de segurança é especificado pela marca de modo de segurança na especificação de vinculação (<xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>`Mode`).  
  
## <a name="transport-based-security"></a>Segurança de transporte  
 Canal par dá suporte a dois tipos de credenciais de autenticação para a proteção de transporte, que exigem configuração limite o `ClientCredentialSettings.Peer` propriedade associado `ChannelFactory`:  
  
-   Senha. Clientes usam o conhecimento de uma senha secreta para autenticar conexões. Quando esse tipo de credencial é usado, `ClientCredentialSettings.Peer.MeshPassword` deve ter uma senha válida e, opcionalmente, um `X509Certificate2` instância.  
  
-   Certificado. Autenticação de aplicativo específico é usada. Quando esse tipo de credencial é usado, você deve usar uma implementação concreta de <xref:System.IdentityModel.Selectors.X509CertificateValidator> em `ClientCredentialSettings.Peer.PeerAuthentication`.  
  
## <a name="message-based-security"></a>Segurança baseada em mensagem  
 Usando a segurança de mensagem, um aplicativo pode assinar mensagens de saída para que todas as partes de recebimento podem verificar que a mensagem é enviada por um terceiro confiável e a mensagem não foi violada. Atualmente, o canal par suporta apenas x. 509 credencial a assinatura de mensagens.  
  
## <a name="best-practices"></a>Práticas recomendadas  
  
-   Esta seção aborda as práticas recomendadas para proteger aplicativos de canal par.  
  
### <a name="enable-security-with-peer-channel-applications"></a>Habilitar a segurança com aplicativos de canal par  
 Devido à natureza distribuída dos protocolos de canal par, é difícil para impor a associação de malha, confidencialidade e privacidade em uma malha não segura. Também é importante lembrar-se de proteger a comunicação entre clientes e o serviço de resolução. Na resolução de protocolo PNRP (Peer Name), use nomes seguros para evitar falsificação e outros ataques comuns. Proteger um serviço resolvedor personalizado, permitindo que a segurança sobre o uso de clientes de conexão para entrar em contato com o serviço de resolução, incluindo os dois segurança com base em mensagem e transporte.  
  
### <a name="use-the-strongest-possible-security-model"></a>Usar o modelo de segurança mais forte  
 Por exemplo, se cada membro da malha precisa ser identificado individualmente, use o modelo de autenticação baseada em certificado. Se não for possível, use a autenticação baseada em senha atuais recomendações a seguir para protegê-los. Isso inclui o compartilhamento de senhas somente com partes confiáveis, transmitir senhas um meio seguro, alterar as senhas com frequência e garantir que as senhas fortes (pelo menos oito caracteres e incluir pelo menos uma letra de ambos os casos, um dígito e um caractere especial).  
  
### <a name="never-accept-self-signed-certificates"></a>Nunca aceitar certificados autoassinados  
 Nunca aceite uma credencial de certificado com base em nomes de entidade. Observe que qualquer pessoa pode criar um certificado, e qualquer pessoa pode escolher um nome que você está validando. Para evitar a possibilidade de falsificação, valide certificados com base na emissão de credenciais de autoridade (um emissor confiável ou uma autoridade de certificação raiz).  
  
### <a name="use-message-authentication"></a>Usar a autenticação de mensagem  
 Use a autenticação de mensagem para verificar se uma mensagem proveniente de uma fonte confiável e que ninguém tenha violado a mensagem durante a transmissão. Sem autenticação de mensagens, é fácil para um cliente mal-intencionado falsificar ou adulterar mensagens na malha.  
  
## <a name="peer-channel-code-examples"></a>Exemplos de código de canal par  
 [Cenários de canal par](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md)  
  
## <a name="see-also"></a>Consulte também  
 [Segurança de canal par](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [Criando um aplicativo de canal par](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
