---
title: Rastreamento de SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6bd8fbe1a29793778d93eeca64b185079d706f3e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="sql-tracking"></a><span data-ttu-id="ffd07-102">Rastreamento de SQL</span><span class="sxs-lookup"><span data-stu-id="ffd07-102">SQL Tracking</span></span>
<span data-ttu-id="ffd07-103">Este exemplo demonstra como escrever um participante de rastreamento SQL personalizado, que grava registros de rastreamento em uma base de dados SQL.</span><span class="sxs-lookup"><span data-stu-id="ffd07-103">This sample demonstrates how to write a custom SQL tracking participant, that writes tracking records to a SQL database.</span></span> [!INCLUDE[wf](../../../../includes/wf-md.md)]<span data-ttu-id="ffd07-104"> fornece o rastreamento de fluxo de trabalho a visibilidade de ganho em execução de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ffd07-104"> provides workflow tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="ffd07-105">O tempo de execução de rastreamento emite-se registros de acompanhamento de fluxo de trabalho durante a execução de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ffd07-105">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ffd07-106">fluxo de trabalho de controle de alterações, consulte [fluxo de trabalho de rastreamento e rastreamento](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="ffd07-106"> workflow tracking, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="ffd07-107">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="ffd07-107">To use this sample</span></span>  
  
1.  <span data-ttu-id="ffd07-108">Verifique têm SQL Server 2008, SQL Server 2008 Express edition ou mais recente instalados.</span><span class="sxs-lookup"><span data-stu-id="ffd07-108">Verify you have SQL Server 2008, SQL Server 2008 Express or newer installed.</span></span> <span data-ttu-id="ffd07-109">Os scripts agrupados com o exemplo assumem o uso de uma instância do SQL express em seu computador local.</span><span class="sxs-lookup"><span data-stu-id="ffd07-109">The scripts packaged with the sample assume the use of a SQL Express instance on your local computer.</span></span> <span data-ttu-id="ffd07-110">Se você tiver uma instância diferente por favor alterar os scripts base de dados - relacionados antes de executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="ffd07-110">If you have a different instance please modify the database-related scripts before running the sample.</span></span>  
  
2.  <span data-ttu-id="ffd07-111">Crie o SQL Server que controla o base de dados executando Trackingsetup.cmd no diretório de scripts (\ \ WF básico rastreamento SqlTracking \ \ \ \ CS scripts).</span><span class="sxs-lookup"><span data-stu-id="ffd07-111">Create the SQL Server tracking database by running Trackingsetup.cmd in the scripts directory (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span></span> <span data-ttu-id="ffd07-112">Isso cria um base de dados chamado TrackingSample.</span><span class="sxs-lookup"><span data-stu-id="ffd07-112">This creates a database called TrackingSample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ffd07-113">O script cria o base de dados na instância padrão do SQL express.</span><span class="sxs-lookup"><span data-stu-id="ffd07-113">The script creates the database on the default instance of SQL Express.</span></span> <span data-ttu-id="ffd07-114">Se você deseja instalá-lo em uma instância diferente de base de dados, editar script de Trackingsetup.cmd.</span><span class="sxs-lookup"><span data-stu-id="ffd07-114">If you want to install it on a different database instance, edit the Trackingsetup.cmd script.</span></span>  
  
3.  <span data-ttu-id="ffd07-115">Abra SqlTrackingSample.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ffd07-115">Open SqlTrackingSample.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
4.  <span data-ttu-id="ffd07-116">Pressione CTRL+SHIFT+B para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="ffd07-116">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
5.  <span data-ttu-id="ffd07-117">Pressione F5 para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ffd07-117">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="ffd07-118">A janela do navegador abre e mostra a listagem de diretório para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ffd07-118">The browser window opens and shows the directory listing for the application.</span></span>  
  
6.  <span data-ttu-id="ffd07-119">No navegador, clique StockPriceService.xamlx.</span><span class="sxs-lookup"><span data-stu-id="ffd07-119">In the browser, click StockPriceService.xamlx.</span></span>  
  
7.  <span data-ttu-id="ffd07-120">O navegador exibe a página de StockPriceService, que contém o endereço de WSDL de serviço local.</span><span class="sxs-lookup"><span data-stu-id="ffd07-120">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="ffd07-121">Copie este endereço.</span><span class="sxs-lookup"><span data-stu-id="ffd07-121">Copy this address.</span></span>  
  
     <span data-ttu-id="ffd07-122">Um exemplo de endereço de WSDL de serviço local é http://localhost:65193/StockPriceService.xamlx?wsdl.</span><span class="sxs-lookup"><span data-stu-id="ffd07-122">An example of the local service WSDL address is http://localhost:65193/StockPriceService.xamlx?wsdl.</span></span>  
  
8.  <span data-ttu-id="ffd07-123">Usando [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], execute o cliente de teste de WCF (WcfTestClient.exe).</span><span class="sxs-lookup"><span data-stu-id="ffd07-123">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], run the WCF test client (WcfTestClient.exe).</span></span> <span data-ttu-id="ffd07-124">Está localizado no Microsoft Visual Studio 10.0 diretório \ Common7 \ IDE.</span><span class="sxs-lookup"><span data-stu-id="ffd07-124">It is located in the Microsoft Visual Studio 10.0\Common7\IDE directory.</span></span>  
  
9. <span data-ttu-id="ffd07-125">No cliente de teste do WCF, clique o **arquivo** menu e selecione **Adicionar serviço**.</span><span class="sxs-lookup"><span data-stu-id="ffd07-125">In the WCF test client, click the **File** menu and select **Add Service**.</span></span> <span data-ttu-id="ffd07-126">Cole o endereço do serviço local na caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="ffd07-126">Paste the local service address in the textbox.</span></span> <span data-ttu-id="ffd07-127">Clique em **Okey** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="ffd07-127">Click **OK** to close the dialog.</span></span>  
  
10. <span data-ttu-id="ffd07-128">O cliente de teste do WCF, clique duas vezes em **GetStockPrice**.</span><span class="sxs-lookup"><span data-stu-id="ffd07-128">In the WCF test client, double click **GetStockPrice**.</span></span> <span data-ttu-id="ffd07-129">Isso abre o `GetStockPrice` operação que usa um parâmetro, digite o valor `Contoso` e clique em **Invoke**.</span><span class="sxs-lookup"><span data-stu-id="ffd07-129">This opens the `GetStockPrice` operation that takes one parameter, type in the value `Contoso` and click **Invoke**.</span></span>  
  
11. <span data-ttu-id="ffd07-130">Os registros emissores de rastreamento são gravados em uma base de dados SQL.</span><span class="sxs-lookup"><span data-stu-id="ffd07-130">The emitted tracking records are written to a SQL database.</span></span> <span data-ttu-id="ffd07-131">Para exibir os registros de rastreamento, abra o base de dados de TrackingSample em SQL Management Studio e navegar para tabelas.</span><span class="sxs-lookup"><span data-stu-id="ffd07-131">To view the tracking records, open the TrackingSample database in SQL Management Studio and navigate to the tables.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ffd07-132">SQL Server Management Studio, consulte [apresentando o SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=165645).</span><span class="sxs-lookup"><span data-stu-id="ffd07-132"> SQL Server Management Studio, see [Introducing SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=165645).</span></span> <span data-ttu-id="ffd07-133">SQL Server 2008 Management Studio Express pode ser baixado [aqui](http://go.microsoft.com/fwlink/?LinkId=180520).</span><span class="sxs-lookup"><span data-stu-id="ffd07-133">SQL Server 2008 Management Studio Express can be downloaded [here](http://go.microsoft.com/fwlink/?LinkId=180520).</span></span> <span data-ttu-id="ffd07-134">Executar uma consulta selecionar as tabelas exibe os dados dentro dos registros de rastreamento armazenados nas tabelas respectivas.</span><span class="sxs-lookup"><span data-stu-id="ffd07-134">Running a select query on the tables displays the data within the tracking records stored in the respective tables.</span></span>  
  
#### <a name="to-uninstall-the-sample"></a><span data-ttu-id="ffd07-135">Para desinstalar o exemplo</span><span class="sxs-lookup"><span data-stu-id="ffd07-135">To uninstall the sample</span></span>  
  
1.  <span data-ttu-id="ffd07-136">Execute o script de theTrackingcleanup.cmd no diretório de exemplo (\ \ WF básico \ \ rastreamento SqlTracking).</span><span class="sxs-lookup"><span data-stu-id="ffd07-136">Run theTrackingcleanup.cmd script in the sample directory (\WF\Basic\Tracking\SqlTracking).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ffd07-137">O Trackingcleanup.cmd tentar excluir o base de dados em seu computador local SQL express.</span><span class="sxs-lookup"><span data-stu-id="ffd07-137">The Trackingcleanup.cmd attempts to delete the database in your local computer SQL Express.</span></span> <span data-ttu-id="ffd07-138">Se você estiver usando outra instância do SQL server, editar Trackingcleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="ffd07-138">If you are using another SQL server instance, edit Trackingcleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ffd07-139">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ffd07-139">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ffd07-140">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="ffd07-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ffd07-141">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="ffd07-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ffd07-142">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="ffd07-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`  
  
## <a name="see-also"></a><span data-ttu-id="ffd07-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ffd07-143">See Also</span></span>  
 [<span data-ttu-id="ffd07-144">Exemplos de monitoramento do AppFabric</span><span class="sxs-lookup"><span data-stu-id="ffd07-144">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
