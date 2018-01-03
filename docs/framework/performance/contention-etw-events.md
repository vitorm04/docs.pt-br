---
title: "Eventos ETW de contenção"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a09419c208d4ac754eb48da0c8d1b5d93386eb3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="contention-etw-events"></a>Eventos ETW de contenção
Eventos de contenção são acionados sempre que há contenção em bloqueios <xref:System.Threading.Monitor?displayProperty=nameWithType> ou bloqueios nativos usados pelo tempo de execução. A contenção ocorre quando um thread aguarda um bloqueio, enquanto outro thread possui o bloqueio.  
  
 A tabela a seguir mostra a palavra-chave com a qual os eventos de contenção são acionados, além do nível dos eventos. (Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Palavra-chave para acionar o evento|Nível|  
|-----------------------------------|-----------|  
|`ContentionKeyword` (0x4000)|Informativo (4)|  
  
 A tabela a seguir mostra as informações do evento.  
  
|evento|ID do evento|Acionado quando|  
|-----------|--------------|-----------------|  
|`ContentionStart_V1`|81|A contenção é iniciada. Esse evento não inclui o tempo de rotação antes que um thread aguarde para adquirir um bloqueio; ele é acionado apenas quando o thread aguarda para adquirir um bloqueio.|  
|`ContentionStop`|81|A contenção é encerrada.|  
  
 A tabela a seguir mostra dados do evento.  
  
|Nome do campo|Tipo de dados|Descrição|  
|----------------|---------------|-----------------|  
|Sinalizadores|win:UInt8|0 para gerenciado; 1 para nativo.|  
|ClrInstanceID|win:UInt16|ID exclusiva da instância do CLR.|  
  
## <a name="see-also"></a>Consulte também  
 [Eventos de CLR ETW](../../../docs/framework/performance/clr-etw-events.md)
