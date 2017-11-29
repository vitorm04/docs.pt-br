---
title: Registro de mensagem e rastreamento
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
caps.latest.revision: "53"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a73c6e544b7aae003a525c29743d68db18a54515
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="tracing-and-message-logging"></a><span data-ttu-id="e7be6-102">Registro de mensagem e rastreamento</span><span class="sxs-lookup"><span data-stu-id="e7be6-102">Tracing and Message Logging</span></span>
<span data-ttu-id="e7be6-103">Este exemplo demonstra como habilitar o rastreamento e o registro de mensagem.</span><span class="sxs-lookup"><span data-stu-id="e7be6-103">This sample demonstrates how to enable tracing and message logging.</span></span> <span data-ttu-id="e7be6-104">Os rastreamentos resultantes e os logs de mensagem são exibidos usando o [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e7be6-104">The resulting traces and message logs are viewed using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="e7be6-105">Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="e7be6-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7be6-106">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="e7be6-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="e7be6-107">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="e7be6-107">Tracing</span></span>  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="e7be6-108">usa o mecanismo de rastreamento definido no <xref:System.Diagnostics> namespace.</span><span class="sxs-lookup"><span data-stu-id="e7be6-108"> uses the tracing mechanism defined in the <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="e7be6-109">Nesse modelo de rastreamento, dados de rastreamento são produzidos por fontes de rastreamento que implementam aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e7be6-109">In this tracing model, trace data is produced by trace sources that applications implement.</span></span> <span data-ttu-id="e7be6-110">Cada origem é identificada por um nome.</span><span class="sxs-lookup"><span data-stu-id="e7be6-110">Each source is identified by a name.</span></span> <span data-ttu-id="e7be6-111">Os consumidores de rastreamento criar ouvintes de rastreamento para as fontes de rastreamento para o qual deseja recuperar informações.</span><span class="sxs-lookup"><span data-stu-id="e7be6-111">Trace consumers create trace listeners for the trace sources for which they want to retrieve information.</span></span> <span data-ttu-id="e7be6-112">Para receber dados de rastreamento, você deve criar um ouvinte para a origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="e7be6-112">To receive trace data, you must create a listener for the trace source.</span></span> <span data-ttu-id="e7be6-113">Em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], isso pode ser feito adicionando o código a seguir do serviço ou o arquivo de configuração do cliente, definindo a origem de rastreamento de modelo de serviço `switchValue`:</span><span class="sxs-lookup"><span data-stu-id="e7be6-113">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], this can be done by adding the following code to either the service’s or client’s configuration file by setting the Service Model trace source `switchValue`:</span></span>  
  
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
  
 <span data-ttu-id="e7be6-114">Para obter mais informações sobre as fontes de rastreamento, consulte a seção origem do rastreamento de [Configurando rastreamento](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="e7be6-114">For more information about trace sources, see the Trace Source section in the [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) topic.</span></span>  
  
## <a name="activity-tracing-and-propagation"></a><span data-ttu-id="e7be6-115">Rastreamento de atividades e propagação</span><span class="sxs-lookup"><span data-stu-id="e7be6-115">Activity Tracing and Propagation</span></span>  
 <span data-ttu-id="e7be6-116">Tendo `ActivityTracing` habilitado e `propagateActivity` definida como `true` no `system.ServiceModel` fontes de rastreamento para o cliente e o serviço fornecem correlação de rastreamentos em unidades lógicas de processamento (atividades) em atividades em pontos de extremidade ( por meio das transferências de atividade) e nas atividades abrangendo vários pontos de extremidade (por meio de propagação de ID de atividade).</span><span class="sxs-lookup"><span data-stu-id="e7be6-116">Having `ActivityTracing` enabled and `propagateActivity` set to `true` in the `system.ServiceModel` trace sources for both the client and service provide correlation of traces within logical units of processing (activities), across activities within endpoints (through activity transfers), and across activities spanning multiple endpoints (through activity ID propagation).</span></span>  
  
 <span data-ttu-id="e7be6-117">Esses três mecanismos (atividades, transferência e propagação) podem ajudar a localizar a causa de um erro mais rapidamente, usando a ferramenta do Visualizador de rastreamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="e7be6-117">These three mechanisms (activities, transfers, and propagation) can help you locate the root cause of an error more quickly using the Service Trace Viewer tool.</span></span> <span data-ttu-id="e7be6-118">Para obter mais informações, consulte [usando o Visualizador de rastreamento de serviço para exibir rastreamentos correlacionados e solução de problemas](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="e7be6-118">For more information, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="e7be6-119">É possível estender o rastreamento que é fornecido pelo ServiceModel Criando rastreamentos de atividade definida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="e7be6-119">It is possible to extend the tracing that is provided by the ServiceModel by creating user-defined activity traces.</span></span> <span data-ttu-id="e7be6-120">Rastreamento de atividade definida pelo usuário permite que o usuário criar atividades de rastreamento para:</span><span class="sxs-lookup"><span data-stu-id="e7be6-120">User-defined activity tracing allows the user to create trace activities to:</span></span>  
  
-   <span data-ttu-id="e7be6-121">Grupo rastreamentos em unidades lógicas de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e7be6-121">Group traces into logical units of work.</span></span>  
  
-   <span data-ttu-id="e7be6-122">Correlacione atividades por meio de transferências e propagação.</span><span class="sxs-lookup"><span data-stu-id="e7be6-122">Correlate activities through transfers and propagation.</span></span>  
  
-   <span data-ttu-id="e7be6-123">Reduzir o custo de desempenho de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] rastreamento (por exemplo, o disco espaço custo de um arquivo de log).</span><span class="sxs-lookup"><span data-stu-id="e7be6-123">Lessen the performance cost of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tracing (for example, the disk space cost of a log file).</span></span>  
  
 <span data-ttu-id="e7be6-124">Para obter mais informações sobre o rastreamento de atividade definida pelo usuário, consulte o [estendendo rastreamento](../../../../docs/framework/wcf/samples/extending-tracing.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="e7be6-124">For more information about user-defined activity trace, please see the [Extending Tracing](../../../../docs/framework/wcf/samples/extending-tracing.md) sample.</span></span>  
  
## <a name="message-logging"></a><span data-ttu-id="e7be6-125">Registro em log de mensagens</span><span class="sxs-lookup"><span data-stu-id="e7be6-125">Message Logging</span></span>  
 <span data-ttu-id="e7be6-126">Registro de mensagem pode ser habilitado tanto no cliente e no serviço de qualquer [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e7be6-126">Message logging can be enabled both on the client and service of any [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application.</span></span> <span data-ttu-id="e7be6-127">Para habilitar o log de mensagem, você deve adicionar o código a seguir ao cliente ou serviço:</span><span class="sxs-lookup"><span data-stu-id="e7be6-127">To enable message logging, you must add the following code to either the client or service:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics>  
      <!-- Enable Message Logging here. -->  
      <!-- log all messages received or sent at the transport or service model levels >  
      <messageLogging logEntireMessage="true"  
                      maxMessagesToLog="300"  
                      logMessagesAtServiceLevel="true"  
                      logMalformedMessages="true"  
                      logMessagesAtTransportLevel="true" />  
    </diagnostics>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="e7be6-128">Quando uma mensagem é gravada, o tipo de rastreamento depende se ele está sendo rastreado no cliente ou no servidor.</span><span class="sxs-lookup"><span data-stu-id="e7be6-128">When a message is recorded, the trace type depends on whether it is being traced at the client or the server.</span></span> <span data-ttu-id="e7be6-129">Por exemplo, uma mensagem de "Adicionar" que é enviada a um cliente é rastreada sob a categoria "TransportWrite" no cliente, enquanto a mesma mensagem é rastreada sob a categoria "TransportRead" no serviço.</span><span class="sxs-lookup"><span data-stu-id="e7be6-129">For example, an "Add" message that is sent to a client is traced under the "TransportWrite" category at the client, whereas the same message is traced under the "TransportRead" category at the service.</span></span>  
  
 <span data-ttu-id="e7be6-130">Configurar o ouvinte de rastreamento adicionando o seguinte código para o <xref:System.Diagnostics> seção do arquivo de App. config do cliente ou do serviço Web. config:</span><span class="sxs-lookup"><span data-stu-id="e7be6-130">Configure the trace listener by adding the following code to the <xref:System.Diagnostics> section of the client's App.config file or the service's Web.config file:</span></span>  
  
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
  
 <span data-ttu-id="e7be6-131">Mensagens são registradas em formato XML no diretório de destino especificado no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="e7be6-131">Messages are logged in XML format in the target directory specified in the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7be6-132">Arquivos de rastreamento não são criados sem criar o diretório de log.</span><span class="sxs-lookup"><span data-stu-id="e7be6-132">Trace files are not created without initially creating the log directory.</span></span> <span data-ttu-id="e7be6-133">Certifique-se de que o diretório C:\logs\ existe, ou especifique um diretório de log alternativo na configuração de ouvinte.</span><span class="sxs-lookup"><span data-stu-id="e7be6-133">Make sure that the directory C:\logs\ exists, or specify an alternate logging directory in the listener configuration.</span></span> <span data-ttu-id="e7be6-134">Consulte as instruções de configuração inicial no final deste documento para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="e7be6-134">See the initial setup instructions at the end of this document for more information.</span></span>  
  
 <span data-ttu-id="e7be6-135">Para obter mais informações sobre o log de mensagem, consulte o [Configurando o log de mensagens](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="e7be6-135">For more information about message logging, see the [Configuring Message Logging](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) topic.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e7be6-136">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="e7be6-136">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e7be6-137">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e7be6-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="e7be6-138">Antes de executar o exemplo de rastreamento e o log de mensagens, crie o diretório C:\logs\ para o serviço para gravar os arquivos .svclog.</span><span class="sxs-lookup"><span data-stu-id="e7be6-138">Before running the Tracing and Message Logging sample, create the directory C:\logs\ for the service to write the .svclog files to.</span></span> <span data-ttu-id="e7be6-139">O nome desta pasta está definido no arquivo de configuração, como o caminho para as mensagens a serem registrados e rastreamentos e pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="e7be6-139">The name of this directory is defined in the configuration file as the path for the traces and messages to be logged and can be changed.</span></span> <span data-ttu-id="e7be6-140">Fornecer ao usuário acesso de gravação do serviço de rede para o diretório de logs.</span><span class="sxs-lookup"><span data-stu-id="e7be6-140">Give the user Network Service write access to the logs directory.</span></span>  
  
3.  <span data-ttu-id="e7be6-141">Para criar a edição do c#, C++ ou Visual Basic .NET da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e7be6-141">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="e7be6-142">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e7be6-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e7be6-143">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="e7be6-143">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e7be6-144">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="e7be6-144">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e7be6-145">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="e7be6-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e7be6-146">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="e7be6-146">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a><span data-ttu-id="e7be6-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7be6-147">See Also</span></span>  
 [<span data-ttu-id="e7be6-148">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="e7be6-148">Tracing</span></span>](../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="e7be6-149">Exemplos de monitoramento do AppFabric</span><span class="sxs-lookup"><span data-stu-id="e7be6-149">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
