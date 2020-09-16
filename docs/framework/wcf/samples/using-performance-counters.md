---
title: Utilizando contadores de desempenho
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: f2b0f39303d000e2e9aab8fc5280f75ab9309c4d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553038"
---
# <a name="using-performance-counters"></a><span data-ttu-id="cf8ea-102">Utilizando contadores de desempenho</span><span class="sxs-lookup"><span data-stu-id="cf8ea-102">Using Performance Counters</span></span>
<span data-ttu-id="cf8ea-103">Este exemplo demonstra como acessar os contadores de desempenho do Windows Communication Foundation (WCF) e como criar contadores de desempenho definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="cf8ea-103">This sample demonstrates how to access Windows Communication Foundation (WCF) performance counters and how to create user-defined performance counters.</span></span> <span data-ttu-id="cf8ea-104">Este exemplo é baseado na [introdução](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="cf8ea-104">This sample is based on the [Getting Started](getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf8ea-105">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="cf8ea-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="cf8ea-106">Neste exemplo, o cliente chama os quatro métodos do `ICalculator` serviço.</span><span class="sxs-lookup"><span data-stu-id="cf8ea-106">In this sample, the client calls the four methods of the `ICalculator` service.</span></span> <span data-ttu-id="cf8ea-107">O cliente continua a fazer isso até que seja interrompido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="cf8ea-107">The client continues to do this until it is interrupted by the user.</span></span> <span data-ttu-id="cf8ea-108">O serviço permanece inalterado.</span><span class="sxs-lookup"><span data-stu-id="cf8ea-108">The service remains unchanged.</span></span>  
  
 <span data-ttu-id="cf8ea-109">Os contadores de desempenho são habilitados na seção diagnóstico do arquivo Web.config para o serviço, conforme mostrado na seguinte configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="cf8ea-109">Performance counters are enabled in the diagnostics section of the Web.config file for the service, as shown in the following sample configuration.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="cf8ea-110">Essa tarefa também pode ser feita usando a [ferramenta do editor de configuração (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="cf8ea-110">This task can also be done using the [Configuration Editor Tool (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="cf8ea-111">Quando os contadores de desempenho estão habilitados, o conjunto inteiro de contadores de desempenho do WCF é habilitado para o serviço.</span><span class="sxs-lookup"><span data-stu-id="cf8ea-111">When performance counters are enabled, the entire suite of WCF performance counters is enabled for the service.</span></span> <span data-ttu-id="cf8ea-112">O .NET Framework mantém automaticamente os dados de desempenho em três níveis: `ServiceModelService` `ServiceModelEndpoint` e `ServiceModelOperation` .</span><span class="sxs-lookup"><span data-stu-id="cf8ea-112">The .NET Framework automatically maintains performance data at three levels: `ServiceModelService`, `ServiceModelEndpoint` and `ServiceModelOperation`.</span></span> <span data-ttu-id="cf8ea-113">Cada um desses níveis tem contadores de desempenho como "chamadas", "chamadas por segundo" e "chamadas de segurança não autorizadas".</span><span class="sxs-lookup"><span data-stu-id="cf8ea-113">Each of these levels has performance counters such as "Calls", "Calls per Second", and "Security Calls Not Authorized".</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cf8ea-114">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="cf8ea-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="cf8ea-115">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cf8ea-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="cf8ea-116">Para criar a edição C# ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cf8ea-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="cf8ea-117">Para executar o exemplo em uma configuração de computador único ou entre computadores, siga as instruções em [executando os exemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cf8ea-117">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
### <a name="to-view-performance-data"></a><span data-ttu-id="cf8ea-118">Para exibir dados de desempenho</span><span class="sxs-lookup"><span data-stu-id="cf8ea-118">To view performance data</span></span>  
  
1. <span data-ttu-id="cf8ea-119">Inicie a ferramenta Monitor de desempenho clicando em **Iniciar**, **executar...**, insira `perfmon` e clique em **OK,** ou, no painel de controle, selecione **Ferramentas administrativas** e clique duas vezes em **desempenho**.</span><span class="sxs-lookup"><span data-stu-id="cf8ea-119">Start the Performance Monitor Tool by clicking **Start**, **Run…**, enter `perfmon` and click **OK,** or from Control Panel, select **Administrative Tools** and double-click **Performance**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="cf8ea-120">Você não pode adicionar contadores até que o código de exemplo esteja em execução.</span><span class="sxs-lookup"><span data-stu-id="cf8ea-120">You cannot add counters until the sample code is running.</span></span>  
  
2. <span data-ttu-id="cf8ea-121">Remova os contadores de desempenho listados selecionando-os e pressionando a tecla Delete.</span><span class="sxs-lookup"><span data-stu-id="cf8ea-121">Remove the performance counters that are listed by selecting them and pressing the Delete key.</span></span>  
  
3. <span data-ttu-id="cf8ea-122">Adicione os contadores do WCF clicando com o botão direito do mouse no painel gráfico e selecionando **Adicionar contadores**.</span><span class="sxs-lookup"><span data-stu-id="cf8ea-122">Add WCF counters by right-clicking the graph pane and selecting **Add Counters**.</span></span> <span data-ttu-id="cf8ea-123">Na caixa de diálogo **Adicionar contadores** , selecione **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 ou ServiceModelService 3.0.0.0** na caixa de listagem suspensa objeto de desempenho.</span><span class="sxs-lookup"><span data-stu-id="cf8ea-123">In the **Add Counters** dialog box, select **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0, or ServiceModelService 3.0.0.0** in the Performance object drop down list box.</span></span> <span data-ttu-id="cf8ea-124">Selecione os contadores que você deseja exibir na lista.</span><span class="sxs-lookup"><span data-stu-id="cf8ea-124">Select the counters you want to view from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="cf8ea-125">Não haverá nenhum contador de desempenho do WCF para um serviço se não houver nenhum serviço WCF em execução no computador.</span><span class="sxs-lookup"><span data-stu-id="cf8ea-125">There are no WCF performance counters for a service if there are no WCF services running on the computer.</span></span>  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a><span data-ttu-id="cf8ea-126">Para usar o editor de configuração para habilitar contadores</span><span class="sxs-lookup"><span data-stu-id="cf8ea-126">To use the Configuration Editor to enable counters</span></span>  
  
1. <span data-ttu-id="cf8ea-127">Abra uma instância do SvcConfigEditor.exe.</span><span class="sxs-lookup"><span data-stu-id="cf8ea-127">Open an instance of the SvcConfigEditor.exe.</span></span>  
  
2. <span data-ttu-id="cf8ea-128">No menu arquivo, clique em **abrir** e em **arquivo de configuração...**.</span><span class="sxs-lookup"><span data-stu-id="cf8ea-128">On the File menu, click **Open** and then click **Config file…**.</span></span>  
  
3. <span data-ttu-id="cf8ea-129">Navegue até a pasta de serviço do aplicativo de exemplo e abra o arquivo Web.config.</span><span class="sxs-lookup"><span data-stu-id="cf8ea-129">Navigate to the sample application's service folder and open the Web.config file.</span></span>  
  
4. <span data-ttu-id="cf8ea-130">Clique em **diagnóstico** na árvore de configuração.</span><span class="sxs-lookup"><span data-stu-id="cf8ea-130">Click **Diagnostics** on the Configuration tree.</span></span>  
  
5. <span data-ttu-id="cf8ea-131">Alterne o **contador de desempenho** na janela de **diagnóstico** para mostrar ' todos '.</span><span class="sxs-lookup"><span data-stu-id="cf8ea-131">Toggle **Performance Counter** in the **Diagnostics** window to show 'All'.</span></span>  
  
6. <span data-ttu-id="cf8ea-132">Salve o arquivo de configuração e saia do editor.</span><span class="sxs-lookup"><span data-stu-id="cf8ea-132">Save the configuration file and exit the editor.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cf8ea-133">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="cf8ea-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="cf8ea-134">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="cf8ea-134">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="cf8ea-135">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="cf8ea-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cf8ea-136">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="cf8ea-136">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a><span data-ttu-id="cf8ea-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="cf8ea-137">See also</span></span>

- <span data-ttu-id="cf8ea-138">[AppFabric que monitora Exemplos](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="cf8ea-138">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
