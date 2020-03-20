---
title: Rastreamento ETW
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: 07379a464e6635a3de10c08647dbc769a5885e4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183697"
---
# <a name="etw-tracing"></a><span data-ttu-id="5a5cd-102">Rastreamento ETW</span><span class="sxs-lookup"><span data-stu-id="5a5cd-102">ETW Tracing</span></span>
<span data-ttu-id="5a5cd-103">Esta amostra demonstra como implementar o rastreamento End-to-End (E2E) usando o ETW de eventos para Windows (ETW) e o `ETWTraceListener` que é fornecido com esta amostra.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-103">This sample demonstrates how to implement End-to-End (E2E) tracing using Event Tracing for Windows (ETW) and the `ETWTraceListener` that is provided with this sample.</span></span> <span data-ttu-id="5a5cd-104">A amostra é baseada no [Rastreamento e](../../../../docs/framework/wcf/samples/getting-started-sample.md) inclui rastreamento ETW.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and includes ETW tracing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5a5cd-105">Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-105">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5a5cd-106">Esta amostra assume que você está familiarizado com [rastreamento e registro de mensagens](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="5a5cd-106">This sample assumes that you are familiar with [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="5a5cd-107">Cada fonte de <xref:System.Diagnostics> rastreamento no modelo de rastreamento pode ter vários ouvintes de rastreamento que determinam onde e como os dados são rastreados.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-107">Each trace source in the <xref:System.Diagnostics> tracing model can have multiple trace listeners that determine where and how the data is traced.</span></span> <span data-ttu-id="5a5cd-108">O tipo de ouvinte define o formato no qual os dados de rastreamento são registrados.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-108">The type of listener defines the format in which trace data is logged.</span></span> <span data-ttu-id="5a5cd-109">A amostra de código a seguir mostra como adicionar o ouvinte à configuração.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-109">The following code sample shows how to add the listener to configuration.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel"
             switchValue="Verbose,ActivityTracing"  
             propagateActivity="true">  
            <listeners>  
                <add type=  
                   "System.Diagnostics.DefaultTraceListener"  
                   name="Default">  
                   <filter type="" />  
                </add>  
                <add name="ETW">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
        <add type=  
            "Microsoft.ServiceModel.Samples.EtwTraceListener, ETWTraceListener"  
            name="ETW" traceOutputOptions="Timestamp">  
            <filter type="" />  
       </add>  
    </sharedListeners>  
</system.diagnostics>  
```  
  
 <span data-ttu-id="5a5cd-110">Antes de usar este ouvinte, uma Sessão de Rastreamento eTW deve ser iniciada.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-110">Before using this listener, an ETW Trace Session must be started.</span></span> <span data-ttu-id="5a5cd-111">Esta sessão pode ser iniciada usando Logman.exe ou Tracelog.exe.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-111">This session can be started by using Logman.exe or Tracelog.exe.</span></span> <span data-ttu-id="5a5cd-112">Um arquivo SetupETW.bat está incluído nesta amostra para que você possa configurar a Sessão de Rastreamento eTW juntamente com um arquivo CleanupETW.bat para encerrar a sessão e completar o arquivo de log.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-112">A SetupETW.bat file is included with this sample so that you can set up the ETW Trace Session along with a CleanupETW.bat file for closing the session and completing the log file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5a5cd-113">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span> <span data-ttu-id="5a5cd-114">Para obter mais informações sobre essas ferramentas, consulte<https://go.microsoft.com/fwlink/?LinkId=56580></span><span class="sxs-lookup"><span data-stu-id="5a5cd-114">For more information about these tools, see <https://go.microsoft.com/fwlink/?LinkId=56580></span></span>  
  
 <span data-ttu-id="5a5cd-115">Ao usar o ETWTraceListener, os rastreamentos são registrados em arquivos binários .etl.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-115">When using the ETWTraceListener, traces are logged in binary .etl files.</span></span> <span data-ttu-id="5a5cd-116">Com o rastreamento servicemodel ligado, todos os traços gerados aparecem no mesmo arquivo.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-116">With ServiceModel tracing turned on, all generated traces appear in the same file.</span></span> <span data-ttu-id="5a5cd-117">Use [a Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) para visualizar arquivos de log .etl e .svclog.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-117">Use [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) for viewing .etl and .svclog log files.</span></span> <span data-ttu-id="5a5cd-118">O espectador cria uma visão de ponta a ponta do sistema que torna possível rastrear uma mensagem de sua fonte até seu destino e ponto de consumo.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-118">The viewer creates an end-to-end view of the system that makes it possible to trace a message from its source to its destination and point of consumption.</span></span>  
  
 <span data-ttu-id="5a5cd-119">O ETW Trace Listener suporta registro circular.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-119">The ETW Trace Listener supports circular logging.</span></span> <span data-ttu-id="5a5cd-120">Para habilitar esse recurso, vá `cmd` para **Iniciar**, **Executar** e digite para iniciar um console de comando.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-120">To enable this feature, go to **Start**, **Run** and type `cmd` to start a command console.</span></span> <span data-ttu-id="5a5cd-121">No comando a seguir, substitua o `<logfilename>` parâmetro pelo nome do seu arquivo de log.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-121">In the following command, replace the `<logfilename>` parameter with the name of your log file.</span></span>  
  
```console  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 <span data-ttu-id="5a5cd-122">Os `-f` `-max` interruptores são opcionais.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-122">The `-f` and `-max` switches are optional.</span></span> <span data-ttu-id="5a5cd-123">Eles especificam o formato circular binário e o tamanho máximo do log de 1000MB, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-123">They specify the binary circular format and max log size of 1000MB respectively.</span></span> <span data-ttu-id="5a5cd-124">O `-p` switch é usado para especificar o provedor de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-124">The `-p` switch is used to specify the trace provider.</span></span> <span data-ttu-id="5a5cd-125">Em nosso `"{411a0819-c24b-428c-83e2-26b41091702e}"` exemplo, está o GUID para "Provedor de Amostra de ETW XML".</span><span class="sxs-lookup"><span data-stu-id="5a5cd-125">In our example, `"{411a0819-c24b-428c-83e2-26b41091702e}"` is the GUID for "XML ETW Sample Provider".</span></span>  
  
 <span data-ttu-id="5a5cd-126">Para iniciar a sessão, digite o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-126">To start the session, type in the following command.</span></span>  
  
```console  
logman start Wcf  
```  
  
 <span data-ttu-id="5a5cd-127">Depois de terminar o registro, você pode interromper a sessão com o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-127">After you have finished logging, you can stop the session with the following command.</span></span>  
  
```console  
logman stop Wcf  
```  
  
 <span data-ttu-id="5a5cd-128">Esse processo gera registros circulares binários que você pode processar com sua ferramenta de escolha, incluindo [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) ou Tracerpt.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-128">This process generates binary circular logs that you can process with your tool of choice, including [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) or Tracerpt.</span></span>  
  
 <span data-ttu-id="5a5cd-129">Você também pode rever a amostra [de Rastreamento Circular](../../../../docs/framework/wcf/samples/circular-tracing.md) para obter mais informações sobre um ouvinte alternativo para realizar o registro circular.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-129">You can also review the [Circular Tracing](../../../../docs/framework/wcf/samples/circular-tracing.md) sample for more information on an alternative listener to perform circular logging.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5a5cd-130">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5cd-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5a5cd-131">Certifique-se de ter realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5a5cd-131">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5a5cd-132">Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5a5cd-132">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5a5cd-133">Para usar os comandos RegisterProvider.bat, SetupETW.bat e CleanupETW.bat, você deve ser executado uma conta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-133">To use the RegisterProvider.bat, SetupETW.bat and CleanupETW.bat commands, you must run under a local administrator account.</span></span> <span data-ttu-id="5a5cd-134">Se você estiver usando o Windows Vista ou posteriormente, você também deve executar o prompt de comando com privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-134">If you are using Windows Vista or later, you must also run the command prompt with elevated privileges.</span></span> <span data-ttu-id="5a5cd-135">Para isso, clique com o botão direito do mouse no ícone de solicitação de comando e clique **em Executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-135">To do so, right-click the command prompt icon, then click **Run as administrator**.</span></span>  
  
3. <span data-ttu-id="5a5cd-136">Antes de executar a amostra, execute RegisterProvider.bat no cliente e no servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-136">Before running the sample, run RegisterProvider.bat on the client and server.</span></span> <span data-ttu-id="5a5cd-137">Isso configura o arquivo ETWTracingSampleLog.etl resultante para gerar vestígios que podem ser lidos pelo Visualizador de rastreamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-137">This sets up the resulting ETWTracingSampleLog.etl file to generate traces that can be read by the Service Trace Viewer.</span></span> <span data-ttu-id="5a5cd-138">Este arquivo pode ser encontrado na pasta C:\logs.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-138">This file can be found in the C:\logs folder.</span></span> <span data-ttu-id="5a5cd-139">Se essa pasta não existir, ela deve ser criada ou não são gerados vestígios.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-139">If this folder does not exist, it must be created or no traces are generated.</span></span> <span data-ttu-id="5a5cd-140">Em seguida, execute setupETW.bat nos computadores cliente e servidor para iniciar a Sessão de Rastreamento eTW.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-140">Then, run SetupETW.bat on the client and server computers to begin the ETW Trace Session.</span></span> <span data-ttu-id="5a5cd-141">O arquivo SetupETW.bat pode ser encontrado na pasta CS\Client.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-141">The SetupETW.bat file can be found under the CS\Client folder.</span></span>  
  
4. <span data-ttu-id="5a5cd-142">Para executar a amostra em uma configuração de computador único ou cruzado, siga as instruções em [Executar as amostras da Fundação](../../../../docs/framework/wcf/samples/running-the-samples.md)de Comunicação do Windows .</span><span class="sxs-lookup"><span data-stu-id="5a5cd-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="5a5cd-143">Quando a amostra estiver concluída, execute CleanupETW.bat para concluir a criação do arquivo ETWTracingSampleLog.etl.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-143">When the sample is completed, run CleanupETW.bat to complete the creation of the ETWTracingSampleLog.etl file.</span></span>  
  
6. <span data-ttu-id="5a5cd-144">Abra o arquivo ETWTracingSampleLog.etl a partir do Visualizador de rastreamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-144">Open the ETWTracingSampleLog.etl file from within the Service Trace Viewer.</span></span> <span data-ttu-id="5a5cd-145">Você será solicitado a salvar o arquivo formatado binário como um arquivo .svclog.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-145">You will be prompted to save the binary formatted file as a .svclog file.</span></span>  
  
7. <span data-ttu-id="5a5cd-146">Abra o arquivo .svclog recém-criado dentro do Service Trace Viewer para visualizar os traços ETW e ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-146">Open the newly created .svclog file from within the Service Trace Viewer to view the ETW and ServiceModel traces.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5a5cd-147">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-147">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5a5cd-148">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-148">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5a5cd-149">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="5a5cd-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5a5cd-150">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="5a5cd-150">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a><span data-ttu-id="5a5cd-151">Confira também</span><span class="sxs-lookup"><span data-stu-id="5a5cd-151">See also</span></span>

- <span data-ttu-id="5a5cd-152">[AppFabric que monitora Exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="5a5cd-152">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
