---
title: 213 - ServiceHostStarted
ms.date: 03/30/2017
ms.assetid: a6f7facc-342f-46bb-9d52-a470178ba6bb
ms.openlocfilehash: 819efa2e13c94e2c7a16c24f6ba9c7ef2b87ef8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781817"
---
# <a name="213---servicehoststarted"></a>213 - ServiceHostStarted
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|213|  
|Palavras-chave|EndToEndMonitoring, HealthMonitoring, solução de problemas, ServiceHost|  
|Nível|LogAlways|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico|  
  
## <a name="description"></a>Descrição  
 Esse evento é emitido quando um host de serviço hospedado na Web é iniciado. Isso geralmente acontece quando o serviço é ativado por uma mensagem. Ele também pode acontecer se o serviço estiver configurado para ser iniciado automaticamente.  
  
## <a name="message"></a>Mensagem  
 ServiceHost iniciado: '%1'.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|Nome do tipo de serviço|`xs:string`|O FullName do CLR do tipo da implementação do serviço.|  
|HostReference|`xs:string`|Os serviços hospedados da Web, este campo identificam exclusivamente o serviço na hierarquia da Web. O formato é definido como ' caminho Virtual do aplicativo de nome de Site&#124;caminho Virtual de serviço&#124;ServiceName'. Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
