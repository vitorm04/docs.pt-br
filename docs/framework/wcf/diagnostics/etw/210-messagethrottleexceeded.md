---
title: 210 - MessageThrottleExceeded
ms.date: 03/30/2017
ms.assetid: 24ca08ea-c11c-4753-946e-98aa820f8711
ms.openlocfilehash: 7ba5948b36642085ef44661b3d580e7f1c4102cb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781870"
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
 Esse evento é emitido quando um do serviço principal três limites forem excedidos. Observe que esse evento só é emitido quando o limite for excedido inicialmente. Por exemplo, se o limite de restrição de chamadas simultâneas for 10, a simultâneas de 11 de resultados da chamada um `MessageThrottleExceeded` eventos. 12 de chamada não resulta em outro evento. Além disso, para evitar um fluxo de eventos com ruídos, que focaliza o limite de atividade não resulta em outro evento. Neste exemplo, se algumas chamadas concluídos, em seguida, há chamadas simultâneas de 9. Se subsequentemente chegam mais chamadas de dois, o valor atual é 11 novamente. Isso não resulta em outro evento. Quando o valor atual fica a 70 por cento do limite de limitação de um evento diferente é emitido que indica que a atividade de velocidade. Atividades futuras que excede o limite de resultados em outra `MessageThrottleExceeded` evento que está sendo emitido. Neste exemplo, se a quantidade de chamadas simultâneas cai para 7 e, em seguida, novamente alcança 11 e outro `MessageThrottleExceeded` evento é emitido.  
  
## <a name="message"></a>Mensagem  
 O limite de restrição '%1' de '%2' foi atingido.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|Nome do acelerador|`xs:string`|O nome do acelerador de foi excedido. Qualquer um dos `MaxConcurrentCalls`, `MaxConcurrentInstances`, ou `MaxConcurrentSessions`,|  
|Limite|`xs:long`|O limite configurado no momento da limitação.|  
|HostReference|`xs:string`|Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web. O formato é definido como ' caminho Virtual do aplicativo de nome de Site&#124;caminho Virtual de serviço&#124;ServiceName'. Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
