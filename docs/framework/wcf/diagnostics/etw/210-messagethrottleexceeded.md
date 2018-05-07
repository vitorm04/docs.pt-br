---
title: 210 - MessageThrottleExceeded
ms.date: 03/30/2017
ms.assetid: 24ca08ea-c11c-4753-946e-98aa820f8711
ms.openlocfilehash: 7ba5948b36642085ef44661b3d580e7f1c4102cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="210---messagethrottleexceeded"></a>210 - MessageThrottleExceeded
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|210|  
|Palavras-chave|EndToEndMonitoring, HealthMonitoring, solução de problemas, ServiceModel|  
|Nível|Aviso|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico|  
  
## <a name="description"></a>Descrição  
 Esse evento é emitido quando um do serviço principal três limitadores tem sido excedidos. Observe que esse evento só é emitido quando o limite for excedido inicialmente. Por exemplo, se o limite de chamadas simultâneas for 10, a simultâneas 11 resultados da chamada um `MessageThrottleExceeded` eventos. 12 de chamada não resulta em outro evento. Além disso, para evitar um fluxo de eventos com ruídos, atividade que passa em torno de limite não resulta em outro evento. Neste exemplo, se duas chamadas concluída, em seguida, há 9 chamadas simultâneas. Se subsequentemente duas chamadas mais entrar, o valor atual é 11 novamente. Não, isso resulta em outro evento. Quando o valor atual a 70 por cento do limite de limitação de um evento diferente é emitido que indica que a atividade tem parou. Atividades futuras que excedem o limite de resultados em outra `MessageThrottleExceeded` evento que está sendo emitido. Neste exemplo, se a quantidade de chamadas simultâneas fica 7 e, em seguida, novamente atinge 11 e outro `MessageThrottleExceeded` evento é emitido.  
  
## <a name="message"></a>Mensagem  
 Foi atingido o limite de restrição '%1' de '%2'.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|Nome do acelerador|`xs:string`|O nome do acelerador foi excedido. O `MaxConcurrentCalls`, `MaxConcurrentInstances`, ou `MaxConcurrentSessions`,|  
|Limite|`xs:long`|O limite configurado no momento do acelerador.|  
|HostReference|`xs:string`|Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web. O formato é definido como ' caminho Virtual do aplicativo Web Site nome&#124;caminho Virtual do serviço&#124;ServiceName'. Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
