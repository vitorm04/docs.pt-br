---
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9e7e87c379c84829934a929ec27bd5dacde3931f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a>Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
Uma mensagem de repetição foi enviada a um coordenador que não responde.  
  
## <a name="description"></a>Descrição  
 Rastreado se o Gerenciador de transações local necessário reenviar uma mensagem de repetição para um coordenador superior porque não recebeu uma resposta em uma determinada quantidade de tempo.  
  
## <a name="troubleshooting"></a>Solução de problemas  
 Investigue os possível problemas na rede ou produto que evitar que sejam entregues em tempo de resposta.  Se muitas dessas mensagens são vistas, ele pode indicar problemas de infraestrutura ou tempos de resposta anormalmente longo. Os dois problemas reduzirá drasticamente a taxa de transferência de transações no sistema.  
  
## <a name="see-also"></a>Consulte também  
 [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Usando o rastreamento para solucionar problemas de seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md) (Administração e diagnósticos)
