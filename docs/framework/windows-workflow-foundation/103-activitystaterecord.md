---
title: 103 - ActivityStateRecord
ms.date: 03/30/2017
ms.assetid: 57636a9a-561e-44aa-aef9-1f1894aaa6dd
ms.openlocfilehash: 38cec570cffebf6af6d35df481cbec8c7dca8cd1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924378"
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
|Arguments|xs:string|Os argumentos que foram rastreadas com esse evento.  Os valores são armazenados em um elemento xml no formato \<itens >\< nome do item = "argumentName" System "> argumentValue\</item > \< /itens >.  Se nenhum argumento foi acompanhado, que contém a cadeia de caracteres \<itens / >. O tamanho do evento de ETW é limitado pelo tamanho do buffer de ETW ou pela carga máxima útil para um evento de ETW. Se o tamanho do evento excede os limites de ETW, então o evento será truncado soltando as anotações e substituindo o valor de anotação com \<itens >...  \< /itens >.  Os seguintes tipos são armazenados como seu valor como retornados por ToString(); cadeia de caracteres, char, bool, int, short, long, uint, ushort, ulong, System.Single, flutuante, double, System.Guid, System.DateTimeOffset, System.DateTime.  Todos os outros tipos são serializados usando System.Runtime.Serialization.NetDataContractSerializer.|  
|Variáveis|xs:string|Variáveis que foram rastreadas com esse evento.  Os valores são armazenados em um elemento xml no formato \<itens >\< nome do item = "variableName" System "> variableValue\</item > \< /itens >.  Se nenhum variável foi acompanhado, que contém a cadeia de caracteres \<itens / >. O tamanho do evento de ETW é limitado pelo tamanho do buffer de ETW ou pela carga máxima útil para um evento de ETW. Se o tamanho do evento excede os limites de ETW, então o evento será truncado soltando as anotações e substituindo o valor de variáveis com \<itens >...  \< /itens >.  Os seguintes tipos são armazenados como seu valor como retornados por ToString(); cadeia de caracteres, char, bool, int, short, long, uint, ushort, ulong, System.Single, flutuante, double, System.Guid, System.DateTimeOffset, System.DateTime.  Todos os outros tipos são serializados usando System.Runtime.Serialization.NetDataContractSerializer.|  
|Anotações|xs:string|As anotações que foram adicionadas a este evento.  Os valores são armazenados em um elemento xml no formato \<itens >\< nome do item = "tipo" System "> annotationValue\</item > \< /itens >.  Se nenhuma anotação é especificada, a cadeia de caracteres contém \<itens / >. O tamanho do evento de ETW é limitado pelo tamanho do buffer de ETW ou pela carga máxima útil para um evento de ETW. Se o tamanho do evento excede os limites de ETW, então o evento será truncado soltando as anotações e substituindo o valor de anotação com \<itens >...  \< /itens >.|  
|ProfileName|xs:string|O nome ou o perfil de rastreamento que levam a este evento que está sendo emitido|  
|HostReference|xs:string|Hospedados para serviços da Web, este campo identifica unicamente o serviço na hierarquia da Web.  O formato é definido como ' caminho Virtual do aplicativo de nome de Site&#124;caminho Virtual de serviço&#124;ServiceName' exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
