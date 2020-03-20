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
# <a name="recommended-settings-for-tracing-and-message-logging"></a><span data-ttu-id="4524c-102">Configurações recomendadas para registro de rastreamento e mensagens</span><span class="sxs-lookup"><span data-stu-id="4524c-102">Recommended Settings for Tracing and Message Logging</span></span>
<span data-ttu-id="4524c-103">Este tópico descreve as configurações recomendadas de rastreamento e registro de mensagens para diferentes ambientes operacionais.</span><span class="sxs-lookup"><span data-stu-id="4524c-103">This topic describes recommended tracing and message logging settings for different operating environments.</span></span>  
  
## <a name="recommended-settings-for-a-production-environment"></a><span data-ttu-id="4524c-104">Configurações recomendadas para um ambiente de produção</span><span class="sxs-lookup"><span data-stu-id="4524c-104">Recommended Settings for a Production Environment</span></span>  
 <span data-ttu-id="4524c-105">Para um ambiente de produção, se você estiver `switchValue` usando fontes de rastreamento WCF, defina o aviso.</span><span class="sxs-lookup"><span data-stu-id="4524c-105">For a production environment, if you are using WCF trace sources, set the `switchValue` to Warning.</span></span> <span data-ttu-id="4524c-106">Se você estiver usando `System.ServiceModel` a fonte `switchValue` de `Warning` rastreamento `propagateActivity` WCF, defina o atributo e o atributo para `true`.</span><span class="sxs-lookup"><span data-stu-id="4524c-106">If you are using the WCF `System.ServiceModel` trace source, set the `switchValue` attribute to `Warning` and the `propagateActivity` attribute to `true`.</span></span> <span data-ttu-id="4524c-107">Se você estiver usando uma fonte de `switchValue` rastreamento `Warning, ActivityTracing`definida pelo usuário, defina o atributo como .</span><span class="sxs-lookup"><span data-stu-id="4524c-107">If you are using a user-defined trace source, set the `switchValue` attribute to `Warning, ActivityTracing`.</span></span> <span data-ttu-id="4524c-108">Isso pode ser feito manualmente usando a [Ferramenta do Editor de Configuração (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="4524c-108">This can be done manually using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span> <span data-ttu-id="4524c-109">Se você não antecipar um hit no `switchValue` desempenho, `Information` você pode definir o atributo em todos os casos mencionados anteriormente, o que gera uma quantidade bastante grande de dados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="4524c-109">If you do not anticipate a hit in performance, you can set the `switchValue` attribute to `Information` in all the previously mentioned cases, which generates a fairly large amount of trace data.</span></span> <span data-ttu-id="4524c-110">O exemplo a seguir demonstra essas configurações recomendadas.</span><span class="sxs-lookup"><span data-stu-id="4524c-110">The following example demonstrates these recommended settings.</span></span>  
  
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
  
## <a name="recommended-settings-for-deployment-or-debugging"></a><span data-ttu-id="4524c-111">Configurações recomendadas para implantação ou depuração</span><span class="sxs-lookup"><span data-stu-id="4524c-111">Recommended Settings for Deployment or Debugging</span></span>  
 <span data-ttu-id="4524c-112">Para implantação ou depuração `Information` `Verbose`do ambiente, escolha ou, juntamente com `ActivityTracing` uma fonte definida pelo usuário ou `System.ServiceModel` trace.</span><span class="sxs-lookup"><span data-stu-id="4524c-112">For deployment or debugging environment, choose `Information` or `Verbose`, along with `ActivityTracing` for either a user-defined or `System.ServiceModel` trace source.</span></span> <span data-ttu-id="4524c-113">Para melhorar a depuração, você também`System.ServiceModel.MessageLogging`deve adicionar uma fonte de rastreamento adicional ( ) à configuração para ativar o registro de mensagens.</span><span class="sxs-lookup"><span data-stu-id="4524c-113">To enhance debugging, you should also add an additional trace source (`System.ServiceModel.MessageLogging`) to the configuration to enable message logging.</span></span> <span data-ttu-id="4524c-114">Observe que `switchValue` o atributo não tem impacto nesta fonte de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="4524c-114">Notice that the `switchValue` attribute has no impact on this trace source.</span></span>  
  
 <span data-ttu-id="4524c-115">O exemplo a seguir demonstra as configurações recomendadas, usando `XmlWriterTraceListener`um ouvinte compartilhado que utiliza o .</span><span class="sxs-lookup"><span data-stu-id="4524c-115">The following example demonstrates the recommended settings, using a shared listener that utilizes the `XmlWriterTraceListener`.</span></span>  
  
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
  
## <a name="using-wmi-to-modify-settings"></a><span data-ttu-id="4524c-116">Usando o WMI para modificar configurações</span><span class="sxs-lookup"><span data-stu-id="4524c-116">Using WMI to Modify Settings</span></span>  
 <span data-ttu-id="4524c-117">Você pode usar o WMI para alterar as configurações em tempo de execução (ativando o atributo `wmiProviderEnabled` na configuração, como demonstrado no exemplo de configuração anterior).</span><span class="sxs-lookup"><span data-stu-id="4524c-117">You can use WMI to change configuration settings at runtime (by enabling the `wmiProviderEnabled` attribute in the configuration, as demonstrated in the previously configuration example).</span></span> <span data-ttu-id="4524c-118">Por exemplo, você pode usar o WMI dentro do CIM Studio para alterar os níveis de origem de rastreamento de Aviso para Informações em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4524c-118">For example, you can use WMI within the CIM Studio to change the trace source levels from Warning to Information at runtime.</span></span> <span data-ttu-id="4524c-119">Você deve estar ciente de que o custo de desempenho da depuração ao vivo desta forma pode ser muito alto.</span><span class="sxs-lookup"><span data-stu-id="4524c-119">You should be aware that the performance cost of live debugging in this way can be very high.</span></span> <span data-ttu-id="4524c-120">Para obter mais informações sobre o uso do WMI, consulte o [tópico Usando a Instrumentação de Gerenciamento do Windows para Diagnósticos.](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)</span><span class="sxs-lookup"><span data-stu-id="4524c-120">For more information about using WMI, see the [Using Windows Management Instrumentation for Diagnostics](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) topic.</span></span>  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a><span data-ttu-id="4524c-121">Habilite eventos correlacionados no rastreamento de ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4524c-121">Enable Correlated Events in ASP.NET Tracing</span></span>  
 <span data-ttu-id="4524c-122">ASP.NET eventos não definam o ID de correlação (ActivityID) a menos que ASP.NET rastreamento de eventos esteja ligado.</span><span class="sxs-lookup"><span data-stu-id="4524c-122">ASP.NET events do not set the correlation ID (ActivityID) unless ASP.NET event tracing is turned on.</span></span> <span data-ttu-id="4524c-123">Para ver os eventos correlacionados corretamente, você tem que ativar ASP.NET rastreamento de eventos usando o seguinte comando no console de comando, que pode ser invocado indo para **Iniciar**, **Executar** e digitar **cmd**,</span><span class="sxs-lookup"><span data-stu-id="4524c-123">To see correlated events properly, you have to turn on ASP.NET events tracing using the following command in the command console, which can be invoked by going to **Start**, **Run** and type **cmd**,</span></span>  
  
```console  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 <span data-ttu-id="4524c-124">Para desativar o rastreamento de eventos ASP.NET, use o seguinte comando,</span><span class="sxs-lookup"><span data-stu-id="4524c-124">To turn off tracing of ASP.NET events, use the following command,</span></span>  
  
```console
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a><span data-ttu-id="4524c-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="4524c-125">See also</span></span>

- [<span data-ttu-id="4524c-126">Usando a Instrumentação de Gerenciamento do Windows para diagnóstico</span><span class="sxs-lookup"><span data-stu-id="4524c-126">Using Windows Management Instrumentation for Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)
