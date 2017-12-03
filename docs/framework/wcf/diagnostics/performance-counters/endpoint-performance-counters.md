---
title: Contadores de desempenho de ponto de extremidade
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 157f0cc5d860841940b0850ca3895f82a12d47ce
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="endpoint-performance-counters"></a>Contadores de desempenho de ponto de extremidade
Contadores de desempenho do ponto de extremidade capturar dados revela como um ponto de extremidade é aceitar mensagens. Eles podem ser encontrados no `ServiceModelEndpoint 4.0.0.0` objeto de desempenho durante a exibição com o Monitor de desempenho. As instâncias são nomeadas usando esse padrão:  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 Os dados é semelhantes ao que coletados para as operações individuais, mas só são agregados entre o ponto de extremidade.  
  
> [!CAUTION]
>  Há um limite de comprimento do nome de uma instância contador de desempenho. Quando um [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] nome de instância do contador excede o comprimento máximo, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] substitui uma parte do nome da instância com um valor de hash.  
  
## <a name="see-also"></a>Consulte também  
 [Contadores de desempenho](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
