---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d4e8eee0ebc3702445b41d1f81742d18dfa98d44
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a>System.ServiceModel.Channels.ConnectionPoolCloseException
Ocorreu uma exceção ao fechar as conexões nesse pool de conexão.  
  
## <a name="description"></a>Descrição  
 Este rastreamento de nível de erro indica que ocorreu um erro ao fechar os pools de conexão usados pelo [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]do recurso do pool de conexão. Um motivo possível para isso é um feriado bem-sucedida de uma conexão em pool ou um conjunto de conexões em pool dentro de CloseTimeout. Quando essa exceção é gerada, quaisquer conexões restantes não fechadas dentro desse pool foram anuladas; conexões não fechadas dentro de outros pools são abandonadas.  
  
## <a name="see-also"></a>Consulte também  
 [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Usando o rastreamento para solucionar problemas de seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md) (Administração e diagnósticos)
