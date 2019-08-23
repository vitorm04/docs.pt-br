---
title: 215 - MessageReceivedByTransport
ms.date: 03/30/2017
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
ms.openlocfilehash: aa1ad30526aa65501e5d9875d3877631ca00879b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964182"
---
# <a name="215---messagereceivedbytransport"></a>215 - MessageReceivedByTransport
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|id|215|  
|Palavras-chave|Solução de problemas, ServiceModel|  
|Nível|Informações|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico|  
  
## <a name="description"></a>Descrição  
 Esse evento ocorre quando um transporte baseado em TCP recebe uma mensagem. Observe que no nível de transporte, várias mensagens podem ser trocadas entre clientes e serviços para uma única operação. Isso pode ser devido ao comportamento da infraestrutura, a segurança é um bom exemplo. Portanto, o número de `MessageReceivedByTransport` eventos emitidos varia de acordo com a associação do seu serviço e sua configuração.  
  
> [!NOTE]
> Esse evento não é emitido para transportes unidirecionais.  
  
## <a name="message"></a>Mensagem  
 O transporte recebeu uma mensagem de '% 1 '.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|Endereço de escuta|`xs:string`|O endereço que recebeu a mensagem.|  
|HostReference|`xs:string`|Para serviços hospedados na Web, esse campo identifica exclusivamente o serviço na hierarquia da Web. Seu formato é definido como ' nome do site aplicativo serviço caminho&#124;virtual do caminho&#124;virtual ServiceName '. Exemplo: "Default Web site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|AppDomain|`xs:string`|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
