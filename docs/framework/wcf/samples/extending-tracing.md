---
title: Estendendo rastreamento
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: a7231d340d2528a42c8cbb5294d812d52db92d54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183683"
---
# <a name="extending-tracing"></a><span data-ttu-id="6b00e-102">Estendendo rastreamento</span><span class="sxs-lookup"><span data-stu-id="6b00e-102">Extending Tracing</span></span>
<span data-ttu-id="6b00e-103">Esta amostra demonstra como estender o recurso de rastreamento da Windows Communication Foundation (WCF) escrevendo traços de atividade definidos pelo usuário no código de cliente e serviço.</span><span class="sxs-lookup"><span data-stu-id="6b00e-103">This sample demonstrates how to extend the Windows Communication Foundation (WCF) tracing feature by writing user-defined activity traces in client and service code.</span></span> <span data-ttu-id="6b00e-104">Isso permite que o usuário crie atividades de rastreamento e rastreamentos em unidades lógicas de trabalho.</span><span class="sxs-lookup"><span data-stu-id="6b00e-104">This allows the user to create trace activities and group traces into logical units of work.</span></span> <span data-ttu-id="6b00e-105">Também é possível correlacionar atividades através de transferências (dentro do mesmo ponto final) e propagação (entre os pontos finais).</span><span class="sxs-lookup"><span data-stu-id="6b00e-105">It is also possible to correlate activities through transfers (within the same endpoint) and propagation (across endpoints).</span></span> <span data-ttu-id="6b00e-106">Nesta amostra, o rastreamento é habilitado tanto para o cliente quanto para o serviço.</span><span class="sxs-lookup"><span data-stu-id="6b00e-106">In this sample, tracing is enabled for both the client and the service.</span></span> <span data-ttu-id="6b00e-107">Para obter mais informações sobre como ativar o rastreamento em arquivos de configuração de clientes e serviços, consulte [Rastreamento e Registro de Mensagens](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="6b00e-107">For more information about how to enable tracing in client and service configuration files, see [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="6b00e-108">Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="6b00e-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6b00e-109">Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="6b00e-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6b00e-110">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="6b00e-110">The samples may already be installed on your computer.</span></span> <span data-ttu-id="6b00e-111">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="6b00e-111">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="6b00e-112">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="6b00e-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6b00e-113">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="6b00e-113">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a><span data-ttu-id="6b00e-114">Rastreamento e Propagação de Atividades</span><span class="sxs-lookup"><span data-stu-id="6b00e-114">Tracing and Activity Propagation</span></span>  
 <span data-ttu-id="6b00e-115">O rastreamento de atividades definido pelo usuário permite que o usuário crie suas próprias atividades de rastreamento para agrupar vestígios em unidades lógicas de trabalho, correlacionar atividades por meio de transferências e propagação e diminuir o custo de desempenho do rastreamento do WCF (por exemplo, o custo do espaço em disco de um arquivo de registro).</span><span class="sxs-lookup"><span data-stu-id="6b00e-115">User-defined activity tracing allows the user to create their own trace activities to group traces into logical units of work, correlate activities through transfers and propagation, and lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
### <a name="adding-custom-sources"></a><span data-ttu-id="6b00e-116">Adicionando fontes personalizadas</span><span class="sxs-lookup"><span data-stu-id="6b00e-116">Adding Custom Sources</span></span>  
 <span data-ttu-id="6b00e-117">Os traços definidos pelo usuário podem ser adicionados ao código de cliente e de serviço.</span><span class="sxs-lookup"><span data-stu-id="6b00e-117">User-defined traces can be added to both client and service code.</span></span> <span data-ttu-id="6b00e-118">A adição de fontes de rastreamento aos arquivos de configuração do cliente ou de serviço permite que esses rastreamentos personalizados sejam gravados e exibidos na [Ferramenta de Visualização de Rastreamento de Serviço (SvcTraceViewer.exe).](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)</span><span class="sxs-lookup"><span data-stu-id="6b00e-118">Adding trace sources to the client or service configuration files allow for these custom traces to be recorded and displayed in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="6b00e-119">O código a seguir mostra como adicionar `ServerCalculatorTraceSource` uma fonte de rastreamento definida pelo usuário nomeada ao arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="6b00e-119">The following code shows how to add a user-defined trace source named `ServerCalculatorTraceSource` to the configuration file.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
        <source name="ServerCalculatorTraceSource" switchValue="Information,ActivityTracing">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
       <add initializeData="C:\logs\ServerTraces.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" traceOutputOptions="Callstack">  
            <filter type="" />  
        </add>  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>....  
....  
```  
  
### <a name="correlating-activities"></a><span data-ttu-id="6b00e-120">Atividades correlacionadas</span><span class="sxs-lookup"><span data-stu-id="6b00e-120">Correlating Activities</span></span>  
 <span data-ttu-id="6b00e-121">Para correlacionar as atividades `propagateActivity` diretamente entre os `true` pontos `System.ServiceModel` finais, o atributo deve ser definido na fonte de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6b00e-121">To correlate activities directly across endpoints, the `propagateActivity` attribute must be set to `true` in the `System.ServiceModel` trace source.</span></span> <span data-ttu-id="6b00e-122">Além disso, para propagar rastreamentos sem passar por atividades do WCF, o ServiceModel Activity Tracing deve ser desligado.</span><span class="sxs-lookup"><span data-stu-id="6b00e-122">Also, to propagate traces without going through WCF activities, ServiceModel Activity Tracing must be turned off.</span></span> <span data-ttu-id="6b00e-123">Isso pode ser visto no seguinte exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="6b00e-123">This can be seen in the following code example.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6b00e-124">Desativar o ServiceModel Activity Ttrace não é o mesmo que `switchValue` ter o nível de rastreamento, denotado pela propriedade, definido como desligado.</span><span class="sxs-lookup"><span data-stu-id="6b00e-124">Turning off ServiceModel Activity Tracing is not the same as having the trace level, denoted by the `switchValue` property, set to off.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a><span data-ttu-id="6b00e-125">Redução do custo de desempenho</span><span class="sxs-lookup"><span data-stu-id="6b00e-125">Lessening Performance Cost</span></span>  
 <span data-ttu-id="6b00e-126">A `ActivityTracing` configuração `System.ServiceModel` na origem do rastreamento gera um arquivo de rastreamento que contém apenas traços de atividade definidos pelo usuário, sem que nenhum dos traços de atividade serviceModel seja incluído.</span><span class="sxs-lookup"><span data-stu-id="6b00e-126">Setting `ActivityTracing` to off in the `System.ServiceModel` trace source generates a trace file that contains only user-defined activity traces, without any of the ServiceModel activity traces included.</span></span> <span data-ttu-id="6b00e-127">Isso resulta em um arquivo de log de tamanho muito menor.</span><span class="sxs-lookup"><span data-stu-id="6b00e-127">This results in a log file of much smaller size.</span></span> <span data-ttu-id="6b00e-128">No entanto, a oportunidade de correlacionar os traços de processamento wcf é perdida.</span><span class="sxs-lookup"><span data-stu-id="6b00e-128">However, the opportunity to correlate WCF processing traces is lost.</span></span>  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6b00e-129">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="6b00e-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="6b00e-130">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6b00e-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="6b00e-131">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6b00e-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="6b00e-132">Para executar a amostra em uma configuração de computador único ou cruzado, siga as instruções em [Executar as amostras da Fundação](../../../../docs/framework/wcf/samples/running-the-samples.md)de Comunicação do Windows .</span><span class="sxs-lookup"><span data-stu-id="6b00e-132">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b00e-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="6b00e-133">See also</span></span>

- <span data-ttu-id="6b00e-134">[AppFabric que monitora Exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="6b00e-134">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
