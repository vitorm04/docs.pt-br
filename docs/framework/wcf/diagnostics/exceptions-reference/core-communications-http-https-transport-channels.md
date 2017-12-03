---
title: "Comunicações principais: Canais de transporte de HTTP-HTTPS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c0a23c9-a663-461c-bdab-58b4d3e23642
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 81eb778d70722cb44fa8dd4bc3f1152a12d87199
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="core-communications-httphttps-transport-channels"></a>Comunicações principais: canais de transportes de HTTP/HTTPS
Este tópico lista todas as exceções geradas pelo [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] canais do transporte HTTP/HTTPS.  
  
## <a name="exception-list"></a>Lista de exceções  
  
|Código do recurso|Cadeia de caracteres de recurso|  
|-------------------|---------------------|  
|DigestExplicitCredsImpersonationLevel|O nível de representação especificado foi especificado. A autenticação Digest de HTTP suporta apenas o nível de 'Representação' quando usada com uma credencial explícita.|  
|FramingContentTypeMismatch|O tipo de conteúdo especificado não era compatível com o serviço especificado. As associações de cliente e serviço talvez não sejam compatíveis.|  
|Hosting_SslSettingsMisconfigured|As configurações de protocolo SSL para o serviço especificado não coincidem com aqueles dos serviços de informações da Internet.|  
|HttpAuthSchemeAndClientCert|A fábrica de escuta HTTPS foi configurada para exigir um certificado de cliente e o esquema de autenticação especificado. No entanto, apenas uma forma de autenticação de cliente pode ser necessária ao mesmo tempo.|  
|HttpReceiveFailure|Ocorreu um erro ao receber a resposta HTTP especificado. A associação de ponto de extremidade de serviço talvez não esteja usando o protocolo HTTP. Outra possibilidade é que um contexto de solicitação HTTP foi encerrado pelo servidor devido a um serviço sendo desligado. Consulte os logs do servidor para obter mais detalhes.|  
|HttpRegistrationAccessDenied|HTTP não é possível registrar a URL especificada. O processo não tem direitos de acesso a este namespace (consulte http://msdn.microsoft.com/library/default.asp?url=/library/http/http/namespace_reservations_registrations_and_routing.asp para obter detalhes).|  
|HttpRegistrationAlreadyExists|HTTP não é possível registrar a URL especificada. Outro aplicativo já registrou essa URL com HTTP. SYS.|  
|HttpRegistrationPortInUse|HTTP não é possível registrar a URL especificada porque a porta TCP especificada está sendo usada por outro aplicativo.|  
|HttpSendFailure|Ocorreu um erro ao fazer a solicitação HTTP especificado. Certifique-se de que a causa não é uma incompatibilidade de associação de segurança. Além disso, certifique-se de que o serviço não está configurado para SSL.|  
|MessageXmlProtocolError|Ocorreu um problema com o XML que foi recebido da rede. Consulte a exceção interna para obter mais detalhes.|  
|MissingContentType|O receptor retornou um erro que indica que o tipo de conteúdo estava ausente na solicitação especificado. Consulte a exceção interna para obter mais informações.|  
|ProxyAuthenticationLevelMismatch|A credencial de autenticação de proxy HTTP especificou um requisito de autenticação mútua mais rígido que o requisito para a autenticação do servidor de destino.|  
|ProxyImpersonationLevelMismatch|A credencial de autenticação de proxy HTTP especificou uma restrição de nível de representação mais rígida que a restrição para a autenticação do servidor de destino.|  
|SecureChannelFailure|Não é possível estabelecer um canal seguro para Secure Socket Layer/Transport Layer Security com a autoridade especificada.|  
|TrustFailure|Não é possível estabelecer uma relação de confiança para o Secure Socket Layer / Transport Layer Security proteger o canal com a autoridade especificada.|  
|UseDefaultWebProxyCantBeUsedWithExplicitProxyAddress|Você não pode especificar um endereço proxy explícito UseDefaultWebProxy = true em seu elemento HttpTransportBinding.|
