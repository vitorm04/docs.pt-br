---
title: 1015 - StartCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
ms.openlocfilehash: 6a2d4c866ec7d43e8ae40b5616a97c3b7adf1843
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509615"
---
# <a name="1015---startcompletionworkitem"></a>1015 - StartCompletionWorkItem
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|1015|  
|Palavras-chave|WFRuntime|  
|Nível|Detalhado|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração|  
  
## <a name="description"></a>Descrição  
 Indica que um CompletionWorkItem está sendo a execução.  
  
## <a name="message"></a>Mensagem  
 Iniciar a execução de um CompletionWorkItem para atividades pai “%1 ", DisplayName: “%2", InstanceId: “%3". Atividade counting “%4 ", DisplayName: “%5", InstanceId: “%6".  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|ParentActivity|xs:string|O nome do tipo de atividade pai.|  
|ParentDisplayName|xs:string|O nome para exibição de atividade pai.|  
|ParentInstanceId|xs:string|A identificação de instância de atividade pai.|  
|CompletedActivity|xs:string|O nome do tipo de atividade concluída.|  
|CompletedActivityDisplayName|xs:string|O nome para exibição de atividade concluída.|  
|CompletedActivityInstanceId|xs:string|A identificação de instância de atividade concluída.|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
