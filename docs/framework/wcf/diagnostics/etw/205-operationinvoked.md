---
title: 205 - OperationInvoked
ms.date: 03/30/2017
ms.assetid: 9c8d6c90-dfa5-4ae0-a589-96679a8fb3ba
ms.openlocfilehash: e95b6923d21307b2ef68d4a5369b3cee86540239
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781973"
---
# <a name="205---operationinvoked"></a>205 - OperationInvoked
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|205|  
|Palavras-chave|Solução de problemas, ServiceModel|  
|Nível|Informações|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico|  
  
## <a name="description"></a>Descrição  
 Esse evento é emitido antes de padrão do modelo de serviço `OperationInvoker` inicia uma chamada para um método.  
  
## <a name="message"></a>Mensagem  
 Objekt OperationInvoker chamado o método '%1'. Informações do chamador: '%2'.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|Nome do método|`xs:string`|O nome do CLR do método que foi invocado pelo `OperationInvoker`.|  
|Informações de chamador|`xs:string`|O endereço IP e porta número do cliente no formato 'IPAddress:PortNumber'. Os dois valores são recuperados da propriedade de mensagem 'Remoteendpointmessageproperty' dentro do contexto de operação. Observe que para associações não TCP esse valor `null`.|  
|HostReference|`xs:string`|Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web. O formato é definido como ' caminho Virtual do aplicativo de nome de Site&#124;caminho Virtual de serviço&#124;ServiceName'. Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
