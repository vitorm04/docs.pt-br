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
# <a name="recommended-settings-for-tracing-and-message-logging"></a><span data-ttu-id="056a8-102">Configurações recomendadas para registro de rastreamento e mensagens</span><span class="sxs-lookup"><span data-stu-id="056a8-102">Recommended Settings for Tracing and Message Logging</span></span>
<span data-ttu-id="056a8-103">Este tópico descreve o rastreamento recomendado e as configurações de log de mensagens para diferentes ambientes operacionais.</span><span class="sxs-lookup"><span data-stu-id="056a8-103">This topic describes recommended tracing and message logging settings for different operating environments.</span></span>  
  
## <a name="recommended-settings-for-a-production-environment"></a><span data-ttu-id="056a8-104">Configurações recomendadas para um ambiente de produção</span><span class="sxs-lookup"><span data-stu-id="056a8-104">Recommended Settings for a Production Environment</span></span>  
 <span data-ttu-id="056a8-105">Para um ambiente de produção, se você estiver usando fontes de rastreamento do WCF `switchValue` , defina o como aviso.</span><span class="sxs-lookup"><span data-stu-id="056a8-105">For a production environment, if you are using WCF trace sources, set the `switchValue` to Warning.</span></span> <span data-ttu-id="056a8-106">Se você estiver usando a origem `System.ServiceModel` de rastreamento do WCF, `switchValue` defina o `Warning` atributo como `propagateActivity` e o `true`atributo como.</span><span class="sxs-lookup"><span data-stu-id="056a8-106">If you are using the WCF `System.ServiceModel` trace source, set the `switchValue` attribute to `Warning` and the `propagateActivity` attribute to `true`.</span></span> <span data-ttu-id="056a8-107">Se você estiver usando uma fonte de rastreamento definida pelo usuário, defina `switchValue` o atributo `Warning, ActivityTracing`como.</span><span class="sxs-lookup"><span data-stu-id="056a8-107">If you are using a user-defined trace source, set the `switchValue` attribute to `Warning, ActivityTracing`.</span></span> <span data-ttu-id="056a8-108">Isso pode ser feito manualmente usando a [ferramenta do editor de configuração (SvcConfigEditor. exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="056a8-108">This can be done manually using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span> <span data-ttu-id="056a8-109">Se você não antecipar um impacto no desempenho, poderá definir o `switchValue` atributo como `Information` em todos os casos mencionados anteriormente, o que gera uma quantidade muito grande de dados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="056a8-109">If you do not anticipate a hit in performance, you can set the `switchValue` attribute to `Information` in all the previously mentioned cases, which generates a fairly large amount of trace data.</span></span> <span data-ttu-id="056a8-110">O exemplo a seguir demonstra essas configurações recomendadas.</span><span class="sxs-lookup"><span data-stu-id="056a8-110">The following example demonstrates these recommended settings.</span></span>  
  
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
  
## <a name="recommended-settings-for-deployment-or-debugging"></a><span data-ttu-id="056a8-111">Configurações recomendadas para implantação ou depuração</span><span class="sxs-lookup"><span data-stu-id="056a8-111">Recommended Settings for Deployment or Debugging</span></span>  
 <span data-ttu-id="056a8-112">Para implantação ou ambiente de depuração, `Information` escolha `Verbose`ou, junto `ActivityTracing` com para uma fonte de rastreamento ou `System.ServiceModel` definida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="056a8-112">For deployment or debugging environment, choose `Information` or `Verbose`, along with `ActivityTracing` for either a user-defined or `System.ServiceModel` trace source.</span></span> <span data-ttu-id="056a8-113">Para aprimorar a depuração, você também deve adicionar uma fonte de`System.ServiceModel.MessageLogging`rastreamento adicional () à configuração para habilitar o log de mensagens.</span><span class="sxs-lookup"><span data-stu-id="056a8-113">To enhance debugging, you should also add an additional trace source (`System.ServiceModel.MessageLogging`) to the configuration to enable message logging.</span></span> <span data-ttu-id="056a8-114">Observe que o `switchValue` atributo não tem impacto sobre essa origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="056a8-114">Notice that the `switchValue` attribute has no impact on this trace source.</span></span>  
  
 <span data-ttu-id="056a8-115">O exemplo a seguir demonstra as configurações recomendadas, usando um ouvinte compartilhado que `XmlWriterTraceListener`utiliza o.</span><span class="sxs-lookup"><span data-stu-id="056a8-115">The following example demonstrates the recommended settings, using a shared listener that utilizes the `XmlWriterTraceListener`.</span></span>  
  
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
  
## <a name="using-wmi-to-modify-settings"></a><span data-ttu-id="056a8-116">Usando o WMI para modificar as configurações</span><span class="sxs-lookup"><span data-stu-id="056a8-116">Using WMI to Modify Settings</span></span>  
 <span data-ttu-id="056a8-117">Você pode usar o WMI para alterar as definições de configuração em tempo de `wmiProviderEnabled` execução (habilitando o atributo na configuração, conforme demonstrado no exemplo de configuração anterior).</span><span class="sxs-lookup"><span data-stu-id="056a8-117">You can use WMI to change configuration settings at runtime (by enabling the `wmiProviderEnabled` attribute in the configuration, as demonstrated in the previously configuration example).</span></span> <span data-ttu-id="056a8-118">Por exemplo, você pode usar o WMI no CIM Studio para alterar os níveis de origem de rastreamento de aviso para informações em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="056a8-118">For example, you can use WMI within the CIM Studio to change the trace source levels from Warning to Information at runtime.</span></span> <span data-ttu-id="056a8-119">Você deve estar ciente de que o custo de desempenho da depuração dinâmica dessa maneira pode ser muito alto.</span><span class="sxs-lookup"><span data-stu-id="056a8-119">You should be aware that the performance cost of live debugging in this way can be very high.</span></span> <span data-ttu-id="056a8-120">Para obter mais informações sobre como usar o WMI, consulte o tópico [usando instrumentação de gerenciamento do Windows para diagnóstico](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) .</span><span class="sxs-lookup"><span data-stu-id="056a8-120">For more information about using WMI, see the [Using Windows Management Instrumentation for Diagnostics](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) topic.</span></span>  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a><span data-ttu-id="056a8-121">Habilitar eventos correlacionados no rastreamento de ASP.NET</span><span class="sxs-lookup"><span data-stu-id="056a8-121">Enable Correlated Events in ASP.NET Tracing</span></span>  
 <span data-ttu-id="056a8-122">Os eventos ASP.NET não definem a ID de correlação (ActivityId), a menos que o rastreamento de eventos do ASP.NET esteja ativado.</span><span class="sxs-lookup"><span data-stu-id="056a8-122">ASP.NET events do not set the correlation ID (ActivityID) unless ASP.NET event tracing is turned on.</span></span> <span data-ttu-id="056a8-123">Para ver os eventos correlacionados corretamente, você precisa ativar o rastreamento de eventos ASP.NET usando o comando a seguir no console de comando, que pode ser invocado acessando **Iniciar**, **executar** e digitar **cmd**,</span><span class="sxs-lookup"><span data-stu-id="056a8-123">To see correlated events properly, you have to turn on ASP.NET events tracing using the following command in the command console, which can be invoked by going to **Start**, **Run** and type **cmd**,</span></span>  
  
```console  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 <span data-ttu-id="056a8-124">Para desativar o rastreamento de eventos ASP.NET, use o comando a seguir,</span><span class="sxs-lookup"><span data-stu-id="056a8-124">To turn off tracing of ASP.NET events, use the following command,</span></span>  
  
```console
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a><span data-ttu-id="056a8-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="056a8-125">See also</span></span>

- [<span data-ttu-id="056a8-126">Usando a Instrumentação de Gerenciamento do Windows para diagnóstico</span><span class="sxs-lookup"><span data-stu-id="056a8-126">Using Windows Management Instrumentation for Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)
