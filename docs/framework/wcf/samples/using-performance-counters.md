---
title: Utilizando contadores de desempenho
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 7ffd9f5de5efb4be22968958246839e804daf23d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143571"
---
# <a name="using-performance-counters"></a><span data-ttu-id="69224-102">Utilizando contadores de desempenho</span><span class="sxs-lookup"><span data-stu-id="69224-102">Using Performance Counters</span></span>
<span data-ttu-id="69224-103">Esta amostra demonstra como acessar os contadores de desempenho da Windows Communication Foundation (WCF) e como criar contadores de desempenho definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="69224-103">This sample demonstrates how to access Windows Communication Foundation (WCF) performance counters and how to create user-defined performance counters.</span></span> <span data-ttu-id="69224-104">Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="69224-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="69224-105">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="69224-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="69224-106">Nesta amostra, o cliente chama os `ICalculator` quatro métodos do serviço.</span><span class="sxs-lookup"><span data-stu-id="69224-106">In this sample, the client calls the four methods of the `ICalculator` service.</span></span> <span data-ttu-id="69224-107">O cliente continua fazendo isso até que seja interrompido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="69224-107">The client continues to do this until it is interrupted by the user.</span></span> <span data-ttu-id="69224-108">O serviço permanece inalterado.</span><span class="sxs-lookup"><span data-stu-id="69224-108">The service remains unchanged.</span></span>  
  
 <span data-ttu-id="69224-109">Os contadores de desempenho estão habilitados na seção de diagnóstico do arquivo Web.config para o serviço, conforme mostrado na configuração da amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="69224-109">Performance counters are enabled in the diagnostics section of the Web.config file for the service, as shown in the following sample configuration.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="69224-110">Essa tarefa também pode ser feita usando a [Ferramenta de Editor de Configuração (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="69224-110">This task can also be done using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="69224-111">Quando os contadores de desempenho são ativados, todo o conjunto de contadores de desempenho WCF está habilitado para o serviço.</span><span class="sxs-lookup"><span data-stu-id="69224-111">When performance counters are enabled, the entire suite of WCF performance counters is enabled for the service.</span></span> <span data-ttu-id="69224-112">O .NET Framework mantém automaticamente os `ServiceModelService` `ServiceModelEndpoint` dados `ServiceModelOperation`de desempenho em três níveis: e .</span><span class="sxs-lookup"><span data-stu-id="69224-112">The .NET Framework automatically maintains performance data at three levels: `ServiceModelService`, `ServiceModelEndpoint` and `ServiceModelOperation`.</span></span> <span data-ttu-id="69224-113">Cada um desses níveis tem contadores de desempenho como "Chamadas", "Chamadas por Segundo" e "Chamadas de Segurança Não Autorizadas".</span><span class="sxs-lookup"><span data-stu-id="69224-113">Each of these levels has performance counters such as "Calls", "Calls per Second", and "Security Calls Not Authorized".</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="69224-114">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="69224-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="69224-115">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="69224-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="69224-116">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="69224-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="69224-117">Para executar a amostra em uma configuração de computador único ou cruzado, siga as instruções em [Executar as amostras da Fundação](../../../../docs/framework/wcf/samples/running-the-samples.md)de Comunicação do Windows .</span><span class="sxs-lookup"><span data-stu-id="69224-117">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-view-performance-data"></a><span data-ttu-id="69224-118">Para exibir dados de desempenho</span><span class="sxs-lookup"><span data-stu-id="69224-118">To view performance data</span></span>  
  
1. <span data-ttu-id="69224-119">Inicie a ferramenta Monitor de Desempenho clicando `perfmon` em **Iniciar**, **Executar...**, digite e clique em **OK,** ou no Painel de Controle, selecione **Ferramentas Administrativas** e clique duas vezes em **Desempenho**.</span><span class="sxs-lookup"><span data-stu-id="69224-119">Start the Performance Monitor Tool by clicking **Start**, **Run…**, enter `perfmon` and click **OK,** or from Control Panel, select **Administrative Tools** and double-click **Performance**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="69224-120">Você não pode adicionar contadores até que o código de amostra esteja em execução.</span><span class="sxs-lookup"><span data-stu-id="69224-120">You cannot add counters until the sample code is running.</span></span>  
  
2. <span data-ttu-id="69224-121">Remova os contadores de desempenho listados selecionando-os e pressionando a tecla Excluir.</span><span class="sxs-lookup"><span data-stu-id="69224-121">Remove the performance counters that are listed by selecting them and pressing the Delete key.</span></span>  
  
3. <span data-ttu-id="69224-122">Adicione contadores WCF clicando com o botão direito do mouse no painel de gráficos e selecionando **Add Counters**.</span><span class="sxs-lookup"><span data-stu-id="69224-122">Add WCF counters by right-clicking the graph pane and selecting **Add Counters**.</span></span> <span data-ttu-id="69224-123">Na caixa de diálogo **Adicionar contadores,** selecione **ServiceModelOperação 3.0.0.0, ServiceModelEndpoint 3.0.0.0 ou ServiceModelService 3.0.0.0** na caixa de lista de lista sosseleta do objeto Desempenho.</span><span class="sxs-lookup"><span data-stu-id="69224-123">In the **Add Counters** dialog box, select **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0, or ServiceModelService 3.0.0.0** in the Performance object drop down list box.</span></span> <span data-ttu-id="69224-124">Selecione os contadores que deseja exibir na lista.</span><span class="sxs-lookup"><span data-stu-id="69224-124">Select the counters you want to view from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="69224-125">Não há contadores de desempenho WCF para um serviço se não houver serviços WCF em execução no computador.</span><span class="sxs-lookup"><span data-stu-id="69224-125">There are no WCF performance counters for a service if there are no WCF services running on the computer.</span></span>  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a><span data-ttu-id="69224-126">Para usar o Editor de configuração para ativar contadores</span><span class="sxs-lookup"><span data-stu-id="69224-126">To use the Configuration Editor to enable counters</span></span>  
  
1. <span data-ttu-id="69224-127">Abra uma instância do SvcConfigEditor.exe.</span><span class="sxs-lookup"><span data-stu-id="69224-127">Open an instance of the SvcConfigEditor.exe.</span></span>  
  
2. <span data-ttu-id="69224-128">No menu Arquivo, clique em **Abrir** e clique em **Config file...**.</span><span class="sxs-lookup"><span data-stu-id="69224-128">On the File menu, click **Open** and then click **Config file…**.</span></span>  
  
3. <span data-ttu-id="69224-129">Navegue até a pasta de serviço do aplicativo de exemplo e abra o arquivo Web.config.</span><span class="sxs-lookup"><span data-stu-id="69224-129">Navigate to the sample application's service folder and open the Web.config file.</span></span>  
  
4. <span data-ttu-id="69224-130">Clique em **Diagnósticos** na árvore Configuração.</span><span class="sxs-lookup"><span data-stu-id="69224-130">Click **Diagnostics** on the Configuration tree.</span></span>  
  
5. <span data-ttu-id="69224-131">Alternar **contador de desempenho** na janela **Diagnósticos** para mostrar 'Todos'.</span><span class="sxs-lookup"><span data-stu-id="69224-131">Toggle **Performance Counter** in the **Diagnostics** window to show 'All'.</span></span>  
  
6. <span data-ttu-id="69224-132">Salve o arquivo de configuração e saia do editor.</span><span class="sxs-lookup"><span data-stu-id="69224-132">Save the configuration file and exit the editor.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="69224-133">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="69224-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="69224-134">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="69224-134">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="69224-135">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="69224-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="69224-136">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="69224-136">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a><span data-ttu-id="69224-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="69224-137">See also</span></span>

- <span data-ttu-id="69224-138">[AppFabric que monitora Exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="69224-138">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
