---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.date: 03/30/2017
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
ms.openlocfilehash: 315122914ebcb3e8e4d72c8d976026a126306168
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218999"
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a>System.ServiceModel.Channels.PeerNodeAuthenticationFailure
O handshake de segurança com um vizinho potencial não foi bem-sucedida.  
  
## <a name="description"></a>Descrição  
 Este rastreamento ocorre ao tentar estabelecer uma conexão segura de vizinho. Isso pode acontecer devido a credenciais insuficientes ou incorretas.  
  
 PeerChannel reconhece um único tipo de token para a identificação de alta segurança, certificados X.509, que fornecem um modelo de identidade forte com base no tipo de autenticação e autorização que pode ser implementada. PeerChannel também fornece suporte para aplicativos simples com o uso de senhas. Senhas podem ser usadas apenas para permitir a entrada para a sessão; eles não podem ser usados para realizar a autenticação de mensagem. Isso ocorre porque um token simétrico que compartilham um grupo de pares é difícil e inadequado usar para autenticação de código-fonte.  
  
## <a name="troubleshooting"></a>Solução de problemas  
 Certifique-se de que todos os vizinhos tenham as credenciais de segurança apropriadas.  
  
## <a name="see-also"></a>Consulte também

- [Segurança de canal par](../../../../../docs/framework/wcf/feature-details/peer-channel-security.md)
- [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Utilizando o rastreamento para solucionar problemas em seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
