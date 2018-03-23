---
title: 302 - UserDefinedWarningOccurred
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d1f0bf1-0151-45e6-be92-573d397b54de
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ae455c9eec2335fcf6eb5473932bd8d9e5d2db95
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/23/2018
---
# <a name="302---userdefinedwarningoccurred"></a>302 - UserDefinedWarningOccurred
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|302|  
|Palavras-chave|Solução de problemas, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring|  
|Nível|Aviso|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico|  
  
## <a name="description"></a>Descrição  
 Esse evento é emitido do código do usuário. Os desenvolvedores podem emitir esse evento quando ocorre um evento de aviso personalizadas em seu serviço. Isso pode ser feito usando o <xref:System.Diagnostics.Eventing> APIs. Além disso, há um exemplo do WCF que encapsula essa API e demonstra como emitir corretamente este evento.  
  
## <a name="message"></a>Mensagem  
 Nome: '%1', referência: '%2', carga: % 3  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|Nome|`xs:string`|O nome do evento definido pelo usuário.|  
|HostReference|`xs:string`|Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web. O formato é definido como ' caminho Virtual do aplicativo Web Site nome&#124;caminho Virtual do serviço&#124;ServiceName'. Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|Carga|`xs:string`|A carga do evento definido pelo usuário.|
