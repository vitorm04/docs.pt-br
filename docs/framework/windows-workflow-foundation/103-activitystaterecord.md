---
title: 103 - ActivityStateRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57636a9a-561e-44aa-aef9-1f1894aaa6dd
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 60dff5365ea98d767a271998a2de9fe3b1aae591
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="103---activitystaterecord"></a>103 - ActivityStateRecord
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|Id|103|  
|Palavras-chave|EndToEndMonitoring, solução de problemas, HealthMonitoring, WFTracking|  
|Nível|Informações|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico|  
  
## <a name="description"></a>Descrição  
 Este evento é emitido pelo participante de rastreamento de ETW quando uma atividade em uma instância de fluxo de trabalho se emite ActivityStateRecord  
  
## <a name="message"></a>Mensagem  
 TrackRecord = ActivityStateRecord, InstanceID = %1, RecordNumber=%2, EventTime=%3, estado = %4, Name=%5, ActivityId=%6, ActivityInstanceId=%7, ActivityTypeName=%8, Arguments=%9, Variables=%10, Annotations=%11, ProfileName = %12  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|A identificação de instância para o fluxo de trabalho|  
|RecordNumber|xs:long|O número de sequência do registro emitido|  
|EventTime|xs:dateTime|A hora UTC quando o evento foi emitido|  
|Estado|xs:string|O estado de atividades|  
|Nome|xs:string|O nome para exibição de atividade que se emitiu o evento|  
|ActivityId|xs:string|A identificação de atividade de atividade emitindo|  
|ActivityInstanceId|xs:string|A identificação de instância de atividade de atividade emitindo|  
|ActivityTypeName|xs:string|O nome do tipo de atividade emitindo|  
|Arguments|xs:string|Os argumentos que foram rastreadas com esse evento.  Os valores são armazenados em um elemento xml no formato \<itens >\< nome do item = "argumentName" type="System.String" > argumentValue\</item > \< /itens >.  Se nenhum argumento eram controlado, a cadeia de caracteres contém \<itens / >. O tamanho do evento de ETW é limitado pelo tamanho do buffer de ETW ou pela carga máxima útil para um evento de ETW. Se o tamanho do evento excede os limites ETW, o evento é truncado descartando as anotações e substituindo o valor anotação com \<itens >...  \< /itens >.  Os seguintes tipos são armazenados como seu valor como retornados por ToString(); cadeia de caracteres, char, bool, int, short, long, uint, ushort, ulong, System.Single, flutuante, double, System.Guid, System.DateTimeOffset, System.DateTime.  Todos os outros tipos são serializados usando System.Runtime.Serialization.NetDataContractSerializer.|  
|Variáveis|xs:string|Variáveis que foram rastreadas com esse evento.  Os valores são armazenados em um elemento xml no formato \<itens >\< nome do item = "variableName" type="System.String" > variableValue\</item > \< /itens >.  Se nenhuma variável eram controladas, que contém a cadeia de caracteres \<itens / >. O tamanho do evento de ETW é limitado pelo tamanho do buffer de ETW ou pela carga máxima útil para um evento de ETW. Se o tamanho do evento excede os limites ETW, o evento é truncado descartando as anotações e substituindo o valor de variáveis com \<itens >...  \< /itens >.  Os seguintes tipos são armazenados como seu valor como retornados por ToString(); cadeia de caracteres, char, bool, int, short, long, uint, ushort, ulong, System.Single, flutuante, double, System.Guid, System.DateTimeOffset, System.DateTime.  Todos os outros tipos são serializados usando System.Runtime.Serialization.NetDataContractSerializer.|  
|Anotações|xs:string|As anotações que foram adicionadas a este evento.  Os valores são armazenados em um elemento xml no formato \<itens >\< nome do item = "annotationName" type="System.String" > annotationValue\</item > \< /itens >.  Se nenhuma anotação é especificada, em seguida, a cadeia de caracteres contém \<itens / >. O tamanho do evento de ETW é limitado pelo tamanho do buffer de ETW ou pela carga máxima útil para um evento de ETW. Se o tamanho do evento excede os limites ETW, o evento é truncado descartando as anotações e substituindo o valor anotação com \<itens >...  \< /itens >.|  
|ProfileName|xs:string|O nome ou o perfil de rastreamento que levam a este evento que está sendo emitido|  
|HostReference|xs:string|Hospedados para serviços da Web, este campo identifica unicamente o serviço na hierarquia da Web.  O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName' exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
