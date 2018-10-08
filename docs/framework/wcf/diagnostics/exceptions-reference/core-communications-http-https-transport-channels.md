---
title: 'Comunicações principais: Canais de transporte de HTTP-HTTPS'
ms.date: 03/30/2017
ms.assetid: 6c0a23c9-a663-461c-bdab-58b4d3e23642
ms.openlocfilehash: 4c4a2537ae615943ffac299a8c8cd00c67094360
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48844183"
---
# <a name="core-communications-httphttps-transport-channels"></a>Comunicações principais: canais de transportes de HTTP/HTTPS
Este tópico lista todas as exceções geradas pelos canais do Windows Communication Foundation (WCF) transporte HTTP/HTTPS.  
  
## <a name="exception-list"></a>Lista de exceções  
  
|Código do recurso|Cadeia de caracteres de recurso|  
|-------------------|---------------------|  
|DigestExplicitCredsImpersonationLevel|O nível de representação especificado foi especificado. Autenticação HTTP Digest suporta apenas o nível de 'Representação' quando usada com uma credencial explícita.|  
|FramingContentTypeMismatch|Não havia suporte para o tipo de conteúdo especificado pelo serviço especificado. As associações de cliente e serviço talvez não sejam compatíveis.|  
|Hosting_SslSettingsMisconfigured|As configurações de protocolo SSL para o serviço especificado não coincidem com aqueles dos serviços de informações da Internet.|  
|HttpAuthSchemeAndClientCert|A fábrica de escuta HTTPS foi configurada para exigir um certificado de cliente e o esquema de autenticação especificado. No entanto, apenas uma forma de autenticação de cliente pode ser necessária ao mesmo tempo.|  
|HttpReceiveFailure|Ocorreu um erro ao receber a resposta HTTP especificado. A associação de ponto de extremidade de serviço pode não estar usando o protocolo HTTP. Outra possibilidade é que um contexto de solicitação HTTP foi encerrado pelo servidor devido a um serviço sendo desligado. Consulte os logs do servidor para obter mais detalhes.|  
|HttpRegistrationAccessDenied|HTTP não é possível registrar a URL especificada. O processo não tem direitos de acesso para esse namespace (consulte [reservas de Namespace, os registros e roteamento](/windows/desktop/http/namespace-reservations-registrations-and-routing) para obter detalhes).|  
|HttpRegistrationAlreadyExists|HTTP não é possível registrar a URL especificada. Outro aplicativo já registrou essa URL com HTTP. SYS.|  
|HttpRegistrationPortInUse|HTTP não é possível registrar a URL especificada porque a porta TCP especificada está sendo usada por outro aplicativo.|  
|HttpSendFailure|Ocorreu um erro ao fazer a solicitação HTTP especificado. Certifique-se de que a causa não é uma incompatibilidade de associação de segurança. Certifique-se também de que o serviço não está configurado para Secure Sockets Layer.|  
|MessageXmlProtocolError|Ocorreu um problema com o XML que foi recebido da rede. Consulte a exceção interna para obter mais detalhes.|  
|MissingContentType|O destinatário retornou um erro que indica que o tipo de conteúdo estava ausente na solicitação especificada. Consulte a exceção interna para obter mais informações.|  
|ProxyAuthenticationLevelMismatch|A credencial de autenticação de proxy HTTP especificado um requisito de autenticação mútua é mais estrito que o requisito para a autenticação do servidor de destino.|  
|ProxyImpersonationLevelMismatch|A credencial de autenticação de proxy HTTP especificou uma restrição de nível de representação que é mais rígida do que a restrição para a autenticação do servidor de destino.|  
|SecureChannelFailure|Não é possível estabelecer um canal seguro para Secure Socket Layer/Transport Layer Security com a autoridade especificada.|  
|TrustFailure|Não é possível estabelecer uma relação de confiança para o Secure Socket Layer / Transport Layer Security Proteja o canal com a autoridade especificada.|  
|UseDefaultWebProxyCantBeUsedWithExplicitProxyAddress|Você não pode especificar um endereço proxy explícito UseDefaultWebProxy = true no elemento HttpTransportBinding.|
