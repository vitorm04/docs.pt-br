---
title: Obter os bancos de dados de exemplo SQL Server para exemplos de código ADO.NET
description: Baixe os bancos de dados de SQL Server de exemplo usados nos exemplos de código na documentação do ADO.NET, bem como SQL Server e ferramentas de gerenciamento
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: f7c0d1eb0089a6bfabc92e1deecf563c3e59cc6a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156050"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a><span data-ttu-id="33098-103">Obter os bancos de dados de exemplo para exemplos de código do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="33098-103">Get the sample databases for ADO.NET code samples</span></span>

<span data-ttu-id="33098-104">Vários exemplos e orientações na [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentação usam bancos de dados de exemplo SQL Server e SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="33098-104">A number of examples and walkthroughs in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation use sample SQL Server databases and SQL Server Express.</span></span> <span data-ttu-id="33098-105">Você pode baixar esses produtos gratuitamente da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="33098-105">You can download these products free of charge from Microsoft.</span></span>

## <a name="get-the-northwind-sample-database-for-sql-server"></a><span data-ttu-id="33098-106">Obtenha o banco de dados de exemplo Northwind para SQL Server</span><span class="sxs-lookup"><span data-stu-id="33098-106">Get the Northwind sample database for SQL Server</span></span>

<span data-ttu-id="33098-107">Baixe o script `instnwnd.sql` do repositório GitHub a seguir para criar e carregar o banco de dados de exemplo Northwind para SQL Server:</span><span class="sxs-lookup"><span data-stu-id="33098-107">Download the script `instnwnd.sql` from the following GitHub repository to create and load the Northwind sample database for SQL Server:</span></span>

[<span data-ttu-id="33098-108">Bancos de dados de exemplo Northwind e pubs para Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="33098-108">Northwind and pubs sample databases for Microsoft SQL Server</span></span>](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

<span data-ttu-id="33098-109">Para poder usar o banco de dados Northwind, você precisa executar o `instnwnd.sql` arquivo de script baixado para recriar o banco de dados em uma instância do SQL Server usando [SQL Server Management Studio](#get_ssms) ou uma ferramenta semelhante.</span><span class="sxs-lookup"><span data-stu-id="33098-109">Before you can use the Northwind database, you have to run the downloaded `instnwnd.sql` script file to recreate the database on an instance of SQL Server by using [SQL Server Management Studio](#get_ssms) or a similar tool.</span></span> <span data-ttu-id="33098-110">Siga as instruções no arquivo Leiame no repositório.</span><span class="sxs-lookup"><span data-stu-id="33098-110">Follow the instructions in the Readme file in the repository.</span></span>

> [!TIP]
> <span data-ttu-id="33098-111">Se você estiver procurando o banco de dados Northwind para Microsoft Access, consulte [instalar o banco de dados de exemplo Northwind para o Microsoft Access](#northwind_access).</span><span class="sxs-lookup"><span data-stu-id="33098-111">If you're looking for the Northwind database for Microsoft Access, see [Install the Northwind sample database for Microsoft Access](#northwind_access).</span></span>

## <a name="get-the-northwind-sample-database-for-microsoft-access"></a><a name="northwind_access"></a> <span data-ttu-id="33098-112">Obter o banco de dados de exemplo Northwind para o Microsoft Access</span><span class="sxs-lookup"><span data-stu-id="33098-112">Get the Northwind sample database for Microsoft Access</span></span>

<span data-ttu-id="33098-113">O banco de dados de exemplo Northwind do Microsoft Access não está disponível no centro de download da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="33098-113">The Northwind sample database for Microsoft Access is not available on the Microsoft Download Center.</span></span> <span data-ttu-id="33098-114">Para instalar o Northwind diretamente de dentro do Access, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="33098-114">To install Northwind directly from within Access, do the following things:</span></span>

1. <span data-ttu-id="33098-115">Abra o Access.</span><span class="sxs-lookup"><span data-stu-id="33098-115">Open Access.</span></span>

1. <span data-ttu-id="33098-116">Digite **Northwind** na caixa **Pesquisar modelos online** e selecione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="33098-116">Enter **Northwind** in the **Search for Online Templates** box, and then select **Enter**.</span></span>

1. <span data-ttu-id="33098-117">Na tela de resultados, selecione **Northwind**.</span><span class="sxs-lookup"><span data-stu-id="33098-117">On the results screen, select **Northwind**.</span></span> <span data-ttu-id="33098-118">Uma nova janela é aberta com uma descrição do banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="33098-118">A new window opens with a description of the Northwind database.</span></span>

1. <span data-ttu-id="33098-119">Na nova janela, na caixa de texto **nome do arquivo** , forneça um nome de arquivo para a cópia do banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="33098-119">In the new window, in the **File Name** text box, provide a filename for your copy of the Northwind database.</span></span>

1. <span data-ttu-id="33098-120">Selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="33098-120">Select **Create**.</span></span> <span data-ttu-id="33098-121">O Access baixa o banco de dados Northwind e prepara o arquivo.</span><span class="sxs-lookup"><span data-stu-id="33098-121">Access downloads the Northwind database and prepares the file.</span></span>

1. <span data-ttu-id="33098-122">Quando esse processo for concluído, o banco de dados será aberto com uma tela de boas-vindas.</span><span class="sxs-lookup"><span data-stu-id="33098-122">When this process is complete, the database opens with a Welcome screen.</span></span>

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="33098-123">Obtenha o banco de dados de exemplo AdventureWorks para SQL Server</span><span class="sxs-lookup"><span data-stu-id="33098-123">Get the AdventureWorks sample database for SQL Server</span></span>

<span data-ttu-id="33098-124">Baixe o banco de dados de exemplo AdventureWorks para SQL Server do seguinte repositório GitHub:</span><span class="sxs-lookup"><span data-stu-id="33098-124">Download the AdventureWorks sample database for SQL Server from the following GitHub repository:</span></span>

[<span data-ttu-id="33098-125">Bancos de dados de exemplo do AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="33098-125">AdventureWorks sample databases</span></span>](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

<span data-ttu-id="33098-126">Depois de baixar um dos arquivos de backup do banco de dados ( \* . bak), restaure o backup para uma instância do SQL Server usando o SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="33098-126">After you download one of the database backup (\*.bak) files, restore the backup to an instance of SQL Server by using SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="33098-127">Consulte [obter SQL Server Management Studio](#get_ssms).</span><span class="sxs-lookup"><span data-stu-id="33098-127">See [Get SQL Server Management Studio](#get_ssms).</span></span>

## <a name="get-sql-server-management-studio"></a><a name="get_ssms"></a> <span data-ttu-id="33098-128">Obter SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="33098-128">Get SQL Server Management Studio</span></span>

<span data-ttu-id="33098-129">Se desejar exibir ou modificar um banco de dados que você baixou, você poderá usar o SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="33098-129">If you want to view or modify a database that you've downloaded, you can use SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="33098-130">Baixe o SSMS da seguinte página:</span><span class="sxs-lookup"><span data-stu-id="33098-130">Download SSMS from the following page:</span></span>

[<span data-ttu-id="33098-131">Baixar o SQL Server Management Studio (SSMS)</span><span class="sxs-lookup"><span data-stu-id="33098-131">Download SQL Server Management Studio (SSMS)</span></span>](/sql/ssms/download-sql-server-management-studio-ssms)

<span data-ttu-id="33098-132">Você também pode exibir e gerenciar bancos de dados no IDE (ambiente de desenvolvimento integrado) do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="33098-132">You can also view and manage databases in the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="33098-133">No [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019), conecte-se ao banco de dados do **pesquisador de objetos do SQL Server**ou crie uma conexão com o banco de dado no **Gerenciador de servidores**.</span><span class="sxs-lookup"><span data-stu-id="33098-133">In [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019), connect to the database from **SQL Server Object Explorer**, or create a Data Connection to the database in **Server Explorer**.</span></span> <span data-ttu-id="33098-134">Abra esses painéis do Explorer no menu **Exibir** .</span><span class="sxs-lookup"><span data-stu-id="33098-134">Open these explorer panes from the **View** menu.</span></span>

## <a name="get-sql-server-express"></a><a name="get_sql"></a> <span data-ttu-id="33098-135">Obter SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="33098-135">Get SQL Server Express</span></span>

<span data-ttu-id="33098-136">SQL Server Express é uma edição gratuita de nível de entrada do SQL Server que você pode redistribuir com aplicativos.</span><span class="sxs-lookup"><span data-stu-id="33098-136">SQL Server Express is a free, entry-level edition of SQL Server that you can redistribute with applications.</span></span> <span data-ttu-id="33098-137">Baixe SQL Server Express da seguinte página:</span><span class="sxs-lookup"><span data-stu-id="33098-137">Download SQL Server Express from the following page:</span></span>
  
[<span data-ttu-id="33098-138">Edição do SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="33098-138">SQL Server Express Edition</span></span>](https://www.microsoft.com/sql-server/sql-server-editions-express)

<span data-ttu-id="33098-139">Se você estiver usando o [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019), o SQL Server Express LocalDB será incluído na edição gratuita da Comunidade do Visual Studio, bem como nas edições Professional e superior.</span><span class="sxs-lookup"><span data-stu-id="33098-139">If you're using [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019), SQL Server Express LocalDB is included in the free Community edition of Visual Studio, as well as the Professional and higher editions.</span></span>  

## <a name="see-also"></a><span data-ttu-id="33098-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="33098-140">See also</span></span>

- [<span data-ttu-id="33098-141">Introdução</span><span class="sxs-lookup"><span data-stu-id="33098-141">Getting Started</span></span>](getting-started.md)
