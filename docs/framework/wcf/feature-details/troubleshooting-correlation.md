---
title: Correlação de solução de problemas
ms.date: 03/30/2017
ms.assetid: 98003875-233d-4512-a688-4b2a1b0b5371
ms.openlocfilehash: fecfaf7374823bb19a4ad3d7f6cb2dbbdf139703
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48027917"
---
# <a name="troubleshooting-correlation"></a><span data-ttu-id="dae55-102">Correlação de solução de problemas</span><span class="sxs-lookup"><span data-stu-id="dae55-102">Troubleshooting Correlation</span></span>
<span data-ttu-id="dae55-103">Correlação é usada para relacionar mensagens do serviço de fluxo de trabalho entre si e com a instância de fluxo de trabalho correto, mas se ele não está configurado corretamente, as mensagens não serão recebidas e aplicativos não funcionarão corretamente.</span><span class="sxs-lookup"><span data-stu-id="dae55-103">Correlation is used to relate workflow service messages to each other and to the correct workflow instance, but if it is not configured correctly, messages will not be received and applications will not work correctly.</span></span> <span data-ttu-id="dae55-104">Este tópico fornece uma visão geral dos vários métodos para solução de problemas de correlação e também lista alguns problemas comuns que podem ocorrer quando você usa a correlação.</span><span class="sxs-lookup"><span data-stu-id="dae55-104">This topic provides an overview of several methods for troubleshooting correlation issues, and also lists some common issues that can occur when you use correlation.</span></span>

## <a name="handle-the-unknownmessagereceived-event"></a><span data-ttu-id="dae55-105">Manipular o evento UnknownMessageReceived</span><span class="sxs-lookup"><span data-stu-id="dae55-105">Handle the UnknownMessageReceived Event</span></span>
 <span data-ttu-id="dae55-106">O <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> evento ocorre quando uma mensagem desconhecida é recebida por um serviço, incluindo as mensagens que não podem ser correlacionadas a uma instância existente.</span><span class="sxs-lookup"><span data-stu-id="dae55-106">The <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> event occurs when an unknown message is received by a service, including messages that cannot be correlated to an existing instance.</span></span> <span data-ttu-id="dae55-107">Para serviços de hospedagem interna, esse evento pode ser tratado no aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="dae55-107">For self-hosted services, this event can be handled in the host application.</span></span>

```csharp
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)
{
    Console.WriteLine("Unknown Message Received:");
    Console.WriteLine(e.Message);
};
```

 <span data-ttu-id="dae55-108">Para serviços hospedados na Web, esse evento pode ser tratado por uma classe a partir <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> e substituindo <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span><span class="sxs-lookup"><span data-stu-id="dae55-108">For Web-hosted services, this event can be handled by deriving a class from <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> and overriding <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span></span>

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

 <span data-ttu-id="dae55-109">Esse custom <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> , em seguida, pode ser especificado no `svc` arquivo para o serviço.</span><span class="sxs-lookup"><span data-stu-id="dae55-109">This custom <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> can then be specified in the `svc` file for the service.</span></span>

```
<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>
```

 <span data-ttu-id="dae55-110">Quando esse manipulador é chamado, a mensagem pode ser recuperada usando o <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> propriedade do <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>e será semelhante a seguinte mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="dae55-110">When this handler is invoked, the message can be retrieved by using the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> property of the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>, and will resemble the following message.</span></span>

```Output
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

 <span data-ttu-id="dae55-111">Inspecionando mensagens enviadas para o <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> manipulador pode fornecer pistas sobre por que a mensagem se correlaciona a uma instância do serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="dae55-111">Inspecting messages dispatched to the <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> handler may provide clues about why the message did not correlate to an instance of the workflow service.</span></span>

## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a><span data-ttu-id="dae55-112">Usar o rastreamento para monitorar o progresso do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="dae55-112">Use Tracking to Monitor the Progress of the Workflow</span></span>
 <span data-ttu-id="dae55-113">Controle fornece uma maneira de monitorar o progresso de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="dae55-113">Tracking provides a way to monitor the progress of a workflow.</span></span> <span data-ttu-id="dae55-114">Por padrão, os registros de rastreamento são emitidos para eventos de ciclo de vida de fluxo de trabalho, eventos de ciclo de vida de atividades, propagação de falha e retomada do indicador.</span><span class="sxs-lookup"><span data-stu-id="dae55-114">By default, tracking records are emitted for workflow life-cycle events, activity life-cycle events, fault propagation, and bookmark resumption.</span></span> <span data-ttu-id="dae55-115">Além disso, os registros personalizados de rastreamento podem ser emitidos por atividades personalizadas.</span><span class="sxs-lookup"><span data-stu-id="dae55-115">Additionally, custom tracking records can be emitted by custom activities.</span></span> <span data-ttu-id="dae55-116">Ao solucionar problemas de correlação, a atividade de acompanhamento de registros, os registros de retomada do indicador e os registros de propagação de falha são mais úteis.</span><span class="sxs-lookup"><span data-stu-id="dae55-116">When troubleshooting correlation, the activity tracking records, the bookmark resumption records, and the fault propagation records are the most useful.</span></span> <span data-ttu-id="dae55-117">A atividade de registros de rastreamento pode ser usada para determinar o progresso atual do fluxo de trabalho e pode ajudar a identificar quais atividades de mensagem no momento está aguardando as mensagens.</span><span class="sxs-lookup"><span data-stu-id="dae55-117">The activity tracking records can be used to determine the current progress of the workflow and can help identify which messaging activity is currently waiting for messages.</span></span> <span data-ttu-id="dae55-118">Registros de retomada de indicador são úteis porque eles indicam que uma mensagem foi recebida pelo fluxo de trabalho e os registros de propagação de falha fornecem um registro de quaisquer falhas no fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="dae55-118">Bookmark resumption records are useful because they indicate that a message was received by the workflow, and fault propagation records provide a record of any faults in the workflow.</span></span> <span data-ttu-id="dae55-119">Para habilitar o acompanhamento, especifique os detalhes desejados <xref:System.Activities.Tracking.TrackingParticipant> no <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> da <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="dae55-119">To enable tracking, specify the desired <xref:System.Activities.Tracking.TrackingParticipant> in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> of the <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="dae55-120">No exemplo a seguir, o `ConsoleTrackingParticipant` (da [acompanhamento personalizado](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) exemplo) é configurada usando o perfil padrão de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="dae55-120">In the following example, the `ConsoleTrackingParticipant` (from the [Custom Tracking](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) sample) is configured by using the default tracking profile.</span></span>

```csharp
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());
```

 <span data-ttu-id="dae55-121">Um participante de rastreamento, como o ConsoleTrackingParticipant é útil para serviços de fluxo de trabalho auto-hospedado que têm uma janela do console.</span><span class="sxs-lookup"><span data-stu-id="dae55-121">A tracking participant such as the ConsoleTrackingParticipant is useful for self-hosted workflow services that have a console window.</span></span> <span data-ttu-id="dae55-122">Para um serviço hospedado na Web, um participante de rastreamento que registra as informações de rastreamento em um repositório durável deve ser usado, como a conta interna <xref:System.Activities.Tracking.EtwTrackingParticipant>, ou um participante de acompanhamento personalizado que registra as informações em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="dae55-122">For a Web-hosted service, a tracking participant that logs the tracking information to a durable store should be used, such as the built-in <xref:System.Activities.Tracking.EtwTrackingParticipant>, or a custom tracking participant that logs the information to a file.</span></span>

 <span data-ttu-id="dae55-123">Para obter mais informações sobre o acompanhamento e configurando o rastreamento para um serviço de fluxo de trabalho hospedados na Web, consulte [fluxo de trabalho, controle e rastreamento](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [Configurando o rastreamento para um fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)e o [ Controle &#91;exemplos do WF&#93; ](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) exemplos.</span><span class="sxs-lookup"><span data-stu-id="dae55-123">For more information about tracking and configuring tracking for a Web-hosted workflow service, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md), and the [Tracking &#91;WF Samples&#93;](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) samples.</span></span>

## <a name="use-wcf-tracing"></a><span data-ttu-id="dae55-124">Use o rastreamento do WCF</span><span class="sxs-lookup"><span data-stu-id="dae55-124">Use WCF Tracing</span></span>
 <span data-ttu-id="dae55-125">Rastreamento do WCF fornece o rastreamento de fluxo de mensagens para e de um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="dae55-125">WCF tracing provides tracing of the flow of messages to and from a workflow service.</span></span> <span data-ttu-id="dae55-126">Essas informações de rastreamento são útil ao solucionar problemas de correlação, especialmente para correlação conteudo base.</span><span class="sxs-lookup"><span data-stu-id="dae55-126">This tracing information is useful when troubleshooting correlation issues, especially for content-based correlation.</span></span> <span data-ttu-id="dae55-127">Para habilitar o rastreamento, especifique os ouvintes de rastreamento desejado na `system.diagnostics` seção o `web.config` se o serviço de fluxo de trabalho estiver hospedado na Web, de arquivos ou o `app.config` arquivo se o serviço de fluxo de trabalho é auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="dae55-127">To enable tracing, specify the desired trace listeners in the `system.diagnostics` section of the `web.config` file if the workflow service is Web-hosted, or the `app.config` file if the workflow service is self-hosted.</span></span> <span data-ttu-id="dae55-128">Para incluir o conteúdo das mensagens no arquivo de rastreamento, especifique `true` para `logEntireMessage` na `messageLogging` elemento no `diagnostics` seção `system.serviceModel`.</span><span class="sxs-lookup"><span data-stu-id="dae55-128">To include the contents of the messages in the trace file, specify `true` for `logEntireMessage` in the `messageLogging` element in the `diagnostics` section of `system.serviceModel`.</span></span> <span data-ttu-id="dae55-129">No exemplo a seguir, as informações de rastreamento, incluindo o conteúdo das mensagens, estão configuradas para ser gravado em um arquivo chamado `service.svclog`.</span><span class="sxs-lookup"><span data-stu-id="dae55-129">In the following example, tracing information, including the content of the messages, is configured to be written to a file that is named `service.svclog`.</span></span>

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

 <span data-ttu-id="dae55-130">Para exibir as informações de rastreamento que estão contidas em `service.svclog`, o [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) é usado.</span><span class="sxs-lookup"><span data-stu-id="dae55-130">To view the trace information that is contained in `service.svclog`, the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) is used.</span></span> <span data-ttu-id="dae55-131">Isso é especialmente útil ao solucionar problemas de correlação conteudo base problemas porque você pode exibir o conteúdo da mensagem e ver exatamente o que está sendo passado, e se ele corresponde ao <xref:System.ServiceModel.CorrelationQuery> para a correlação conteudo base.</span><span class="sxs-lookup"><span data-stu-id="dae55-131">This is especially useful when troubleshooting content-based correlation issues because you can view the message contents and see exactly what is being passed, and whether it matches the <xref:System.ServiceModel.CorrelationQuery> for the content-based correlation.</span></span> <span data-ttu-id="dae55-132">Para obter mais informações sobre rastreamento de WCF, consulte [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Configurando o rastreamento](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), e [usando o rastreamento para solucionar problemas de seu aplicativo](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span><span class="sxs-lookup"><span data-stu-id="dae55-132">For more information about WCF tracing, see [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), and [Using Tracing to Troubleshoot Your Application](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>

## <a name="common-context-exchange-correlation-issues"></a><span data-ttu-id="dae55-133">Problemas de correlação de troca de contexto comuns</span><span class="sxs-lookup"><span data-stu-id="dae55-133">Common Context Exchange Correlation Issues</span></span>
 <span data-ttu-id="dae55-134">Determinados tipos de correlação exigem que um tipo específico de associação é usado para a correlação funcione corretamente.</span><span class="sxs-lookup"><span data-stu-id="dae55-134">Certain types of correlation require that a specific type of binding is used for the correlation to work correctly.</span></span> <span data-ttu-id="dae55-135">Os exemplos incluem a correlação de solicitação-resposta, o que exige uma vinculação bidirecional, como <xref:System.ServiceModel.BasicHttpBinding>e correlação de intercâmbio de contexto, que exige uma com base no contexto de associação, como <xref:System.ServiceModel.BasicHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="dae55-135">Examples include request-reply correlation, which requires a two-way binding such as <xref:System.ServiceModel.BasicHttpBinding>, and context exchange correlation, which requires a context-based binding such as <xref:System.ServiceModel.BasicHttpContextBinding>.</span></span> <span data-ttu-id="dae55-136">A maioria das ligações dar suporte a operações bidirecionais para que isso não é um problema comum para a correlação de solicitação-resposta, mas há apenas um punhado de associações de contexto base incluindo <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, e <xref:System.ServiceModel.NetTcpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="dae55-136">Most bindings support two-way operations so this is not a common issue for request-reply correlation, but there are only a handful of context-based bindings including <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, and <xref:System.ServiceModel.NetTcpContextBinding>.</span></span> <span data-ttu-id="dae55-137">Se uma dessas associações não é usada, a chamada inicial para um serviço de fluxo de trabalho terá êxito, mas as chamadas subsequentes falharão com o seguinte <xref:System.ServiceModel.FaultException>.</span><span class="sxs-lookup"><span data-stu-id="dae55-137">If one of these bindings is not used, the initial call to a workflow service will succeed, but subsequent calls will fail with the following <xref:System.ServiceModel.FaultException>.</span></span>

```Output
There is no context attached to the incoming message for the service
and the current operation is not marked with "CanCreateInstance = true".
In order to communicate with this service check whether the incoming binding
supports the context protocol and has a valid context initialized.
```

 <span data-ttu-id="dae55-138">As informações de contexto que são usadas para correlação de contexto podem ser retornadas pela <xref:System.ServiceModel.Activities.SendReply> para o <xref:System.ServiceModel.Activities.Receive> atividade que inicializa a correlação de contexto quando usando uma operação bidirecional, ou ele pode ser especificado pelo chamador se a operação unidirecional.</span><span class="sxs-lookup"><span data-stu-id="dae55-138">The context information that is used for context correlation can be returned by the <xref:System.ServiceModel.Activities.SendReply> to the <xref:System.ServiceModel.Activities.Receive> activity that initializes the context correlation when using a two-way operation, or it can be specified by the caller if the operation is one-way.</span></span> <span data-ttu-id="dae55-139">Se o contexto não é enviado pelo chamador ou retornado pelo serviço de fluxo de trabalho, em seguida, o mesmo <xref:System.ServiceModel.FaultException> descritas anteriormente serão retornados quando uma operação subsequente é invocada.</span><span class="sxs-lookup"><span data-stu-id="dae55-139">If the context is not sent by the caller or returned by the workflow service, then the same <xref:System.ServiceModel.FaultException> described previously will be returned when a subsequent operation is invoked.</span></span>

## <a name="common-request-reply-correlation-issues"></a><span data-ttu-id="dae55-140">Problemas comuns de correlação de solicitação-resposta</span><span class="sxs-lookup"><span data-stu-id="dae55-140">Common Request-Reply Correlation Issues</span></span>
 <span data-ttu-id="dae55-141">Correlação de solicitação-resposta é usada com um <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> par para implementar uma operação bidirecional em um serviço de fluxo de trabalho e com um <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> par que chama uma operação bidirecional em outra Web serviço.</span><span class="sxs-lookup"><span data-stu-id="dae55-141">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="dae55-142">Ao invocar uma operação bidirecional em um serviço WCF, o serviço pode ser qualquer um tradicional imperativo serviço do WCF com base no código ou pode ser um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="dae55-142">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based WCF service or it can be a workflow service.</span></span> <span data-ttu-id="dae55-143">Para usar uma associação bidirecional forem usada, como de correlação de solicitação-resposta <xref:System.ServiceModel.BasicHttpBinding>, e as operações devem ser bidirecionais.</span><span class="sxs-lookup"><span data-stu-id="dae55-143">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>, and the operations must be two-way.</span></span>

 <span data-ttu-id="dae55-144">Se o serviço de fluxo de trabalho tiver bidirecionais operações em paralelo ou sobrepostos <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> ou <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pares e, em seguida, a correlação implícita lidar com gerenciamento fornecido pelo <xref:System.ServiceModel.Activities.WorkflowServiceHost>pode não ser suficiente, especialmente em cenários de alto desgaste, e as mensagens não podem ser roteadas corretamente.</span><span class="sxs-lookup"><span data-stu-id="dae55-144">If the workflow service has two-way operations in parallel, or overlapping <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> or <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pairs, then the implicit correlation handle management provided by <xref:System.ServiceModel.Activities.WorkflowServiceHost> may not be sufficient, especially in high-stress scenarios, and messages may not be correctly routed.</span></span> <span data-ttu-id="dae55-145">Para evitar que esse problema ocorra, é recomendável que você sempre especifique explicitamente um <xref:System.ServiceModel.Activities.CorrelationHandle> ao usar a correlação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="dae55-145">To prevent this issue from occurring, we recommend that you always explicitly specify a <xref:System.ServiceModel.Activities.CorrelationHandle> when using request-reply correlation.</span></span> <span data-ttu-id="dae55-146">Ao usar o **SendAndReceiveReply** e **ReceiveAndSendReply** modelos da seção de mensagens a **caixa de ferramentas** no designer de fluxo de trabalho, um <xref:System.ServiceModel.Activities.CorrelationHandle> é explicitamente configurado por padrão.</span><span class="sxs-lookup"><span data-stu-id="dae55-146">When using the **SendAndReceiveReply** and **ReceiveAndSendReply** templates from the Messaging section of the **Toolbox** in the workflow designer, a <xref:System.ServiceModel.Activities.CorrelationHandle> is explicitly configured by default.</span></span> <span data-ttu-id="dae55-147">Ao criar um fluxo de trabalho por meio de código, o <xref:System.ServiceModel.Activities.CorrelationHandle> é especificado no <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> da primeira atividade no par.</span><span class="sxs-lookup"><span data-stu-id="dae55-147">When building a workflow by using code, the <xref:System.ServiceModel.Activities.CorrelationHandle> is specified in the <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> of the first activity in the pair.</span></span> <span data-ttu-id="dae55-148">No exemplo a seguir, uma <xref:System.ServiceModel.Activities.Receive> atividade está configurada com uma explícita <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> especificado no <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span><span class="sxs-lookup"><span data-stu-id="dae55-148">In the following example, a <xref:System.ServiceModel.Activities.Receive> activity is configured with an explicit <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> specified in the <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span></span>

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

 <span data-ttu-id="dae55-149">Persistência não é permitida entre um <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> par ou uma <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> par.</span><span class="sxs-lookup"><span data-stu-id="dae55-149">Persistence is not permitted between a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair or a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair.</span></span> <span data-ttu-id="dae55-150">Uma zona sem persistir é criada que dura até que ambas as atividades sejam concluídas.</span><span class="sxs-lookup"><span data-stu-id="dae55-150">A no-persist zone is created that lasts until both activities have completed.</span></span> <span data-ttu-id="dae55-151">Se uma atividade, como uma atividade de atraso é nesta zona sem persistir e faz com que o fluxo de trabalho se torne ocioso, o fluxo de trabalho não persistirá mesmo que ele o host está configurado para persistir fluxos de trabalho quando eles se tornam ociosos.</span><span class="sxs-lookup"><span data-stu-id="dae55-151">If an activity, such as a delay activity, is in this no-persist zone and causes the workflow to become idle, the workflow will not persist even if it the host is configured to persist workflows when they become idle.</span></span> <span data-ttu-id="dae55-152">Se uma atividade, como uma atividade persist, tentar persistir explicitamente na zona sem persistir, uma exceção fatal é lançada, as anulações de fluxo de trabalho e um <xref:System.ServiceModel.FaultException> é retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="dae55-152">If an activity, such as a persist activity, attempts to explicitly persist in the no-persist zone, a fatal exception is thrown, the workflow aborts, and a <xref:System.ServiceModel.FaultException> is returned to the caller.</span></span> <span data-ttu-id="dae55-153">A mensagem de exceção fatal é "System. InvalidOperationException: Manter atividades não podem ser contidas dentro de blocos sem persistência.".</span><span class="sxs-lookup"><span data-stu-id="dae55-153">The fatal exception message is "System.InvalidOperationException: Persist activities cannot be contained within no persistence blocks.".</span></span> <span data-ttu-id="dae55-154">Essa exceção não é retornada ao chamador, mas pode ser observada se o rastreamento está habilitado.</span><span class="sxs-lookup"><span data-stu-id="dae55-154">This exception is not returned to the caller but can be observed if tracking is enabled.</span></span> <span data-ttu-id="dae55-155">A mensagem para o <xref:System.ServiceModel.FaultException> retornado ao chamador é "a operação pode não ser executada como WorkflowInstance '5836145b 7da2 - 49 d 0-a052-a49162adeab6' foi concluída".</span><span class="sxs-lookup"><span data-stu-id="dae55-155">The message for the <xref:System.ServiceModel.FaultException> returned to the caller is "The operation could not be performed because WorkflowInstance '5836145b-7da2-49d0-a052-a49162adeab6' has completed".</span></span>

 <span data-ttu-id="dae55-156">Para obter mais informações sobre a correlação de solicitação-resposta, consulte [solicitação-resposta](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).</span><span class="sxs-lookup"><span data-stu-id="dae55-156">For more information about request-reply correlation, see [Request-Reply](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).</span></span>

## <a name="common-content-correlation-issues"></a><span data-ttu-id="dae55-157">Problemas comuns de correlação de conteúdo</span><span class="sxs-lookup"><span data-stu-id="dae55-157">Common Content Correlation Issues</span></span>
 <span data-ttu-id="dae55-158">Correlação conteudo base é usada quando um serviço de fluxo de trabalho recebe várias mensagens e uma parte dos dados em que as mensagens trocadas identifica a instância desejada.</span><span class="sxs-lookup"><span data-stu-id="dae55-158">Content-based correlation is used when a workflow service receives multiple messages and a piece of data in the exchanged messages identifies the desired instance.</span></span> <span data-ttu-id="dae55-159">Correlação conteudo base que usa esses dados na mensagem, como um número ou a ordem de ID de cliente, para rotear mensagens para a instância de fluxo de trabalho correto.</span><span class="sxs-lookup"><span data-stu-id="dae55-159">Content-based correlation uses this data in the message, such as a customer number or order ID, to route messages to the correct workflow instance.</span></span> <span data-ttu-id="dae55-160">Esta seção descreve vários problemas comuns que podem ocorrer ao usar a correlação conteudo base.</span><span class="sxs-lookup"><span data-stu-id="dae55-160">This section describes several common issues that may occur when using content-based correlation.</span></span>

### <a name="ensure-the-identifying-data-is-unique"></a><span data-ttu-id="dae55-161">Verifique se que os dados de identificação são exclusivos</span><span class="sxs-lookup"><span data-stu-id="dae55-161">Ensure the Identifying Data Is Unique</span></span>
 <span data-ttu-id="dae55-162">Os dados que são usados para identificar a instância são transformados em uma chave de correlação.</span><span class="sxs-lookup"><span data-stu-id="dae55-162">The data that is used to identify the instance is hashed into a correlation key.</span></span> <span data-ttu-id="dae55-163">Deve-se ter cuidado para garantir que os dados que são usados para correlação são exclusivos ou então colisões na chave de hash podem ocorrer e causar mensagens acabe sendo enviado.</span><span class="sxs-lookup"><span data-stu-id="dae55-163">Care must be taken to guarantee that the data that is used for correlation is unique or else collisions in the hashed key might occur and cause messages to be misrouted.</span></span> <span data-ttu-id="dae55-164">Por exemplo, uma correlação com base somente em um nome de cliente pode causar uma colisão, porque pode haver vários clientes que têm o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="dae55-164">For example, a correlation based only on a customer name may cause a collision because there may be multiple customers who have the same name.</span></span> <span data-ttu-id="dae55-165">Os dois-pontos (:) não devem ser usado como parte dos dados que são usados para correlacionar a mensagem porque ele já é usado para delimitar a chave e o valor para formar a cadeia de caracteres de hash, posteriormente, a consulta de mensagem.</span><span class="sxs-lookup"><span data-stu-id="dae55-165">The colon (:) should not be used as part of the data that is used to correlate the message because it is already used to delimit the message query’s key and value to form the string that is subsequently hashed.</span></span> <span data-ttu-id="dae55-166">Se a persistência está sendo usada, certifique-se de que os dados que identificam atuais não foi usados por uma instância previamente persistida.</span><span class="sxs-lookup"><span data-stu-id="dae55-166">If persistence is being used, make sure that the current identifying data has not been used by a previously persisted instance.</span></span> <span data-ttu-id="dae55-167">Desabilitar temporariamente a persistência pode ajudar a identificar esse problema.</span><span class="sxs-lookup"><span data-stu-id="dae55-167">Temporarily disabling persistence can help identify this issue.</span></span> <span data-ttu-id="dae55-168">Rastreamento de WCF pode ser usado para exibir a chave de correlação calculada e é útil para depurar esse tipo de problema.</span><span class="sxs-lookup"><span data-stu-id="dae55-168">WCF tracing can be used to view the calculated correlation key and is useful for debugging this kind of issue.</span></span>

### <a name="race-conditions"></a><span data-ttu-id="dae55-169">Condições de corrida</span><span class="sxs-lookup"><span data-stu-id="dae55-169">Race Conditions</span></span>
 <span data-ttu-id="dae55-170">Há um pequeno espaço no tempo entre o serviço receber uma mensagem e a correlação, na verdade, que está sendo inicializado, durante o qual as mensagens de acompanhamento serão ignoradas.</span><span class="sxs-lookup"><span data-stu-id="dae55-170">There is a small gap in time between the service receiving a message and the correlation actually being initialized, during which follow-up messages will be ignored.</span></span> <span data-ttu-id="dae55-171">Se um serviço de fluxo de trabalho inicializa a correlação conteudo base usando os dados passados do cliente em uma operação unidirecional e o chamador envia mensagens de acompanhamento de imediatas, essas mensagens serão ignoradas durante esse intervalo.</span><span class="sxs-lookup"><span data-stu-id="dae55-171">If a workflow service initializes the content-based correlation by using data passed from the client over a one-way operation, and the caller sends immediate follow-up messages, these messages will be ignored during this interval.</span></span> <span data-ttu-id="dae55-172">Isso pode ser evitado por meio de uma operação bidirecional para inicializar a correlação, ou usando um <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="dae55-172">This can be avoided by using a two-way operation to initialize the correlation, or by using a <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span>

### <a name="correlation-query-issues"></a><span data-ttu-id="dae55-173">Problemas de correlação de consulta</span><span class="sxs-lookup"><span data-stu-id="dae55-173">Correlation Query Issues</span></span>
 <span data-ttu-id="dae55-174">Consultas de correlação são usadas para especificar quais dados em uma mensagem são usados para correlacionar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="dae55-174">Correlation queries are used to specify what data in a message is used to correlate the message.</span></span> <span data-ttu-id="dae55-175">Esses dados são especificados usando uma consulta XPath.</span><span class="sxs-lookup"><span data-stu-id="dae55-175">This data is specified by using an XPath query.</span></span> <span data-ttu-id="dae55-176">Se as mensagens para um serviço não estão sendo despachadas, mesmo que tudo parece estar correta, uma estratégia para solução de problemas é para especificar um valor literal que corresponde ao valor dos dados da mensagem, em vez de uma consulta XPath.</span><span class="sxs-lookup"><span data-stu-id="dae55-176">If messages to a service are not being dispatched even though everything appears to be correct, one strategy for troubleshooting is to specify a literal value that matches the value of the message data instead of an XPath query.</span></span> <span data-ttu-id="dae55-177">Para especificar um valor literal, use o `string` função.</span><span class="sxs-lookup"><span data-stu-id="dae55-177">To specify a literal value, use the `string` function.</span></span> <span data-ttu-id="dae55-178">No exemplo a seguir, uma <xref:System.ServiceModel.MessageQuerySet> está configurado para usar um valor literal `11445` para o `OrderId` e a consulta XPath é comentada.</span><span class="sxs-lookup"><span data-stu-id="dae55-178">In the following example, a <xref:System.ServiceModel.MessageQuerySet> is configured to use a literal value of `11445` for the `OrderId` and the XPath query is commented out.</span></span>

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

 <span data-ttu-id="dae55-179">Se uma consulta XPath está configurada incorretamente, de modo que nenhum dado de correlação é recuperado, uma falha será retornada com a seguinte mensagem: "uma consulta de correlação gerou um conjunto de resultados vazio.</span><span class="sxs-lookup"><span data-stu-id="dae55-179">If an XPath query is configured incorrectly such that no correlation data is retrieved, a fault is returned with the following message: "A correlation query yielded an empty result set.</span></span> <span data-ttu-id="dae55-180">Verifique se as consultas de correlação para o ponto de extremidade estão configuradas corretamente."</span><span class="sxs-lookup"><span data-stu-id="dae55-180">Please ensure correlation queries for the endpoint are correctly configured."</span></span> <span data-ttu-id="dae55-181">Uma maneira rápida de solucionar esse problema é substituir a consulta XPath com um valor literal, conforme descrito na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="dae55-181">One quick way to troubleshoot this is to replace the XPath query with a literal value as described in the previous section.</span></span> <span data-ttu-id="dae55-182">Esse problema pode ocorrer se você usar o construtor de consultas XPath na **adicionar inicializadores de correlação** ou **definição de CorrelatesOn** caixas de diálogo e seu serviço de fluxo de trabalho usa contratos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="dae55-182">This issue can occur if you use the XPath query builder in the **Add Correlation Initializers** or **CorrelatesOn Definition** dialog boxes and your workflow service uses message contracts.</span></span> <span data-ttu-id="dae55-183">No exemplo a seguir, uma classe de contrato de mensagem é definida.</span><span class="sxs-lookup"><span data-stu-id="dae55-183">In the following example, a message contract class is defined.</span></span>

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

 <span data-ttu-id="dae55-184">Este contrato de mensagem é usado por um <xref:System.ServiceModel.Activities.Receive> atividade em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="dae55-184">This message contract is used by a <xref:System.ServiceModel.Activities.Receive> activity in a workflow.</span></span> <span data-ttu-id="dae55-185">O `CartId` no cabeçalho da mensagem é usada para correlacionar a mensagem para a instância correta.</span><span class="sxs-lookup"><span data-stu-id="dae55-185">The `CartId` in the header of the message is used to correlate the message to the correct instance.</span></span> <span data-ttu-id="dae55-186">Se a consulta XPath que recupera o `CartId` é criado usando as caixas de diálogo correlação no designer de fluxo de trabalho, o XPath incorreto a seguir consulta é gerada.</span><span class="sxs-lookup"><span data-stu-id="dae55-186">If the XPath query that retrieves the `CartId` is created using the correlation dialogs in the workflow designer, the following incorrect XPath query is generated.</span></span>

```
sm:body()/xg0:AddItemMessage/xg0:CartId
```

 <span data-ttu-id="dae55-187">Essa consulta XPath estaria correta se o <xref:System.ServiceModel.Activities.Receive> atividade os parâmetros usados para os dados, mas uma vez que ele está usando um contrato de mensagem é incorreto.</span><span class="sxs-lookup"><span data-stu-id="dae55-187">This XPath query would be correct if the <xref:System.ServiceModel.Activities.Receive> activity used parameters for the data, but since it is using a message contract it is incorrect.</span></span> <span data-ttu-id="dae55-188">A seguinte consulta XPath é a consulta XPath correta para recuperar o `CartId` do cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="dae55-188">The following XPath query is the correct XPath query to retrieve the `CartId` from the header.</span></span>

```
sm:header()/tempuri:CartId
```

<span data-ttu-id="dae55-189">Isso pode ser confirmado ao examinar o corpo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="dae55-189">This can be confirmed by examining the body of the message.</span></span>

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

<span data-ttu-id="dae55-190">A exemplo a seguir mostra uma <xref:System.ServiceModel.Activities.Receive> atividade configurada para um `AddItem` operação que usa o contrato de mensagem anterior para receber dados.</span><span class="sxs-lookup"><span data-stu-id="dae55-190">The following example shows a <xref:System.ServiceModel.Activities.Receive> activity configured for an `AddItem` operation that uses the previous message contract to receive data.</span></span> <span data-ttu-id="dae55-191">A consulta XPath está configurada corretamente.</span><span class="sxs-lookup"><span data-stu-id="dae55-191">The XPath query is correctly configured.</span></span>

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
