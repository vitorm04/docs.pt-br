---
title: 108 - CustomTrackingRecordInfo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5bee501e-4e00-42cd-b949-e88009c3d4e8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8357e6afac6ea1d59e4850bf0e32c60726b7c5f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="108---customtrackingrecordinfo"></a>108 - CustomTrackingRecordInfo
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|Id|108|  
|Palavras-chave|UserEvents, EndToEndMonitoring, solução de problemas, HealthMonitoring, WFTracking|  
|Nível|Informações|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico|  
  
## <a name="description"></a>Descrição  
 Este evento é emitido pelo participante de rastreamento de ETW quando uma atividade em uma instância de fluxo de trabalho se emite CustomTrackingRecord com informações de liberação.  
  
## <a name="message"></a>Mensagem  
 TrackRecord = CustomTrackingRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, nome = %4, Nome_da_atividade = %5, ActivityId = %6, ActivityInstanceId = %7, ActivityTypeName = %8, dados = %9, anotações = % 10, ProfileName = % 11  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|A identificação de instância para o fluxo de trabalho|  
|RecordNumber|xs:long|O número de sequência do registro emitido|  
|EventTime|xs:dateTime|A hora UTC quando o evento foi emitido|  
|Nome|xs:string|O nome de CustomTrackingRecord|  
|ActivityName|xs:string|O nome da atividade que se emitiu o CustomTrackingRecord|  
|ActivityId|xs:string|A identificação da atividade que se emitiu o CustomTrackingRecord|  
|ActivityInstanceId|xs:string|A identificação de instância de atividade que se emitiu o CustomTrackingRecord|  
|ActivityTypeName|xs:string|O nome da atividade que se emitiu o CustomTrackingRecord|  
|Dados|xs:string|Os dados que foram rastreadas com esse evento.  Os valores são armazenados em um elemento xml no formato \<itens >\< nome do item = "dataName" type="System.String" > dataValue\</item > \< /itens >.  Se nenhum dado foi controlado, a cadeia de caracteres contém \<itens / >. O tamanho do evento de ETW é limitado pelo tamanho do buffer de ETW ou pela carga máxima útil para um evento de ETW. Se o tamanho do evento excede os limites ETW, o evento é truncado descartando as anotações e substituindo o valor de dados com \<itens >...  \< /itens >.  Os seguintes tipos são armazenados como seu valor como retornados por ToString(); cadeia de caracteres, char, bool, int, short, long, uint, ushort, ulong, System.Single, flutuante, double, System.Guid, System.DateTimeOffset, System.DateTime.  Todos os outros tipos são serializados usando System.Runtime.Serialization.NetDataContractSerializer.|  
|Anotações|xs:string|As anotações que foram adicionadas a este evento.  Os valores são armazenados em um elemento xml no formato \<itens >\< nome do item = "annotationName" type="System.String" > annotationValue\</item > \< /itens >.  Se nenhuma anotação é especificada, em seguida, a cadeia de caracteres contém \<itens / >. O tamanho do evento de ETW é limitado pelo tamanho do buffer de ETW ou pela carga máxima útil para um evento de ETW. Se o tamanho do evento excede os limites ETW, o evento é truncado descartando as anotações e substituindo o valor anotação com \<itens >...  \< /itens >.|  
|ProfileName|xs:string|O nome ou o perfil de rastreamento que levam a este evento que está sendo emitido|  
|HostReference|xs:string|Hospedados para serviços da Web, este campo identifica unicamente o serviço na hierarquia da Web.  O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName' exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
