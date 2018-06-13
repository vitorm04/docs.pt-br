---
title: 1041 - WorkflowApplicationPersistableIdle
ms.date: 03/30/2017
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
ms.openlocfilehash: 07be0ae603443a1ef06cb539bba7b227d7b3e325
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509632"
---
# <a name="1041---workflowapplicationpersistableidle"></a>1041 - WorkflowApplicationPersistableIdle
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|1041|  
|Palavras-chave|WFRuntime|  
|Nível|Informações|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração|  
  
## <a name="description"></a>Descrição  
 Indica que um aplicativo de fluxo de trabalho estiver ocioso e persistable. O aplicativo de fluxo de trabalho será rodado em marcha lento ou persistente.  
  
## <a name="message"></a>Mensagem  
 WorkflowApplication Id: '%1' está ociosa e persistente.  A seguinte ação será tomada: %2.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|WorkflowApplicationId|xs:string|A identificação do aplicativo de fluxo de trabalho|  
|ActionTaken|xs:string|A ação a ser tomada no aplicativo de fluxo de trabalho.|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
