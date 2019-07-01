---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: 93354fbdd0c1726280526ca07a8b3dd1c57c8a25
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486765"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a>Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
O serviço de protocolo WS-AT recebeu uma mensagem de repetição de um participante durável, que não respondeu à preparação. Consequentemente, a transação foi anulada.  
  
## <a name="description"></a>Descrição  
 Rastreados se uma mensagem de repetição é recebida enquanto ainda está se preparando um participante durável. Esta é uma mensagem ilegal para este estado e a transação será anulada.  
  
## <a name="troubleshooting"></a>Solução de problemas

Recebendo esse erro pode indicar que um participante durável (incluindo TransactionManagers subordinado) se recuperou de falha; No entanto, ele não tem certo de que o resultado da transação e solicita seu status.  
  
## <a name="see-also"></a>Consulte também

- [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Usando o rastreamento para solucionar problemas do seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
