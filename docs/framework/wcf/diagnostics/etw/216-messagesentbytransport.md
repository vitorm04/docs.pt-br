---
title: 216 - MessageSentByTransport
ms.date: 03/30/2017
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
ms.openlocfilehash: fa21568e4c8c38eefe359c417d47ec0a9d30a7c4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781804"
---
# <a name="216---messagesentbytransport"></a>216 - MessageSentByTransport
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|216|  
|Palavras-chave|Solução de problemas, ServiceModel|  
|Nível|Informações|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico|  
  
## <a name="description"></a>Descrição  
 Esse evento ocorre quando um transporte de TCP envia uma mensagem. Observe que no nível do transporte várias mensagens podem ser trocadas entre clientes e serviços para uma única operação. Isso pode ser devido ao comportamento de infraestrutura, segurança, sendo um bom exemplo. Portanto, o número de **MessageSentByTransport** eventos que são emitidos variam com base na associação do seu serviço e sua configuração.  
  
## <a name="message"></a>Mensagem  
 O transporte enviou uma mensagem para '%1'.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|DestinationAddress|`xs:string`|O endereço que recebeu a mensagem de solicitação.|  
|HostReference|xs:string|Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web. O formato é definido como ' caminho Virtual do aplicativo de nome de Site&#124;caminho Virtual de serviço&#124;ServiceName'. Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
