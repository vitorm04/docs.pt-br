---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.date: 03/30/2017
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
ms.openlocfilehash: 86d47ab0a83ff3e4a68bfa8ccf1349cf2b345b23
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597730"
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a>System.ServiceModel.ManualFlowThrottleLimitReached
System.ServiceModel.ManualFlowThrottleLimitReached  
  
## <a name="description"></a>Descrição  
 O sistema atingiu o limite definido para o Acelerador de ManualFlowControlLimit. O valor de restrição pode ser alterado modificando a propriedade ManualFlowControlLimit no ServiceHost ou InstanceContext, conforme aplicável.  
  
 Esse rastreamento é emitido quando o limite de controle de fluxo manual inicialmente é reduzido a 0. As alterações subsequentes 0 não são rastreadas. Limite de controle de fluxo no contexto de instância é rastreada de uma vez para cada contexto.  
  
## <a name="see-also"></a>Consulte também
- [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Usando o rastreamento para solucionar problemas do seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
