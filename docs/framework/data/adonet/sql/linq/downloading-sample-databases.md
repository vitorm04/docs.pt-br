---
title: Obter os bancos de dados de exemplo para exemplos de código do ADO.NET
description: Baixe os bancos de dados de exemplo usados nos exemplos de código na documentação do ADO.NET, bem como ferramentas de gerenciamento e do SQL Server
ms.date: 10/12/2018
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 75ae1895d683b669f51b33130fc2f47010e39814
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49347488"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a><span data-ttu-id="c5a0a-103">Obter os bancos de dados de exemplo para exemplos de código do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c5a0a-103">Get the sample databases for ADO.NET code samples</span></span>

<span data-ttu-id="c5a0a-104">Um número de exemplos e explicações passo a passo no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentação usar bancos de dados de exemplo e o SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="c5a0a-104">A number of samples and walkthroughs in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation use sample databases and SQL Server Express.</span></span> <span data-ttu-id="c5a0a-105">Você pode baixar esses produtos gratuitos da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c5a0a-105">You can download these products free of charge from Microsoft.</span></span>

## <a name="get-the-adventureworks-sample-database"></a><span data-ttu-id="c5a0a-106">Obter dados de exemplo AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="c5a0a-106">Get the AdventureWorks sample database</span></span>

<span data-ttu-id="c5a0a-107">Baixe o banco de dados de exemplo AdventureWorks do repositório do GitHub a seguir:</span><span class="sxs-lookup"><span data-stu-id="c5a0a-107">Download the AdventureWorks sample database from the following GitHub repository:</span></span>

[<span data-ttu-id="c5a0a-108">Bancos de dados de exemplo AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="c5a0a-108">AdventureWorks sample databases</span></span>](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

<span data-ttu-id="c5a0a-109">Depois de baixar um backup de banco de dados de (\*. bak) arquivos, restaure o backup para uma instância do SQL Server usando o SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="c5a0a-109">After you download one of the database backup (\*.bak) files, restore the backup to an instance of SQL Server by using SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="c5a0a-110">Ver [obter o SQL Server Management Studio](#get_ssms).</span><span class="sxs-lookup"><span data-stu-id="c5a0a-110">See [Get SQL Server Management Studio](#get_ssms).</span></span>

## <a name="get-the-northwind-sample-database"></a><span data-ttu-id="c5a0a-111">Obter dados de exemplo Northwind</span><span class="sxs-lookup"><span data-stu-id="c5a0a-111">Get the Northwind sample database</span></span>

<span data-ttu-id="c5a0a-112">Baixe o banco de dados de exemplo Northwind na seguinte página no Microsoft Download Center:</span><span class="sxs-lookup"><span data-stu-id="c5a0a-112">Download the Northwind sample database from the following page in the Microsoft Download Center:</span></span>

[<span data-ttu-id="c5a0a-113">Northwind e Pubs Sample Databases</span><span class="sxs-lookup"><span data-stu-id="c5a0a-113">Northwind and Pubs Sample Databases</span></span>](https://go.microsoft.com/fwlink?linkid=64296)

<span data-ttu-id="c5a0a-114">Depois que o arquivo é baixado, clique duas vezes no arquivo para extrair os bancos de dados e scripts.</span><span class="sxs-lookup"><span data-stu-id="c5a0a-114">After the file has downloaded, double-click the file to extract the databases and scripts.</span></span> <span data-ttu-id="c5a0a-115">Por padrão, os arquivos são instalados na pasta `<drive>:\SQL Server 2000 Sample Databases`.</span><span class="sxs-lookup"><span data-stu-id="c5a0a-115">By default, the files are installed in the folder `<drive>:\SQL Server 2000 Sample Databases`.</span></span>

<span data-ttu-id="c5a0a-116">Antes de usar o banco de dados Northwind, você deve fazer uma das seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="c5a0a-116">Before you can use the Northwind database, you have to do one of the following things:</span></span>

- <span data-ttu-id="c5a0a-117">Recriar o banco de dados em uma instância do SQL Server executando o `instnwnd.sql` arquivo de script na pasta de instalação.</span><span class="sxs-lookup"><span data-stu-id="c5a0a-117">Recreate the database on an instance of SQL Server by running the `instnwnd.sql` script file in the installation folder.</span></span>

- <span data-ttu-id="c5a0a-118">Anexar a `northwnd.mdf` arquivo com correspondente `*.ldf` arquivo de log para uma instância do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c5a0a-118">Attach the `northwnd.mdf` file with its corresponding `*.ldf` log file to an instance of SQL Server.</span></span>

## <a name="get_sql"></a> <span data-ttu-id="c5a0a-119">Obtenha o SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="c5a0a-119">Get SQL Server Express</span></span>

<span data-ttu-id="c5a0a-120">SQL Server Express é uma edição gratuita do SQL Server que pode ser redistribuído com aplicativos de nível básica.</span><span class="sxs-lookup"><span data-stu-id="c5a0a-120">SQL Server Express is a free, entry-level edition of SQL Server that you can redistribute with applications.</span></span> <span data-ttu-id="c5a0a-121">Baixe o SQL Server Express da seguinte página:</span><span class="sxs-lookup"><span data-stu-id="c5a0a-121">Download SQL Server Express from the following page:</span></span>
  
[<span data-ttu-id="c5a0a-122">Edições Express do SQL Server</span><span class="sxs-lookup"><span data-stu-id="c5a0a-122">SQL Server Express Editions</span></span>](https://www.microsoft.com/sql-server/sql-server-editions-express)

<span data-ttu-id="c5a0a-123">Se você estiver usando [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB está incluído na Community edition, bem como as edições Professional e superior.</span><span class="sxs-lookup"><span data-stu-id="c5a0a-123">If you're using [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB is included in the Community edition as well as the Professional and higher editions.</span></span>  

## <a name="get_ssms"></a> <span data-ttu-id="c5a0a-124">Obtenha o SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c5a0a-124">Get SQL Server Management Studio</span></span>
<span data-ttu-id="c5a0a-125">Se você quiser exibir ou modificar um banco de dados que você baixou, você pode usar o SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="c5a0a-125">If you want to view or modify a database that you've downloaded, you can use SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="c5a0a-126">Baixe o SSMS na seguinte página:</span><span class="sxs-lookup"><span data-stu-id="c5a0a-126">Download SSMS from the following page:</span></span>

[<span data-ttu-id="c5a0a-127">Baixar o SQL Server Management Studio (SSMS)</span><span class="sxs-lookup"><span data-stu-id="c5a0a-127">Download SQL Server Management Studio (SSMS)</span></span>](/sql/ssms/download-sql-server-management-studio-ssms) 

<span data-ttu-id="c5a0a-128">Você também pode exibir e gerenciar bancos de dados no ambiente de desenvolvimento integrado (IDE) do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c5a0a-128">You can also view and manage databases in the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="c5a0a-129">Na [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), conecte-se ao banco de dados do **Pesquisador de objetos do SQL Server**, ou criar uma Conexão de dados ao banco de dados **Gerenciador de servidores**.</span><span class="sxs-lookup"><span data-stu-id="c5a0a-129">In [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), connect to the database from **SQL Server Object Explorer**, or create a Data Connection to the database in **Server Explorer**.</span></span> <span data-ttu-id="c5a0a-130">Abrir esses painéis explorer do **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="c5a0a-130">Open these explorer panes from the **View** menu.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c5a0a-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c5a0a-131">See also</span></span>

- [<span data-ttu-id="c5a0a-132">Introdução</span><span class="sxs-lookup"><span data-stu-id="c5a0a-132">Getting Started</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
