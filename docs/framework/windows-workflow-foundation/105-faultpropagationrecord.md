---
title: 105 - FaultPropagationRecord
ms.date: 03/30/2017
ms.assetid: 168473b1-b1e5-4e9f-8a2a-35bbdb2ef531
ms.openlocfilehash: c48f42a91ad9a15b49aad8c1ab684f2348954174
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924196"
---
# <a name="105---faultpropagationrecord"></a>105 - FaultPropagationRecord
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|Id|105|  
|Palavras-chave|EndToEndMonitoring, solução de problemas, HealthMonitoring, WFTracking|  
|Nível|Aviso|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico|  
  
## <a name="description"></a>Descrição  
 Este evento é emitido pelo participante de rastreamento de ETW quando uma atividade com a instância de fluxo de trabalho se emite FaultPropagationRecord.  
  
## <a name="message"></a>Mensagem  
 TrackRecord = {1&gt;faultpropagationrecord&lt;1, InstanceID = %1, RecordNumber = %2, EventTime = %3, FaultSourceActivityName = %4, FaultSourceActivityId = %5, FaultSourceActivityInstanceId = %6, FaultSourceActivityTypeName =, %7 FaultHandlerActivityName =, %8  FaultHandlerActivityId = %9, FaultHandlerActivityInstanceId = % 10, FaultHandlerActivityTypeName = falha de 11, % = IsFaultSource de 12, % = anotações de % 13, 14, ProfileName = % 15  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|A identificação de instância para o fluxo de trabalho|  
|RecordNumber|xs:long|O número de sequência do registro emitido|  
|EventTime|xs:dateTime|A hora UTC quando o evento foi emitido|  
|FaultSourceActivityName|xs:string|O nome da atividade que se emitiu a falha|  
|FaultSourceActivityId|xs:string|A identificação da atividade que se emitiu a falha|  
|FaultSourceActivityInstanceId|xs:string|A identificação de instância de atividade que se emitiu a falha|  
|FaultSourceActivityTypeName|xs:string|O tipo de atividade que se emitiu a falha|  
|FaultHandlerActivityName|xs:string|O nome para exibição de atividade do manipulador de falha|  
|FaultHandlerActivityId|xs:string|A identificação de atividade do manipulador de falha|  
|FaultHandlerActivityInstanceId|xs:string|A identificação de instância de atividade do manipulador de falha|  
|FaultHandlerActivityTypeName|xs:string|O tipo de atividade do manipulador de falha|  
|Fault|xs:string|Os detalhes de falha|  
|IsFaultSource|xs:unsignedByte|Indica se o evento foi emitido de origem de falha|  
|Anotações|xs:string|As anotações que foram adicionadas a este evento.  Os valores são armazenados em um elemento xml no formato \<itens >\< nome do item = "tipo" System "> annotationValue\</item > \< /itens >.  Se nenhuma anotação é especificada, a cadeia de caracteres contém \<itens / >. O tamanho do evento de ETW é limitado pelo tamanho do buffer de ETW ou pela carga máxima útil para um evento de ETW. Se o tamanho do evento excede os limites de ETW, então o evento será truncado soltando as anotações e substituindo o valor de anotação com \<itens >...  \< /itens >.|  
|ProfileName|xs:string|O nome ou o perfil de rastreamento que levam a este evento que está sendo emitido|  
|HostReference|xs:string|Hospedados para serviços da Web, este campo identifica unicamente o serviço na hierarquia da Web.  O formato é definido como ' caminho Virtual do aplicativo de nome de Site&#124;caminho Virtual de serviço&#124;ServiceName' exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
