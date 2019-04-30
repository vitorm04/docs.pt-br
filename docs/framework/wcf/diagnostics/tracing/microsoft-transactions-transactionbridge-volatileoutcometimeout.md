---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: 22992b4dfad4b4867adda0fcbbd8ecc5eb67d87e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61997601"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a>Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
O serviço de protocolo WS-AT atingiu o tempo limite aguardando uma resposta a uma mensagem de resultado de um participante volátil. O resultado da transação pode estar em dúvida se o participante de retornar.  
  
## <a name="description"></a>Descrição  
 Rastreada quando um participante volátil decidiu confirmar ou anular, mas não respondeu a uma solicitação de confirmação ou reversão dentro de um determinado período de tempo.  
  
## <a name="troubleshooting"></a>Solução de problemas  
 Certifique-se de que todos os participantes voláteis sejam capazes de responder em determinado período de tempo. Período o padrão é 180 segundos.  Se isso for insuficiente, aumente o `VolatileOutcomeDelay` política de timer para WS-AT.  
  
## <a name="see-also"></a>Consulte também

- [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Usando o rastreamento para solucionar problemas do seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
