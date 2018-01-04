---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4ffca9a587bdb32afc252f9719eb35e3139dd3f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a>System.ServiceModel.Channels.PeerNodeAuthenticationFailure
O handshake de segurança com um potencial neighbor não foi bem-sucedida.  
  
## <a name="description"></a>Descrição  
 Este rastreamento ocorre ao tentar estabelecer uma conexão segura vizinho. Isso pode acontecer devido a credenciais insuficientes ou incorretas.  
  
 PeerChannel reconhece um único tipo de token para identificação de alta segurança, certificados x. 509, que fornecem um modelo de identidade de alta segurança com base no tipo de autenticação e autorização que pode ser implementada. PeerChannel também oferece suporte para aplicativos simples com o uso de senhas. Senhas podem ser usadas apenas para permitir a entrada para a sessão; eles não podem ser usados para realizar a autenticação de mensagem. Isso ocorre porque um token simétrico que compartilham um grupo de pontos é difícil e inadequada usar para autenticação de origem.  
  
## <a name="troubleshooting"></a>Solução de problemas  
 Certifique-se de que todos os vizinhos tem as credenciais de segurança apropriadas.  
  
## <a name="see-also"></a>Consulte também  
 [Segurança de canal par](../../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Usando o rastreamento para solucionar problemas do seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
