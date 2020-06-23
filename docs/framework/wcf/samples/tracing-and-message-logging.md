---
title: Registro de mensagem e rastreamento
description: Saiba como usar a ferramenta Visualizador de rastreamento de serviço (SvcTraceViewer.exe) para exibir rastreamentos e logs de mensagens usando este exemplo WFC.
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: bb49334252c2415223b0f8f5559a6dc838d175e3
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246019"
---
# <a name="tracing-and-message-logging"></a><span data-ttu-id="c46be-103">Registro de mensagem e rastreamento</span><span class="sxs-lookup"><span data-stu-id="c46be-103">Tracing and Message Logging</span></span>
<span data-ttu-id="c46be-104">Este exemplo demonstra como habilitar o rastreamento e o log de mensagens.</span><span class="sxs-lookup"><span data-stu-id="c46be-104">This sample demonstrates how to enable tracing and message logging.</span></span> <span data-ttu-id="c46be-105">Os rastreamentos e os logs de mensagens resultantes são exibidos usando a [ferramenta do Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="c46be-105">The resulting traces and message logs are viewed using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="c46be-106">Este exemplo é baseado na [introdução](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="c46be-106">This sample is based on the [Getting Started](getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c46be-107">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="c46be-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="c46be-108">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="c46be-108">Tracing</span></span>  
 <span data-ttu-id="c46be-109">Windows Communication Foundation (WCF) usa o mecanismo de rastreamento definido no <xref:System.Diagnostics> namespace.</span><span class="sxs-lookup"><span data-stu-id="c46be-109">Windows Communication Foundation (WCF) uses the tracing mechanism defined in the <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="c46be-110">Nesse modelo de rastreamento, os dados de rastreamento são produzidos por fontes de rastreamento que os aplicativos implementam.</span><span class="sxs-lookup"><span data-stu-id="c46be-110">In this tracing model, trace data is produced by trace sources that applications implement.</span></span> <span data-ttu-id="c46be-111">Cada fonte é identificada por um nome.</span><span class="sxs-lookup"><span data-stu-id="c46be-111">Each source is identified by a name.</span></span> <span data-ttu-id="c46be-112">Os consumidores de rastreamento criam ouvintes de rastreamento para as fontes de rastreamento para as quais desejam recuperar informações.</span><span class="sxs-lookup"><span data-stu-id="c46be-112">Trace consumers create trace listeners for the trace sources for which they want to retrieve information.</span></span> <span data-ttu-id="c46be-113">Para receber dados de rastreamento, você deve criar um ouvinte para a origem do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c46be-113">To receive trace data, you must create a listener for the trace source.</span></span> <span data-ttu-id="c46be-114">No WCF, isso pode ser feito adicionando o código a seguir ao arquivo de configuração do cliente ou do serviço definindo a fonte de rastreamento do modelo de serviço `switchValue` :</span><span class="sxs-lookup"><span data-stu-id="c46be-114">In WCF, this can be done by adding the following code to either the service’s or client’s configuration file by setting the Service Model trace source `switchValue`:</span></span>  
  
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
  
 <span data-ttu-id="c46be-115">Para obter mais informações sobre fontes de rastreamento, consulte a seção origem do rastreamento no tópico [Configurando o rastreamento](../diagnostics/tracing/configuring-tracing.md) .</span><span class="sxs-lookup"><span data-stu-id="c46be-115">For more information about trace sources, see the Trace Source section in the [Configuring Tracing](../diagnostics/tracing/configuring-tracing.md) topic.</span></span>  
  
## <a name="activity-tracing-and-propagation"></a><span data-ttu-id="c46be-116">Rastreamento e propagação de atividades</span><span class="sxs-lookup"><span data-stu-id="c46be-116">Activity Tracing and Propagation</span></span>  
 <span data-ttu-id="c46be-117">Ter `ActivityTracing` habilitado e `propagateActivity` definido como `true` nas `system.ServiceModel` fontes de rastreamento para o cliente e o serviço fornecem a correlação de rastreamentos dentro de unidades lógicas de processamento (atividades), entre atividades em pontos de extremidade (por meio de transferências de atividade) e entre atividades que abrangem vários pontos de extremidade (por meio da propagação de ID de atividade).</span><span class="sxs-lookup"><span data-stu-id="c46be-117">Having `ActivityTracing` enabled and `propagateActivity` set to `true` in the `system.ServiceModel` trace sources for both the client and service provide correlation of traces within logical units of processing (activities), across activities within endpoints (through activity transfers), and across activities spanning multiple endpoints (through activity ID propagation).</span></span>  
  
 <span data-ttu-id="c46be-118">Esses três mecanismos (atividades, transferências e propagação) podem ajudá-lo a localizar a causa raiz de um erro mais rapidamente usando a ferramenta do Visualizador de rastreamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="c46be-118">These three mechanisms (activities, transfers, and propagation) can help you locate the root cause of an error more quickly using the Service Trace Viewer tool.</span></span> <span data-ttu-id="c46be-119">Para obter mais informações, consulte [usando o Visualizador de rastreamento de serviço para exibir rastreamentos correlacionados e solução de problemas](../diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="c46be-119">For more information, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="c46be-120">É possível estender o rastreamento fornecido pelo ServiceModel criando rastreamentos de atividade definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="c46be-120">It is possible to extend the tracing that is provided by the ServiceModel by creating user-defined activity traces.</span></span> <span data-ttu-id="c46be-121">O rastreamento de atividade definido pelo usuário permite que o usuário crie atividades de rastreamento para:</span><span class="sxs-lookup"><span data-stu-id="c46be-121">User-defined activity tracing allows the user to create trace activities to:</span></span>  
  
- <span data-ttu-id="c46be-122">Agrupa rastreamentos em unidades lógicas de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c46be-122">Group traces into logical units of work.</span></span>  
  
- <span data-ttu-id="c46be-123">Correlacione atividades por meio de transferências e propagação.</span><span class="sxs-lookup"><span data-stu-id="c46be-123">Correlate activities through transfers and propagation.</span></span>  
  
- <span data-ttu-id="c46be-124">Diminua o custo de desempenho do rastreamento do WCF (por exemplo, o custo de espaço em disco de um arquivo de log).</span><span class="sxs-lookup"><span data-stu-id="c46be-124">Lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
 <span data-ttu-id="c46be-125">Para obter mais informações sobre o rastreamento de atividade definido pelo usuário, consulte o exemplo de [rastreamento de extensão](extending-tracing.md) .</span><span class="sxs-lookup"><span data-stu-id="c46be-125">For more information about user-defined activity trace, please see the [Extending Tracing](extending-tracing.md) sample.</span></span>  
  
## <a name="message-logging"></a><span data-ttu-id="c46be-126">Registro em log de mensagens</span><span class="sxs-lookup"><span data-stu-id="c46be-126">Message Logging</span></span>  
 <span data-ttu-id="c46be-127">O log de mensagens pode ser habilitado no cliente e no serviço de qualquer aplicativo WCF.</span><span class="sxs-lookup"><span data-stu-id="c46be-127">Message logging can be enabled both on the client and service of any WCF application.</span></span> <span data-ttu-id="c46be-128">Para habilitar o log de mensagens, você deve adicionar o seguinte código ao cliente ou ao serviço:</span><span class="sxs-lookup"><span data-stu-id="c46be-128">To enable message logging, you must add the following code to either the client or service:</span></span>  
  
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
  
 <span data-ttu-id="c46be-129">Quando uma mensagem é gravada, o tipo de rastreamento depende se ele está sendo rastreado no cliente ou no servidor.</span><span class="sxs-lookup"><span data-stu-id="c46be-129">When a message is recorded, the trace type depends on whether it is being traced at the client or the server.</span></span> <span data-ttu-id="c46be-130">Por exemplo, uma mensagem "Adicionar" enviada a um cliente é rastreada sob a categoria "TransportWrite" no cliente, enquanto a mesma mensagem é rastreada sob a categoria "TransportRead" no serviço.</span><span class="sxs-lookup"><span data-stu-id="c46be-130">For example, an "Add" message that is sent to a client is traced under the "TransportWrite" category at the client, whereas the same message is traced under the "TransportRead" category at the service.</span></span>  
  
 <span data-ttu-id="c46be-131">Configure o ouvinte de rastreamento adicionando o seguinte código à <xref:System.Diagnostics> seção do arquivo de App.config do cliente ou do arquivo de Web.config do serviço:</span><span class="sxs-lookup"><span data-stu-id="c46be-131">Configure the trace listener by adding the following code to the <xref:System.Diagnostics> section of the client's App.config file or the service's Web.config file:</span></span>  
  
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
  
 <span data-ttu-id="c46be-132">As mensagens são registradas em formato XML no diretório de destino especificado no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="c46be-132">Messages are logged in XML format in the target directory specified in the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c46be-133">Os arquivos de rastreamento não são criados sem criar inicialmente o diretório de log.</span><span class="sxs-lookup"><span data-stu-id="c46be-133">Trace files are not created without initially creating the log directory.</span></span> <span data-ttu-id="c46be-134">Verifique se o diretório C:\logs\ existe ou especifique um diretório de log alternativo na configuração do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="c46be-134">Make sure that the directory C:\logs\ exists, or specify an alternate logging directory in the listener configuration.</span></span> <span data-ttu-id="c46be-135">Consulte as instruções de instalação inicial no final deste documento para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="c46be-135">See the initial setup instructions at the end of this document for more information.</span></span>  
  
 <span data-ttu-id="c46be-136">Para obter mais informações sobre o log de mensagens, consulte o tópico [Configurando o log de mensagens](../diagnostics/configuring-message-logging.md) .</span><span class="sxs-lookup"><span data-stu-id="c46be-136">For more information about message logging, see the [Configuring Message Logging](../diagnostics/configuring-message-logging.md) topic.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c46be-137">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="c46be-137">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c46be-138">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c46be-138">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c46be-139">Antes de executar o rastreamento e o log de mensagens de exemplo, crie o diretório C:\logs\ para o serviço para o qual gravar os arquivos. svclog Connector.</span><span class="sxs-lookup"><span data-stu-id="c46be-139">Before running the Tracing and Message Logging sample, create the directory C:\logs\ for the service to write the .svclog files to.</span></span> <span data-ttu-id="c46be-140">O nome desse diretório é definido no arquivo de configuração como o caminho para os rastreamentos e mensagens a serem registrados e podem ser alterados.</span><span class="sxs-lookup"><span data-stu-id="c46be-140">The name of this directory is defined in the configuration file as the path for the traces and messages to be logged and can be changed.</span></span> <span data-ttu-id="c46be-141">Conceda ao serviço de rede do usuário acesso de gravação ao diretório de logs.</span><span class="sxs-lookup"><span data-stu-id="c46be-141">Give the user Network Service write access to the logs directory.</span></span>  
  
3. <span data-ttu-id="c46be-142">Para criar a edição C#, C++ ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c46be-142">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="c46be-143">Para executar o exemplo em uma configuração de computador único ou entre computadores, siga as instruções em [executando os exemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c46be-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c46be-144">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="c46be-144">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c46be-145">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="c46be-145">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c46be-146">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="c46be-146">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c46be-147">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="c46be-147">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a><span data-ttu-id="c46be-148">Veja também</span><span class="sxs-lookup"><span data-stu-id="c46be-148">See also</span></span>

- [<span data-ttu-id="c46be-149">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="c46be-149">Tracing</span></span>](../diagnostics/tracing/index.md)
- <span data-ttu-id="c46be-150">[AppFabric que monitora Exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="c46be-150">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
