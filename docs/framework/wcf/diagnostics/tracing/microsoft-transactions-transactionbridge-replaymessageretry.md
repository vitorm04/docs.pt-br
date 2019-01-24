---
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.date: 03/30/2017
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
ms.openlocfilehash: bb7f6fcf95d1ff253fa0e2963610bee2b65ef3c2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597106"
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a>Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
Uma tentativa de repetição de mensagem foi enviada a um coordenador não responder.  
  
## <a name="description"></a>Descrição  
 Rastreados se o Gerenciador de transações local necessário reenviar uma mensagem de repetição para um coordenador superior porque não recebeu uma resposta em uma determinada quantidade de tempo.  
  
## <a name="troubleshooting"></a>Solução de problemas  
 Investigar os potencial rede ou problemas do produto que evitar que sejam entregues em tempo de resposta.  Se muitas dessas mensagens são vistas, isso pode indicar problemas de infraestrutura ou tempos de resposta anormalmente longo. Os dois problemas reduzirá drasticamente a taxa de transferência de transações no sistema.  
  
## <a name="see-also"></a>Consulte também
- [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Usando o rastreamento para solucionar problemas do seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
