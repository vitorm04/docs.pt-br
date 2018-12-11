---
title: Obter os bancos de dados do SQL Server de exemplo para exemplos de código do ADO.NET
description: Baixe os bancos de dados do exemplo do SQL Server usados nos exemplos de código na documentação do ADO.NET, bem como ferramentas de gerenciamento e do SQL Server
ms.date: 10/18/2018
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 8ab65f992c9cf2b65271a237fa06eb96e358ae6a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153482"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a><span data-ttu-id="71692-103">Obter os bancos de dados de exemplo para exemplos de código do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="71692-103">Get the sample databases for ADO.NET code samples</span></span>

<span data-ttu-id="71692-104">Um número de exemplos e explicações passo a passo no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentação usar bancos de dados do SQL Server e SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="71692-104">A number of examples and walkthroughs in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation use sample SQL Server databases and SQL Server Express.</span></span> <span data-ttu-id="71692-105">Você pode baixar esses produtos gratuitos da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="71692-105">You can download these products free of charge from Microsoft.</span></span>

## <a name="get-the-northwind-sample-database-for-sql-server"></a><span data-ttu-id="71692-106">Obter dados de exemplo Northwind para SQL Server</span><span class="sxs-lookup"><span data-stu-id="71692-106">Get the Northwind sample database for SQL Server</span></span>

<span data-ttu-id="71692-107">Baixe o script `instnwnd.sql` do repositório do GitHub para criar e carregar dados de exemplo Northwind do SQL Server:</span><span class="sxs-lookup"><span data-stu-id="71692-107">Download the script `instnwnd.sql` from the following GitHub repository to create and load the Northwind sample database for SQL Server:</span></span>

[<span data-ttu-id="71692-108">Bancos de dados de exemplo do Northwind e pubs para o Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="71692-108">Northwind and pubs sample databases for Microsoft SQL Server</span></span>](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

<span data-ttu-id="71692-109">Antes de usar o banco de dados Northwind, você precisa executar o baixado `instnwnd.sql` arquivo de script para recriar o banco de dados em uma instância do SQL Server usando [SQL Server Management Studio](#get_ssms) ou uma ferramenta semelhante.</span><span class="sxs-lookup"><span data-stu-id="71692-109">Before you can use the Northwind database, you have to run the downloaded `instnwnd.sql` script file to recreate the database on an instance of SQL Server by using [SQL Server Management Studio](#get_ssms) or a similar tool.</span></span> <span data-ttu-id="71692-110">Siga as instruções no arquivo Leiame no repositório.</span><span class="sxs-lookup"><span data-stu-id="71692-110">Follow the instructions in the Readme file in the repository.</span></span>

> [!TIP]
> <span data-ttu-id="71692-111">Se você estiver procurando por banco de dados Northwind do Microsoft Access, consulte [instalar o banco de dados de exemplo Northwind para o Microsoft Access](#northwind_access).</span><span class="sxs-lookup"><span data-stu-id="71692-111">If you're looking for the Northwind database for Microsoft Access, see [Install the Northwind sample database for Microsoft Access](#northwind_access).</span></span>

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="71692-112">Obter dados de exemplo AdventureWorks para SQL Server</span><span class="sxs-lookup"><span data-stu-id="71692-112">Get the AdventureWorks sample database for SQL Server</span></span>

<span data-ttu-id="71692-113">Baixe o banco de dados de exemplo AdventureWorks para SQL Server do repositório do GitHub a seguir:</span><span class="sxs-lookup"><span data-stu-id="71692-113">Download the AdventureWorks sample database for SQL Server from the following GitHub repository:</span></span>

[<span data-ttu-id="71692-114">Bancos de dados de exemplo AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="71692-114">AdventureWorks sample databases</span></span>](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

<span data-ttu-id="71692-115">Depois de baixar um backup de banco de dados de (\*. bak) arquivos, restaure o backup para uma instância do SQL Server usando o SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="71692-115">After you download one of the database backup (\*.bak) files, restore the backup to an instance of SQL Server by using SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="71692-116">Ver [obter o SQL Server Management Studio](#get_ssms).</span><span class="sxs-lookup"><span data-stu-id="71692-116">See [Get SQL Server Management Studio](#get_ssms).</span></span>

## <a name="get_sql"></a> <span data-ttu-id="71692-117">Obtenha o SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="71692-117">Get SQL Server Express</span></span>

<span data-ttu-id="71692-118">SQL Server Express é uma edição gratuita do SQL Server que pode ser redistribuído com aplicativos de nível básica.</span><span class="sxs-lookup"><span data-stu-id="71692-118">SQL Server Express is a free, entry-level edition of SQL Server that you can redistribute with applications.</span></span> <span data-ttu-id="71692-119">Baixe o SQL Server Express da seguinte página:</span><span class="sxs-lookup"><span data-stu-id="71692-119">Download SQL Server Express from the following page:</span></span>
  
[<span data-ttu-id="71692-120">SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="71692-120">SQL Server Express Edition</span></span>](https://www.microsoft.com/sql-server/sql-server-editions-express)

<span data-ttu-id="71692-121">Se você estiver usando [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB está incluído na Community edition gratuita do Visual Studio, bem como as edições Professional e superior.</span><span class="sxs-lookup"><span data-stu-id="71692-121">If you're using [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB is included in the free Community edition of Visual Studio, as well as the Professional and higher editions.</span></span>  

## <a name="get_ssms"></a> <span data-ttu-id="71692-122">Obtenha o SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="71692-122">Get SQL Server Management Studio</span></span>
<span data-ttu-id="71692-123">Se você quiser exibir ou modificar um banco de dados que você baixou, você pode usar o SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="71692-123">If you want to view or modify a database that you've downloaded, you can use SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="71692-124">Baixe o SSMS na seguinte página:</span><span class="sxs-lookup"><span data-stu-id="71692-124">Download SSMS from the following page:</span></span>

[<span data-ttu-id="71692-125">Baixar o SQL Server Management Studio (SSMS)</span><span class="sxs-lookup"><span data-stu-id="71692-125">Download SQL Server Management Studio (SSMS)</span></span>](/sql/ssms/download-sql-server-management-studio-ssms) 

<span data-ttu-id="71692-126">Você também pode exibir e gerenciar bancos de dados no ambiente de desenvolvimento integrado (IDE) do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="71692-126">You can also view and manage databases in the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="71692-127">Na [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), conecte-se ao banco de dados do **Pesquisador de objetos do SQL Server**, ou criar uma Conexão de dados ao banco de dados **Gerenciador de servidores**.</span><span class="sxs-lookup"><span data-stu-id="71692-127">In [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), connect to the database from **SQL Server Object Explorer**, or create a Data Connection to the database in **Server Explorer**.</span></span> <span data-ttu-id="71692-128">Abrir esses painéis explorer do **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="71692-128">Open these explorer panes from the **View** menu.</span></span>

## <a name="northwind_access"></a> <span data-ttu-id="71692-129">Instalar o banco de dados de exemplo Northwind do Microsoft Access</span><span class="sxs-lookup"><span data-stu-id="71692-129">Install the Northwind sample database for Microsoft Access</span></span>

<span data-ttu-id="71692-130">O banco de dados de exemplo Northwind para o Microsoft Access não está disponível no Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="71692-130">The Northwind sample database for Microsoft Access is not available on the Microsoft Download Center.</span></span> <span data-ttu-id="71692-131">Para instalar o Northwind diretamente de dentro do Access, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="71692-131">To install Northwind directly from within Access, do the following things:</span></span>

1. <span data-ttu-id="71692-132">Abra o Access.</span><span class="sxs-lookup"><span data-stu-id="71692-132">Open Access.</span></span>

1. <span data-ttu-id="71692-133">ENTER **Northwind** na **pesquisar modelos Online** caixa e, em seguida, selecione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="71692-133">Enter **Northwind** in the **Search for Online Templates** box, and then select **Enter**.</span></span>

1. <span data-ttu-id="71692-134">Na tela de resultados, selecione **Northwind**.</span><span class="sxs-lookup"><span data-stu-id="71692-134">On the results screen, select **Northwind**.</span></span> <span data-ttu-id="71692-135">Uma nova janela é aberta com uma descrição do banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="71692-135">A new window opens with a description of the Northwind database.</span></span>

1. <span data-ttu-id="71692-136">Na nova janela, na **nome do arquivo** texto caixa, forneça um nome de arquivo de sua cópia do banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="71692-136">In the new window, in the **File Name** text box, provide a filename for your copy of the Northwind database.</span></span>

1. <span data-ttu-id="71692-137">Selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="71692-137">Select **Create**.</span></span> <span data-ttu-id="71692-138">Acesso downloads para o banco de dados Northwind e prepara o arquivo.</span><span class="sxs-lookup"><span data-stu-id="71692-138">Access downloads the Northwind database and prepares the file.</span></span>

1. <span data-ttu-id="71692-139">Quando esse processo for concluído, o banco de dados é aberta com uma tela de boas-vindas.</span><span class="sxs-lookup"><span data-stu-id="71692-139">When this process is complete, the database opens with a Welcome screen.</span></span>

## <a name="see-also"></a><span data-ttu-id="71692-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71692-140">See also</span></span>

- [<span data-ttu-id="71692-141">Introdução</span><span class="sxs-lookup"><span data-stu-id="71692-141">Getting Started</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
