---
title: "Contadores de desempenho de operação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c752c56fa60cd717f54a7a06d0d3be8b70e7772
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="operation-performance-counters"></a>Contadores de desempenho de operação
Contadores de desempenho da operação estão localizados sob o `ServiceModelOperation 4.0.0.0` objeto de desempenho durante a exibição com o Monitor de desempenho (Perfmon.exe). Cada operação tem uma instância individual. Ou seja, se um dado contrato tem operações de 10, 10 instâncias de contador de operação são associadas com esse contrato. As instâncias de objeto são nomeadas usando o seguinte padrão:  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 Esse contador permite avaliar como a chamada está sendo usada e como a operação está sendo executado.  
  
> [!CAUTION]
>  Há um limite de comprimento do nome de uma instância contador de desempenho. Quando um [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] nome de instância do contador excede o comprimento máximo, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] substitui uma parte do nome da instância com um valor de hash.  
  
## <a name="see-also"></a>Consulte também  
 [Contadores de desempenho](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
