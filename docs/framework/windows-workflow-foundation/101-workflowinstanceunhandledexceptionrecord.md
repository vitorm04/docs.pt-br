---
title: 101 - WorkflowInstanceUnhandledExceptionRecord
ms.date: 03/30/2017
ms.assetid: ab7d50a0-5347-4390-8445-1def4dfdff6a
ms.openlocfilehash: af7f471e135ed7ec782f7d9a5c7cee3de09e7187
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924599"
---
# <a name="101---workflowinstanceunhandledexceptionrecord"></a>101 - WorkflowInstanceUnhandledExceptionRecord
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|Id|101|  
|Palavras-chave|EndToEndMonitoring, solução de problemas, HealthMonitoring, WFTracking|  
|Nível|Erro|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico|  
  
## <a name="description"></a>Descrição  
 Este evento é emitido pelo participante de rastreamento de ETW quando uma instância de fluxo de trabalho se emite WorkflowInstanceUnhandledExceptionRecord.  
  
## <a name="message"></a>Mensagem  
 TrackRecord = WorkflowInstanceUnhandledExceptionRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, SourceName = %5, SourceId = %6, SourceInstanceId =, %7 SourceTypeName=%8, Exception=%9, Annotations= %10, ProfileName = %11  
  
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
|Anotações|xs:string|As anotações que foram adicionadas a este evento.  Os valores são armazenados em um elemento xml no formato \<itens >\< nome do item = "tipo" System "> annotationValue\</item > \< /itens >.  Se nenhuma anotação é especificada, a cadeia de caracteres contém \<itens / >. O tamanho do evento de ETW é limitado pelo tamanho do buffer de ETW ou pela carga máxima útil para um evento de ETW. Se o tamanho do evento excede os limites de ETW, então o evento será truncado soltando as anotações e substituindo o valor de anotação com \<itens >...  \< /itens >.|  
|ProfileName|xs:string|O nome ou o perfil de rastreamento que levam a este evento que está sendo emitido|  
|HostReference|xs:string|Hospedados para serviços da Web, este campo identifica unicamente o serviço na hierarquia da Web.  É formato é definido como ' caminho Virtual do aplicativo de nome de Site&#124;caminho Virtual de serviço&#124;ServiceName' exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
