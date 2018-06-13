---
title: 118 - WorkflowInstanceUnhandledExceptionRecordWithId
ms.date: 03/30/2017
ms.assetid: 2ce4b193-e141-4cc4-86a3-2e8c984c110d
ms.openlocfilehash: eb69fc4760cd89294e24680b5aab83fcd058feb0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514305"
---
# <a name="118---workflowinstanceunhandledexceptionrecordwithid"></a>118 - WorkflowInstanceUnhandledExceptionRecordWithId
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|118|  
|Palavras-chave|HealthMonitoring, WFTracking|  
|Nível|Erro|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico|  
  
## <a name="description"></a>Descrição  
 Este evento é emitido pelo participante de rastreamento de ETW quando uma instância de fluxo de trabalho se emite WorkflowInstanceUnhandledExceptionRecord.  
  
## <a name="message"></a>Mensagem  
 TrackRecord = WorkflowInstanceUnhandledExceptionRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, SourceName = %5, SourceId = %6, SourceInstanceId = %7, SourceTypeName = %8, exceção = %9, anotações = % 10, ProfileName = % 11, WorkflowDefinitionIdentity = % 12  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|A identificação de instância para o fluxo de trabalho|  
|RecordNumber|xs:long|O número de sequência do registro emitido|  
|EventTime|xs:dateTime|A hora UTC quando o evento foi emitido|  
|ActivityDefinitionId|xs:string|O nome da atividade raiz no fluxo de trabalho|  
|SourceName|xs:string|O nome de atividade de origem que criticou resultando no unhandledException|  
|SourceId|xs:string|A identificação de atividade de atividade de origem de falha|  
|SourceInstanceId|xs:string|A identificação de instância de atividade de atividade de origem de falha|  
|SourceTypeName|xs:string|O nome do tipo de atividade de origem que criticou resultando no unhandledException|  
|Exceção|xs:string|Os detalhes de exceção para a exceção sem tratamento|  
|Estado|xs:string|O estado atual de fluxo de trabalho.|  
|Anotações|xs:string|As anotações que foram adicionadas a este evento. Os valores são armazenados em um elemento xml no formato \<itens >\< nome do item = "annotationName" type="System.String" > annotationValue\</item > \< /itens >. Se nenhuma anotação é especificada, em seguida, a cadeia de caracteres contém \<itens / >. O tamanho do evento de ETW é limitado pelo tamanho do buffer de ETW ou pela carga máxima útil para um evento de ETW. Se o tamanho do evento excede os limites ETW, o evento é truncado descartando as anotações e substituindo o valor anotação com \<itens >...  \< /itens >.|  
|ProfileName|xs:string|O nome ou o perfil de rastreamento que levam a este evento que está sendo emitido|  
|WorkflowDefinitionIdentity|xs:string|A identificação da definição de fluxo de trabalho|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
