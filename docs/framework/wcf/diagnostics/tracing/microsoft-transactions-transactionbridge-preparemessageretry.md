---
title: Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
ms.date: 03/30/2017
ms.assetid: ada4baa5-b60d-46b8-ad46-4d69f8d8a9fa
ms.openlocfilehash: 02e275fa212128c65beda4bc3703949e75ea5092
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61997900"
---
# <a name="microsofttransactionstransactionbridgepreparemessageretry"></a>Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
Uma tentativa de preparação de mensagem foi enviada a um participante sem resposta.  
  
## <a name="description"></a>Descrição  
 Rastreados se o Gerenciador de transações local necessário reenviar uma mensagem de preparação para um participante subordinado porque não recebeu uma resposta em uma determinada quantidade de tempo.  
  
## <a name="troubleshooting"></a>Solução de problemas  
 Investigar os potencial rede ou problemas do produto que evitar que sejam entregues em tempo de resposta.  Se muitas dessas mensagens são vistas, isso pode indicar problemas de infraestrutura ou tempos de resposta anormalmente longo. Os dois problemas podem reduzir drasticamente a taxa de transferência de transações no sistema.  
  
## <a name="see-also"></a>Consulte também

- [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Usando o rastreamento para solucionar problemas do seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
