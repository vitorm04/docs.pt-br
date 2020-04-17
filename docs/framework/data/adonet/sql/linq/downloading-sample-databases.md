---
title: Obtenha os bancos de dados sql server de amostra para amostras de código ADO.NET
description: Baixe os bancos de dados sql server de amostra usados nas amostras de código na documentação ADO.NET, bem como sql server e ferramentas de gerenciamento
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 3449f502834f449f5023bd52457d45ffaf9b0fa1
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607978"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a><span data-ttu-id="e52a0-103">Obtenha os bancos de dados de amostras para amostras de código ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e52a0-103">Get the sample databases for ADO.NET code samples</span></span>

<span data-ttu-id="e52a0-104">Uma série de exemplos e passo [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] a passo na documentação usam bancos de dados SQL Server de amostra e SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="e52a0-104">A number of examples and walkthroughs in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation use sample SQL Server databases and SQL Server Express.</span></span> <span data-ttu-id="e52a0-105">Você pode baixar esses produtos gratuitamente da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e52a0-105">You can download these products free of charge from Microsoft.</span></span>

## <a name="get-the-northwind-sample-database-for-sql-server"></a><span data-ttu-id="e52a0-106">Obtenha o banco de dados de amostra do Northwind para SQL Server</span><span class="sxs-lookup"><span data-stu-id="e52a0-106">Get the Northwind sample database for SQL Server</span></span>

<span data-ttu-id="e52a0-107">Baixe o `instnwnd.sql` script do seguinte repositório do GitHub para criar e carregar o banco de dados de amostra do Northwind para o SQL Server:</span><span class="sxs-lookup"><span data-stu-id="e52a0-107">Download the script `instnwnd.sql` from the following GitHub repository to create and load the Northwind sample database for SQL Server:</span></span>

[<span data-ttu-id="e52a0-108">Northwind e pubs mostram bancos de dados para Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="e52a0-108">Northwind and pubs sample databases for Microsoft SQL Server</span></span>](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

<span data-ttu-id="e52a0-109">Antes de usar o banco de dados Northwind, você tem que executar o arquivo de script baixado `instnwnd.sql` para recriar o banco de dados em uma instância do SQL Server usando o [SQL Server Management Studio](#get_ssms) ou uma ferramenta semelhante.</span><span class="sxs-lookup"><span data-stu-id="e52a0-109">Before you can use the Northwind database, you have to run the downloaded `instnwnd.sql` script file to recreate the database on an instance of SQL Server by using [SQL Server Management Studio](#get_ssms) or a similar tool.</span></span> <span data-ttu-id="e52a0-110">Siga as instruções no arquivo Readme no repositório.</span><span class="sxs-lookup"><span data-stu-id="e52a0-110">Follow the instructions in the Readme file in the repository.</span></span>

> [!TIP]
> <span data-ttu-id="e52a0-111">Se você estiver procurando o banco de dados Northwind para o Microsoft Access, consulte [Instalar o banco de dados de amostras do Northwind para o Microsoft Access](#northwind_access).</span><span class="sxs-lookup"><span data-stu-id="e52a0-111">If you're looking for the Northwind database for Microsoft Access, see [Install the Northwind sample database for Microsoft Access](#northwind_access).</span></span>

## <a name="get-the-northwind-sample-database-for-microsoft-access"></a><a name="northwind_access"></a><span data-ttu-id="e52a0-112">Obtenha o banco de dados de exemplo do Northwind para o Microsoft Access</span><span class="sxs-lookup"><span data-stu-id="e52a0-112">Get the Northwind sample database for Microsoft Access</span></span>

<span data-ttu-id="e52a0-113">O banco de dados de exemplo northwind para O Microsoft Access não está disponível no Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="e52a0-113">The Northwind sample database for Microsoft Access is not available on the Microsoft Download Center.</span></span> <span data-ttu-id="e52a0-114">Para instalar o Northwind diretamente do Access, faça as seguintes coisas:</span><span class="sxs-lookup"><span data-stu-id="e52a0-114">To install Northwind directly from within Access, do the following things:</span></span>

1. <span data-ttu-id="e52a0-115">Acesso Aberto.</span><span class="sxs-lookup"><span data-stu-id="e52a0-115">Open Access.</span></span>

1. <span data-ttu-id="e52a0-116">Digite **Northwind** na caixa **Pesquisar modelos online** e, em seguida, selecione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="e52a0-116">Enter **Northwind** in the **Search for Online Templates** box, and then select **Enter**.</span></span>

1. <span data-ttu-id="e52a0-117">Na tela de resultados, selecione **Northwind**.</span><span class="sxs-lookup"><span data-stu-id="e52a0-117">On the results screen, select **Northwind**.</span></span> <span data-ttu-id="e52a0-118">Uma nova janela se abre com uma descrição do banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="e52a0-118">A new window opens with a description of the Northwind database.</span></span>

1. <span data-ttu-id="e52a0-119">Na nova janela, na caixa de texto **Nome do arquivo,** forneça um nome de arquivo para sua cópia do banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="e52a0-119">In the new window, in the **File Name** text box, provide a filename for your copy of the Northwind database.</span></span>

1. <span data-ttu-id="e52a0-120">Selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="e52a0-120">Select **Create**.</span></span> <span data-ttu-id="e52a0-121">O Access baixa o banco de dados northwind e prepara o arquivo.</span><span class="sxs-lookup"><span data-stu-id="e52a0-121">Access downloads the Northwind database and prepares the file.</span></span>

1. <span data-ttu-id="e52a0-122">Quando esse processo estiver concluído, o banco de dados será aberto com uma tela de boas-vindas.</span><span class="sxs-lookup"><span data-stu-id="e52a0-122">When this process is complete, the database opens with a Welcome screen.</span></span>

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="e52a0-123">Obtenha o banco de dados de exemplo AdventureWorks para SQL Server</span><span class="sxs-lookup"><span data-stu-id="e52a0-123">Get the AdventureWorks sample database for SQL Server</span></span>

<span data-ttu-id="e52a0-124">Baixe o banco de dados de exemplo AdventureWorks para SQL Server no seguinte repositório do GitHub:</span><span class="sxs-lookup"><span data-stu-id="e52a0-124">Download the AdventureWorks sample database for SQL Server from the following GitHub repository:</span></span>

[<span data-ttu-id="e52a0-125">Bancos de dados de exemplo do AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="e52a0-125">AdventureWorks sample databases</span></span>](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

<span data-ttu-id="e52a0-126">Depois de baixar um dos\*arquivos de backup do banco de dados (.bak), restaure o backup em uma instância do SQL Server usando o SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="e52a0-126">After you download one of the database backup (\*.bak) files, restore the backup to an instance of SQL Server by using SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="e52a0-127">Consulte [get SQL Server Management Studio](#get_ssms).</span><span class="sxs-lookup"><span data-stu-id="e52a0-127">See [Get SQL Server Management Studio](#get_ssms).</span></span>

## <a name="get-sql-server-management-studio"></a><a name="get_ssms"></a><span data-ttu-id="e52a0-128">Obtenha o SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e52a0-128">Get SQL Server Management Studio</span></span>
<span data-ttu-id="e52a0-129">Se você quiser visualizar ou modificar um banco de dados que você baixou, você pode usar o SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="e52a0-129">If you want to view or modify a database that you've downloaded, you can use SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="e52a0-130">Baixe SSMS na seguinte página:</span><span class="sxs-lookup"><span data-stu-id="e52a0-130">Download SSMS from the following page:</span></span>

[<span data-ttu-id="e52a0-131">Baixar o SQL Server Management Studio (SSMS)</span><span class="sxs-lookup"><span data-stu-id="e52a0-131">Download SQL Server Management Studio (SSMS)</span></span>](/sql/ssms/download-sql-server-management-studio-ssms)

<span data-ttu-id="e52a0-132">Você também pode visualizar e gerenciar bancos de dados no ambiente de desenvolvimento integrado (IDE) do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e52a0-132">You can also view and manage databases in the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="e52a0-133">No [Visual Studio,](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)conecte-se ao banco de dados do **SQL Server Object Explorer**ou crie uma conexão de dados com o banco de dados no Server **Explorer**.</span><span class="sxs-lookup"><span data-stu-id="e52a0-133">In [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019), connect to the database from **SQL Server Object Explorer**, or create a Data Connection to the database in **Server Explorer**.</span></span> <span data-ttu-id="e52a0-134">Abra esses painéis de explorador no menu **Ver.**</span><span class="sxs-lookup"><span data-stu-id="e52a0-134">Open these explorer panes from the **View** menu.</span></span>

## <a name="get-sql-server-express"></a><a name="get_sql"></a><span data-ttu-id="e52a0-135">Obter SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="e52a0-135">Get SQL Server Express</span></span>

<span data-ttu-id="e52a0-136">SQL Server Express é uma edição gratuita e de nível básico do SQL Server que você pode redistribuir com aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e52a0-136">SQL Server Express is a free, entry-level edition of SQL Server that you can redistribute with applications.</span></span> <span data-ttu-id="e52a0-137">Baixe SQL Server Express na seguinte página:</span><span class="sxs-lookup"><span data-stu-id="e52a0-137">Download SQL Server Express from the following page:</span></span>
  
[<span data-ttu-id="e52a0-138">SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="e52a0-138">SQL Server Express Edition</span></span>](https://www.microsoft.com/sql-server/sql-server-editions-express)

<span data-ttu-id="e52a0-139">Se você estiver usando [o Visual Studio,](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)o SQL Server Express LocalDB está incluído na edição gratuita da Comunidade do Visual Studio, bem como nas edições Profissional e superior.</span><span class="sxs-lookup"><span data-stu-id="e52a0-139">If you're using [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019), SQL Server Express LocalDB is included in the free Community edition of Visual Studio, as well as the Professional and higher editions.</span></span>  

## <a name="see-also"></a><span data-ttu-id="e52a0-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="e52a0-140">See also</span></span>

- [<span data-ttu-id="e52a0-141">Introdução</span><span class="sxs-lookup"><span data-stu-id="e52a0-141">Getting Started</span></span>](getting-started.md)
