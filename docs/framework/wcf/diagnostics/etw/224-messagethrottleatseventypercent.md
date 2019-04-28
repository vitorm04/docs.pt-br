---
title: 224 - MessageThrottleAtSeventyPercent
ms.date: 03/30/2017
ms.assetid: 82bbbfd7-10d2-41fd-805d-2443b0c1b96b
ms.openlocfilehash: f70dc235e037b4f490a25866940fe2bccceae2a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916299"
---
# <a name="224---messagethrottleatseventypercent"></a>224 - MessageThrottleAtSeventyPercent
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|224|  
|Palavras-chave|EndToEndMonitoring, HealthMonitoring, solução de problemas, ServiceModel|  
|Nível|Aviso|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico|  
  
## <a name="description"></a>Descrição  
 Quando uma das restrições de serviço principal foi excedida, o `MessageThrottleExceeded` evento é emitido. Quando diminui o pico de atividade e o valor atual a limitação é de 70% do limite atual, em seguida, esse evento é emitido. Observe que esse evento só é emitido depois que estiver tornando a como a atividade. Se o valor atual é posicionado na marca de 70 por cento, (por exemplo, 70,69,70,71,70,69), somente a primeira ocorrência de 70% resulta em um evento. Depois que esse evento é emitido, ocorrências futuras de exceder a limitação limitam resultados em um `MessageThrottleExceeded` eventos.  
  
## <a name="message"></a>Mensagem  
 O limite de restrição '%1' de '%2' está em 70% %.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|Nome do acelerador|`xs:string`|O nome do acelerador de foi excedido. Qualquer um dos `MaxConcurrentCalls`, `MaxConcurrentInstances`, ou `MaxConcurrentSessions`,|  
|Limite|`xs:long`|O limite configurado no momento da limitação.|  
|HostReference|`xs:string`|Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web. O formato é definido como ' caminho Virtual do aplicativo de nome de Site&#124;caminho Virtual de serviço&#124;ServiceName'. Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
