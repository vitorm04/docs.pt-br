---
title: Microsoft.Transactions.TransactionBridge.PreparedMessageRetry
ms.date: 03/30/2017
ms.assetid: 2194292d-bf5f-4aef-9336-cd3c4795cb71
ms.openlocfilehash: e5735596f1b724e47cdaadd30f07629ea6b772eb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585923"
---
# <a name="microsofttransactionstransactionbridgepreparedmessageretry"></a>Microsoft.Transactions.TransactionBridge.PreparedMessageRetry
Uma tentativa de mensagem preparada foi enviada a um coordenador não responder.  
  
## <a name="description"></a>Descrição  
 Rastreados se o Gerenciador de transações local necessário reenviar uma mensagem preparada para um coordenador superior porque não recebeu uma resposta em uma determinada quantidade de tempo /  
  
## <a name="troubleshooting"></a>Solução de problemas  
 Investigar os potencial rede ou problemas do produto que evitar que sejam entregues em tempo de resposta.  Se muitas dessas mensagens são vistas, isso pode indicar problemas de infraestrutura ou tempos de resposta anormalmente longo. Os dois problemas reduzirá drasticamente a taxa de transferência de transações no sistema.  
  
## <a name="see-also"></a>Consulte também
- [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Usando o rastreamento para solucionar problemas do seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
