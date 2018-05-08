---
title: 1005 - WorkflowApplicationIdled
ms.date: 03/30/2017
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
ms.openlocfilehash: 6bbd12e8025b6a127dbfec8e5d3690825c188c4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="1005---workflowapplicationidled"></a>1005 - WorkflowApplicationIdled
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|1005|  
|Palavras-chave|WFRuntime|  
|Nível|Informações|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração|  
  
## <a name="description"></a>Descrição  
 Indica que um aplicativo de fluxo de trabalho rodou em marcha lenta.  
  
## <a name="message"></a>Mensagem  
 Identificação de WorkflowApplication: “%1 " foi ociosa.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|A identificação do aplicativo de fluxo de trabalho|  
|AppDomain|`xs:string`|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
