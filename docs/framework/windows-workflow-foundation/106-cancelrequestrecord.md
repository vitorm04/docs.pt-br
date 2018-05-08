---
title: 106 - CancelRequestRecord
ms.date: 03/30/2017
ms.assetid: f72a59aa-8093-4a8e-94df-40acaffb1ffb
ms.openlocfilehash: 4d2e9bd271c04a9e26150e7dddffc33963dfe0a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="106---cancelrequestrecord"></a>106 - CancelRequestRecord
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|Id|106|  
|Palavras-chave|EndToEndMonitoring, solução de problemas, HealthMonitoring, WFTracking|  
|Nível|Informações|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico|  
  
## <a name="description"></a>Descrição  
 Este evento é emitido pelo participante de rastreamento de ETW quando uma atividade em uma instância de fluxo de trabalho se chama o cancelrequestedrecord.  
  
## <a name="message"></a>Mensagem  
 TrackRecord = CancelRequestedRecord, InstanceID=%1, RecordNumber=%2, EventTime=%3, Name=%4, ActivityId=%5, ActivityInstanceId=%6, ActivityTypeName =, %7 ChildActivityName =, %8 ChildActivityId = %9, ChildActivityInstanceId = %10, ChildActivityTypeName =%11, Annotations=%12, ProfileName = %13  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|A identificação de instância para o fluxo de trabalho|  
|RecordNumber|xs:long|O número de sequência do registro emitido|  
|EventTime|xs:dateTime|A hora UTC quando o evento foi emitido|  
|Nome|xs:string|O nome da atividade que solicitou a operação de cancelamento|  
|ActivityId|xs:string|A identificação da atividade que solicitou a operação de cancelamento|  
|ActivityInstanceId|xs:string|A identificação de instância de atividade que solicitou a operação de cancelamento|  
|ActivityTypeName|xs:string|O tipo de atividade que solicitou a operação de cancelamento|  
|ChildActivityName|xs:string|O nome da atividade que está sendo cancelada|  
|ChildActivityId|xs:string|A identificação da atividade que está sendo cancelada|  
|ChildActivityInstanceId|xs:string|A identificação de instância de atividade que está sendo cancelada|  
|ChildActivityTypeName|xs:string|O tipo de atividade que está sendo cancelada|  
|Anotações|xs:string|As anotações que foram adicionadas a este evento.  Os valores são armazenados em um elemento xml no formato \<itens >\< nome do item = "annotationName" type="System.String" > annotationValue\</item > \< /itens >.  Se nenhuma anotação é especificada, em seguida, a cadeia de caracteres contém \<itens / >. O tamanho do evento de ETW é limitado pelo tamanho do buffer de ETW ou pela carga máxima útil para um evento de ETW. Se o tamanho do evento excede os limites ETW, o evento é truncado descartando as anotações e substituindo o valor anotação com \<itens >...  \< /itens >.|  
|ProfileName|xs:string|O nome ou o perfil de rastreamento que levam a este evento que está sendo emitido|  
|HostReference|xs:string|Hospedados para serviços da Web, este campo identifica unicamente o serviço na hierarquia da Web.  O formato é definido como ' caminho Virtual do aplicativo Web Site nome&#124;caminho Virtual do serviço&#124;ServiceName' exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
