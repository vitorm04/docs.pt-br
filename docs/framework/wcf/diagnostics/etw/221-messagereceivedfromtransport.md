---
title: 221 - MessageReceivedFromTransport
ms.date: 03/30/2017
ms.assetid: 4995f0d5-c182-4d97-981f-6951da6df1fb
ms.openlocfilehash: 98dbf2728242fa73b3e54b7cf32f9e227e5251b2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781713"
---
# <a name="221---messagereceivedfromtransport"></a>221 - MessageReceivedFromTransport
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|221|  
|Palavras-chave|EndToEndMonitoring, solução de problemas, ServiceModel|  
|Nível|Informações|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico|  
  
## <a name="description"></a>Descrição  
 Esse evento é emitido quando o modelo de serviço recebe uma mensagem de transporte.  
  
## <a name="message"></a>Mensagem  
 O Dispatcher recebeu uma mensagem de transporte. ID de correlação = = '%1'.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|ID de correlação|`xs:GUID`|A atividade de ID usado para correlacionar uma `MessageSentToTransport` eventos de um serviço ou cliente para seus respectivos `MessageReceivedFromTransport` na outra extremidade.|  
|HostReference|`xs:string`|Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web. O formato é definido como ' caminho Virtual do aplicativo de nome de Site&#124;caminho Virtual de serviço&#124;ServiceName'. Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
