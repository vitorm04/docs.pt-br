---
title: Utilizando contadores de desempenho
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 8784b4a481b8313d370aad1d8f265dcb44ab3ed6
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807313"
---
# <a name="using-performance-counters"></a><span data-ttu-id="1146a-102">Utilizando contadores de desempenho</span><span class="sxs-lookup"><span data-stu-id="1146a-102">Using Performance Counters</span></span>
<span data-ttu-id="1146a-103">Este exemplo demonstra como acessar os contadores de desempenho do Windows Communication Foundation (WCF) e como criar contadores de desempenho definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="1146a-103">This sample demonstrates how to access Windows Communication Foundation (WCF) performance counters and how to create user-defined performance counters.</span></span> <span data-ttu-id="1146a-104">Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="1146a-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1146a-105">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="1146a-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1146a-106">Neste exemplo, o cliente chama os quatro métodos do `ICalculator` service.</span><span class="sxs-lookup"><span data-stu-id="1146a-106">In this sample, the client calls the four methods of the `ICalculator` service.</span></span> <span data-ttu-id="1146a-107">O cliente continua até que ele seja interrompido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="1146a-107">The client continues to do this until it is interrupted by the user.</span></span> <span data-ttu-id="1146a-108">O serviço permanecerá inalterado.</span><span class="sxs-lookup"><span data-stu-id="1146a-108">The service remains unchanged.</span></span>  
  
 <span data-ttu-id="1146a-109">Contadores de desempenho estão habilitados na seção de diagnóstico do arquivo Web. config para o serviço, conforme mostrado no exemplo de configuração.</span><span class="sxs-lookup"><span data-stu-id="1146a-109">Performance counters are enabled in the diagnostics section of the Web.config file for the service, as shown in the following sample configuration.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />   
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="1146a-110">Essa tarefa também pode ser feita usando o [ferramenta Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="1146a-110">This task can also be done using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="1146a-111">Quando os contadores de desempenho estão habilitados, o conjunto completo de contadores de desempenho do WCF está habilitado para o serviço.</span><span class="sxs-lookup"><span data-stu-id="1146a-111">When performance counters are enabled, the entire suite of WCF performance counters is enabled for the service.</span></span> <span data-ttu-id="1146a-112">O .NET Framework mantém automaticamente os dados de desempenho em três níveis: `ServiceModelService`, `ServiceModelEndpoint` e `ServiceModelOperation`.</span><span class="sxs-lookup"><span data-stu-id="1146a-112">The .NET Framework automatically maintains performance data at three levels: `ServiceModelService`, `ServiceModelEndpoint` and `ServiceModelOperation`.</span></span> <span data-ttu-id="1146a-113">Cada um desses níveis tem contadores de desempenho, como "chamadas de", "Chamadas por segundo" e "Chamadas de segurança não autorizado".</span><span class="sxs-lookup"><span data-stu-id="1146a-113">Each of these levels has performance counters such as "Calls", "Calls per Second", and "Security Calls Not Authorized".</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1146a-114">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="1146a-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="1146a-115">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1146a-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="1146a-116">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1146a-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="1146a-117">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1146a-117">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-view-performance-data"></a><span data-ttu-id="1146a-118">Para exibir dados de desempenho</span><span class="sxs-lookup"><span data-stu-id="1146a-118">To view performance data</span></span>  
  
1.  <span data-ttu-id="1146a-119">Inicie a ferramenta de Monitor de desempenho clicando **iniciar**, **executar...** , digite `perfmon` e clique em **Okey,** ou, no painel de controle, selecione **ferramentas administrativas** e clique duas vezes em **desempenho**.</span><span class="sxs-lookup"><span data-stu-id="1146a-119">Start the Performance Monitor Tool by clicking **Start**, **Run…**, enter `perfmon` and click **OK,** or from Control Panel, select **Administrative Tools** and double-click **Performance**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1146a-120">Não é possível adicionar contadores, até que o código de exemplo está em execução.</span><span class="sxs-lookup"><span data-stu-id="1146a-120">You cannot add counters until the sample code is running.</span></span>  
  
2.  <span data-ttu-id="1146a-121">Remova os contadores de desempenho listados selecionando-os e pressionando a tecla Delete.</span><span class="sxs-lookup"><span data-stu-id="1146a-121">Remove the performance counters that are listed by selecting them and pressing the Delete key.</span></span>  
  
3.  <span data-ttu-id="1146a-122">Adicionar contadores WCF, clicando duas vezes no painel gráfico e selecionando **adicionar contadores**.</span><span class="sxs-lookup"><span data-stu-id="1146a-122">Add WCF counters by right-clicking the graph pane and selecting **Add Counters**.</span></span> <span data-ttu-id="1146a-123">No **adicionar contadores** caixa de diálogo, selecione **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 ou ServiceModelService 3.0.0.0** no objeto de desempenho lista caixa suspensa.</span><span class="sxs-lookup"><span data-stu-id="1146a-123">In the **Add Counters** dialog box, select **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0, or ServiceModelService 3.0.0.0** in the Performance object drop down list box.</span></span> <span data-ttu-id="1146a-124">Selecione os contadores que você deseja exibir na lista.</span><span class="sxs-lookup"><span data-stu-id="1146a-124">Select the counters you want to view from the list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1146a-125">Não há nenhum contador de desempenho para um serviço WCF se não houver nenhum serviço WCF em execução no computador.</span><span class="sxs-lookup"><span data-stu-id="1146a-125">There are no WCF performance counters for a service if there are no WCF services running on the computer.</span></span>  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a><span data-ttu-id="1146a-126">Para usar o Editor de configuração para habilitar os contadores</span><span class="sxs-lookup"><span data-stu-id="1146a-126">To use the Configuration Editor to enable counters</span></span>  
  
1.  <span data-ttu-id="1146a-127">Abra uma instância do SvcConfigEditor.exe.</span><span class="sxs-lookup"><span data-stu-id="1146a-127">Open an instance of the SvcConfigEditor.exe.</span></span>  
  
2.  <span data-ttu-id="1146a-128">No menu Arquivo, clique em **abrir** e, em seguida, clique em **arquivo de configuração...** .</span><span class="sxs-lookup"><span data-stu-id="1146a-128">On the File menu, click **Open** and then click **Config file…**.</span></span>  
  
3.  <span data-ttu-id="1146a-129">Navegue até a pasta do serviço do aplicativo de exemplo e abra o arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="1146a-129">Navigate to the sample application's service folder and open the Web.config file.</span></span>  
  
4.  <span data-ttu-id="1146a-130">Clique em **diagnóstico** na árvore de configuração.</span><span class="sxs-lookup"><span data-stu-id="1146a-130">Click **Diagnostics** on the Configuration tree.</span></span>  
  
5.  <span data-ttu-id="1146a-131">Ativar/desativar **contador de desempenho** no **diagnóstico** janela Mostrar 'Todos'.</span><span class="sxs-lookup"><span data-stu-id="1146a-131">Toggle **Performance Counter** in the **Diagnostics** window to show 'All'.</span></span>  
  
6.  <span data-ttu-id="1146a-132">Salve o arquivo de configuração e saia do editor.</span><span class="sxs-lookup"><span data-stu-id="1146a-132">Save the configuration file and exit the editor.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1146a-133">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="1146a-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1146a-134">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="1146a-134">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1146a-135">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="1146a-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1146a-136">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="1146a-136">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a><span data-ttu-id="1146a-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1146a-137">See Also</span></span>  
 [<span data-ttu-id="1146a-138">Exemplos de monitoramento do AppFabric</span><span class="sxs-lookup"><span data-stu-id="1146a-138">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
