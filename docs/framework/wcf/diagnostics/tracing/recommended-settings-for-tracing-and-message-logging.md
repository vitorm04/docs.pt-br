---
title: "Configurações recomendadas para registro de rastreamento e mensagens"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1894ee59b6120abfe4cb216baba086fcd1650f77
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a>Configurações recomendadas para registro de rastreamento e mensagens
Este tópico descreve o rastreamento recomendado e as configurações de log de mensagem para ambientes operacionais diferentes.  
  
## <a name="recommended-settings-for-a-production-environment"></a>Configurações recomendadas para um ambiente de produção  
 Para um ambiente de produção, se você estiver usando fontes de rastreamento do WCF, defina o `switchValue` para aviso. Se você estiver usando o WCF `System.ServiceModel` origem do rastreamento, defina o `switchValue` atributo `Warning` e `propagateActivity` atributo `true`. Se você estiver usando uma origem de rastreamento definidos pelo usuário, defina o `switchValue` atributo `Warning, ActivityTracing`. Isso pode ser feito manualmente usando o [ferramenta Configuration Editor (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md). Se você não pretende um impacto no desempenho, você pode definir o `switchValue` atributo `Information` em todos os casos mencionados anteriormente, que gera uma quantidade muito grande de dados de rastreamento. O exemplo a seguir demonstra essas configurações recomendadas.  
  
```xml  
<configuration>  
 <system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel"  
            switchValue="Warning"  
            propagateActivity="true" >  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="myUserTraceSource"  
            switchValue="Warning, ActivityTracing">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="xml"  
         type="System.Diagnostics.XmlWriterTraceListener"  
               initializeData="C:\logs\Traces.svclog" />  
  </sharedListeners>  
 </system.diagnostics>  
  
<system.serviceModel>  
  <diagnostics wmiProviderEnabled="true">  
  </diagnostics>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="recommended-settings-for-deployment-or-debugging"></a>Configurações recomendadas para a implantação ou a depuração  
 Para implantação ou ambiente de depuração, escolha `Information` ou `Verbose`, juntamente com `ActivityTracing` para qualquer uma definida pelo usuário ou `System.ServiceModel` origem do rastreamento. Para aprimorar a depuração, você também deve adicionar uma origem de rastreamento adicionais (`System.ServiceModel.MessageLogging`) para a configuração para habilitar o log de mensagem. Observe que o `switchValue` atributo não tem impacto sobre a origem de rastreamento.  
  
 O exemplo a seguir demonstra as configurações recomendadas, usando um ouvinte compartilhado que utiliza o `XmlWriterTraceListener`.  
  
```xml  
<configuration>  
 <system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel"  
            switchValue="Information, ActivityTracing"  
            propagateActivity="true" >  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="System.ServiceModel.MessageLogging">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="myUserTraceSource"  
            switchValue="Information, ActivityTracing">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="xml"  
         type="System.Diagnostics.XmlWriterTraceListener"  
               initializeData="C:\logs\Traces.svclog" />  
  </sharedListeners>  
 </system.diagnostics>  
  
 <system.serviceModel>  
  <diagnostics wmiProviderEnabled="true">  
      <messageLogging   
           logEntireMessage="true"   
           logMalformedMessages="true"  
           logMessagesAtServiceLevel="true"   
           logMessagesAtTransportLevel="true"  
           maxMessagesToLog="3000"   
       />  
  </diagnostics>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="using-wmi-to-modify-settings"></a>Usando a WMI para modificar as configurações  
 Você pode usar o WMI para alterar as definições de configuração em tempo de execução (habilitando o `wmiProviderEnabled` atributo na configuração, conforme demonstrado no anteriormente exemplo de configuração). Por exemplo, você pode usar o WMI no CIM Studio para alterar os níveis de origem de rastreamento de aviso para obter informações em tempo de execução. Você deve estar ciente de que o custo de desempenho de depuração ao vivo dessa maneira pode ser muito alto. Para obter mais informações sobre como usar o WMI, consulte o [usando o Windows Management Instrumentation para diagnóstico](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) tópico.  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a>Habilitar eventos correlacionados no rastreamento do ASP.NET  
 Eventos do ASP.NET não define a ID de correlação (ActivityID), a menos que o rastreamento de eventos do ASP.NET é ativado. Para ver os eventos correlacionados corretamente, você precisa ativar eventos do ASP.NET rastreamento usando o seguinte comando no console de comando, que pode ser invocado acessando **iniciar**, **executar** e tipo **cmd** ,  
  
```  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 Para desativar o rastreamento de eventos do ASP.NET, use o seguinte comando,  
  
```  
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a>Consulte também  
 [Usando o Windows Management Instrumentation para diagnóstico](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)
