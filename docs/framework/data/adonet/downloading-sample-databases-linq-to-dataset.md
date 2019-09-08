---
title: Bases de dados de exemplo de transferência (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
ms.openlocfilehash: c67ee699cf594f476a728c7345b47b0c32dea7ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795169"
---
# <a name="downloading-sample-databases-linq-to-dataset"></a><span data-ttu-id="d7367-102">Bases de dados de exemplo de transferência (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="d7367-102">Downloading Sample Databases (LINQ to DataSet)</span></span>
<span data-ttu-id="d7367-103">Os exemplos e orientações na documentação do LINQ to DataSet usam o banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d7367-103">The samples and walkthroughs in the LINQ to DataSet documentation use the AdventureWorks sample database.</span></span> <span data-ttu-id="d7367-104">Você pode baixar este produto gratuitamente do site de download da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d7367-104">You can download this product free of charge from the Microsoft download site.</span></span> <span data-ttu-id="d7367-105">Os exemplos e orientações na documentação do LINQ to DataSet usam SQL Server como o armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="d7367-105">The samples and walkthroughs in the LINQ to DataSet documentation use SQL Server as the data store.</span></span> <span data-ttu-id="d7367-106">O SQL Server Express edition, que está disponível sem carregamento, também pode ser usada como o armazenamento de dados em vez do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d7367-106">SQL Server Express Edition, which is available without charge, can also be used as the data store instead of SQL Server.</span></span>  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a><span data-ttu-id="d7367-107">Download e instalar o base de dados AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="d7367-107">Downloading and Installing the AdventureWorks Database</span></span>  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="d7367-108">Para baixar e instalar o base de dados de exemplo AdventureWorks do SQL Server</span><span class="sxs-lookup"><span data-stu-id="d7367-108">To download and install the AdventureWorks sample database for SQL Server</span></span>  
  
1. <span data-ttu-id="d7367-109">Abra o Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="d7367-109">Open Internet Explorer.</span></span>  
  
2. <span data-ttu-id="d7367-110">Vá para o site de [exemplos do SQL Server 2005 e bancos de dados de exemplo](https://go.microsoft.com/fwlink/?linkid=31046) .</span><span class="sxs-lookup"><span data-stu-id="d7367-110">Go to the [SQL Server 2005 Samples and Sample Databases](https://go.microsoft.com/fwlink/?linkid=31046) Web site.</span></span>  
  
3. <span data-ttu-id="d7367-111">Siga as instruções para baixar o base de dados de exemplo AdventureWorks para o tipo do processador (como AdventureWorksDB.msi), e salve o arquivo .msi para seu computador local.</span><span class="sxs-lookup"><span data-stu-id="d7367-111">Follow the instructions for downloading the AdventureWorks sample database for your processor type (such as AdventureWorksDB.msi), and save the .MSI file to your local computer.</span></span>  
  
4. <span data-ttu-id="d7367-112">Se você tiver uma versão anterior AdventureWorks instalado de download ou durante a configuração do SQL Server, você deve remova-o antes de executar AdventureWorks.msi.</span><span class="sxs-lookup"><span data-stu-id="d7367-112">If you have a previous version of AdventureWorks installed from the download or during the SQL Server setup, you must remove it before running AdventureWorks.msi.</span></span>  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a><span data-ttu-id="d7367-113">Para remover um download anterior de um base de dados de exemplo AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="d7367-113">To remove a previous download of an AdventureWorks sample database</span></span>  
  
1. <span data-ttu-id="d7367-114">Solte o base de dados AdventureWorks ou de AdventureWorksDW.</span><span class="sxs-lookup"><span data-stu-id="d7367-114">Drop the AdventureWorks or AdventureWorksDW database.</span></span>  
  
2. <span data-ttu-id="d7367-115">Em **Adicionar ou remover programas**, selecione **AdventureWorksDB** ou **AdventureWorksBI** e clique em **remover**.</span><span class="sxs-lookup"><span data-stu-id="d7367-115">From **Add or Remove Programs**, select **AdventureWorksDB** or **AdventureWorksBI** and click **Remove**.</span></span>  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a><span data-ttu-id="d7367-116">Para remover um base de dados de exemplo AdventureWorks instalado anteriormente usando a configuração</span><span class="sxs-lookup"><span data-stu-id="d7367-116">To remove an AdventureWorks sample database previously installed using Setup</span></span>  
  
1. <span data-ttu-id="d7367-117">Solte o base de dados AdventureWorks ou de AdventureWorksDW.</span><span class="sxs-lookup"><span data-stu-id="d7367-117">Drop the AdventureWorks or AdventureWorksDW database.</span></span>  
  
2. <span data-ttu-id="d7367-118">Em **Adicionar ou remover programas**, selecione **Microsoft SQL Server 2005** e clique em **alterar**.</span><span class="sxs-lookup"><span data-stu-id="d7367-118">From **Add or Remove Programs**, select **Microsoft SQL Server 2005** and click **Change**.</span></span>  
  
3. <span data-ttu-id="d7367-119">Em **seleção de componentes**, selecione **componentes da estação de trabalho** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="d7367-119">From **Component Selection**, select **Workstation Components** and then click **Next**.</span></span>  
  
4. <span data-ttu-id="d7367-120">Em **Bem-vindo ao assistente de instalação do SQL Server**, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="d7367-120">From **Welcome to the SQL Server Installation Wizard**, click **Next**.</span></span>  
  
5. <span data-ttu-id="d7367-121">Em **verificação de configuração do sistema**, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="d7367-121">From **System Configuration Check**, click **Next**.</span></span>  
  
6. <span data-ttu-id="d7367-122">Em **alterar ou remover instância**, clique em **alterar componentes instalados**.</span><span class="sxs-lookup"><span data-stu-id="d7367-122">From **Change or Remove Instance**, click **Change Installed Components**.</span></span>  
  
7. <span data-ttu-id="d7367-123">Na **seleção de recursos**, expanda o nó **documentação, exemplos e bancos de dados de exemplo** .</span><span class="sxs-lookup"><span data-stu-id="d7367-123">From **Feature Selection**, expand the **Documentation, Samples, and Sample Databases** node.</span></span>  
  
8. <span data-ttu-id="d7367-124">Selecione **código e aplicativos de exemplo**.</span><span class="sxs-lookup"><span data-stu-id="d7367-124">Select **Sample Code and Applications**.</span></span> <span data-ttu-id="d7367-125">Expanda bancos de dados de **exemplo**, selecione o banco de dados de exemplo a ser removido e selecione o **recurso inteiro estará indisponível**.</span><span class="sxs-lookup"><span data-stu-id="d7367-125">Expand **Sample Databases**, select the sample database to be removed, and select **Entire feature will be unavailable**.</span></span> <span data-ttu-id="d7367-126">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="d7367-126">Click **Next**.</span></span>  
  
9. <span data-ttu-id="d7367-127">Clique em **instalar** e conclua o assistente de instalação.</span><span class="sxs-lookup"><span data-stu-id="d7367-127">Click **Install** and finish the installation wizard.</span></span>  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a><span data-ttu-id="d7367-128">Para anexar arquivos de base de dados de exemplo AdventureWorks a uma instância de SQL Server</span><span class="sxs-lookup"><span data-stu-id="d7367-128">To attach the AdventureWorks sample database files to an instance of SQL Server</span></span>  
  
1. <span data-ttu-id="d7367-129">Depois que o arquivo do instalador do banco de dados de exemplo de arquivo for baixado, clique duas vezes no arquivo **AdventureWorksDB. msi** (ou no arquivo que você baixou) para instalar o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="d7367-129">After the file sample database installer file has downloaded, double-click the **AdventureWorksDB.msi** file (or the file you downloaded) to install the database.</span></span> <span data-ttu-id="d7367-130">Por padrão, o base de dados é instalado em c:\Program Files\Microsoft SQL Server \ MSSQL.1 \ MSSQL \ dados.</span><span class="sxs-lookup"><span data-stu-id="d7367-130">By default, the database is installed at c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.</span></span>  
  
2. <span data-ttu-id="d7367-131">Anexar arquivos de base de dados AdventureWorks a uma instância do SQL Server executando o seguinte script SQLCMD ou o SQL Server Management Studio:</span><span class="sxs-lookup"><span data-stu-id="d7367-131">Attach the AdventureWorks database files to an instance of SQL Server by executing the following script SQLCMD or SQL Server Management Studio:</span></span>  
  
    ```sql
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     <span data-ttu-id="d7367-132">Se você instalar esses arquivos a uma unidade ou para um diretório diferente, você deve revisar os caminhos corretamente antes de executar o procedimento armazenado `sp_attach_db` .</span><span class="sxs-lookup"><span data-stu-id="d7367-132">If you have installed these files to a different drive or directory, you must revise the paths appropriately before you execute the `sp_attach_db` stored procedure.</span></span>  
  
## <a name="downloading-sql-server-express-edition"></a><span data-ttu-id="d7367-133">Baixando o SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="d7367-133">Downloading SQL Server Express Edition</span></span>  
 <span data-ttu-id="d7367-134">Os exemplos e orientações na seção LINQ to DataSet usam SQL Server 2005 como o armazenamento de dados, mas podem ser modificados para usar a edição do SQL Server Express, em vez disso.</span><span class="sxs-lookup"><span data-stu-id="d7367-134">The samples and walkthroughs in the LINQ to DataSet section use SQL Server 2005 as the data store but can be modified to use SQL Server Express Edition, instead.</span></span> <span data-ttu-id="d7367-135">O SQL Server Express Edition está disponível gratuitamente, e você pode redistribuí-lo com os aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d7367-135">SQL Server Express Edition is available without charge, and you can redistribute it with applications.</span></span> <span data-ttu-id="d7367-136">Se você estiver usando o Visual Studio, o SQL Server Express Edition estará incluído nas edições Pro e superior.</span><span class="sxs-lookup"><span data-stu-id="d7367-136">If you are using Visual Studio, SQL Server Express Edition is included in the Pro and higher editions.</span></span>  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a><span data-ttu-id="d7367-137">Para baixar e instalar o SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="d7367-137">To download and install SQL Server Express Edition</span></span>  
  
1. <span data-ttu-id="d7367-138">Inicie o Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="d7367-138">Start Internet Explorer.</span></span>  
  
2. <span data-ttu-id="d7367-139">Vá para a página de download do [Microsoft SQL Server 2005 Express Edition](https://go.microsoft.com/fwlink/?LinkID=31070) .</span><span class="sxs-lookup"><span data-stu-id="d7367-139">Go to the  [Microsoft SQL Server 2005 Express Edition](https://go.microsoft.com/fwlink/?LinkID=31070) download page.</span></span>  
  
3. <span data-ttu-id="d7367-140">Siga as instruções de instalação no site.</span><span class="sxs-lookup"><span data-stu-id="d7367-140">Follow the installation instructions on the Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7367-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7367-141">See also</span></span>

- [<span data-ttu-id="d7367-142">Introdução</span><span class="sxs-lookup"><span data-stu-id="d7367-142">Getting Started</span></span>](getting-started-linq-to-dataset.md)
