---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: b2d49910ecbcd67beca83e2fbeabfbcafe6e1dd0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628015"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a>System.ServiceModel.Channels.ConnectionPoolCloseException
Ocorreu uma exceção ao fechar as conexões nesse pool de conexão.  
  
## <a name="description"></a>Descrição  
 Rastreamento de nível de erro indica que ocorreu um erro ao fechar os pools de conexão usados pela conexão Windows Communication Foundation (WCF) do pool de recursos. Um motivo possível para isso é um fechamento malsucedido de uma conexão em pool ou um conjunto de conexões em pool dentro de CloseTimeout. Quando essa exceção é lançada, quaisquer conexões não fechadas restantes no pool são anuladas; conexões não fechadas dentro de outros pools são abandonadas.  
  
## <a name="see-also"></a>Consulte também
- [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Usando o rastreamento para solucionar problemas do seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
