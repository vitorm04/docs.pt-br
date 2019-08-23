---
title: 220 - MessageSentToTransport
ms.date: 03/30/2017
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
ms.openlocfilehash: 9f95edf42e0b1ec19d2019773def282fc279871b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948290"
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
> Esse evento não será emitido para transportes unidirecionais.  
  
## <a name="message"></a>Mensagem  
 O Dispatcher enviou uma mensagem para o transporte. ID de correlação = = '% 1 '.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|ID de correlação|`xs:GUID`|A ID da atividade usada para correlacionar um `MessageSentToTransport` evento de um serviço ou cliente ao seu correspondente `MessageReceivedFromTransport` no outro final.|  
|HostReference|`xs:string`|Para serviços hospedados na Web, esse campo identifica exclusivamente o serviço na hierarquia da Web. Seu formato é definido como ' nome do site aplicativo serviço caminho&#124;virtual do caminho&#124;virtual ServiceName '. Exemplo: "Default Web site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|AppDomain|`xs:string`|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
