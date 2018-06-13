---
title: 117 - WorkflowInstanceTerminatedRecordWithId
ms.date: 03/30/2017
ms.assetid: e68539d0-5338-468a-9f75-7e5b09d39a3c
ms.openlocfilehash: d1d6930a08eeb513dbb017b6c9b409916e5b1a2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512392"
---
# <a name="117---workflowinstanceterminatedrecordwithid"></a>117 - WorkflowInstanceTerminatedRecordWithId
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|117|  
|Palavras-chave|HealthMonitoring, WFTracking|  
|Nível|Erro|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico|  
  
## <a name="description"></a>Descrição  
 Este evento é emitido pelo participante de rastreamento de ETW quando uma instância de fluxo de trabalho se emite WorkflowInstanceTerminatedRecord.  
  
## <a name="message"></a>Mensagem  
 TrackRecord = WorkflowInstanceTerminatedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, motivo = %5, anotações = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|A identificação de instância para o fluxo de trabalho|  
|RecordNumber|xs:long|O número de sequência do registro emitido|  
|EventTime|xs:dateTime|A hora UTC quando o evento foi emitido|  
|ActivityDefinitionId|xs:string|O nome da atividade raiz no fluxo de trabalho|  
|Estado|xs:string|O estado atual de fluxo de trabalho.|  
|Anotações|xs:string|As anotações que foram adicionadas a este evento. Os valores são armazenados em um elemento xml no formato \<itens >\< nome do item = "annotationName" type="System.String" > annotationValue\</item > \< /itens >. Se nenhuma anotação é especificada, em seguida, a cadeia de caracteres contém \<itens / >. O tamanho do evento de ETW é limitado pelo tamanho do buffer de ETW ou pela carga máxima útil para um evento de ETW. Se o tamanho do evento excede os limites ETW, o evento é truncado descartando as anotações e substituindo o valor anotação com \<itens >...  \< /itens >.|  
|ProfileName|xs:string|O nome ou o perfil de rastreamento que levam a este evento que está sendo emitido|  
|WorkflowDefinitionIdentity|xs:string|A identificação da definição de fluxo de trabalho|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
