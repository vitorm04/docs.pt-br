---
title: 100 - WorkflowInstanceRecord
ms.date: 03/30/2017
ms.assetid: ed4d1851-b378-489b-a22d-c1db09571fb4
ms.openlocfilehash: c7abb2c59c65e0b0f4c4f209e3c7c2d0cf4641d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="100---workflowinstancerecord"></a>100 - WorkflowInstanceRecord
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|Id|100|  
|Palavras-chave|EndToEndMonitoring, solução de problemas, HealthMonitoring, WFTracking|  
|Nível|Informações|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico|  
  
## <a name="description"></a>Descrição  
 Este evento é emitido pelo participante de rastreamento de ETW quando uma instância de fluxo de trabalho se emite WorkflowInstanceRecord para o estados de fluxo de trabalho: Iniciado, que, persistente, ociosa, excluído, concluído, cancelado, descarregada, não suspenso.  
  
## <a name="message"></a>Mensagem  
 TrackRecord= WorkflowInstanceRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, estado = %5, anotações = %6 ProfileName, %7 =  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|A identificação de instância para o fluxo de trabalho|  
|RecordNumber|xs:long|O número de sequência do registro emitido|  
|EventTime|xs:dateTime|A hora UTC quando o evento foi emitido|  
|ActivityDefinitionId|xs:string|O nome da atividade raiz no fluxo de trabalho|  
|Estado|xs:string|O estado atual de fluxo de trabalho.|  
|Anotações|xs:string|As anotações que foram adicionadas a este evento.  Os valores são armazenados em um elemento xml no formato \<itens >\< nome do item = "annotationName" type="System.String" > annotationValue\</item > \< /itens >.  Se nenhuma anotação é especificada, em seguida, a cadeia de caracteres contém \<itens / >. O tamanho do evento de ETW é limitado pelo tamanho do buffer de ETW ou pela carga máxima útil para um evento de ETW. Se o tamanho do evento excede os limites ETW, o evento é truncado descartando as anotações e substituindo o valor anotação com \<itens >...  \< /itens >.|  
|ProfileName|xs:string|O nome ou o perfil de rastreamento que levam a este evento que está sendo emitido|  
|HostReference|xs:string|Hospedados para serviços da Web, este campo identifica unicamente o serviço na hierarquia da Web.  O formato é definido como ' caminho Virtual do aplicativo Web Site nome&#124;caminho Virtual do serviço&#124;ServiceName' exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
