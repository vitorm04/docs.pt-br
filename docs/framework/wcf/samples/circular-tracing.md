---
title: Rastreamento circular
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 21a455c0fcb7a6b4164da6f7fdc7efaa007273ae
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="circular-tracing"></a><span data-ttu-id="8ac28-102">Rastreamento circular</span><span class="sxs-lookup"><span data-stu-id="8ac28-102">Circular Tracing</span></span>
<span data-ttu-id="8ac28-103">Este exemplo demonstra a implementação de um ouvinte de rastreamento de buffer circular.</span><span class="sxs-lookup"><span data-stu-id="8ac28-103">This sample demonstrates the implementation of a circular buffer trace listener.</span></span> <span data-ttu-id="8ac28-104">Um cenário comum para serviços de produção é ter os serviços que estão disponíveis por longos períodos de tempo e ter o log de rastreamento habilitado em um nível baixo.</span><span class="sxs-lookup"><span data-stu-id="8ac28-104">A common scenario for production services is to have services that are available for long periods of time and to have trace logging enabled at a low level.</span></span> <span data-ttu-id="8ac28-105">Esses serviços consumam muito espaço em disco.</span><span class="sxs-lookup"><span data-stu-id="8ac28-105">These services consume a lot of disk space.</span></span> <span data-ttu-id="8ac28-106">Ao solucionar problemas de um serviço, os dados mais recentes no log de rastreamento são relevantes para resolver um problema.</span><span class="sxs-lookup"><span data-stu-id="8ac28-106">When troubleshooting a service, the most recent data in the trace log is relevant to solving a problem.</span></span> <span data-ttu-id="8ac28-107">Este exemplo demonstra uma implementação de um ouvinte de rastreamento de buffer circular na qual somente os rastreamentos mais recentes são mantidos no disco até um período configurável de dados.</span><span class="sxs-lookup"><span data-stu-id="8ac28-107">This sample demonstrates an implementation of a circular buffer trace listener in which only the most recent traces are kept on disk up to a configurable amount of data.</span></span> <span data-ttu-id="8ac28-108">Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) e inclui um ouvinte de rastreamento personalizada.</span><span class="sxs-lookup"><span data-stu-id="8ac28-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and includes a custom tracing listener.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ac28-109">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="8ac28-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="8ac28-110">Este exemplo pressupõe que você esteja familiarizado com o [rastreamento e registro em log de mensagem](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) de exemplo e leu a documentação fornecida para o [rastreamento e registro em log de mensagem](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="8ac28-110">This sample assumes that you are familiar with the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample and have read the documentation provided for the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample.</span></span>  
  
## <a name="circular-buffer-trace-listener"></a><span data-ttu-id="8ac28-111">Ouvinte de rastreamento de Buffer circular</span><span class="sxs-lookup"><span data-stu-id="8ac28-111">Circular Buffer Trace Listener</span></span>  
 <span data-ttu-id="8ac28-112">O conceito inerente a implementação do ouvinte de rastreamento de Buffer Circular é ter dois arquivos de que cada uma podem armazenar até a metade dos dados do log de rastreamento desejado total.</span><span class="sxs-lookup"><span data-stu-id="8ac28-112">The concept behind the implementation of the Circular Buffer Trace Listener is to have two files that can each store up to half of the total desired trace log data.</span></span> <span data-ttu-id="8ac28-113">O ouvinte cria um arquivo e grava no arquivo até atingir o limite de metade do tamanho dos dados, no ponto em que alterna um segundo arquivo.</span><span class="sxs-lookup"><span data-stu-id="8ac28-113">The listener creates one file and writes to that file until it reaches the limit of half of the data size, at which point it switches to a second file.</span></span> <span data-ttu-id="8ac28-114">Quando o ouvinte atinge o limite para o segundo arquivo - ele substitui o primeiro arquivo com novos rastreamentos.</span><span class="sxs-lookup"><span data-stu-id="8ac28-114">When the listener reaches the limit for the second file - it overwrites the first file with new traces.</span></span>  
  
 <span data-ttu-id="8ac28-115">Este ouvinte deriva o `XmlWriteTraceListener` e permite que os logs sejam exibidos com o [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="8ac28-115">This listener derives from the `XmlWriteTraceListener` and allows the logs to be viewed with the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="8ac28-116">Ao tentar exibir os logs, os dois arquivos de log podem facilmente recombined abrindo ambos os arquivos de log ao mesmo tempo em que a ferramenta do Visualizador de rastreamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="8ac28-116">When attempting to view the logs, the two log files can be easily recombined by opening both of the log files at the same time in the Service Trace Viewer tool.</span></span> <span data-ttu-id="8ac28-117">A ferramenta do Visualizador de rastreamento de serviço automaticamente cuida de classificação, os rastreamentos para que apareçam na ordem correta.</span><span class="sxs-lookup"><span data-stu-id="8ac28-117">The Service Trace Viewer tool automatically takes care of sorting the traces so that they appear in the correct order.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="8ac28-118">Configuração</span><span class="sxs-lookup"><span data-stu-id="8ac28-118">Configuration</span></span>  
 <span data-ttu-id="8ac28-119">Um serviço pode ser configurado para usar o ouvinte de rastreamento de Buffer Circular, adicionando o código a seguir para elementos do ouvinte e fonte.</span><span class="sxs-lookup"><span data-stu-id="8ac28-119">A service can be configured to use the Circular Buffer Trace Listener by adding the following code for a listener and source elements.</span></span> <span data-ttu-id="8ac28-120">O tamanho máximo de arquivo é especificado pela configuração de `maxFileSizeKB` atributo na configuração do ouvinte de rastreamento circular.</span><span class="sxs-lookup"><span data-stu-id="8ac28-120">The max file size is specified by setting the `maxFileSizeKB` attribute in the circular trace listener's configuration.</span></span> <span data-ttu-id="8ac28-121">Isso é demonstrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="8ac28-121">This is demonstrated in the following code.</span></span>  
  
```xml  
<system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel" switchValue="Information,ActivityTracing" propagateActivity="true">  
      <listeners>  
        <add name="CircularTraceListener" />  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="CircularTraceListener" type="Microsoft. Samples.ServiceModel.CircularTraceListener,CircularTraceListener"   
         initializeData="c:\logs\CircularTracing-service.svclog" maxFileSizeKB="100" />  
  </sharedListeners>  
  <trace autoflush="true" />  
</system.diagnostics>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8ac28-122">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="8ac28-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="8ac28-123">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8ac28-123">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="8ac28-124">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8ac28-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="8ac28-125">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8ac28-125">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8ac28-126">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="8ac28-126">The samples may already be installed on your computer.</span></span> <span data-ttu-id="8ac28-127">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="8ac28-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8ac28-128">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="8ac28-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8ac28-129">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="8ac28-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`  
  
## <a name="see-also"></a><span data-ttu-id="8ac28-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ac28-130">See Also</span></span>  
 [<span data-ttu-id="8ac28-131">Exemplos de monitoramento do AppFabric</span><span class="sxs-lookup"><span data-stu-id="8ac28-131">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
