---
title: 1148 - FlowchartSwitchCaseNotFound
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9ee7fcee-e040-4306-968e-ed840a1cb00c
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f95ea8aa8c3d6b012fb50a45b5a37c118928e048
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1148---flowchartswitchcasenotfound"></a>1148 - FlowchartSwitchCaseNotFound
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|1148|  
|Palavras-chave|WFActivities|  
|Nível|Informações|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração|  
  
## <a name="description"></a>Descrição  
 Indica que nem casos compatíveis ou casos padrão em uma opção do fluxograma podem ser localizados. A execução do fluxograma será finalizada.  
  
## <a name="message"></a>Mensagem  
 O fluxograma “%1 " /FlowSwitch - pôde localizar ou uma atividade dos casos ou casos padrão que correspondem ao resultado da expressão. A execução do fluxograma será finalizada.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|Fluxograma|xs:string|O nome para exibição do fluxograma.|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
