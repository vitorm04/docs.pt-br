---
title: 220 - MessageSentToTransport
ms.date: 03/30/2017
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
ms.openlocfilehash: 92ec664aead15470fbed576bf157d64d984ddebf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="220---messagesenttotransport"></a>220 - MessageSentToTransport
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|Id|220|  
|Palavras-chave|EndToEndMonitoring, solução de problemas, ServiceModel|  
|Nível|Informações|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico|  
  
## <a name="description"></a>Descrição  
 Esse evento é emitido quando o modelo de serviço envia uma mensagem para o transporte.  
  
> [!NOTE]
>  Esse evento não será emitido para transportes unidirecionais.  
  
## <a name="message"></a>Mensagem  
 O Dispatcher enviou uma mensagem para o transporte. ID de correlação = = '%1'.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|ID de correlação|`xs:GUID`|A atividade de ID usada para correlacionar uma `MessageSentToTransport` evento em um serviço ou cliente correspondente `MessageReceivedFromTransport` na outra extremidade.|  
|HostReference|`xs:string`|Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web. O formato é definido como ' caminho Virtual do aplicativo Web Site nome&#124;caminho Virtual do serviço&#124;ServiceName'. Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
