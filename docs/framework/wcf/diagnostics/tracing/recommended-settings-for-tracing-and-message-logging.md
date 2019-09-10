---
title: Configurações recomendadas para registro de rastreamento e mensagens
ms.date: 03/30/2017
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
ms.openlocfilehash: 6e671762edb2d1ca71ce14cb6ef66c64e02bc297
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856088"
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a>Configurações recomendadas para registro de rastreamento e mensagens
Este tópico descreve o rastreamento recomendado e as configurações de log de mensagens para diferentes ambientes operacionais.  
  
## <a name="recommended-settings-for-a-production-environment"></a>Configurações recomendadas para um ambiente de produção  
 Para um ambiente de produção, se você estiver usando fontes de rastreamento do WCF `switchValue` , defina o como aviso. Se você estiver usando a origem `System.ServiceModel` de rastreamento do WCF, `switchValue` defina o `Warning` atributo como `propagateActivity` e o `true`atributo como. Se você estiver usando uma fonte de rastreamento definida pelo usuário, defina `switchValue` o atributo `Warning, ActivityTracing`como. Isso pode ser feito manualmente usando a [ferramenta do editor de configuração (SvcConfigEditor. exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md). Se você não antecipar um impacto no desempenho, poderá definir o `switchValue` atributo como `Information` em todos os casos mencionados anteriormente, o que gera uma quantidade muito grande de dados de rastreamento. O exemplo a seguir demonstra essas configurações recomendadas.  
  
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
 Para implantação ou ambiente de depuração, `Information` escolha `Verbose`ou, junto `ActivityTracing` com para uma fonte de rastreamento ou `System.ServiceModel` definida pelo usuário. Para aprimorar a depuração, você também deve adicionar uma fonte de`System.ServiceModel.MessageLogging`rastreamento adicional () à configuração para habilitar o log de mensagens. Observe que o `switchValue` atributo não tem impacto sobre essa origem de rastreamento.  
  
 O exemplo a seguir demonstra as configurações recomendadas, usando um ouvinte compartilhado que `XmlWriterTraceListener`utiliza o.  
  
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
 Você pode usar o WMI para alterar as definições de configuração em tempo de `wmiProviderEnabled` execução (habilitando o atributo na configuração, conforme demonstrado no exemplo de configuração anterior). Por exemplo, você pode usar o WMI no CIM Studio para alterar os níveis de origem de rastreamento de aviso para informações em tempo de execução. Você deve estar ciente de que o custo de desempenho da depuração dinâmica dessa maneira pode ser muito alto. Para obter mais informações sobre como usar o WMI, consulte o tópico [usando instrumentação de gerenciamento do Windows para diagnóstico](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) .  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a>Habilitar eventos correlacionados no rastreamento de ASP.NET  
 Os eventos ASP.NET não definem a ID de correlação (ActivityId), a menos que o rastreamento de eventos do ASP.NET esteja ativado. Para ver os eventos correlacionados corretamente, você precisa ativar o rastreamento de eventos ASP.NET usando o comando a seguir no console de comando, que pode ser invocado acessando **Iniciar**, **executar** e digitar **cmd**,  
  
```console  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 Para desativar o rastreamento de eventos ASP.NET, use o comando a seguir,  
  
```console
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a>Consulte também

- [Usando a Instrumentação de Gerenciamento do Windows para diagnóstico](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)
