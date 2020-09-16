---
title: Rastreamento de SQL
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: 916c04b03dee296b7e6f5c792f0c4e50fb4203c0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559344"
---
# <a name="sql-tracking"></a><span data-ttu-id="6b468-102">Rastreamento do SQL</span><span class="sxs-lookup"><span data-stu-id="6b468-102">SQL tracking</span></span>

<span data-ttu-id="6b468-103">Este exemplo demonstra como gravar um participante de rastreamento do SQL personalizado que grava registros de rastreamento em um banco de dados SQL.</span><span class="sxs-lookup"><span data-stu-id="6b468-103">This sample demonstrates how to write a custom SQL tracking participant that writes tracking records to a SQL database.</span></span> <span data-ttu-id="6b468-104">Windows Workflow Foundation (WF) fornece rastreamento de fluxo de trabalho para obter visibilidade da execução de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="6b468-104">Windows Workflow Foundation (WF) provides workflow tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="6b468-105">O runtime de rastreamento emite-se registros de acompanhamento de fluxo de trabalho durante a execução de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="6b468-105">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="6b468-106">Para obter mais informações sobre o rastreamento de fluxo de trabalho, consulte rastreamento [e acompanhamento de fluxo de trabalho](../workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="6b468-106">For more information about workflow tracking, see [Workflow Tracking and Tracing](../workflow-tracking-and-tracing.md).</span></span>

## <a name="use-the-sample"></a><span data-ttu-id="6b468-107">Usar o exemplo</span><span class="sxs-lookup"><span data-stu-id="6b468-107">Use the sample</span></span>

1. <span data-ttu-id="6b468-108">Verifique têm SQL Server 2008, SQL Server 2008 Express edition ou mais recente instalados.</span><span class="sxs-lookup"><span data-stu-id="6b468-108">Verify you have SQL Server 2008, SQL Server 2008 Express or newer installed.</span></span> <span data-ttu-id="6b468-109">Os scripts agrupados com o exemplo assumem o uso de uma instância do SQL express em seu computador local.</span><span class="sxs-lookup"><span data-stu-id="6b468-109">The scripts packaged with the sample assume the use of a SQL Express instance on your local computer.</span></span> <span data-ttu-id="6b468-110">Se você tiver uma instância diferente por favor alterar os scripts base de dados - relacionados antes de executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="6b468-110">If you have a different instance please modify the database-related scripts before running the sample.</span></span>

2. <span data-ttu-id="6b468-111">Crie o SQL Server que controla o base de dados executando Trackingsetup.cmd no diretório de scripts (\ \ WF básico rastreamento SqlTracking \ \ \ \ CS scripts).</span><span class="sxs-lookup"><span data-stu-id="6b468-111">Create the SQL Server tracking database by running Trackingsetup.cmd in the scripts directory (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span></span> <span data-ttu-id="6b468-112">Isso cria um base de dados chamado TrackingSample.</span><span class="sxs-lookup"><span data-stu-id="6b468-112">This creates a database called TrackingSample.</span></span>

   > [!NOTE]
   > <span data-ttu-id="6b468-113">O script cria o base de dados na instância padrão do SQL express.</span><span class="sxs-lookup"><span data-stu-id="6b468-113">The script creates the database on the default instance of SQL Express.</span></span> <span data-ttu-id="6b468-114">Se você deseja instalá-lo em uma instância diferente de base de dados, editar script de Trackingsetup.cmd.</span><span class="sxs-lookup"><span data-stu-id="6b468-114">If you want to install it on a different database instance, edit the Trackingsetup.cmd script.</span></span>

3. <span data-ttu-id="6b468-115">Abra SqlTrackingSample. sln no Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="6b468-115">Open SqlTrackingSample.sln in Visual Studio 2010.</span></span>

4. <span data-ttu-id="6b468-116">Pressione **Ctrl** + **Shift** + **B** para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="6b468-116">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

5. <span data-ttu-id="6b468-117">Pressione **F5** para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6b468-117">Press **F5** to run the application.</span></span>

   <span data-ttu-id="6b468-118">A janela do navegador abre e mostra a listagem de diretório para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6b468-118">The browser window opens and shows the directory listing for the application.</span></span>

6. <span data-ttu-id="6b468-119">No navegador, clique StockPriceService.xamlx.</span><span class="sxs-lookup"><span data-stu-id="6b468-119">In the browser, click StockPriceService.xamlx.</span></span>

7. <span data-ttu-id="6b468-120">O navegador exibe a página de StockPriceService, que contém o endereço de WSDL de serviço local.</span><span class="sxs-lookup"><span data-stu-id="6b468-120">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="6b468-121">Copie este endereço.</span><span class="sxs-lookup"><span data-stu-id="6b468-121">Copy this address.</span></span>

   <span data-ttu-id="6b468-122">Um exemplo do endereço WSDL do serviço local é `http://localhost:65193/StockPriceService.xamlx?wsdl` .</span><span class="sxs-lookup"><span data-stu-id="6b468-122">An example of the local service WSDL address is `http://localhost:65193/StockPriceService.xamlx?wsdl`.</span></span>

8. <span data-ttu-id="6b468-123">Usando o explorador de arquivos, execute o cliente de teste do WCF (WcfTestClient.exe).</span><span class="sxs-lookup"><span data-stu-id="6b468-123">Using File Explorer, run the WCF test client (WcfTestClient.exe).</span></span> <span data-ttu-id="6b468-124">Ele está localizado no *diretório Microsoft Visual Studio 10.0 \ Common7\IDE*</span><span class="sxs-lookup"><span data-stu-id="6b468-124">It's located in the *Microsoft Visual Studio 10.0\Common7\IDE directory*.</span></span>

9. <span data-ttu-id="6b468-125">No cliente de teste do WCF, clique no menu **arquivo** e selecione **Adicionar serviço**.</span><span class="sxs-lookup"><span data-stu-id="6b468-125">In the WCF test client, click the **File** menu and select **Add Service**.</span></span> <span data-ttu-id="6b468-126">Cole o endereço do serviço local na caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="6b468-126">Paste the local service address in the textbox.</span></span> <span data-ttu-id="6b468-127">Clique em **OK** para fechar o diálogo.</span><span class="sxs-lookup"><span data-stu-id="6b468-127">Click **OK** to close the dialog.</span></span>

10. <span data-ttu-id="6b468-128">No cliente de teste do WCF, clique duas vezes em **GetStockPrice**.</span><span class="sxs-lookup"><span data-stu-id="6b468-128">In the WCF test client, double click **GetStockPrice**.</span></span> <span data-ttu-id="6b468-129">Isso abre a `GetStockPrice` operação que usa um parâmetro, digita o valor `Contoso` e clica em **invocar**.</span><span class="sxs-lookup"><span data-stu-id="6b468-129">This opens the `GetStockPrice` operation that takes one parameter, type in the value `Contoso` and click **Invoke**.</span></span>

11. <span data-ttu-id="6b468-130">Os registros emissores de rastreamento são gravados em uma base de dados SQL.</span><span class="sxs-lookup"><span data-stu-id="6b468-130">The emitted tracking records are written to a SQL database.</span></span> <span data-ttu-id="6b468-131">Para exibir os registros de rastreamento, abra o base de dados de TrackingSample em SQL Management Studio e navegar para tabelas.</span><span class="sxs-lookup"><span data-stu-id="6b468-131">To view the tracking records, open the TrackingSample database in SQL Management Studio and navigate to the tables.</span></span> <span data-ttu-id="6b468-132">Executar uma consulta selecionar as tabelas exibe os dados dentro dos registros de rastreamento armazenados nas tabelas respectivas.</span><span class="sxs-lookup"><span data-stu-id="6b468-132">Running a select query on the tables displays the data within the tracking records stored in the respective tables.</span></span>

   <span data-ttu-id="6b468-133">Para obter mais informações sobre SQL Server Management Studio, consulte [introdução a SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms).</span><span class="sxs-lookup"><span data-stu-id="6b468-133">For more information about SQL Server Management Studio, see [Introducing SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms).</span></span> <span data-ttu-id="6b468-134">Baixe SQL Server Management Studio [aqui](https://aka.ms/ssmsfullsetup).</span><span class="sxs-lookup"><span data-stu-id="6b468-134">Download SQL Server Management Studio [here](https://aka.ms/ssmsfullsetup).</span></span>

## <a name="uninstall-the-sample"></a><span data-ttu-id="6b468-135">Desinstalar o exemplo</span><span class="sxs-lookup"><span data-stu-id="6b468-135">Uninstall the sample</span></span>

1. <span data-ttu-id="6b468-136">Execute o script theTrackingcleanup. cmd no diretório de exemplo (*\WF\Basic\Tracking\SqlTracking*).</span><span class="sxs-lookup"><span data-stu-id="6b468-136">Run theTrackingcleanup.cmd script in the sample directory (*\WF\Basic\Tracking\SqlTracking*).</span></span>

    > [!NOTE]
    > <span data-ttu-id="6b468-137">O Trackingcleanup.cmd tentar excluir o base de dados em seu computador local SQL express.</span><span class="sxs-lookup"><span data-stu-id="6b468-137">The Trackingcleanup.cmd attempts to delete the database in your local computer SQL Express.</span></span> <span data-ttu-id="6b468-138">Se você estiver usando outra instância do SQL server, editar Trackingcleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="6b468-138">If you are using another SQL server instance, edit Trackingcleanup.cmd.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6b468-139">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="6b468-139">The samples may already be installed on your computer.</span></span> <span data-ttu-id="6b468-140">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="6b468-140">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="6b468-141">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="6b468-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6b468-142">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="6b468-142">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`

## <a name="see-also"></a><span data-ttu-id="6b468-143">Confira também</span><span class="sxs-lookup"><span data-stu-id="6b468-143">See also</span></span>

- <span data-ttu-id="6b468-144">[AppFabric que monitora Exemplos](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="6b468-144">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
