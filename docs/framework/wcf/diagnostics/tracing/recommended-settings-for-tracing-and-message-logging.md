---
title: Configurações recomendadas para registro de rastreamento e mensagens
ms.date: 03/30/2017
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
ms.openlocfilehash: 604aae2c0a0c5390428e7f1a2c99e17e90ee76a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185725"
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a>Configurações recomendadas para registro de rastreamento e mensagens
Este tópico descreve as configurações recomendadas de rastreamento e registro de mensagens para diferentes ambientes operacionais.  
  
## <a name="recommended-settings-for-a-production-environment"></a>Configurações recomendadas para um ambiente de produção  
 Para um ambiente de produção, se você estiver `switchValue` usando fontes de rastreamento WCF, defina o aviso. Se você estiver usando `System.ServiceModel` a fonte `switchValue` de `Warning` rastreamento `propagateActivity` WCF, defina o atributo e o atributo para `true`. Se você estiver usando uma fonte de `switchValue` rastreamento `Warning, ActivityTracing`definida pelo usuário, defina o atributo como . Isso pode ser feito manualmente usando a [Ferramenta do Editor de Configuração (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md). Se você não antecipar um hit no `switchValue` desempenho, `Information` você pode definir o atributo em todos os casos mencionados anteriormente, o que gera uma quantidade bastante grande de dados de rastreamento. O exemplo a seguir demonstra essas configurações recomendadas.  
  
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
 Para implantação ou depuração `Information` `Verbose`do ambiente, escolha ou, juntamente com `ActivityTracing` uma fonte definida pelo usuário ou `System.ServiceModel` trace. Para melhorar a depuração, você também`System.ServiceModel.MessageLogging`deve adicionar uma fonte de rastreamento adicional ( ) à configuração para ativar o registro de mensagens. Observe que `switchValue` o atributo não tem impacto nesta fonte de rastreamento.  
  
 O exemplo a seguir demonstra as configurações recomendadas, usando `XmlWriterTraceListener`um ouvinte compartilhado que utiliza o .  
  
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
  
## <a name="using-wmi-to-modify-settings"></a>Usando o WMI para modificar configurações  
 Você pode usar o WMI para alterar as configurações em tempo de execução (ativando o atributo `wmiProviderEnabled` na configuração, como demonstrado no exemplo de configuração anterior). Por exemplo, você pode usar o WMI dentro do CIM Studio para alterar os níveis de origem de rastreamento de Aviso para Informações em tempo de execução. Você deve estar ciente de que o custo de desempenho da depuração ao vivo desta forma pode ser muito alto. Para obter mais informações sobre o uso do WMI, consulte o [tópico Usando a Instrumentação de Gerenciamento do Windows para Diagnósticos.](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a>Habilite eventos correlacionados no rastreamento de ASP.NET  
 ASP.NET eventos não definam o ID de correlação (ActivityID) a menos que ASP.NET rastreamento de eventos esteja ligado. Para ver os eventos correlacionados corretamente, você tem que ativar ASP.NET rastreamento de eventos usando o seguinte comando no console de comando, que pode ser invocado indo para **Iniciar**, **Executar** e digitar **cmd**,  
  
```console  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 Para desativar o rastreamento de eventos ASP.NET, use o seguinte comando,  
  
```console
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a>Confira também

- [Usando a Instrumentação de Gerenciamento do Windows para diagnóstico](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)
