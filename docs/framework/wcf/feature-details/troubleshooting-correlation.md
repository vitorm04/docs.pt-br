---
title: Correlação de solução de problemas
ms.date: 03/30/2017
ms.assetid: 98003875-233d-4512-a688-4b2a1b0b5371
ms.openlocfilehash: be48a55a87d199829de4038e7e2a7642c102acf2
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976027"
---
# <a name="troubleshooting-correlation"></a><span data-ttu-id="a3bda-102">Correlação de solução de problemas</span><span class="sxs-lookup"><span data-stu-id="a3bda-102">Troubleshooting Correlation</span></span>
<span data-ttu-id="a3bda-103">A correlação é usada para relacionar mensagens do serviço de fluxo de trabalho entre si e com a instância de fluxo de trabalho correta, mas se não estiver configurada corretamente, as mensagens não serão recebidas e os aplicativos não funcionarão corretamente.</span><span class="sxs-lookup"><span data-stu-id="a3bda-103">Correlation is used to relate workflow service messages to each other and to the correct workflow instance, but if it is not configured correctly, messages will not be received and applications will not work correctly.</span></span> <span data-ttu-id="a3bda-104">Este tópico fornece uma visão geral de vários métodos para solucionar problemas de correlação e também lista alguns problemas comuns que podem ocorrer quando você usa a correlação.</span><span class="sxs-lookup"><span data-stu-id="a3bda-104">This topic provides an overview of several methods for troubleshooting correlation issues, and also lists some common issues that can occur when you use correlation.</span></span>

## <a name="handle-the-unknownmessagereceived-event"></a><span data-ttu-id="a3bda-105">Manipular o evento UnknownMessageReceived</span><span class="sxs-lookup"><span data-stu-id="a3bda-105">Handle the UnknownMessageReceived Event</span></span>
 <span data-ttu-id="a3bda-106">O evento <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> ocorre quando uma mensagem desconhecida é recebida por um serviço, incluindo mensagens que não podem ser correlacionadas a uma instância existente.</span><span class="sxs-lookup"><span data-stu-id="a3bda-106">The <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> event occurs when an unknown message is received by a service, including messages that cannot be correlated to an existing instance.</span></span> <span data-ttu-id="a3bda-107">Para serviços hospedados internamente, esse evento pode ser tratado no aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="a3bda-107">For self-hosted services, this event can be handled in the host application.</span></span>

```csharp
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)
{
    Console.WriteLine("Unknown Message Received:");
    Console.WriteLine(e.Message);
};
```

 <span data-ttu-id="a3bda-108">Para serviços hospedados na Web, esse evento pode ser tratado pela derivação de uma classe de <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> e substituição de <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span><span class="sxs-lookup"><span data-stu-id="a3bda-108">For Web-hosted services, this event can be handled by deriving a class from <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> and overriding <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span></span>

```csharp
class CustomFactory : WorkflowServiceHostFactory
{
    protected override WorkflowServiceHost CreateWorkflowServiceHost(Activity activity, Uri[] baseAddresses)
    {
        // Create the WorkflowServiceHost.
        WorkflowServiceHost host = new WorkflowServiceHost(activity, baseAddresses);

        // Handle the UnknownMessageReceived event.
        host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)
        {
            Console.WriteLine("Unknown Message Received:");
            Console.WriteLine(e.Message);
        };

        return host;
    }
}
```

 <span data-ttu-id="a3bda-109">Esse <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> personalizado pode ser especificado no arquivo de `svc` para o serviço.</span><span class="sxs-lookup"><span data-stu-id="a3bda-109">This custom <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> can then be specified in the `svc` file for the service.</span></span>

`<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>`

 <span data-ttu-id="a3bda-110">Quando esse manipulador é invocado, a mensagem pode ser recuperada usando a propriedade <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> do <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>e será semelhante à mensagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="a3bda-110">When this handler is invoked, the message can be retrieved by using the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> property of the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>, and will resemble the following message.</span></span>

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header>
    <To s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://localhost:8080/OrderService</To>
    <Action s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://tempuri.org/IService/AddItem</Action>
  </s:Header>
  <s:Body>
    <AddItem xmlns="http://tempuri.org/">
      <Item>Books</Item>
    </AddItem>
  </s:Body>
</s:Envelope>
```

 <span data-ttu-id="a3bda-111">Inspecionar mensagens expedidas para o manipulador de <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> pode fornecer pistas sobre o motivo da mensagem não estar correlacionada a uma instância do serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a3bda-111">Inspecting messages dispatched to the <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> handler may provide clues about why the message did not correlate to an instance of the workflow service.</span></span>

## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a><span data-ttu-id="a3bda-112">Use o rastreamento para monitorar o progresso do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="a3bda-112">Use Tracking to Monitor the Progress of the Workflow</span></span>
 <span data-ttu-id="a3bda-113">O rastreamento fornece uma maneira de monitorar o progresso de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a3bda-113">Tracking provides a way to monitor the progress of a workflow.</span></span> <span data-ttu-id="a3bda-114">Por padrão, os registros de rastreamento são emitidos para eventos do ciclo de vida do fluxo de trabalho, eventos do ciclo de vida da atividade, propagação de falha e continuação do indicador.</span><span class="sxs-lookup"><span data-stu-id="a3bda-114">By default, tracking records are emitted for workflow life-cycle events, activity life-cycle events, fault propagation, and bookmark resumption.</span></span> <span data-ttu-id="a3bda-115">Além disso, os registros de controle personalizados podem ser emitidos por atividades personalizadas.</span><span class="sxs-lookup"><span data-stu-id="a3bda-115">Additionally, custom tracking records can be emitted by custom activities.</span></span> <span data-ttu-id="a3bda-116">Ao solucionar problemas de correlação, os registros de rastreamento de atividade, os registros de continuação de indicador e os registros de propagação de falha são os mais úteis.</span><span class="sxs-lookup"><span data-stu-id="a3bda-116">When troubleshooting correlation, the activity tracking records, the bookmark resumption records, and the fault propagation records are the most useful.</span></span> <span data-ttu-id="a3bda-117">Os registros de rastreamento de atividade podem ser usados para determinar o progresso atual do fluxo de trabalho e podem ajudar a identificar qual atividade de mensagens está aguardando mensagens no momento.</span><span class="sxs-lookup"><span data-stu-id="a3bda-117">The activity tracking records can be used to determine the current progress of the workflow and can help identify which messaging activity is currently waiting for messages.</span></span> <span data-ttu-id="a3bda-118">Os registros de continuação de indicador são úteis porque indicam que uma mensagem foi recebida pelo fluxo de trabalho e os registros de propagação de falha fornecem um registro de quaisquer falhas no fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a3bda-118">Bookmark resumption records are useful because they indicate that a message was received by the workflow, and fault propagation records provide a record of any faults in the workflow.</span></span> <span data-ttu-id="a3bda-119">Para habilitar o acompanhamento, especifique as <xref:System.Activities.Tracking.TrackingParticipant> desejadas no <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> do <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a3bda-119">To enable tracking, specify the desired <xref:System.Activities.Tracking.TrackingParticipant> in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> of the <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="a3bda-120">No exemplo a seguir, a `ConsoleTrackingParticipant` (do exemplo de [rastreamento personalizado](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) ) é configurada usando o perfil de rastreamento padrão.</span><span class="sxs-lookup"><span data-stu-id="a3bda-120">In the following example, the `ConsoleTrackingParticipant` (from the [Custom Tracking](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) sample) is configured by using the default tracking profile.</span></span>

```csharp
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());
```

 <span data-ttu-id="a3bda-121">Um participante de rastreamento como o ConsoleTrackingParticipant é útil para serviços de fluxo de trabalho autohospedados que têm uma janela de console.</span><span class="sxs-lookup"><span data-stu-id="a3bda-121">A tracking participant such as the ConsoleTrackingParticipant is useful for self-hosted workflow services that have a console window.</span></span> <span data-ttu-id="a3bda-122">Para um serviço hospedado na Web, um participante de rastreamento que registra as informações de rastreamento em um repositório durável deve ser usado, como o <xref:System.Activities.Tracking.EtwTrackingParticipant>interno, ou um participante de rastreamento personalizado que registra as informações em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="a3bda-122">For a Web-hosted service, a tracking participant that logs the tracking information to a durable store should be used, such as the built-in <xref:System.Activities.Tracking.EtwTrackingParticipant>, or a custom tracking participant that logs the information to a file.</span></span>

 <span data-ttu-id="a3bda-123">Para obter mais informações sobre como controlar e configurar o acompanhamento de um serviço de fluxo de trabalho hospedado na Web, consulte rastreamento [e acompanhamento de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [Configurando o acompanhamento de um fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)e o exemplo de [acompanhamento &#91;de exemplos&#93; do WF](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md)</span><span class="sxs-lookup"><span data-stu-id="a3bda-123">For more information about tracking and configuring tracking for a Web-hosted workflow service, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md), and the [Tracking &#91;WF Samples&#93;](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) samples.</span></span>

## <a name="use-wcf-tracing"></a><span data-ttu-id="a3bda-124">Usar o rastreamento do WCF</span><span class="sxs-lookup"><span data-stu-id="a3bda-124">Use WCF Tracing</span></span>
 <span data-ttu-id="a3bda-125">O rastreamento do WCF fornece rastreamento do fluxo de mensagens de e para um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a3bda-125">WCF tracing provides tracing of the flow of messages to and from a workflow service.</span></span> <span data-ttu-id="a3bda-126">Essas informações de rastreamento são úteis ao solucionar problemas de correlação, especialmente para correlação baseada em conteúdo.</span><span class="sxs-lookup"><span data-stu-id="a3bda-126">This tracing information is useful when troubleshooting correlation issues, especially for content-based correlation.</span></span> <span data-ttu-id="a3bda-127">Para habilitar o rastreamento, especifique os ouvintes de rastreamento desejados na seção `system.diagnostics` do arquivo `web.config` se o serviço de fluxo de trabalho for hospedado na Web ou o arquivo de `app.config` se o serviço de fluxo de trabalho for auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="a3bda-127">To enable tracing, specify the desired trace listeners in the `system.diagnostics` section of the `web.config` file if the workflow service is Web-hosted, or the `app.config` file if the workflow service is self-hosted.</span></span> <span data-ttu-id="a3bda-128">Para incluir o conteúdo das mensagens no arquivo de rastreamento, especifique `true` para `logEntireMessage` no elemento `messageLogging` na seção `diagnostics` de `system.serviceModel`.</span><span class="sxs-lookup"><span data-stu-id="a3bda-128">To include the contents of the messages in the trace file, specify `true` for `logEntireMessage` in the `messageLogging` element in the `diagnostics` section of `system.serviceModel`.</span></span> <span data-ttu-id="a3bda-129">No exemplo a seguir, as informações de rastreamento, incluindo o conteúdo das mensagens, estão configuradas para serem gravadas em um arquivo chamado `service.svclog`.</span><span class="sxs-lookup"><span data-stu-id="a3bda-129">In the following example, tracing information, including the content of the messages, is configured to be written to a file that is named `service.svclog`.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.diagnostics>
    <sources>
      <source name="System.ServiceModel" switchValue="Information" propagateActivity="true">
        <listeners>
          <add name="corr"/>
        </listeners>
      </source>
      <source name="System.ServiceModel.MessageLogging">
        <listeners>
          <add name="corr"/>
        </listeners>
      </source>
    </sources>

    <sharedListeners>
      <add name="corr" type="System.Diagnostics.XmlWriterTraceListener" initializeData="c:\logs\service.svclog">
      </add>
    </sharedListeners>
  </system.diagnostics>

  <system.serviceModel>
    <diagnostics>
      <messageLogging logEntireMessage="true" logMalformedMessages="false"
         logMessagesAtServiceLevel="false" logMessagesAtTransportLevel="true" maxSizeOfMessageToLog="2147483647">
      </messageLogging>
    </diagnostics>
  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="a3bda-130">Para exibir as informações de rastreamento contidas no `service.svclog`, a [ferramenta do Visualizador de rastreamento de serviço (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) é usada.</span><span class="sxs-lookup"><span data-stu-id="a3bda-130">To view the trace information that is contained in `service.svclog`, the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) is used.</span></span> <span data-ttu-id="a3bda-131">Isso é especialmente útil ao solucionar problemas de correlação baseada em conteúdo, pois você pode exibir o conteúdo da mensagem e ver exatamente o que está sendo passado e se ele corresponde ao <xref:System.ServiceModel.CorrelationQuery> para a correlação baseada em conteúdo.</span><span class="sxs-lookup"><span data-stu-id="a3bda-131">This is especially useful when troubleshooting content-based correlation issues because you can view the message contents and see exactly what is being passed, and whether it matches the <xref:System.ServiceModel.CorrelationQuery> for the content-based correlation.</span></span> <span data-ttu-id="a3bda-132">Para obter mais informações sobre o rastreamento do WCF, consulte [ferramenta do Visualizador de rastreamento de serviço (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Configurando o rastreamento](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)e [usando o rastreamento para solucionar problemas de seu aplicativo](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span><span class="sxs-lookup"><span data-stu-id="a3bda-132">For more information about WCF tracing, see [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), and [Using Tracing to Troubleshoot Your Application](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>

## <a name="common-context-exchange-correlation-issues"></a><span data-ttu-id="a3bda-133">Problemas comuns de correlação do Exchange de contexto</span><span class="sxs-lookup"><span data-stu-id="a3bda-133">Common Context Exchange Correlation Issues</span></span>
 <span data-ttu-id="a3bda-134">Determinados tipos de correlação exigem que um tipo específico de associação seja usado para que a correlação funcione corretamente.</span><span class="sxs-lookup"><span data-stu-id="a3bda-134">Certain types of correlation require that a specific type of binding is used for the correlation to work correctly.</span></span> <span data-ttu-id="a3bda-135">Os exemplos incluem a correlação de solicitação-resposta, que requer uma associação bidirecional, como <xref:System.ServiceModel.BasicHttpBinding>e correlação do Exchange de contexto, que requer uma associação baseada em contexto, como <xref:System.ServiceModel.BasicHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="a3bda-135">Examples include request-reply correlation, which requires a two-way binding such as <xref:System.ServiceModel.BasicHttpBinding>, and context exchange correlation, which requires a context-based binding such as <xref:System.ServiceModel.BasicHttpContextBinding>.</span></span> <span data-ttu-id="a3bda-136">A maioria das associações dá suporte a operações bidirecionais, portanto, isso não é um problema comum para a correlação de solicitação-resposta, mas há apenas algumas associações baseadas em contexto, incluindo <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>e <xref:System.ServiceModel.NetTcpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="a3bda-136">Most bindings support two-way operations so this is not a common issue for request-reply correlation, but there are only a handful of context-based bindings including <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, and <xref:System.ServiceModel.NetTcpContextBinding>.</span></span> <span data-ttu-id="a3bda-137">Se uma dessas associações não for usada, a chamada inicial para um serviço de fluxo de trabalho terá êxito, mas as chamadas subsequentes falharão com as <xref:System.ServiceModel.FaultException>a seguir.</span><span class="sxs-lookup"><span data-stu-id="a3bda-137">If one of these bindings is not used, the initial call to a workflow service will succeed, but subsequent calls will fail with the following <xref:System.ServiceModel.FaultException>.</span></span>

```output
There is no context attached to the incoming message for the service
and the current operation is not marked with "CanCreateInstance = true".
In order to communicate with this service check whether the incoming binding
supports the context protocol and has a valid context initialized.
```

 <span data-ttu-id="a3bda-138">As informações de contexto usadas para correlação de contexto podem ser retornadas pelo <xref:System.ServiceModel.Activities.SendReply> para a atividade <xref:System.ServiceModel.Activities.Receive> que inicializa a correlação de contexto ao usar uma operação bidirecional, ou pode ser especificada pelo chamador se a operação for unidirecional.</span><span class="sxs-lookup"><span data-stu-id="a3bda-138">The context information that is used for context correlation can be returned by the <xref:System.ServiceModel.Activities.SendReply> to the <xref:System.ServiceModel.Activities.Receive> activity that initializes the context correlation when using a two-way operation, or it can be specified by the caller if the operation is one-way.</span></span> <span data-ttu-id="a3bda-139">Se o contexto não for enviado pelo chamador ou retornado pelo serviço de fluxo de trabalho, o mesmo <xref:System.ServiceModel.FaultException> descrito anteriormente será retornado quando uma operação subsequente for invocada.</span><span class="sxs-lookup"><span data-stu-id="a3bda-139">If the context is not sent by the caller or returned by the workflow service, then the same <xref:System.ServiceModel.FaultException> described previously will be returned when a subsequent operation is invoked.</span></span>

## <a name="common-request-reply-correlation-issues"></a><span data-ttu-id="a3bda-140">Problemas comuns de correlação de solicitação-resposta</span><span class="sxs-lookup"><span data-stu-id="a3bda-140">Common Request-Reply Correlation Issues</span></span>
 <span data-ttu-id="a3bda-141">A correlação de solicitação-resposta é usada com um <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> par implementar uma operação bidirecional em um serviço de fluxo de trabalho e com um <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> par que invoca uma operação bidirecional em outro serviço Web.</span><span class="sxs-lookup"><span data-stu-id="a3bda-141">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="a3bda-142">Ao invocar uma operação bidirecional em um serviço WCF, o serviço pode ser um serviço WCF baseado em código imperativo tradicional ou pode ser um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a3bda-142">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based WCF service or it can be a workflow service.</span></span> <span data-ttu-id="a3bda-143">Para usar a correlação de solicitação-resposta, uma associação bidirecional deve ser usada, como <xref:System.ServiceModel.BasicHttpBinding>, e as operações devem ser bidirecionais.</span><span class="sxs-lookup"><span data-stu-id="a3bda-143">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>, and the operations must be two-way.</span></span>

 <span data-ttu-id="a3bda-144">Se o serviço de fluxo de trabalho tiver operações bidirecionais em paralelo ou sobrepondo <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> ou <xref:System.ServiceModel.Activities.Send>/pares de <xref:System.ServiceModel.Activities.ReceiveReply>, o gerenciamento de identificador de correlação implícito fornecido pelo <xref:System.ServiceModel.Activities.WorkflowServiceHost> pode não ser suficiente, especialmente em cenários de alto estresse, e as mensagens podem não ser roteadas corretamente.</span><span class="sxs-lookup"><span data-stu-id="a3bda-144">If the workflow service has two-way operations in parallel, or overlapping <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> or <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pairs, then the implicit correlation handle management provided by <xref:System.ServiceModel.Activities.WorkflowServiceHost> may not be sufficient, especially in high-stress scenarios, and messages may not be correctly routed.</span></span> <span data-ttu-id="a3bda-145">Para evitar que esse problema ocorra, é recomendável que você sempre especifique explicitamente um <xref:System.ServiceModel.Activities.CorrelationHandle> ao usar a correlação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="a3bda-145">To prevent this issue from occurring, we recommend that you always explicitly specify a <xref:System.ServiceModel.Activities.CorrelationHandle> when using request-reply correlation.</span></span> <span data-ttu-id="a3bda-146">Ao usar os modelos **SendAndReceiveReply** e **ReceiveAndSendReply** da seção mensagens da caixa de **ferramentas** no designer de fluxo de trabalho, um <xref:System.ServiceModel.Activities.CorrelationHandle> é explicitamente configurado por padrão.</span><span class="sxs-lookup"><span data-stu-id="a3bda-146">When using the **SendAndReceiveReply** and **ReceiveAndSendReply** templates from the Messaging section of the **Toolbox** in the workflow designer, a <xref:System.ServiceModel.Activities.CorrelationHandle> is explicitly configured by default.</span></span> <span data-ttu-id="a3bda-147">Ao criar um fluxo de trabalho usando código, o <xref:System.ServiceModel.Activities.CorrelationHandle> é especificado no <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> da primeira atividade no par.</span><span class="sxs-lookup"><span data-stu-id="a3bda-147">When building a workflow by using code, the <xref:System.ServiceModel.Activities.CorrelationHandle> is specified in the <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> of the first activity in the pair.</span></span> <span data-ttu-id="a3bda-148">No exemplo a seguir, uma atividade <xref:System.ServiceModel.Activities.Receive> é configurada com um <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> explícito especificado no <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span><span class="sxs-lookup"><span data-stu-id="a3bda-148">In the following example, a <xref:System.ServiceModel.Activities.Receive> activity is configured with an explicit <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> specified in the <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span></span>

```csharp
Variable<CorrelationHandle> RRHandle = new Variable<CorrelationHandle>();

Receive StartOrder = new Receive
{
    CanCreateInstance = true,
    ServiceContractName = OrderContractName,
    OperationName = "StartOrder",
    CorrelationInitializers =
    {
        new RequestReplyCorrelationInitializer
        {
            CorrelationHandle = RRHandle
        }
    }
};

SendReply ReplyToStartOrder = new SendReply
{
    Request = StartOrder,
    Content = ... // Contains the return value, if any.
};

// Construct a workflow using StartOrder and ReplyToStartOrder.
```

 <span data-ttu-id="a3bda-149">A persistência não é permitida entre um par <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> ou um par <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply>.</span><span class="sxs-lookup"><span data-stu-id="a3bda-149">Persistence is not permitted between a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair or a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair.</span></span> <span data-ttu-id="a3bda-150">Uma zona de não persistência é criada e dura até que ambas as atividades sejam concluídas.</span><span class="sxs-lookup"><span data-stu-id="a3bda-150">A no-persist zone is created that lasts until both activities have completed.</span></span> <span data-ttu-id="a3bda-151">Se uma atividade, como uma atividade de atraso, estiver nessa zona de não persistência e fizer com que o fluxo de trabalho se torne ocioso, o fluxo de trabalho não persistirá mesmo se ele estiver configurado para persistir os fluxos de trabalho quando eles ficarem ociosos.</span><span class="sxs-lookup"><span data-stu-id="a3bda-151">If an activity, such as a delay activity, is in this no-persist zone and causes the workflow to become idle, the workflow will not persist even if it the host is configured to persist workflows when they become idle.</span></span> <span data-ttu-id="a3bda-152">Se uma atividade, como uma atividade Persist, tentar persistir explicitamente na zona no-Persist, uma exceção fatal será lançada, o fluxo de trabalho abortará e uma <xref:System.ServiceModel.FaultException> será retornada ao chamador.</span><span class="sxs-lookup"><span data-stu-id="a3bda-152">If an activity, such as a persist activity, attempts to explicitly persist in the no-persist zone, a fatal exception is thrown, the workflow aborts, and a <xref:System.ServiceModel.FaultException> is returned to the caller.</span></span> <span data-ttu-id="a3bda-153">A mensagem de exceção fatal é "System. InvalidOperationException: as atividades de persistência não podem estar contidas em blocos de persistência.".</span><span class="sxs-lookup"><span data-stu-id="a3bda-153">The fatal exception message is "System.InvalidOperationException: Persist activities cannot be contained within no persistence blocks.".</span></span> <span data-ttu-id="a3bda-154">Essa exceção não é retornada para o chamador, mas pode ser observada se o controle estiver habilitado.</span><span class="sxs-lookup"><span data-stu-id="a3bda-154">This exception is not returned to the caller but can be observed if tracking is enabled.</span></span> <span data-ttu-id="a3bda-155">A mensagem para a <xref:System.ServiceModel.FaultException> retornada ao chamador é "a operação não pôde ser executada porque WorkflowInstance ' 5836145b-7da2-49d0-A052-a49162adeab6 ' foi concluída".</span><span class="sxs-lookup"><span data-stu-id="a3bda-155">The message for the <xref:System.ServiceModel.FaultException> returned to the caller is "The operation could not be performed because WorkflowInstance '5836145b-7da2-49d0-a052-a49162adeab6' has completed".</span></span>

 <span data-ttu-id="a3bda-156">Para obter mais informações sobre a correlação de solicitação-resposta, consulte [solicitação-resposta](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).</span><span class="sxs-lookup"><span data-stu-id="a3bda-156">For more information about request-reply correlation, see [Request-Reply](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).</span></span>

## <a name="common-content-correlation-issues"></a><span data-ttu-id="a3bda-157">Problemas comuns de correlação de conteúdo</span><span class="sxs-lookup"><span data-stu-id="a3bda-157">Common Content Correlation Issues</span></span>
 <span data-ttu-id="a3bda-158">A correlação baseada em conteúdo é usada quando um serviço de fluxo de trabalho recebe várias mensagens e um dado nas mensagens trocadas identifica a instância desejada.</span><span class="sxs-lookup"><span data-stu-id="a3bda-158">Content-based correlation is used when a workflow service receives multiple messages and a piece of data in the exchanged messages identifies the desired instance.</span></span> <span data-ttu-id="a3bda-159">A correlação baseada em conteúdo usa esses dados na mensagem, como um número de cliente ou ID do pedido, para rotear mensagens para a instância de fluxo de trabalho correta.</span><span class="sxs-lookup"><span data-stu-id="a3bda-159">Content-based correlation uses this data in the message, such as a customer number or order ID, to route messages to the correct workflow instance.</span></span> <span data-ttu-id="a3bda-160">Esta seção descreve vários problemas comuns que podem ocorrer ao usar a correlação baseada em conteúdo.</span><span class="sxs-lookup"><span data-stu-id="a3bda-160">This section describes several common issues that may occur when using content-based correlation.</span></span>

### <a name="ensure-the-identifying-data-is-unique"></a><span data-ttu-id="a3bda-161">Verifique se os dados de identificação são exclusivos</span><span class="sxs-lookup"><span data-stu-id="a3bda-161">Ensure the Identifying Data Is Unique</span></span>
 <span data-ttu-id="a3bda-162">Os dados usados para identificar a instância são codificados em hash em uma chave de correlação.</span><span class="sxs-lookup"><span data-stu-id="a3bda-162">The data that is used to identify the instance is hashed into a correlation key.</span></span> <span data-ttu-id="a3bda-163">Deve-se ter cuidado para garantir que os dados usados para correlação sejam exclusivos ou outras colisões na chave com hash possam ocorrer e fazer com que as mensagens sejam roteadas erroneamente.</span><span class="sxs-lookup"><span data-stu-id="a3bda-163">Care must be taken to guarantee that the data that is used for correlation is unique or else collisions in the hashed key might occur and cause messages to be misrouted.</span></span> <span data-ttu-id="a3bda-164">Por exemplo, uma correlação baseada apenas em um nome de cliente pode causar uma colisão porque pode haver vários clientes que têm o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="a3bda-164">For example, a correlation based only on a customer name may cause a collision because there may be multiple customers who have the same name.</span></span> <span data-ttu-id="a3bda-165">Os dois-pontos (:) Não deve ser usado como parte dos dados usados para correlacionar a mensagem porque ela já está sendo usada para delimitar a chave e o valor da consulta de mensagem para formar a cadeia de caracteres que é subsequentemente com hash.</span><span class="sxs-lookup"><span data-stu-id="a3bda-165">The colon (:) should not be used as part of the data that is used to correlate the message because it is already used to delimit the message query’s key and value to form the string that is subsequently hashed.</span></span> <span data-ttu-id="a3bda-166">Se a persistência estiver sendo usada, certifique-se de que os dados de identificação atuais não foram usados por uma instância persistente anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a3bda-166">If persistence is being used, make sure that the current identifying data has not been used by a previously persisted instance.</span></span> <span data-ttu-id="a3bda-167">Desabilitar temporariamente a persistência pode ajudar a identificar esse problema.</span><span class="sxs-lookup"><span data-stu-id="a3bda-167">Temporarily disabling persistence can help identify this issue.</span></span> <span data-ttu-id="a3bda-168">O rastreamento do WCF pode ser usado para exibir a chave de correlação calculada e é útil para depurar esse tipo de problema.</span><span class="sxs-lookup"><span data-stu-id="a3bda-168">WCF tracing can be used to view the calculated correlation key and is useful for debugging this kind of issue.</span></span>

### <a name="race-conditions"></a><span data-ttu-id="a3bda-169">Condições de corrida</span><span class="sxs-lookup"><span data-stu-id="a3bda-169">Race Conditions</span></span>
 <span data-ttu-id="a3bda-170">Há um pequeno intervalo de tempo entre o serviço que recebe uma mensagem e a correlação realmente inicializada, durante a qual as mensagens de acompanhamento serão ignoradas.</span><span class="sxs-lookup"><span data-stu-id="a3bda-170">There is a small gap in time between the service receiving a message and the correlation actually being initialized, during which follow-up messages will be ignored.</span></span> <span data-ttu-id="a3bda-171">Se um serviço de fluxo de trabalho inicializar a correlação baseada em conteúdo usando dados passados do cliente em uma operação unidirecional e o chamador enviar mensagens de acompanhamento imediatos, essas mensagens serão ignoradas durante esse intervalo.</span><span class="sxs-lookup"><span data-stu-id="a3bda-171">If a workflow service initializes the content-based correlation by using data passed from the client over a one-way operation, and the caller sends immediate follow-up messages, these messages will be ignored during this interval.</span></span> <span data-ttu-id="a3bda-172">Isso pode ser evitado usando uma operação bidirecional para inicializar a correlação ou usando um <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="a3bda-172">This can be avoided by using a two-way operation to initialize the correlation, or by using a <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span>

### <a name="correlation-query-issues"></a><span data-ttu-id="a3bda-173">Problemas de consulta de correlação</span><span class="sxs-lookup"><span data-stu-id="a3bda-173">Correlation Query Issues</span></span>
 <span data-ttu-id="a3bda-174">As consultas de correlação são usadas para especificar quais dados em uma mensagem são usados para correlacionar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="a3bda-174">Correlation queries are used to specify what data in a message is used to correlate the message.</span></span> <span data-ttu-id="a3bda-175">Esses dados são especificados usando uma consulta XPath.</span><span class="sxs-lookup"><span data-stu-id="a3bda-175">This data is specified by using an XPath query.</span></span> <span data-ttu-id="a3bda-176">Se as mensagens para um serviço não estiverem sendo expedidas mesmo que tudo pareça correto, uma estratégia para solucionar problemas é especificar um valor literal que corresponda ao valor dos dados da mensagem em vez de uma consulta XPath.</span><span class="sxs-lookup"><span data-stu-id="a3bda-176">If messages to a service are not being dispatched even though everything appears to be correct, one strategy for troubleshooting is to specify a literal value that matches the value of the message data instead of an XPath query.</span></span> <span data-ttu-id="a3bda-177">Para especificar um valor literal, use a função `string`.</span><span class="sxs-lookup"><span data-stu-id="a3bda-177">To specify a literal value, use the `string` function.</span></span> <span data-ttu-id="a3bda-178">No exemplo a seguir, uma <xref:System.ServiceModel.MessageQuerySet> está configurada para usar um valor literal de `11445` para a `OrderId` e a consulta XPath é comentada.</span><span class="sxs-lookup"><span data-stu-id="a3bda-178">In the following example, a <xref:System.ServiceModel.MessageQuerySet> is configured to use a literal value of `11445` for the `OrderId` and the XPath query is commented out.</span></span>

```csharp
MessageQuerySet = new MessageQuerySet
{
    {
        "OrderId",
        //new XPathMessageQuery("sm:body()/tempuri:StartOrderResponse/tempuri:OrderId")
        new XPathMessageQuery("string('11445')")
    }
}
```

 <span data-ttu-id="a3bda-179">Se uma consulta XPath estiver configurada incorretamente, de modo que nenhum dado de correlação seja recuperado, uma falha será retornada com a seguinte mensagem: "uma consulta de correlação gerou um conjunto de resultados vazio.</span><span class="sxs-lookup"><span data-stu-id="a3bda-179">If an XPath query is configured incorrectly such that no correlation data is retrieved, a fault is returned with the following message: "A correlation query yielded an empty result set.</span></span> <span data-ttu-id="a3bda-180">Verifique se as consultas de correlação para o ponto de extremidade estão configuradas corretamente. "</span><span class="sxs-lookup"><span data-stu-id="a3bda-180">Please ensure correlation queries for the endpoint are correctly configured."</span></span> <span data-ttu-id="a3bda-181">Uma maneira rápida de solucionar isso é substituir a consulta XPath por um valor literal, conforme descrito na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="a3bda-181">One quick way to troubleshoot this is to replace the XPath query with a literal value as described in the previous section.</span></span> <span data-ttu-id="a3bda-182">Esse problema pode ocorrer se você usar o construtor de consultas XPath nas caixas de diálogo **Adicionar inicializadores de correlação** ou **definição de CorrelatesOn** e seu serviço de fluxo de trabalho usar contratos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="a3bda-182">This issue can occur if you use the XPath query builder in the **Add Correlation Initializers** or **CorrelatesOn Definition** dialog boxes and your workflow service uses message contracts.</span></span> <span data-ttu-id="a3bda-183">No exemplo a seguir, uma classe de contrato de mensagem é definida.</span><span class="sxs-lookup"><span data-stu-id="a3bda-183">In the following example, a message contract class is defined.</span></span>

```csharp
[MessageContract]
public class AddItemMessage
{
    [MessageHeader]
    public string CartId;

    [MessageBodyMember]
    public string Item;
}
```

 <span data-ttu-id="a3bda-184">Este contrato de mensagem é usado por uma atividade de <xref:System.ServiceModel.Activities.Receive> em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a3bda-184">This message contract is used by a <xref:System.ServiceModel.Activities.Receive> activity in a workflow.</span></span> <span data-ttu-id="a3bda-185">O `CartId` no cabeçalho da mensagem é usado para correlacionar a mensagem à instância correta.</span><span class="sxs-lookup"><span data-stu-id="a3bda-185">The `CartId` in the header of the message is used to correlate the message to the correct instance.</span></span> <span data-ttu-id="a3bda-186">Se a consulta XPath que recupera a `CartId` for criada usando as caixas de diálogo de correlação no designer de fluxo de trabalho, a seguinte consulta XPath incorreta será gerada.</span><span class="sxs-lookup"><span data-stu-id="a3bda-186">If the XPath query that retrieves the `CartId` is created using the correlation dialogs in the workflow designer, the following incorrect XPath query is generated.</span></span>

```
sm:body()/xg0:AddItemMessage/xg0:CartId
```

 <span data-ttu-id="a3bda-187">Essa consulta XPath estaria correta se a atividade de <xref:System.ServiceModel.Activities.Receive> usava parâmetros para os dados, mas como está usando um contrato de mensagem, ele está incorreto.</span><span class="sxs-lookup"><span data-stu-id="a3bda-187">This XPath query would be correct if the <xref:System.ServiceModel.Activities.Receive> activity used parameters for the data, but since it is using a message contract it is incorrect.</span></span> <span data-ttu-id="a3bda-188">A consulta XPath a seguir é a consulta XPath correta para recuperar o `CartId` do cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="a3bda-188">The following XPath query is the correct XPath query to retrieve the `CartId` from the header.</span></span>

```
sm:header()/tempuri:CartId
```

<span data-ttu-id="a3bda-189">Isso pode ser confirmado examinando o corpo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="a3bda-189">This can be confirmed by examining the body of the message.</span></span>

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header>
    <Action s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://tempuri.org/IService/AddItem</Action>
    <h:CartId xmlns:h="http://tempuri.org/">80c95b41-c98d-4660-a6c1-99412206e54c</h:CartId>
  </s:Header>
  <s:Body>
    <AddItemMessage xmlns="http://tempuri.org/">
      <Item>Books</Item>
    </AddItemMessage>
  </s:Body>
</s:Envelope>
```

<span data-ttu-id="a3bda-190">O exemplo a seguir mostra uma atividade de <xref:System.ServiceModel.Activities.Receive> configurada para uma operação `AddItem` que usa o contrato de mensagem anterior para receber dados.</span><span class="sxs-lookup"><span data-stu-id="a3bda-190">The following example shows a <xref:System.ServiceModel.Activities.Receive> activity configured for an `AddItem` operation that uses the previous message contract to receive data.</span></span> <span data-ttu-id="a3bda-191">A consulta XPath está configurada corretamente.</span><span class="sxs-lookup"><span data-stu-id="a3bda-191">The XPath query is correctly configured.</span></span>

```xaml
<Receive CorrelatesWith="[CCHandle] OperationName="AddItem" ServiceContractName="p:IService">
  <Receive.CorrelatesOn>
    <XPathMessageQuery x:Key="key1">
      <XPathMessageQuery.Namespaces>
        <ssx:XPathMessageContextMarkup>
          <x:String x:Key="xg0">http://schemas.datacontract.org/2004/07/MessageContractWFService</x:String>
        </ssx:XPathMessageContextMarkup>
      </XPathMessageQuery.Namespaces>sm:header()/tempuri:CartId</XPathMessageQuery>
  </Receive.CorrelatesOn>
  <ReceiveMessageContent DeclaredMessageType="m:AddItemMessage">
    <p1:OutArgument x:TypeArguments="m:AddItemMessage">[AddItemMessage]</p1:OutArgument>
  </ReceiveMessageContent>
</Receive>
```
