---
title: 213 - ServiceHostStarted
ms.date: 03/30/2017
ms.assetid: a6f7facc-342f-46bb-9d52-a470178ba6bb
ms.openlocfilehash: 819efa2e13c94e2c7a16c24f6ba9c7ef2b87ef8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458468"
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
 Esse evento é emitido quando um host de serviço hospedado da Web é iniciado. Isso geralmente acontece quando o serviço está ativado por uma mensagem. Ele também pode ocorrer se o serviço está configurado para ser iniciado automaticamente.  
  
## <a name="message"></a>Mensagem  
 ServiceHost iniciado: '%1'.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|Nome do tipo de serviço|`xs:string`|O FullName do CLR do tipo de implementação do serviço.|  
|HostReference|`xs:string`|Os serviços hospedados da Web, este campo identificam exclusivamente o serviço na hierarquia da Web. O formato é definido como ' caminho Virtual do aplicativo Web Site nome&#124;caminho Virtual do serviço&#124;ServiceName'. Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
