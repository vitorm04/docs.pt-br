---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: fe88e70ab4955305d78baa1158cd73a93ba2ed2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a>Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
O serviço de protocolo WS-AT recebeu uma mensagem de repetição de um participante permanente, não respondeu à preparação. Consequentemente, a transação foi anulada.  
  
## <a name="description"></a>Descrição  
 Rastreados se uma mensagem de repetição é recebida enquanto ainda está se preparando um participante permanente. Esta é uma mensagem ilegal para este estado e a transação será anulada.  
  
## <a name="troubleshooting"></a>Solução de problemas  
 Recebendo esse erro pode indiate que um participante permanente (incluindo TransactionManagers subordinada) foi recuperado após falha, no entanto, é seguro sobre o resultado da transação e o status da solicitação.  
  
## <a name="see-also"></a>Consulte também  
 [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Usando o rastreamento para solucionar problemas do seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
