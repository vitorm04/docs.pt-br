---
title: Correlação de solução de problemas
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98003875-233d-4512-a688-4b2a1b0b5371
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5bdf111e6802692aef893cf9dcae88f0f51aa467
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="troubleshooting-correlation"></a><span data-ttu-id="4dee0-102">Correlação de solução de problemas</span><span class="sxs-lookup"><span data-stu-id="4dee0-102">Troubleshooting Correlation</span></span>
<span data-ttu-id="4dee0-103">Correlação é usada para relacionar as mensagens do serviço de fluxo de trabalho entre si e com a instância de fluxo de trabalho correto, mas se ele não está configurado corretamente, as mensagens não serão recebidas e aplicativos não funcionarão corretamente.</span><span class="sxs-lookup"><span data-stu-id="4dee0-103">Correlation is used to relate workflow service messages to each other and to the correct workflow instance, but if it is not configured correctly, messages will not be received and applications will not work correctly.</span></span> <span data-ttu-id="4dee0-104">Este tópico fornece uma visão geral dos vários métodos para solução de problemas de correlação e também lista alguns problemas comuns que podem ocorrer quando você usar a correlação.</span><span class="sxs-lookup"><span data-stu-id="4dee0-104">This topic provides an overview of several methods for troubleshooting correlation issues, and also lists some common issues that can occur when you use correlation.</span></span>  
  
## <a name="handle-the-unknownmessagereceived-event"></a><span data-ttu-id="4dee0-105">Manipular o evento UnknownMessageReceived</span><span class="sxs-lookup"><span data-stu-id="4dee0-105">Handle the UnknownMessageReceived Event</span></span>  
 <span data-ttu-id="4dee0-106">O <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> evento ocorre quando uma mensagem desconhecida é recebida por um serviço, inclusive as mensagens que não podem ser correlacionadas a uma instância existente.</span><span class="sxs-lookup"><span data-stu-id="4dee0-106">The <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> event occurs when an unknown message is received by a service, including messages that cannot be correlated to an existing instance.</span></span> <span data-ttu-id="4dee0-107">Para serviços de hospedagem interna, este evento pode ser tratado no aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="4dee0-107">For self-hosted services, this event can be handled in the host application.</span></span>  
  
```csharp  
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)  
{  
    Console.WriteLine("Unknown Message Received:");  
    Console.WriteLine(e.Message);  
};  
```  
  
 <span data-ttu-id="4dee0-108">Para serviços hospedados na Web, esse evento pode ser tratado derivando uma classe de <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> e substituindo <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span><span class="sxs-lookup"><span data-stu-id="4dee0-108">For Web-hosted services, this event can be handled by deriving a class from <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> and overriding <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span></span>  
  
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
  
 <span data-ttu-id="4dee0-109">Este arquivo <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> , em seguida, pode ser especificado no `svc` arquivo para o serviço.</span><span class="sxs-lookup"><span data-stu-id="4dee0-109">This custom <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> can then be specified in the `svc` file for the service.</span></span>  
  
```  
<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>  
```  
  
 <span data-ttu-id="4dee0-110">Quando esse manipulador é chamado, a mensagem pode ser recuperada usando o <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> propriedade o <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>e será parecida com a seguinte mensagem.</span><span class="sxs-lookup"><span data-stu-id="4dee0-110">When this handler is invoked, the message can be retrieved by using the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> property of the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>, and will resemble the following message.</span></span>  
  
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
  
 <span data-ttu-id="4dee0-111">Inspecionar mensagens enviadas para o <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> manipulador possam fornecer pistas sobre por que a mensagem não correlacionar a uma instância do serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4dee0-111">Inspecting messages dispatched to the <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> handler may provide clues about why the message did not correlate to an instance of the workflow service.</span></span>  
  
## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a><span data-ttu-id="4dee0-112">Usar o rastreamento para monitorar o andamento do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="4dee0-112">Use Tracking to Monitor the Progress of the Workflow</span></span>  
 <span data-ttu-id="4dee0-113">Controle fornece uma maneira de monitorar o progresso de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4dee0-113">Tracking provides a way to monitor the progress of a workflow.</span></span> <span data-ttu-id="4dee0-114">Por padrão, os registros de rastreamento são emitidos para eventos de ciclo de vida do fluxo de trabalho, eventos de ciclo de vida da atividade, a propagação de falhas e retomada de indicador.</span><span class="sxs-lookup"><span data-stu-id="4dee0-114">By default, tracking records are emitted for workflow life-cycle events, activity life-cycle events, fault propagation, and bookmark resumption.</span></span> <span data-ttu-id="4dee0-115">Além disso, os registros de rastreamento personalizadas podem ser emitidos por atividades personalizadas.</span><span class="sxs-lookup"><span data-stu-id="4dee0-115">Additionally, custom tracking records can be emitted by custom activities.</span></span> <span data-ttu-id="4dee0-116">Ao solucionar problemas de correlação, a atividade de controle de registros, o indicador retomada e os registros de propagação de falha são mais úteis.</span><span class="sxs-lookup"><span data-stu-id="4dee0-116">When troubleshooting correlation, the activity tracking records, the bookmark resumption records, and the fault propagation records are the most useful.</span></span> <span data-ttu-id="4dee0-117">A atividade de registros de controle pode ser usada para determinar o progresso atual do fluxo de trabalho e pode ajudar a identificar quais mensagens atividade está aguardando para mensagens.</span><span class="sxs-lookup"><span data-stu-id="4dee0-117">The activity tracking records can be used to determine the current progress of the workflow and can help identify which messaging activity is currently waiting for messages.</span></span> <span data-ttu-id="4dee0-118">Registros de retomada de indicador são úteis porque elas indicam que uma mensagem foi recebida pelo fluxo de trabalho e os registros de propagação de falhas fornecem um registro de qualquer falha no fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4dee0-118">Bookmark resumption records are useful because they indicate that a message was received by the workflow, and fault propagation records provide a record of any faults in the workflow.</span></span> <span data-ttu-id="4dee0-119">Para habilitar o rastreamento, especifique os detalhes desejados <xref:System.Activities.Tracking.TrackingParticipant> no <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> do <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="4dee0-119">To enable tracking, specify the desired <xref:System.Activities.Tracking.TrackingParticipant> in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> of the <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="4dee0-120">No exemplo a seguir, o `ConsoleTrackingParticipant` (da [controle personalizado](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) exemplo) é configurada usando o controle de perfil padrão.</span><span class="sxs-lookup"><span data-stu-id="4dee0-120">In the following example, the `ConsoleTrackingParticipant` (from the [Custom Tracking](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) sample) is configured by using the default tracking profile.</span></span>  
  
```csharp  
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());  
```  
  
 <span data-ttu-id="4dee0-121">Um participante de rastreamento como o ConsoleTrackingParticipant é útil para serviços de hospedagem interna de fluxo de trabalho que têm uma janela do console.</span><span class="sxs-lookup"><span data-stu-id="4dee0-121">A tracking participant such as the ConsoleTrackingParticipant is useful for self-hosted workflow services that have a console window.</span></span> <span data-ttu-id="4dee0-122">Para um serviço hospedado na Web, um participante de rastreamento que registra as informações de rastreamento em um armazenamento durável deve ser usado, como o interno <xref:System.Activities.Tracking.EtwTrackingParticipant>, ou um participante de acompanhamento personalizado que registra as informações em um arquivo, como o `TextWriterTrackingParticpant` do [ Usando um arquivo de texto de controle](../../../../docs/framework/windows-workflow-foundation/samples/tracking-using-a-text-file.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="4dee0-122">For a Web-hosted service, a tracking participant that logs the tracking information to a durable store should be used, such as the built-in <xref:System.Activities.Tracking.EtwTrackingParticipant>, or a custom tracking participant that logs the information to a file, such as the `TextWriterTrackingParticpant` from the [Tracking Using a Text File](../../../../docs/framework/windows-workflow-foundation/samples/tracking-using-a-text-file.md) sample.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="4dee0-123"> controle e configurando o controle para um serviço de fluxo de trabalho hospedado na Web, consulte [fluxo de trabalho de rastreamento e rastreamento](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [configurar rastreamento para um fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)e o [controle &#91;WF Exemplos de&#93; ](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) exemplos.</span><span class="sxs-lookup"><span data-stu-id="4dee0-123"> tracking and configuring tracking for a Web-hosted workflow service, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md), and the [Tracking &#91;WF Samples&#93;](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) samples.</span></span>  
  
## <a name="use-wcf-tracing"></a><span data-ttu-id="4dee0-124">Usar o rastreamento do WCF</span><span class="sxs-lookup"><span data-stu-id="4dee0-124">Use WCF Tracing</span></span>  
 <span data-ttu-id="4dee0-125">Rastreamento de WCF fornece o rastreamento do fluxo de mensagens para e de um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4dee0-125">WCF tracing provides tracing of the flow of messages to and from a workflow service.</span></span> <span data-ttu-id="4dee0-126">Essas informações de rastreamento são útil ao solucionar problemas de correlação, especialmente para correlação baseada em conteúdo.</span><span class="sxs-lookup"><span data-stu-id="4dee0-126">This tracing information is useful when troubleshooting correlation issues, especially for content-based correlation.</span></span> <span data-ttu-id="4dee0-127">Para habilitar o rastreamento, especifique os ouvintes de rastreamento desejado no `system.diagnostics` seção o `web.config` arquivo se o serviço de fluxo de trabalho estiver hospedado na Web, ou o `app.config` arquivo caso o serviço de fluxo de trabalho é hospedado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="4dee0-127">To enable tracing, specify the desired trace listeners in the `system.diagnostics` section of the `web.config` file if the workflow service is Web-hosted, or the `app.config` file if the workflow service is self-hosted.</span></span> <span data-ttu-id="4dee0-128">Para incluir o conteúdo das mensagens de erro no arquivo de rastreamento, especifique `true` para `logEntireMessage` no `messageLogging` elemento o `diagnostics` seção `system.serviceModel`.</span><span class="sxs-lookup"><span data-stu-id="4dee0-128">To include the contents of the messages in the trace file, specify `true` for `logEntireMessage` in the `messageLogging` element in the `diagnostics` section of `system.serviceModel`.</span></span> <span data-ttu-id="4dee0-129">No exemplo a seguir, as informações de rastreamento, incluindo o conteúdo das mensagens, estão configuradas para ser gravado em um arquivo chamado `service.svclog`.</span><span class="sxs-lookup"><span data-stu-id="4dee0-129">In the following example, tracing information, including the content of the messages, is configured to be written to a file that is named `service.svclog`.</span></span>  
  
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
  
 <span data-ttu-id="4dee0-130">Para exibir as informações de rastreamento que estão contidas no `service.svclog`, o [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) é usado.</span><span class="sxs-lookup"><span data-stu-id="4dee0-130">To view the trace information that is contained in `service.svclog`, the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) is used.</span></span> <span data-ttu-id="4dee0-131">Isso é especialmente útil quando correlação baseada em conteúdo de solução de problemas problemas porque você pode exibir o conteúdo da mensagem e veja exatamente o que está sendo passado, e se ele corresponde a <xref:System.ServiceModel.CorrelationQuery> para a correlação baseada em conteúdo.</span><span class="sxs-lookup"><span data-stu-id="4dee0-131">This is especially useful when troubleshooting content-based correlation issues because you can view the message contents and see exactly what is being passed, and whether it matches the <xref:System.ServiceModel.CorrelationQuery> for the content-based correlation.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="4dee0-132"> WCF de rastreamento, consulte [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Configurando o rastreamento](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), e [usando o rastreamento para solucionar problemas de seu aplicativo](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span><span class="sxs-lookup"><span data-stu-id="4dee0-132"> WCF tracing, see [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), and [Using Tracing to Troubleshoot Your Application](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>  
  
## <a name="common-context-exchange-correlation-issues"></a><span data-ttu-id="4dee0-133">Problemas comuns de correlação de troca de contexto</span><span class="sxs-lookup"><span data-stu-id="4dee0-133">Common Context Exchange Correlation Issues</span></span>  
 <span data-ttu-id="4dee0-134">Certos tipos de correlação exigem que um tipo específico de associação é usado para a correlação funcione corretamente.</span><span class="sxs-lookup"><span data-stu-id="4dee0-134">Certain types of correlation require that a specific type of binding is used for the correlation to work correctly.</span></span> <span data-ttu-id="4dee0-135">Os exemplos incluem a correlação de solicitação-resposta, o que exige uma associação bidirecional como <xref:System.ServiceModel.BasicHttpBinding>e a correlação de intercâmbio de contexto, o que exige um baseado no contexto de associação, como <xref:System.ServiceModel.BasicHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="4dee0-135">Examples include request-reply correlation, which requires a two-way binding such as <xref:System.ServiceModel.BasicHttpBinding>, and context exchange correlation, which requires a context-based binding such as <xref:System.ServiceModel.BasicHttpContextBinding>.</span></span> <span data-ttu-id="4dee0-136">A maioria das ligações oferece suporte a operações bidirecionais para que isso não é um problema comum para a correlação de solicitação-resposta, mas há apenas uma série de associações com base em contexto incluindo <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, e <xref:System.ServiceModel.NetTcpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="4dee0-136">Most bindings support two-way operations so this is not a common issue for request-reply correlation, but there are only a handful of context-based bindings including <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, and <xref:System.ServiceModel.NetTcpContextBinding>.</span></span> <span data-ttu-id="4dee0-137">Se um essas associações não é usado, a chamada inicial para um serviço de fluxo de trabalho será bem-sucedida, mas as chamadas subsequentes falhará com o seguinte <xref:System.ServiceModel.FaultException>.</span><span class="sxs-lookup"><span data-stu-id="4dee0-137">If one of these bindings is not used, the initial call to a workflow service will succeed, but subsequent calls will fail with the following <xref:System.ServiceModel.FaultException>.</span></span>  
  
```Output  
There is no context attached to the incoming message for the service   
and the current operation is not marked with "CanCreateInstance = true".   
In order to communicate with this service check whether the incoming binding   
supports the context protocol and has a valid context initialized.  
```  
  
 <span data-ttu-id="4dee0-138">As informações de contexto que são usadas para a correlação de contexto podem ser retornadas pelo <xref:System.ServiceModel.Activities.SendReply> para o <xref:System.ServiceModel.Activities.Receive> atividade que inicializa a correlação de contexto quando usando uma operação bidirecional, ou pode ser especificado pelo chamador se a operação unidirecional.</span><span class="sxs-lookup"><span data-stu-id="4dee0-138">The context information that is used for context correlation can be returned by the <xref:System.ServiceModel.Activities.SendReply> to the <xref:System.ServiceModel.Activities.Receive> activity that initializes the context correlation when using a two-way operation, or it can be specified by the caller if the operation is one-way.</span></span> <span data-ttu-id="4dee0-139">Se o contexto não é enviado pelo chamador ou retornado, o serviço de fluxo de trabalho e o mesmo <xref:System.ServiceModel.FaultException> descritas anteriormente serão retornados quando uma operação subsequente é invocada.</span><span class="sxs-lookup"><span data-stu-id="4dee0-139">If the context is not sent by the caller or returned by the workflow service, then the same <xref:System.ServiceModel.FaultException> described previously will be returned when a subsequent operation is invoked.</span></span>  
  
 <span data-ttu-id="4dee0-140">Para obter mais informações, consulte [intercâmbio de contexto](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md).</span><span class="sxs-lookup"><span data-stu-id="4dee0-140">For more information, see [Context Exchange](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md).</span></span>  
  
## <a name="common-request-reply-correlation-issues"></a><span data-ttu-id="4dee0-141">Problemas comuns de correlação de solicitação-resposta</span><span class="sxs-lookup"><span data-stu-id="4dee0-141">Common Request-Reply Correlation Issues</span></span>  
 <span data-ttu-id="4dee0-142">Correlação de solicitação-resposta é usada com um <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> par para implementar uma operação bidirecional em um serviço de fluxo de trabalho e com um <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> par que invoca uma operação bidirecional em outra Web serviço.</span><span class="sxs-lookup"><span data-stu-id="4dee0-142">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="4dee0-143">Ao invocar uma operação bidirecional em um serviço WCF, o serviço pode ser uma imperativa tradicional baseada em código [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço ou pode ser um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4dee0-143">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service or it can be a workflow service.</span></span> <span data-ttu-id="4dee0-144">Para usar uma associação bidirecional forem usada, como de correlação de solicitação-resposta <xref:System.ServiceModel.BasicHttpBinding>, e as operações devem ser bidirecionais.</span><span class="sxs-lookup"><span data-stu-id="4dee0-144">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>, and the operations must be two-way.</span></span>  
  
 <span data-ttu-id="4dee0-145">Se o serviço de fluxo de trabalho tem bidirecionais operações em paralelo ou sobreposição <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> ou <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pares e a correlação implícita lidar com gerenciamento fornecido pelo <xref:System.ServiceModel.Activities.WorkflowServiceHost>pode não ser suficiente, principalmente em cenários de alto estresse, e as mensagens não podem ser roteadas corretamente.</span><span class="sxs-lookup"><span data-stu-id="4dee0-145">If the workflow service has two-way operations in parallel, or overlapping <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> or <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pairs, then the implicit correlation handle management provided by <xref:System.ServiceModel.Activities.WorkflowServiceHost> may not be sufficient, especially in high-stress scenarios, and messages may not be correctly routed.</span></span> <span data-ttu-id="4dee0-146">Para evitar que esse problema ocorra, é recomendável sempre especificar explicitamente um <xref:System.ServiceModel.Activities.CorrelationHandle> ao usar a correlação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="4dee0-146">To prevent this issue from occurring, we recommend that you always explicitly specify a <xref:System.ServiceModel.Activities.CorrelationHandle> when using request-reply correlation.</span></span> <span data-ttu-id="4dee0-147">Ao usar o **SendAndReceiveReply** e **ReceiveAndSendReply** modelos da seção de mensagens do **caixa de ferramentas** no designer de fluxo de trabalho, um <xref:System.ServiceModel.Activities.CorrelationHandle> é explicitamente configurado por padrão.</span><span class="sxs-lookup"><span data-stu-id="4dee0-147">When using the **SendAndReceiveReply** and **ReceiveAndSendReply** templates from the Messaging section of the **Toolbox** in the workflow designer, a <xref:System.ServiceModel.Activities.CorrelationHandle> is explicitly configured by default.</span></span> <span data-ttu-id="4dee0-148">Ao criar um fluxo de trabalho por meio de código, o <xref:System.ServiceModel.Activities.CorrelationHandle> é especificado no <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> da primeira atividade do par.</span><span class="sxs-lookup"><span data-stu-id="4dee0-148">When building a workflow by using code, the <xref:System.ServiceModel.Activities.CorrelationHandle> is specified in the <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> of the first activity in the pair.</span></span> <span data-ttu-id="4dee0-149">No exemplo a seguir, uma <xref:System.ServiceModel.Activities.Receive> atividade está configurada com uma explícita <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> especificado no <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span><span class="sxs-lookup"><span data-stu-id="4dee0-149">In the following example, a <xref:System.ServiceModel.Activities.Receive> activity is configured with an explicit <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> specified in the <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span></span>  
  
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
  
 <span data-ttu-id="4dee0-150">Persistência não é permitida entre um <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> par ou um <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> par.</span><span class="sxs-lookup"><span data-stu-id="4dee0-150">Persistence is not permitted between a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair or a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair.</span></span> <span data-ttu-id="4dee0-151">É criada uma zona no-persist dura até concluíram as duas atividades.</span><span class="sxs-lookup"><span data-stu-id="4dee0-151">A no-persist zone is created that lasts until both activities have completed.</span></span> <span data-ttu-id="4dee0-152">Se uma atividade, como uma atividade de atraso é desta zona no-persist e faz com que o fluxo de trabalho ficar ocioso, o fluxo de trabalho não será mantido até mesmo se o host está configurada para manter os fluxos de trabalho quando eles se tornam ociosos.</span><span class="sxs-lookup"><span data-stu-id="4dee0-152">If an activity, such as a delay activity, is in this no-persist zone and causes the workflow to become idle, the workflow will not persist even if it the host is configured to persist workflows when they become idle.</span></span> <span data-ttu-id="4dee0-153">Se uma atividade, como uma atividade persist, tenta manter explicitamente na zona não persistente, uma exceção fatal for lançada, anula o fluxo de trabalho e um <xref:System.ServiceModel.FaultException> é retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="4dee0-153">If an activity, such as a persist activity, attempts to explicitly persist in the no-persist zone, a fatal exception is thrown, the workflow aborts, and a <xref:System.ServiceModel.FaultException> is returned to the caller.</span></span> <span data-ttu-id="4dee0-154">Mensagem de exceção fatal "System. InvalidOperationException: Manter atividades não podem ser contidas em blocos sem persistência.".</span><span class="sxs-lookup"><span data-stu-id="4dee0-154">The fatal exception message is "System.InvalidOperationException: Persist activities cannot be contained within no persistence blocks.".</span></span> <span data-ttu-id="4dee0-155">Essa exceção não é retornada ao chamador, mas pode ser observada se o rastreamento está habilitado.</span><span class="sxs-lookup"><span data-stu-id="4dee0-155">This exception is not returned to the caller but can be observed if tracking is enabled.</span></span> <span data-ttu-id="4dee0-156">A mensagem para o <xref:System.ServiceModel.FaultException> retornado ao chamador é "a operação não foi executada porque WorkflowInstance '5836145b 7da2 - 49 d 0-a052-a49162adeab6' foi concluída".</span><span class="sxs-lookup"><span data-stu-id="4dee0-156">The message for the <xref:System.ServiceModel.FaultException> returned to the caller is "The operation could not be performed because WorkflowInstance '5836145b-7da2-49d0-a052-a49162adeab6' has completed".</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="4dee0-157"> correlação de solicitação-resposta, consulte [solicitação-resposta](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).</span><span class="sxs-lookup"><span data-stu-id="4dee0-157"> request-reply correlation, see [Request-Reply](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).</span></span>  
  
## <a name="common-content-correlation-issues"></a><span data-ttu-id="4dee0-158">Problemas comuns de correlação de conteúdo</span><span class="sxs-lookup"><span data-stu-id="4dee0-158">Common Content Correlation Issues</span></span>  
 <span data-ttu-id="4dee0-159">Correlação baseada em conteúdo é usada quando um serviço de fluxo de trabalho recebe várias mensagens e uma parte dos dados nas mensagens trocadas identifica a instância desejada.</span><span class="sxs-lookup"><span data-stu-id="4dee0-159">Content-based correlation is used when a workflow service receives multiple messages and a piece of data in the exchanged messages identifies the desired instance.</span></span> <span data-ttu-id="4dee0-160">Correlação baseada em conteúdo usa esses dados na mensagem, como um número ou a ordem de ID de cliente, para rotear mensagens para a instância de fluxo de trabalho correto.</span><span class="sxs-lookup"><span data-stu-id="4dee0-160">Content-based correlation uses this data in the message, such as a customer number or order ID, to route messages to the correct workflow instance.</span></span> <span data-ttu-id="4dee0-161">Esta seção descreve alguns problemas comuns que podem ocorrer ao usar a correlação baseada em conteúdo.</span><span class="sxs-lookup"><span data-stu-id="4dee0-161">This section describes several common issues that may occur when using content-based correlation.</span></span>  
  
### <a name="ensure-the-identifying-data-is-unique"></a><span data-ttu-id="4dee0-162">Certifique-se de que os dados de identificação são exclusivos</span><span class="sxs-lookup"><span data-stu-id="4dee0-162">Ensure the Identifying Data Is Unique</span></span>  
 <span data-ttu-id="4dee0-163">Os dados que são usados para identificar a instância são transformados em uma chave de correlação.</span><span class="sxs-lookup"><span data-stu-id="4dee0-163">The data that is used to identify the instance is hashed into a correlation key.</span></span> <span data-ttu-id="4dee0-164">Deve-se ter cuidado para garantir que os dados que são usados para correlação são exclusivos ou então colisões na chave de hash podem ocorrer e gerar mensagens acabe sendo enviado.</span><span class="sxs-lookup"><span data-stu-id="4dee0-164">Care must be taken to guarantee that the data that is used for correlation is unique or else collisions in the hashed key might occur and cause messages to be misrouted.</span></span> <span data-ttu-id="4dee0-165">Por exemplo, uma correlação com base apenas em um nome de cliente pode causar um conflito porque pode haver vários clientes que têm o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="4dee0-165">For example, a correlation based only on a customer name may cause a collision because there may be multiple customers who have the same name.</span></span> <span data-ttu-id="4dee0-166">Os dois-pontos (:) não devem ser usado como parte dos dados que são usados para correlacionar a mensagem porque ele já é usado para delimitar a consulta de mensagem chave e valor para formar a cadeia de caracteres que é transformado em hash posteriormente.</span><span class="sxs-lookup"><span data-stu-id="4dee0-166">The colon (:) should not be used as part of the data that is used to correlate the message because it is already used to delimit the message query’s key and value to form the string that is subsequently hashed.</span></span> <span data-ttu-id="4dee0-167">Se estiver sendo usada a persistência, certifique-se de que os dados que identificam atuais não foi usados por uma instância previamente persistida.</span><span class="sxs-lookup"><span data-stu-id="4dee0-167">If persistence is being used, make sure that the current identifying data has not been used by a previously persisted instance.</span></span> <span data-ttu-id="4dee0-168">Desabilitar temporariamente persistência pode ajudar a identificar o problema.</span><span class="sxs-lookup"><span data-stu-id="4dee0-168">Temporarily disabling persistence can help identify this issue.</span></span> <span data-ttu-id="4dee0-169">O rastreamento do WCF pode ser usado para exibir a chave de correlação calculada e é útil para depurar esse tipo de problema.</span><span class="sxs-lookup"><span data-stu-id="4dee0-169">WCF tracing can be used to view the calculated correlation key and is useful for debugging this kind of issue.</span></span>  
  
### <a name="race-conditions"></a><span data-ttu-id="4dee0-170">Condições de corrida</span><span class="sxs-lookup"><span data-stu-id="4dee0-170">Race Conditions</span></span>  
 <span data-ttu-id="4dee0-171">Há um pequeno espaço no tempo entre o serviço de recebimento de uma mensagem e a correlação, na verdade, está sendo inicializado, durante o qual as mensagens de acompanhamento serão ignoradas.</span><span class="sxs-lookup"><span data-stu-id="4dee0-171">There is a small gap in time between the service receiving a message and the correlation actually being initialized, during which follow-up messages will be ignored.</span></span> <span data-ttu-id="4dee0-172">Se um serviço de fluxo de trabalho inicializa a correlação baseada em conteúdo usando dados passados do cliente em uma operação unidirecional, e o chamador envia mensagens de acompanhamento imediatas, essas mensagens serão ignoradas durante esse intervalo.</span><span class="sxs-lookup"><span data-stu-id="4dee0-172">If a workflow service initializes the content-based correlation by using data passed from the client over a one-way operation, and the caller sends immediate follow-up messages, these messages will be ignored during this interval.</span></span> <span data-ttu-id="4dee0-173">Isso pode ser evitado usando-se uma operação bidirecional para inicializar a correlação, ou usando um <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="4dee0-173">This can be avoided by using a two-way operation to initialize the correlation, or by using a <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span>  
  
### <a name="correlation-query-issues"></a><span data-ttu-id="4dee0-174">Problemas de correlação de consulta</span><span class="sxs-lookup"><span data-stu-id="4dee0-174">Correlation Query Issues</span></span>  
 <span data-ttu-id="4dee0-175">Consultas de correlação são usadas para especificar quais dados em uma mensagem são usados para correlacionar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="4dee0-175">Correlation queries are used to specify what data in a message is used to correlate the message.</span></span> <span data-ttu-id="4dee0-176">Esses dados são especificados usando uma consulta XPath.</span><span class="sxs-lookup"><span data-stu-id="4dee0-176">This data is specified by using an XPath query.</span></span> <span data-ttu-id="4dee0-177">Se as mensagens para um serviço não estão sendo despachadas, embora tudo parece estar correta, uma estratégia para solução de problemas é para especificar um valor literal que corresponde ao valor dos dados de mensagem em vez de uma consulta XPath.</span><span class="sxs-lookup"><span data-stu-id="4dee0-177">If messages to a service are not being dispatched even though everything appears to be correct, one strategy for troubleshooting is to specify a literal value that matches the value of the message data instead of an XPath query.</span></span> <span data-ttu-id="4dee0-178">Para especificar um valor literal, use o `string` função.</span><span class="sxs-lookup"><span data-stu-id="4dee0-178">To specify a literal value, use the `string` function.</span></span> <span data-ttu-id="4dee0-179">No exemplo a seguir, uma <xref:System.ServiceModel.MessageQuerySet> está configurado para usar um valor de literal `11445` para o `OrderId` e a consulta XPath é comentada.</span><span class="sxs-lookup"><span data-stu-id="4dee0-179">In the following example, a <xref:System.ServiceModel.MessageQuerySet> is configured to use a literal value of `11445` for the `OrderId` and the XPath query is commented out.</span></span>  
  
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
  
 <span data-ttu-id="4dee0-180">Se uma consulta XPath é configurada incorretamente, de modo que nenhum dado de correlação é recuperado, uma falha será retornada com a seguinte mensagem: "uma consulta de correlação gerou um conjunto de resultados vazio.</span><span class="sxs-lookup"><span data-stu-id="4dee0-180">If an XPath query is configured incorrectly such that no correlation data is retrieved, a fault is returned with the following message: "A correlation query yielded an empty result set.</span></span> <span data-ttu-id="4dee0-181">Verifique se as consultas para o ponto de extremidade de correlação estão definidas corretamente."</span><span class="sxs-lookup"><span data-stu-id="4dee0-181">Please ensure correlation queries for the endpoint are correctly configured."</span></span> <span data-ttu-id="4dee0-182">Uma maneira rápida de solucionar esse problema é substituir a consulta XPath com um valor literal, conforme descrito na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="4dee0-182">One quick way to troubleshoot this is to replace the XPath query with a literal value as described in the previous section.</span></span> <span data-ttu-id="4dee0-183">Esse problema pode ocorrer se você usar o construtor de consultas XPath no **adicionar inicializadores de correlação** ou **definição de CorrelatesOn** caixas de diálogo e o serviço de fluxo de trabalho usa contratos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="4dee0-183">This issue can occur if you use the XPath query builder in the **Add Correlation Initializers** or **CorrelatesOn Definition** dialog boxes and your workflow service uses message contracts.</span></span> <span data-ttu-id="4dee0-184">No exemplo a seguir, é definida uma classe de contrato de mensagem.</span><span class="sxs-lookup"><span data-stu-id="4dee0-184">In the following example, a message contract class is defined.</span></span>  
  
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
  
 <span data-ttu-id="4dee0-185">Este contrato de mensagem é usado por um <xref:System.ServiceModel.Activities.Receive> atividade em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4dee0-185">This message contract is used by a <xref:System.ServiceModel.Activities.Receive> activity in a workflow.</span></span> <span data-ttu-id="4dee0-186">O `CartId` no cabeçalho da mensagem é usada para correlacionar a mensagem para a instância correta.</span><span class="sxs-lookup"><span data-stu-id="4dee0-186">The `CartId` in the header of the message is used to correlate the message to the correct instance.</span></span> <span data-ttu-id="4dee0-187">Se a consulta XPath que recupera o `CartId` é criado usando as caixas de diálogo correlação no designer de fluxo de trabalho, o XPath incorreto a seguir consulta é gerada.</span><span class="sxs-lookup"><span data-stu-id="4dee0-187">If the XPath query that retrieves the `CartId` is created using the correlation dialogs in the workflow designer, the following incorrect XPath query is generated.</span></span>  
  
```  
sm:body()/xg0:AddItemMessage/xg0:CartId  
```  
  
 <span data-ttu-id="4dee0-188">Essa consulta XPath estaria correta se a <xref:System.ServiceModel.Activities.Receive> atividade parâmetros usados para os dados, mas como ele está usando um contrato de mensagem é incorreto.</span><span class="sxs-lookup"><span data-stu-id="4dee0-188">This XPath query would be correct if the <xref:System.ServiceModel.Activities.Receive> activity used parameters for the data, but since it is using a message contract it is incorrect.</span></span> <span data-ttu-id="4dee0-189">A seguinte consulta XPath é a consulta XPath correta para recuperar o `CartId` do cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="4dee0-189">The following XPath query is the correct XPath query to retrieve the `CartId` from the header.</span></span>  
  
```  
sm:header()/tempuri:CartId  
```  
  
 <span data-ttu-id="4dee0-190">Isso pode ser confirmado ao examinar o corpo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="4dee0-190">This can be confirmed by examining the body of the message.</span></span>  
  
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
  
 <span data-ttu-id="4dee0-191">A exemplo a seguir mostra um <xref:System.ServiceModel.Activities.Receive> atividade configurada para um `AddItem` operação que usa o contrato de mensagem anterior para receber dados.</span><span class="sxs-lookup"><span data-stu-id="4dee0-191">The following example shows a <xref:System.ServiceModel.Activities.Receive> activity configured for an `AddItem` operation that uses the previous message contract to receive data.</span></span> <span data-ttu-id="4dee0-192">A consulta XPath está configurada corretamente.</span><span class="sxs-lookup"><span data-stu-id="4dee0-192">The XPath query is correctly configured.</span></span>  
  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="4dee0-193"> correlação baseada em conteúdo, consulte [baseada em conteúdo](../../../../docs/framework/wcf/feature-details/content-based-correlation.md) e [Calculadora correlacionada](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="4dee0-193"> content-based correlation, see [Content Based](../../../../docs/framework/wcf/feature-details/content-based-correlation.md) and the [Correlated Calculator](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md) sample.</span></span>
