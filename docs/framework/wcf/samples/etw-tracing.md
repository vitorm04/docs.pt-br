---
title: Rastreamento ETW
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
caps.latest.revision: "42"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 39164d6334be40de86f422e2faa4debf1d4f31f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="etw-tracing"></a><span data-ttu-id="bf9e4-102">Rastreamento ETW</span><span class="sxs-lookup"><span data-stu-id="bf9e4-102">ETW Tracing</span></span>
<span data-ttu-id="bf9e4-103">Este exemplo demonstra como implementar o rastreamento de ponta a ponta (E2E) usando o rastreamento de eventos para Windows (ETW) e o `ETWTraceListener` que é fornecido com este exemplo.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-103">This sample demonstrates how to implement End-to-End (E2E) tracing using Event Tracing for Windows (ETW) and the `ETWTraceListener` that is provided with this sample.</span></span> <span data-ttu-id="bf9e4-104">O exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) e inclui o rastreamento ETW.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and includes ETW tracing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf9e4-105">Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-105">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="bf9e4-106">Este exemplo pressupõe que você esteja familiarizado com [rastreamento e registro em log de mensagem](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="bf9e4-106">This sample assumes that you are familiar with [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="bf9e4-107">Cada origem de rastreamento no <xref:System.Diagnostics> modelo de rastreamento pode ter vários ouvintes de rastreamento que determinam onde e como os dados são rastreados.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-107">Each trace source in the <xref:System.Diagnostics> tracing model can have multiple trace listeners that determine where and how the data is traced.</span></span> <span data-ttu-id="bf9e4-108">O tipo de ouvinte define o formato no qual os dados de rastreamento serão registrados.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-108">The type of listener defines the format in which trace data is logged.</span></span> <span data-ttu-id="bf9e4-109">O exemplo de código a seguir mostra como adicionar o ouvinte para a configuração.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-109">The following code sample shows how to add the listener to configuration.</span></span>  
  
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
  
 <span data-ttu-id="bf9e4-110">Antes de usar este ouvinte, uma sessão de rastreamento ETW deve ser iniciada.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-110">Before using this listener, an ETW Trace Session must be started.</span></span> <span data-ttu-id="bf9e4-111">Essa sessão pode ser iniciada usando Logman.exe ou Tracelog.exe.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-111">This session can be started by using Logman.exe or Tracelog.exe.</span></span> <span data-ttu-id="bf9e4-112">Um arquivo de SetupETW.bat é incluído com este exemplo, para que você pode configurar a sessão de rastreamento ETW junto com um arquivo CleanupETW.bat para fechar a sessão e concluir o arquivo de log.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-112">A SetupETW.bat file is included with this sample so that you can set up the ETW Trace Session along with a CleanupETW.bat file for closing the session and completing the log file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf9e4-113">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span> <span data-ttu-id="bf9e4-114">Para obter mais informações sobre essas ferramentas, consulte [http://go.microsoft.com/fwlink/?LinkId=56580](http://go.microsoft.com/fwlink/?LinkId=56580)</span><span class="sxs-lookup"><span data-stu-id="bf9e4-114">For more information about these tools, see [http://go.microsoft.com/fwlink/?LinkId=56580](http://go.microsoft.com/fwlink/?LinkId=56580)</span></span>  
  
 <span data-ttu-id="bf9e4-115">Ao usar o ETWTraceListener, os rastreamentos serão registrados em arquivos. etl binário.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-115">When using the ETWTraceListener, traces are logged in binary .etl files.</span></span> <span data-ttu-id="bf9e4-116">Com o rastreamento de ServiceModel ativado, todos os rastreamentos gerados aparecem no mesmo arquivo.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-116">With ServiceModel tracing turned on, all generated traces appear in the same file.</span></span> <span data-ttu-id="bf9e4-117">Use [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) para exibir os arquivos de log. etl e .svclog.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-117">Use [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) for viewing .etl and .svclog log files.</span></span> <span data-ttu-id="bf9e4-118">O Visualizador de cria uma exibição de ponta a ponta do sistema que torna possível rastrear uma mensagem de sua origem para o destino e o ponto de consumo.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-118">The viewer creates an end-to-end view of the system that makes it possible to trace a message from its source to its destination and point of consumption.</span></span>  
  
 <span data-ttu-id="bf9e4-119">O ouvinte de rastreamento ETW oferece suporte ao registro em log circular.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-119">The ETW Trace Listener supports circular logging.</span></span> <span data-ttu-id="bf9e4-120">Para habilitar esse recurso, vá para **iniciar**, **executar** e tipo `cmd` para iniciar o console de comando.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-120">To enable this feature, go to **Start**, **Run** and type `cmd` to start a command console.</span></span> <span data-ttu-id="bf9e4-121">No comando a seguir, substitua o `<logfilename>` parâmetro com o nome do seu arquivo de log.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-121">In the following command, replace the `<logfilename>` parameter with the name of your log file.</span></span>  
  
```  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 <span data-ttu-id="bf9e4-122">O `-f` e `-max` switches são opcionais.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-122">The `-f` and `-max` switches are optional.</span></span> <span data-ttu-id="bf9e4-123">Eles especificam o formato circular binário e o tamanho de log máximo de 1000MB respectivamente.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-123">They specify the binary circular format and max log size of 1000MB respectively.</span></span> <span data-ttu-id="bf9e4-124">O `-p` switch é usada para especificar o provedor de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-124">The `-p` switch is used to specify the trace provider.</span></span> <span data-ttu-id="bf9e4-125">Em nosso exemplo, `"{411a0819-c24b-428c-83e2-26b41091702e}"` é o GUID "Provedor de exemplo do XML ETW".</span><span class="sxs-lookup"><span data-stu-id="bf9e4-125">In our example, `"{411a0819-c24b-428c-83e2-26b41091702e}"` is the GUID for "XML ETW Sample Provider".</span></span>  
  
 <span data-ttu-id="bf9e4-126">Para iniciar a sessão, digite o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-126">To start the session, type in the following command.</span></span>  
  
```  
Logman start Wcf  
```  
  
 <span data-ttu-id="bf9e4-127">Depois de concluir o registro em log, você pode parar a sessão com o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-127">After you have finished logging, you can stop the session with the following command.</span></span>  
  
```  
Logman stop Wcf  
```  
  
 <span data-ttu-id="bf9e4-128">Esse processo gera logs circulares binários que você pode processar com a ferramenta de sua escolha, incluindo [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) ou Tracerpt.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-128">This process generates binary circular logs that you can process with your tool of choice, including [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) or Tracerpt.</span></span>  
  
 <span data-ttu-id="bf9e4-129">Você também pode examinar o [rastreamento Circular](../../../../docs/framework/wcf/samples/circular-tracing.md) exemplo para obter mais informações sobre um ouvinte alternativa para executar o log circular.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-129">You can also review the [Circular Tracing](../../../../docs/framework/wcf/samples/circular-tracing.md) sample for more information on an alternative listener to perform circular logging.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bf9e4-130">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="bf9e4-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="bf9e4-131">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bf9e4-131">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="bf9e4-132">Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bf9e4-132">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bf9e4-133">Para usar os comandos RegisterProvider.bat, SetupETW.bat e CleanupETW.bat, você deve executar sob uma conta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-133">To use the RegisterProvider.bat, SetupETW.bat and CleanupETW.bat commands, you must run under a local administrator account.</span></span> <span data-ttu-id="bf9e4-134">Se você estiver usando [!INCLUDE[wv](../../../../includes/wv-md.md)] ou posterior, você também deve executar o prompt de comando com privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-134">If you are using [!INCLUDE[wv](../../../../includes/wv-md.md)] or later, you must also run the command prompt with elevated privileges.</span></span> <span data-ttu-id="bf9e4-135">Para fazer isso, clique no ícone de prompt de comando, clique em **executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-135">To do so, right-click the command prompt icon, then click **Run as administrator**.</span></span>  
  
3.  <span data-ttu-id="bf9e4-136">Antes de executar o exemplo, execute RegisterProvider.bat no cliente e no servidor.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-136">Before running the sample, run RegisterProvider.bat on the client and server.</span></span> <span data-ttu-id="bf9e4-137">Isso configura o arquivo ETWTracingSampleLog.etl resultante para gerar rastreamentos podem ser lidos pelo Visualizador de rastreamento do serviço.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-137">This sets up the resulting ETWTracingSampleLog.etl file to generate traces that can be read by the Service Trace Viewer.</span></span> <span data-ttu-id="bf9e4-138">Esse arquivo pode ser encontrado na pasta c:\Logs.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-138">This file can be found in the C:\logs folder.</span></span> <span data-ttu-id="bf9e4-139">Se essa pasta não existir, ele deve ser criado ou nenhum rastreamento é gerado.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-139">If this folder does not exist, it must be created or no traces are generated.</span></span> <span data-ttu-id="bf9e4-140">Em seguida, execute SetupETW.bat nos computadores cliente e servidor para iniciar a sessão de rastreamento ETW.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-140">Then, run SetupETW.bat on the client and server computers to begin the ETW Trace Session.</span></span> <span data-ttu-id="bf9e4-141">O arquivo SetupETW.bat pode ser encontrado na pasta CS\Client.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-141">The SetupETW.bat file can be found under the CS\Client folder.</span></span>  
  
4.  <span data-ttu-id="bf9e4-142">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bf9e4-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="bf9e4-143">Quando o exemplo for concluído, execute CleanupETW.bat para concluir a criação do arquivo ETWTracingSampleLog.etl.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-143">When the sample is completed, run CleanupETW.bat to complete the creation of the ETWTracingSampleLog.etl file.</span></span>  
  
6.  <span data-ttu-id="bf9e4-144">Abra o arquivo de ETWTracingSampleLog.etl de dentro do Visualizador de rastreamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-144">Open the ETWTracingSampleLog.etl file from within the Service Trace Viewer.</span></span> <span data-ttu-id="bf9e4-145">Você será solicitado a salvar o arquivo com formato binário como um arquivo de .svclog.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-145">You will be prompted to save the binary formatted file as a .svclog file.</span></span>  
  
7.  <span data-ttu-id="bf9e4-146">Abra o arquivo recém-criado .svclog de dentro do Visualizador de rastreamento de serviço para exibir os rastreamentos ETW e ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-146">Open the newly created .svclog file from within the Service Trace Viewer to view the ETW and ServiceModel traces.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bf9e4-147">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-147">The samples may already be installed on your computer.</span></span> <span data-ttu-id="bf9e4-148">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-148">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bf9e4-149">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bf9e4-150">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="bf9e4-150">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a><span data-ttu-id="bf9e4-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf9e4-151">See Also</span></span>  
 [<span data-ttu-id="bf9e4-152">Exemplos de monitoramento do AppFabric</span><span class="sxs-lookup"><span data-stu-id="bf9e4-152">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
