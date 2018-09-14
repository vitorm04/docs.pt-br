---
title: Registro de mensagem e rastreamento
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: 7f729e845fe552d523a46a1783404baf4e0bbfca
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45618673"
---
# <a name="tracing-and-message-logging"></a><span data-ttu-id="97b8a-102">Registro de mensagem e rastreamento</span><span class="sxs-lookup"><span data-stu-id="97b8a-102">Tracing and Message Logging</span></span>
<span data-ttu-id="97b8a-103">Este exemplo demonstra como habilitar o rastreamento e o registro de mensagem.</span><span class="sxs-lookup"><span data-stu-id="97b8a-103">This sample demonstrates how to enable tracing and message logging.</span></span> <span data-ttu-id="97b8a-104">Os rastreamentos resultantes e logs de mensagem são exibidos usando o [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="97b8a-104">The resulting traces and message logs are viewed using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="97b8a-105">Este exemplo se baseia a [Introdução ao](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="97b8a-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="97b8a-106">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="97b8a-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="97b8a-107">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="97b8a-107">Tracing</span></span>  
 <span data-ttu-id="97b8a-108">Windows Communication Foundation (WCF) usa o mecanismo de rastreamento definido na <xref:System.Diagnostics> namespace.</span><span class="sxs-lookup"><span data-stu-id="97b8a-108">Windows Communication Foundation (WCF) uses the tracing mechanism defined in the <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="97b8a-109">Nesse modelo de rastreamento, dados de rastreamento são produzidos por fontes de rastreamento que implementam a aplicativos.</span><span class="sxs-lookup"><span data-stu-id="97b8a-109">In this tracing model, trace data is produced by trace sources that applications implement.</span></span> <span data-ttu-id="97b8a-110">Cada origem é identificada por um nome.</span><span class="sxs-lookup"><span data-stu-id="97b8a-110">Each source is identified by a name.</span></span> <span data-ttu-id="97b8a-111">Os consumidores de rastreamento criam ouvintes de rastreamento para as fontes de rastreamento para o qual deseja recuperar informações.</span><span class="sxs-lookup"><span data-stu-id="97b8a-111">Trace consumers create trace listeners for the trace sources for which they want to retrieve information.</span></span> <span data-ttu-id="97b8a-112">Para receber dados de rastreamento, você deve criar um ouvinte para a origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="97b8a-112">To receive trace data, you must create a listener for the trace source.</span></span> <span data-ttu-id="97b8a-113">No WCF, isso pode ser feito adicionando o seguinte código ao arquivo de configuração do serviço ou do cliente, configurando a origem de rastreamento do modelo de serviço `switchValue`:</span><span class="sxs-lookup"><span data-stu-id="97b8a-113">In WCF, this can be done by adding the following code to either the service’s or client’s configuration file by setting the Service Model trace source `switchValue`:</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-service.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>  
```  
  
 <span data-ttu-id="97b8a-114">Para obter mais informações sobre as fontes de rastreamento, consulte a seção origem de rastreamento de [Configurando o rastreamento](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="97b8a-114">For more information about trace sources, see the Trace Source section in the [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) topic.</span></span>  
  
## <a name="activity-tracing-and-propagation"></a><span data-ttu-id="97b8a-115">Rastreamento de atividades e propagação</span><span class="sxs-lookup"><span data-stu-id="97b8a-115">Activity Tracing and Propagation</span></span>  
 <span data-ttu-id="97b8a-116">Tendo `ActivityTracing` habilitado e `propagateActivity` definido como `true` no `system.ServiceModel` origens de rastreamento para o cliente e o serviço fornecem a correlação de rastreamentos em unidades lógicas de processamento (atividades), entre as atividades dentro de pontos de extremidade ( por meio de transferências de atividades) e entre as atividades que abrangem vários pontos de extremidade (por meio de propagação de ID de atividade).</span><span class="sxs-lookup"><span data-stu-id="97b8a-116">Having `ActivityTracing` enabled and `propagateActivity` set to `true` in the `system.ServiceModel` trace sources for both the client and service provide correlation of traces within logical units of processing (activities), across activities within endpoints (through activity transfers), and across activities spanning multiple endpoints (through activity ID propagation).</span></span>  
  
 <span data-ttu-id="97b8a-117">Esses três mecanismos (atividades, transferências e propagação) podem ajudá-lo a localizar a causa raiz de um erro mais rapidamente usando a ferramenta Visualizador de rastreamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="97b8a-117">These three mechanisms (activities, transfers, and propagation) can help you locate the root cause of an error more quickly using the Service Trace Viewer tool.</span></span> <span data-ttu-id="97b8a-118">Para obter mais informações, consulte [usando o Visualizador de rastreamento de serviço para exibir rastreamentos correlacionados e soluções de problemas](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="97b8a-118">For more information, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="97b8a-119">É possível estender o rastreamento que é fornecido pelo ServiceModel Criando rastreamentos de atividade definida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="97b8a-119">It is possible to extend the tracing that is provided by the ServiceModel by creating user-defined activity traces.</span></span> <span data-ttu-id="97b8a-120">Rastreamento de atividades definidos pelo usuário permite ao usuário criar atividades de rastreamento para:</span><span class="sxs-lookup"><span data-stu-id="97b8a-120">User-defined activity tracing allows the user to create trace activities to:</span></span>  
  
-   <span data-ttu-id="97b8a-121">Rastreamentos de grupo em unidades lógicas de trabalho.</span><span class="sxs-lookup"><span data-stu-id="97b8a-121">Group traces into logical units of work.</span></span>  
  
-   <span data-ttu-id="97b8a-122">Correlacione atividades por meio de transferências e propagação.</span><span class="sxs-lookup"><span data-stu-id="97b8a-122">Correlate activities through transfers and propagation.</span></span>  
  
-   <span data-ttu-id="97b8a-123">Diminui o custo de desempenho de rastreamento do WCF (por exemplo, o custo de espaço em disco de um arquivo de log).</span><span class="sxs-lookup"><span data-stu-id="97b8a-123">Lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
 <span data-ttu-id="97b8a-124">Para obter mais informações sobre rastreamento de atividade definida pelo usuário, consulte o [estendendo rastreamento](../../../../docs/framework/wcf/samples/extending-tracing.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="97b8a-124">For more information about user-defined activity trace, please see the [Extending Tracing](../../../../docs/framework/wcf/samples/extending-tracing.md) sample.</span></span>  
  
## <a name="message-logging"></a><span data-ttu-id="97b8a-125">Registro em log de mensagens</span><span class="sxs-lookup"><span data-stu-id="97b8a-125">Message Logging</span></span>  
 <span data-ttu-id="97b8a-126">Log de mensagens pode ser habilitado tanto no cliente e o serviço de qualquer aplicativo WCF.</span><span class="sxs-lookup"><span data-stu-id="97b8a-126">Message logging can be enabled both on the client and service of any WCF application.</span></span> <span data-ttu-id="97b8a-127">Para habilitar o registro em log de mensagem, você deve adicionar o código a seguir para o cliente ou serviço:</span><span class="sxs-lookup"><span data-stu-id="97b8a-127">To enable message logging, you must add the following code to either the client or service:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics>  
      <!-- Enable Message Logging here. -->  
      <!-- log all messages received or sent at the transport or service model levels -->  
      <messageLogging logEntireMessage="true"  
                      maxMessagesToLog="300"  
                      logMessagesAtServiceLevel="true"  
                      logMalformedMessages="true"  
                      logMessagesAtTransportLevel="true" />  
    </diagnostics>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="97b8a-128">Quando uma mensagem é gravada, o tipo de rastreamento depende se ela está sendo rastreada no cliente ou servidor.</span><span class="sxs-lookup"><span data-stu-id="97b8a-128">When a message is recorded, the trace type depends on whether it is being traced at the client or the server.</span></span> <span data-ttu-id="97b8a-129">Por exemplo, uma mensagem de "Adicionar" é enviada a um cliente é rastreada sob a categoria "TransportWrite" no cliente, enquanto a mesma mensagem é rastreada sob a categoria "TransportRead" no serviço.</span><span class="sxs-lookup"><span data-stu-id="97b8a-129">For example, an "Add" message that is sent to a client is traced under the "TransportWrite" category at the client, whereas the same message is traced under the "TransportRead" category at the service.</span></span>  
  
 <span data-ttu-id="97b8a-130">Configurar o ouvinte de rastreamento, adicionando o seguinte código para o <xref:System.Diagnostics> seção do arquivo de App. config do cliente ou do serviço Web. config:</span><span class="sxs-lookup"><span data-stu-id="97b8a-130">Configure the trace listener by adding the following code to the <xref:System.Diagnostics> section of the client's App.config file or the service's Web.config file:</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-client.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
```  
  
 <span data-ttu-id="97b8a-131">As mensagens são registradas no formato XML no diretório de destino especificado no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="97b8a-131">Messages are logged in XML format in the target directory specified in the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="97b8a-132">Arquivos de rastreamento não são criados sem criar inicialmente o diretório de log.</span><span class="sxs-lookup"><span data-stu-id="97b8a-132">Trace files are not created without initially creating the log directory.</span></span> <span data-ttu-id="97b8a-133">Certifique-se de que o diretório C:\logs\ existe, ou especifique um diretório de log alternativo na configuração de ouvinte.</span><span class="sxs-lookup"><span data-stu-id="97b8a-133">Make sure that the directory C:\logs\ exists, or specify an alternate logging directory in the listener configuration.</span></span> <span data-ttu-id="97b8a-134">Consulte as instruções de configuração inicial no final deste documento para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="97b8a-134">See the initial setup instructions at the end of this document for more information.</span></span>  
  
 <span data-ttu-id="97b8a-135">Para obter mais informações sobre o log de mensagem, consulte a [Configurando o log de mensagens](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="97b8a-135">For more information about message logging, see the [Configuring Message Logging](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) topic.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="97b8a-136">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="97b8a-136">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="97b8a-137">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="97b8a-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="97b8a-138">Antes de executar o exemplo de rastreamento e registro em log de mensagem, crie o diretório C:\logs\ para o serviço para gravar os arquivos. svclog para.</span><span class="sxs-lookup"><span data-stu-id="97b8a-138">Before running the Tracing and Message Logging sample, create the directory C:\logs\ for the service to write the .svclog files to.</span></span> <span data-ttu-id="97b8a-139">O nome desse diretório é definido no arquivo de configuração como o caminho para as mensagens a serem registrados e rastreamentos e pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="97b8a-139">The name of this directory is defined in the configuration file as the path for the traces and messages to be logged and can be changed.</span></span> <span data-ttu-id="97b8a-140">Dar ao usuário acesso de gravação do serviço de rede para o diretório de logs.</span><span class="sxs-lookup"><span data-stu-id="97b8a-140">Give the user Network Service write access to the logs directory.</span></span>  
  
3.  <span data-ttu-id="97b8a-141">Para compilar a edição de c#, C++ ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="97b8a-141">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="97b8a-142">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="97b8a-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="97b8a-143">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="97b8a-143">The samples may already be installed on your computer.</span></span> <span data-ttu-id="97b8a-144">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="97b8a-144">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="97b8a-145">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="97b8a-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="97b8a-146">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="97b8a-146">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a><span data-ttu-id="97b8a-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97b8a-147">See Also</span></span>  
 [<span data-ttu-id="97b8a-148">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="97b8a-148">Tracing</span></span>](../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="97b8a-149">AppFabric que monitora exemplos</span><span class="sxs-lookup"><span data-stu-id="97b8a-149">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
