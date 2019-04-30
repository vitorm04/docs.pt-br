---
title: 214 - OperationCompleted
ms.date: 03/30/2017
ms.assetid: a6287eef-023f-4816-813c-1802c82366df
ms.openlocfilehash: da1021b674b555b683f8f745f5a2a0073c9567e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967993"
---
# <a name="214---operationcompleted"></a>214 - OperationCompleted
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|214|  
|Palavras-chave|HealthMonitoring, EndToEndMonitoring, solução de problemas, ServiceModel|  
|Nível|Informações|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico|  
  
## <a name="description"></a>Descrição  
 Esse evento é emitido quando padrão do modelo de serviço `OperationInvoker` concluiu uma chamada para um método sem esse método lançar uma exceção.  
  
## <a name="message"></a>Mensagem  
 Objekt OperationInvoker concluir a chamada para o método '%1'. A duração da chamada de método era '%2' ms.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|Nome do método|`xs:string`|O nome do CLR do método que foi invocado pelo `OperationInvoker`.|  
|Duração|`xs:long`|O tempo, em milissegundos, que levou o `OperationInvoker` para invocar o método.|  
|HostReference|`xs:string`|Para serviços hospedados na web, este campo identifica exclusivamente o serviço na hierarquia da Web. O formato é definido como ' caminho Virtual do aplicativo de nome de Site&#124;caminho Virtual de serviço&#124;ServiceName'. Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
