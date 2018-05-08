---
title: 218 - ClientOperationCompleted
ms.date: 03/30/2017
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
ms.openlocfilehash: 83f39be84a8d62962b85652b0e39b537c92e612c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="218---clientoperationcompleted"></a>218 - ClientOperationCompleted
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|218|  
|Palavras-chave|Solução de problemas, ServiceModel|  
|Nível|Informações|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico|  
  
## <a name="description"></a>Descrição  
 Esse evento é emitido por clientes depois que uma operação é concluída. Para operações unidirecionais, isso é apenas depois que a mensagem é enviada com êxito. Para operações de solicitação-resposta, isso é após o recebimento da resposta.  
  
## <a name="message"></a>Mensagem  
 O cliente concluiu a execução da ação '%1' associada ao contrato '%2'. A mensagem foi enviada para '%3'.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|Ação|xs:string|O cabeçalho de ação SOAP da mensagem de saída.|  
|Nome do contrato|`xs:string`|O nome do contrato. Exemplo: ICalculator.|  
|Destino|`xs:string`|O endereço do ponto de extremidade de serviço que a mensagem foi enviada ao.|  
|HostReference|`xs:string`|Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web. O formato é definido como ' caminho Virtual do aplicativo Web Site nome&#124;caminho Virtual do serviço&#124;ServiceName'. Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
