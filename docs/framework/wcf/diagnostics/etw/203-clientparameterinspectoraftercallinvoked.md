---
title: 203 - ClientParameterInspectorAfterCallInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9592212-07e2-43e0-8b00-affd195cf55a
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b736d9e2827708caea54fbe230b0b638492adb96
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="203---clientparameterinspectoraftercallinvoked"></a>203 - ClientParameterInspectorAfterCallInvoked
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|203|  
|Palavras-chave|Solução de problemas, ServiceModel|  
|Nível|Informações|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico|  
  
## <a name="description"></a>Descrição  
 Esse evento é emitido após o modelo de serviço foi invocado o `AfterCall` método em um Inspetor de parâmetro do cliente.  
  
## <a name="message"></a>Mensagem  
 O Dispatcher invocou 'AfterCall' em um ClientParameterInspector do tipo '%1'.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|NomeDoTipo|`xs:string`|O FullName do CLR do tipo do Inspetor invocado.|  
|HostReference|`xs:string`|Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web. O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'. Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.|  
|AppDomain|`xs:string`|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
