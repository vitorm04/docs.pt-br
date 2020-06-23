---
title: Configurações recomendadas para registro de rastreamento e mensagens
description: Saiba mais sobre as configurações recomendadas de rastreamento e registro de mensagens para diferentes ambientes operacionais no WCF.
ms.date: 03/30/2017
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
ms.openlocfilehash: 71067a4d6f4cec65a148a8162c40e44d82b85784
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245317"
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a><span data-ttu-id="81df3-103">Configurações recomendadas para registro de rastreamento e mensagens</span><span class="sxs-lookup"><span data-stu-id="81df3-103">Recommended Settings for Tracing and Message Logging</span></span>
<span data-ttu-id="81df3-104">Este tópico descreve o rastreamento recomendado e as configurações de log de mensagens para diferentes ambientes operacionais.</span><span class="sxs-lookup"><span data-stu-id="81df3-104">This topic describes recommended tracing and message logging settings for different operating environments.</span></span>  
  
## <a name="recommended-settings-for-a-production-environment"></a><span data-ttu-id="81df3-105">Configurações recomendadas para um ambiente de produção</span><span class="sxs-lookup"><span data-stu-id="81df3-105">Recommended Settings for a Production Environment</span></span>  
 <span data-ttu-id="81df3-106">Para um ambiente de produção, se você estiver usando fontes de rastreamento do WCF, defina o `switchValue` como aviso.</span><span class="sxs-lookup"><span data-stu-id="81df3-106">For a production environment, if you are using WCF trace sources, set the `switchValue` to Warning.</span></span> <span data-ttu-id="81df3-107">Se você estiver usando a origem de rastreamento do WCF `System.ServiceModel` , defina o `switchValue` atributo como `Warning` e o `propagateActivity` atributo como `true` .</span><span class="sxs-lookup"><span data-stu-id="81df3-107">If you are using the WCF `System.ServiceModel` trace source, set the `switchValue` attribute to `Warning` and the `propagateActivity` attribute to `true`.</span></span> <span data-ttu-id="81df3-108">Se você estiver usando uma fonte de rastreamento definida pelo usuário, defina o `switchValue` atributo como `Warning, ActivityTracing` .</span><span class="sxs-lookup"><span data-stu-id="81df3-108">If you are using a user-defined trace source, set the `switchValue` attribute to `Warning, ActivityTracing`.</span></span> <span data-ttu-id="81df3-109">Isso pode ser feito manualmente usando a [ferramenta do editor de configuração (SvcConfigEditor.exe)](../../configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="81df3-109">This can be done manually using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../configuration-editor-tool-svcconfigeditor-exe.md).</span></span> <span data-ttu-id="81df3-110">Se você não antecipar um impacto no desempenho, poderá definir o `switchValue` atributo como `Information` em todos os casos mencionados anteriormente, o que gera uma quantidade muito grande de dados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="81df3-110">If you do not anticipate a hit in performance, you can set the `switchValue` attribute to `Information` in all the previously mentioned cases, which generates a fairly large amount of trace data.</span></span> <span data-ttu-id="81df3-111">O exemplo a seguir demonstra essas configurações recomendadas.</span><span class="sxs-lookup"><span data-stu-id="81df3-111">The following example demonstrates these recommended settings.</span></span>  
  
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
  
## <a name="recommended-settings-for-deployment-or-debugging"></a><span data-ttu-id="81df3-112">Configurações recomendadas para implantação ou depuração</span><span class="sxs-lookup"><span data-stu-id="81df3-112">Recommended Settings for Deployment or Debugging</span></span>  
 <span data-ttu-id="81df3-113">Para implantação ou ambiente de depuração, escolha `Information` ou `Verbose` , junto com `ActivityTracing` para uma fonte de rastreamento ou definida pelo usuário `System.ServiceModel` .</span><span class="sxs-lookup"><span data-stu-id="81df3-113">For deployment or debugging environment, choose `Information` or `Verbose`, along with `ActivityTracing` for either a user-defined or `System.ServiceModel` trace source.</span></span> <span data-ttu-id="81df3-114">Para aprimorar a depuração, você também deve adicionar uma fonte de rastreamento adicional ( `System.ServiceModel.MessageLogging` ) à configuração para habilitar o log de mensagens.</span><span class="sxs-lookup"><span data-stu-id="81df3-114">To enhance debugging, you should also add an additional trace source (`System.ServiceModel.MessageLogging`) to the configuration to enable message logging.</span></span> <span data-ttu-id="81df3-115">Observe que o `switchValue` atributo não tem impacto sobre essa origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="81df3-115">Notice that the `switchValue` attribute has no impact on this trace source.</span></span>  
  
 <span data-ttu-id="81df3-116">O exemplo a seguir demonstra as configurações recomendadas, usando um ouvinte compartilhado que utiliza o `XmlWriterTraceListener` .</span><span class="sxs-lookup"><span data-stu-id="81df3-116">The following example demonstrates the recommended settings, using a shared listener that utilizes the `XmlWriterTraceListener`.</span></span>  
  
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
  
## <a name="using-wmi-to-modify-settings"></a><span data-ttu-id="81df3-117">Usando o WMI para modificar as configurações</span><span class="sxs-lookup"><span data-stu-id="81df3-117">Using WMI to Modify Settings</span></span>  
 <span data-ttu-id="81df3-118">Você pode usar o WMI para alterar as definições de configuração em tempo de execução (habilitando o `wmiProviderEnabled` atributo na configuração, conforme demonstrado no exemplo de configuração anterior).</span><span class="sxs-lookup"><span data-stu-id="81df3-118">You can use WMI to change configuration settings at runtime (by enabling the `wmiProviderEnabled` attribute in the configuration, as demonstrated in the previously configuration example).</span></span> <span data-ttu-id="81df3-119">Por exemplo, você pode usar o WMI no CIM Studio para alterar os níveis de origem de rastreamento de aviso para informações em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="81df3-119">For example, you can use WMI within the CIM Studio to change the trace source levels from Warning to Information at runtime.</span></span> <span data-ttu-id="81df3-120">Você deve estar ciente de que o custo de desempenho da depuração dinâmica dessa maneira pode ser muito alto.</span><span class="sxs-lookup"><span data-stu-id="81df3-120">You should be aware that the performance cost of live debugging in this way can be very high.</span></span> <span data-ttu-id="81df3-121">Para obter mais informações sobre como usar o WMI, consulte o tópico [usando instrumentação de gerenciamento do Windows para diagnóstico](../wmi/index.md) .</span><span class="sxs-lookup"><span data-stu-id="81df3-121">For more information about using WMI, see the [Using Windows Management Instrumentation for Diagnostics](../wmi/index.md) topic.</span></span>  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a><span data-ttu-id="81df3-122">Habilitar eventos correlacionados no rastreamento de ASP.NET</span><span class="sxs-lookup"><span data-stu-id="81df3-122">Enable Correlated Events in ASP.NET Tracing</span></span>  
 <span data-ttu-id="81df3-123">Os eventos ASP.NET não definem a ID de correlação (ActivityId), a menos que o rastreamento de eventos do ASP.NET esteja ativado.</span><span class="sxs-lookup"><span data-stu-id="81df3-123">ASP.NET events do not set the correlation ID (ActivityID) unless ASP.NET event tracing is turned on.</span></span> <span data-ttu-id="81df3-124">Para ver os eventos correlacionados corretamente, você precisa ativar o rastreamento de eventos ASP.NET usando o comando a seguir no console de comando, que pode ser invocado acessando **Iniciar**, **executar** e digitar **cmd**,</span><span class="sxs-lookup"><span data-stu-id="81df3-124">To see correlated events properly, you have to turn on ASP.NET events tracing using the following command in the command console, which can be invoked by going to **Start**, **Run** and type **cmd**,</span></span>  
  
```console  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 <span data-ttu-id="81df3-125">Para desativar o rastreamento de eventos ASP.NET, use o comando a seguir,</span><span class="sxs-lookup"><span data-stu-id="81df3-125">To turn off tracing of ASP.NET events, use the following command,</span></span>  
  
```console
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a><span data-ttu-id="81df3-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="81df3-126">See also</span></span>

- [<span data-ttu-id="81df3-127">Usando Instrumentação de Gerenciamento do Windows para diagnóstico</span><span class="sxs-lookup"><span data-stu-id="81df3-127">Using Windows Management Instrumentation for Diagnostics</span></span>](../wmi/index.md)
