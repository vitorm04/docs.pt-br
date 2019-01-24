---
title: Configurações recomendadas para registro de rastreamento e mensagens
ms.date: 03/30/2017
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
ms.openlocfilehash: dff4b20547cccca628ac76afc890a2817e838907
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585205"
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a>Configurações recomendadas para registro de rastreamento e mensagens
Este tópico descreve o rastreamento recomendado e configurações de registro em log de mensagem para ambientes operacionais diferentes.  
  
## <a name="recommended-settings-for-a-production-environment"></a>Configurações recomendadas para um ambiente de produção  
 Para um ambiente de produção, se você estiver usando fontes de rastreamento do WCF, defina o `switchValue` ao aviso. Se você estiver usando o WCF `System.ServiceModel` fonte de rastreamento, defina o `switchValue` atributo `Warning` e o `propagateActivity` atributo `true`. Se você estiver usando uma origem de rastreamento definidos pelo usuário, defina as `switchValue` atributo `Warning, ActivityTracing`. Isso pode ser feito manualmente usando o [ferramenta de Editor de configuração (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md). Se você não pretende um impacto no desempenho, você pode definir as `switchValue` atributo `Information` em todos os casos mencionados anteriormente, que gera uma quantidade muito grande de dados de rastreamento. O exemplo a seguir demonstra essas configurações recomendadas.  
  
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
  
## <a name="recommended-settings-for-deployment-or-debugging"></a>Configurações recomendadas para implantação ou depuração  
 Para implantação ou ambiente de depuração, escolha `Information` ou `Verbose`, juntamente com `ActivityTracing` para qualquer uma definida pelo usuário ou `System.ServiceModel` origem de rastreamento. Para melhorar a depuração, você também deve adicionar uma origem de rastreamento adicionais (`System.ServiceModel.MessageLogging`) para a configuração para habilitar o log de mensagem. Observe que o `switchValue` atributo não tem impacto sobre a origem de rastreamento.  
  
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
  
## <a name="using-wmi-to-modify-settings"></a>Usando o WMI para modificar as configurações  
 Você pode usar o WMI para alterar as configurações em tempo de execução (, permitindo a `wmiProviderEnabled` de atributo na configuração, conforme demonstrado no exemplo de configuração anteriormente). Por exemplo, você pode usar o WMI no CIM Studio para alterar os níveis de origem de rastreamento de aviso para obter informações em tempo de execução. Você deve estar ciente de que o custo de desempenho de depuração ao vivo dessa maneira pode ser muito alto. Para obter mais informações sobre como usar o WMI, consulte o [usando o Windows Management Instrumentation para diagnóstico](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) tópico.  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a>Habilitar eventos correlacionados no rastreamento do ASP.NET  
 Eventos do ASP.NET não definem a ID de correlação (ActivityID), a menos que o rastreamento de eventos do ASP.NET está ativado. Para ver eventos correlacionados corretamente, você precisa ativar eventos do ASP.NET rastreamento usando o seguinte comando no console de comando, que pode ser invocado acessando **iniciar**, **execute** e o tipo **cmd** ,  
  
```  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 Para desativar o rastreamento de eventos do ASP.NET, use o seguinte comando,  
  
```  
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a>Consulte também
- [Usando a Instrumentação de Gerenciamento do Windows para diagnóstico](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)
