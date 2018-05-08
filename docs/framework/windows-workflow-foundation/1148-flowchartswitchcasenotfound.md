---
title: 1148 - FlowchartSwitchCaseNotFound
ms.date: 03/30/2017
ms.assetid: 9ee7fcee-e040-4306-968e-ed840a1cb00c
ms.openlocfilehash: 7e96b5b7652d404e6fdbe2c04c6a4069ca78f20f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
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
