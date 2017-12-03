---
title: 214 - OperationCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6287eef-023f-4816-813c-1802c82366df
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 09a8dc1994da30c0f0c180640e3f66c8806e4528
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
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
 Esse evento é emitido ao padrão do modelo de serviço `OperationInvoker` concluiu uma chamada para um método sem esse método lançar uma exceção.  
  
## <a name="message"></a>Mensagem  
 Um OperationInvoker concluiu a chamada ao método '%1'. A duração da chamada de método foi '%2' ms.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|Nome do método|`xs:string`|O nome CLR do método que foi invocado pelo `OperationInvoker`.|  
|Duração|`xs:long`|O tempo, em milissegundos, que levou o `OperationInvoker` para invocar o método.|  
|HostReference|`xs:string`|Para serviços hospedados na web, este campo identifica exclusivamente o serviço na hierarquia da Web. O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'. Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.|  
|AppDomain|`xs:string`|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
