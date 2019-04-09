---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 3fa5ec62c5e8ac83f3f81fb406499b7e596b3dac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59161324"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a>System.ServiceModel.Channels.MsmqMessageDropped
A mensagem descartada do MSMQ.  
  
## <a name="description"></a>Descrição  
 O rastreamento indica que uma mensagem MSMQ foi descartada. Mensagens MSMQ podem ser descartadas quando o Windows Communication Foundation (WCF) (usado com o NetMsmqBinding ou MsmqIntegrationBinding) não pode processá-los. Essas mensagens são denominadas mensagens suspeitas.  
  
 Uma mensagem suspeita será removida quando o `ReceiveErrorHandling` sobre o NetMsmqBinding ou MsmqIntegrationBinding estiver definida como `Drop`. Uma mensagem descartada é removida da fila e não é recuperável.  
  
 Ver [tratamento de mensagens suspeitas](https://go.microsoft.com/fwlink/?LinkID=99546) para obter mais detalhes sobre quando as mensagens se tornarão suspeitas e como configurar seu serviço para tratá-las adequadamente.  
  
## <a name="see-also"></a>Consulte também

- [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Utilizando o rastreamento para solucionar problemas em seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Manipulação de mensagens suspeitas](https://go.microsoft.com/fwlink/?LinkID=99546)
