---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: e56a9ed1d837af27d481282e0e106d537ec41ee3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164288"
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a>Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
O serviço de protocolo WS-AT Falha ao registrar um participante para um protocolo de controle.  
  
## <a name="description"></a>Descrição  
 Rastreados se MSDTC detectar uma solicitação de registro inválido. Isso pode ser causado por várias solicitações de registro de conclusão e erros internos.  
  
## <a name="troubleshooting"></a>Solução de problemas  
 Não tente registrar-se para a conclusão mais de uma vez.  Além disso, inspecione a cadeia de caracteres de status dentro da mensagem de rastreamento para determinar se há qualquer item acionável.  
  
## <a name="see-also"></a>Consulte também

- [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Utilizando o rastreamento para solucionar problemas em seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
