---
title: Registro de mensagem e rastreamento
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: 9ffb7a99540b953fc93a22d2296caf86f294d25d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143818"
---
# <a name="tracing-and-message-logging"></a><span data-ttu-id="21392-102">Registro de mensagem e rastreamento</span><span class="sxs-lookup"><span data-stu-id="21392-102">Tracing and Message Logging</span></span>
<span data-ttu-id="21392-103">Esta amostra demonstra como ativar o rastreamento e o registro de mensagens.</span><span class="sxs-lookup"><span data-stu-id="21392-103">This sample demonstrates how to enable tracing and message logging.</span></span> <span data-ttu-id="21392-104">Os traços e registros de mensagens resultantes são visualizados usando a [Ferramenta de Visualização de Rastreamento de Serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="21392-104">The resulting traces and message logs are viewed using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="21392-105">Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="21392-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="21392-106">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="21392-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="21392-107">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="21392-107">Tracing</span></span>  
 <span data-ttu-id="21392-108">A Windows Communication Foundation (WCF) usa <xref:System.Diagnostics> o mecanismo de rastreamento definido no namespace.</span><span class="sxs-lookup"><span data-stu-id="21392-108">Windows Communication Foundation (WCF) uses the tracing mechanism defined in the <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="21392-109">Neste modelo de rastreamento, os dados de rastreamento são produzidos por fontes de rastreamento que os aplicativos implementam.</span><span class="sxs-lookup"><span data-stu-id="21392-109">In this tracing model, trace data is produced by trace sources that applications implement.</span></span> <span data-ttu-id="21392-110">Cada fonte é identificada por um nome.</span><span class="sxs-lookup"><span data-stu-id="21392-110">Each source is identified by a name.</span></span> <span data-ttu-id="21392-111">Os consumidores de rastreamento criam rastreadores para as fontes de rastreamento para as quais eles querem recuperar informações.</span><span class="sxs-lookup"><span data-stu-id="21392-111">Trace consumers create trace listeners for the trace sources for which they want to retrieve information.</span></span> <span data-ttu-id="21392-112">Para receber dados de rastreamento, você deve criar um ouvinte para a fonte de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="21392-112">To receive trace data, you must create a listener for the trace source.</span></span> <span data-ttu-id="21392-113">No WCF, isso pode ser feito adicionando o seguinte código ao arquivo de configuração `switchValue`do serviço ou do cliente, definindo a fonte de rastreamento do Modelo de Serviço:</span><span class="sxs-lookup"><span data-stu-id="21392-113">In WCF, this can be done by adding the following code to either the service’s or client’s configuration file by setting the Service Model trace source `switchValue`:</span></span>  
  
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
  
 <span data-ttu-id="21392-114">Para obter mais informações sobre as fontes de rastreamento, consulte a seção Trace Source no tópico [Configurando rastreamento.](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="21392-114">For more information about trace sources, see the Trace Source section in the [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) topic.</span></span>  
  
## <a name="activity-tracing-and-propagation"></a><span data-ttu-id="21392-115">Rastreamento e Propagação de Atividades</span><span class="sxs-lookup"><span data-stu-id="21392-115">Activity Tracing and Propagation</span></span>  
 <span data-ttu-id="21392-116">Tendo `ActivityTracing` ativado `propagateActivity` e `true` definido `system.ServiceModel` nas fontes de rastreamento tanto para o cliente quanto para o serviço, fornecem correlação de traços dentro de unidades lógicas de processamento (atividades), em atividades dentro de endpoints (através de transferências de atividades) e em atividades que abrangem vários pontos finais (através da propagação de ID de atividade).</span><span class="sxs-lookup"><span data-stu-id="21392-116">Having `ActivityTracing` enabled and `propagateActivity` set to `true` in the `system.ServiceModel` trace sources for both the client and service provide correlation of traces within logical units of processing (activities), across activities within endpoints (through activity transfers), and across activities spanning multiple endpoints (through activity ID propagation).</span></span>  
  
 <span data-ttu-id="21392-117">Esses três mecanismos (atividades, transferências e propagação) podem ajudá-lo a localizar a causa raiz de um erro mais rapidamente usando a ferramenta Visualizador de rastreamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="21392-117">These three mechanisms (activities, transfers, and propagation) can help you locate the root cause of an error more quickly using the Service Trace Viewer tool.</span></span> <span data-ttu-id="21392-118">Para obter mais informações, consulte [Usando o Visualizador de rastreamento de serviço para visualizar traços correlacionados e solução de problemas](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="21392-118">For more information, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="21392-119">É possível estender o rastreamento fornecido pelo ServiceModel criando traços de atividade definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="21392-119">It is possible to extend the tracing that is provided by the ServiceModel by creating user-defined activity traces.</span></span> <span data-ttu-id="21392-120">O rastreamento de atividades definido pelo usuário permite que o usuário crie atividades de rastreamento para:</span><span class="sxs-lookup"><span data-stu-id="21392-120">User-defined activity tracing allows the user to create trace activities to:</span></span>  
  
- <span data-ttu-id="21392-121">Traços de grupo em unidades lógicas de trabalho.</span><span class="sxs-lookup"><span data-stu-id="21392-121">Group traces into logical units of work.</span></span>  
  
- <span data-ttu-id="21392-122">Correlacionar atividades através de transferências e propagação.</span><span class="sxs-lookup"><span data-stu-id="21392-122">Correlate activities through transfers and propagation.</span></span>  
  
- <span data-ttu-id="21392-123">Diminuir o custo de desempenho do rastreamento WCF (por exemplo, o custo do espaço em disco de um arquivo de log).</span><span class="sxs-lookup"><span data-stu-id="21392-123">Lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
 <span data-ttu-id="21392-124">Para obter mais informações sobre o rastreamento de atividade definido pelo usuário, consulte a amostra [de rastreamento de extensão.](../../../../docs/framework/wcf/samples/extending-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="21392-124">For more information about user-defined activity trace, please see the [Extending Tracing](../../../../docs/framework/wcf/samples/extending-tracing.md) sample.</span></span>  
  
## <a name="message-logging"></a><span data-ttu-id="21392-125">Registro em log de mensagens</span><span class="sxs-lookup"><span data-stu-id="21392-125">Message Logging</span></span>  
 <span data-ttu-id="21392-126">O registro de mensagens pode ser ativado tanto no cliente quanto no serviço de qualquer aplicativo WCF.</span><span class="sxs-lookup"><span data-stu-id="21392-126">Message logging can be enabled both on the client and service of any WCF application.</span></span> <span data-ttu-id="21392-127">Para habilitar o registro de mensagens, você deve adicionar o seguinte código ao cliente ou ao serviço:</span><span class="sxs-lookup"><span data-stu-id="21392-127">To enable message logging, you must add the following code to either the client or service:</span></span>  
  
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
  
 <span data-ttu-id="21392-128">Quando uma mensagem é gravada, o tipo de rastreamento depende se ela está sendo rastreada no cliente ou no servidor.</span><span class="sxs-lookup"><span data-stu-id="21392-128">When a message is recorded, the trace type depends on whether it is being traced at the client or the server.</span></span> <span data-ttu-id="21392-129">Por exemplo, uma mensagem "Adicionar" enviada a um cliente é rastreada na categoria "TransportWrite" no cliente, enquanto a mesma mensagem é rastreada na categoria "TransportRead" no serviço.</span><span class="sxs-lookup"><span data-stu-id="21392-129">For example, an "Add" message that is sent to a client is traced under the "TransportWrite" category at the client, whereas the same message is traced under the "TransportRead" category at the service.</span></span>  
  
 <span data-ttu-id="21392-130">Configure o ouvinte de rastreamento adicionando <xref:System.Diagnostics> o seguinte código à seção do arquivo App.config do cliente ou ao arquivo Web.config do serviço:</span><span class="sxs-lookup"><span data-stu-id="21392-130">Configure the trace listener by adding the following code to the <xref:System.Diagnostics> section of the client's App.config file or the service's Web.config file:</span></span>  
  
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
  
 <span data-ttu-id="21392-131">As mensagens são registradas no formato XML no diretório de destino especificado no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="21392-131">Messages are logged in XML format in the target directory specified in the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="21392-132">Os arquivos trace não são criados sem criar inicialmente o diretório de log.</span><span class="sxs-lookup"><span data-stu-id="21392-132">Trace files are not created without initially creating the log directory.</span></span> <span data-ttu-id="21392-133">Certifique-se de que o diretório C:\logs\ existe ou especifique um diretório de registro alternativo na configuração do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="21392-133">Make sure that the directory C:\logs\ exists, or specify an alternate logging directory in the listener configuration.</span></span> <span data-ttu-id="21392-134">Consulte as instruções iniciais de configuração no final deste documento para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="21392-134">See the initial setup instructions at the end of this document for more information.</span></span>  
  
 <span data-ttu-id="21392-135">Para obter mais informações sobre o registro de mensagens, consulte o tópico [Configurando registro de mensagens.](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)</span><span class="sxs-lookup"><span data-stu-id="21392-135">For more information about message logging, see the [Configuring Message Logging](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) topic.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="21392-136">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="21392-136">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="21392-137">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="21392-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="21392-138">Antes de executar a amostra De rastreamento e registro de mensagens, crie o diretório C:\logs\ para que o serviço escreva os arquivos .svclog para.</span><span class="sxs-lookup"><span data-stu-id="21392-138">Before running the Tracing and Message Logging sample, create the directory C:\logs\ for the service to write the .svclog files to.</span></span> <span data-ttu-id="21392-139">O nome deste diretório é definido no arquivo de configuração como o caminho para que os traços e mensagens sejam registrados e possam ser alterados.</span><span class="sxs-lookup"><span data-stu-id="21392-139">The name of this directory is defined in the configuration file as the path for the traces and messages to be logged and can be changed.</span></span> <span data-ttu-id="21392-140">Dê ao usuário Network Service para gravar acesso ao diretório de logs.</span><span class="sxs-lookup"><span data-stu-id="21392-140">Give the user Network Service write access to the logs directory.</span></span>  
  
3. <span data-ttu-id="21392-141">Para construir a edição C#, C++ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="21392-141">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="21392-142">Para executar a amostra em uma configuração de computador único ou cruzado, siga as instruções em [Executar as amostras da Fundação](../../../../docs/framework/wcf/samples/running-the-samples.md)de Comunicação do Windows .</span><span class="sxs-lookup"><span data-stu-id="21392-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="21392-143">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="21392-143">The samples may already be installed on your computer.</span></span> <span data-ttu-id="21392-144">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="21392-144">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="21392-145">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="21392-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="21392-146">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="21392-146">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a><span data-ttu-id="21392-147">Confira também</span><span class="sxs-lookup"><span data-stu-id="21392-147">See also</span></span>

- [<span data-ttu-id="21392-148">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="21392-148">Tracing</span></span>](../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- <span data-ttu-id="21392-149">[AppFabric que monitora Exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="21392-149">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
