---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: f3474fc1bb0ed0d11df6289ed6470447d815f5ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a>System.ServiceModel.Channels.ConnectionPoolCloseException
Ocorreu uma exceção ao fechar as conexões nesse pool de conexão.  
  
## <a name="description"></a>Descrição  
 Este rastreamento de nível de erro indica que ocorreu um erro ao fechar os pools de conexão usados pela conexão do Windows Communication Foundation (WCF) do pool de recursos. Um motivo possível para isso é um feriado bem-sucedida de uma conexão em pool ou um conjunto de conexões em pool dentro de CloseTimeout. Quando essa exceção é gerada, quaisquer conexões restantes não fechadas dentro desse pool foram anuladas; conexões não fechadas dentro de outros pools são abandonadas.  
  
## <a name="see-also"></a>Consulte também  
 [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Usando o rastreamento para solucionar problemas do seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
