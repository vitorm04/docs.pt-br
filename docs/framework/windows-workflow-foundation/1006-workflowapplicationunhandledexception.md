---
title: 1006 - WorkflowApplicationUnhandledException
ms.date: 03/30/2017
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
ms.openlocfilehash: 471f3ecea66ebbd07a09686ab536a84b25d46e6b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924703"
---
# <a name="1006---workflowapplicationunhandledexception"></a>1006 - WorkflowApplicationUnhandledException
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|1006|  
|Palavras-chave|WFRuntime|  
|Nível|Erro|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração|  
  
## <a name="description"></a>Descrição  
 Indica que um aplicativo de fluxo de trabalho após uma exceção sem tratamento.  
  
## <a name="message"></a>Mensagem  
 Identificação de WorkflowInstance: "%1" encontrou uma exceção sem tratamento.  A exceção proveniente da atividade "%2", DisplayName: '%3'.  A seguir ação será necessária: %4.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|A identificação de instância para o fluxo de trabalho|  
|Exceção|`xs:string`|Os detalhes de exceção para a exceção|  
|AppDomain|`xs:string`|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
