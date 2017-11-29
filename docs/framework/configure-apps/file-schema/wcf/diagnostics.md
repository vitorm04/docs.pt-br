---
title: "&lt;diagnóstico&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
caps.latest.revision: "20"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: df86d364d75f62cbe8be5f72e0b3b120784c35a4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltdiagnosticsgt"></a>&lt;diagnóstico&gt;
O `diagnostics` elemento define configurações que podem ser usadas por um administrador para inspeção de tempo de execução e o controle.  
  
 \<sistema. ServiceModel >  
\<diagnóstico >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.serviceModel>  
   <diagnostics etwProviderId="String"       performanceCounters="Off/ServiceOnly/All/Default"              wmiProviderEnabled="Boolean" >       <endToEndTracing activityTracing="Boolean"  
          messageFlowTracing="Boolean"  
          propagateActivity="Boolean" />  
       <messageLogging logEntireMessage="Boolean"  
          logMalformedMessages="Boolean"  
          logMessagesAtServiceLevel="Boolean"  
          logMessagesAtTransportLevel="Boolean"  
          maxMessagesToLog="Integer"  
          maxSizeOfMessageToLog="Integer" >  
          <filters>  
             <clear />  
          </filters>  
       </messageLogging>  
   </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|etwProviderId|Uma cadeia de caracteres que especifica o identificador para o provedor de rastreamento de eventos, que grava eventos em sessões ETW.|  
|performanceCounters|Especifica se os contadores de desempenho para o assembly estão habilitados. Os valores válidos são<br /><br /> -Off: Os contadores de desempenho estão desabilitados.<br />-ServiceOnly: Somente contadores de desempenho relevantes para esse serviço está habilitado.<br />-Todos os: Desempenho contadores podem ser visualizados em tempo de execução.<br />-Padrão: Um _WCF_Admin de instância do contador de desempenho é criada. Esta instância é usada para habilitar a coleta de dados SQM usado pela infraestrutura. Nenhum dos valores de contador para esta instância são atualizadas e, portanto, permanecerão em zero. Este é o valor padrão se nenhuma configuração estiver presente para o WCF.|  
|wmiProviderEnabled|Um valor booleano que especifica se o provedor WMI para o assembly está habilitado. O provedor WMI é necessário para o usuário acessar o tempo de execução para os recursos de inspeção e controle do Windows Communication Foundation (WCF). O padrão é `false`.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<endToEndTracing >](../../../../../docs/framework/configure-apps/file-schema/wcf/endtoendtracing.md)|Um elemento de configuração que permite habilitar e desabilitar diferentes aspectos de rastreamento ponta a ponta durante a execução de um aplicativo de serviço.|  
|[\<messageLogging >](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)|Descreve as configurações de log de mensagens do WCF.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|ServiceModel|O elemento raiz de todos os elementos de configuração do WCF.|  
  
## <a name="remarks"></a>Comentários  
 O `diagnostics` seção define as configurações de diagnóstico para todos os serviços localizados em um assembly. Não é possível definir as configurações de diagnóstico separada no nível de serviço, a menos que haja apenas um serviço no assembly. Atributos são definidos de acordo com os requisitos da seção.  
  
## <a name="example"></a>Exemplo  
  
```xml  
<diagnostics wmiProviderEnabled="false"  
       performanceCounters="all">  
       <messageLogging logEntireMessage="true"  
          logMalformedMessages="true"  
          logMessagesAtServiceLevel="true"  
          logMessagesAtTransportLevel="true"  
          maxMessagesToLog="42"  
          maxSizeOfMessageToLog="42">  
         <filters>  
         <clear />  
    </filters>  
       </messageLogging>  
</diagnostics>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>
