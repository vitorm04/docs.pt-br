---
title: Operações de cópia em massa no SQL Server
description: Aprenda a usar a classe SqlBulkCopy para escrever soluções de código gerenciado que copiam arquivos grandes em massa em tabelas ou exibições em bancos de dados SQL Server.
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: 4f877836aa45efe162cce3c42cb5733f86deab2c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286514"
---
# <a name="bulk-copy-operations-in-sql-server"></a><span data-ttu-id="cd06d-103">Operações de cópia em massa no SQL Server</span><span class="sxs-lookup"><span data-stu-id="cd06d-103">Bulk Copy Operations in SQL Server</span></span>
<span data-ttu-id="cd06d-104">O Microsoft SQL Server inclui um utilitário de linha de comando popular chamado **bcp** para copiar rapidamente grandes arquivos em massa em tabelas ou exibições em bancos de dados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="cd06d-104">Microsoft SQL Server includes a popular command-line utility named **bcp** for quickly bulk copying large files into tables or views in SQL Server databases.</span></span> <span data-ttu-id="cd06d-105">A classe <xref:System.Data.SqlClient.SqlBulkCopy> permite escrever soluções de código gerenciado que fornecem funcionalidade semelhante.</span><span class="sxs-lookup"><span data-stu-id="cd06d-105">The <xref:System.Data.SqlClient.SqlBulkCopy> class allows you to write managed code solutions that provide similar functionality.</span></span> <span data-ttu-id="cd06d-106">Há outras maneiras de carregar dados em uma tabela do SQL Server (instruções INSERT, por exemplo), mas <xref:System.Data.SqlClient.SqlBulkCopy> oferece uma vantagem de desempenho significativa sobre eles.</span><span class="sxs-lookup"><span data-stu-id="cd06d-106">There are other ways to load data into a SQL Server table (INSERT statements, for example) but <xref:System.Data.SqlClient.SqlBulkCopy> offers a significant performance advantage over them.</span></span>  
  
 <span data-ttu-id="cd06d-107">A classe <xref:System.Data.SqlClient.SqlBulkCopy> pode ser usada para gravar dados somente em tabelas do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="cd06d-107">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="cd06d-108">Mas a fonte de dados não está limitada a SQL Server; qualquer fonte de dados pode ser usada, desde que os dados possam ser carregados em uma <xref:System.Data.DataTable> instância ou lidos com uma <xref:System.Data.IDataReader> instância do.</span><span class="sxs-lookup"><span data-stu-id="cd06d-108">But the data source is not limited to SQL Server; any data source can be used, as long as the data can be loaded to a <xref:System.Data.DataTable> instance or read with a <xref:System.Data.IDataReader> instance.</span></span>  
  
 <span data-ttu-id="cd06d-109">Usando a classe <xref:System.Data.SqlClient.SqlBulkCopy>, você pode executar:</span><span class="sxs-lookup"><span data-stu-id="cd06d-109">Using the <xref:System.Data.SqlClient.SqlBulkCopy> class, you can perform:</span></span>  
  
- <span data-ttu-id="cd06d-110">Uma única operação de cópia em massa</span><span class="sxs-lookup"><span data-stu-id="cd06d-110">A single bulk copy operation</span></span>  
  
- <span data-ttu-id="cd06d-111">Várias operações de cópia em massa</span><span class="sxs-lookup"><span data-stu-id="cd06d-111">Multiple bulk copy operations</span></span>  
  
- <span data-ttu-id="cd06d-112">Uma operação de cópia em massa dentro de uma transação</span><span class="sxs-lookup"><span data-stu-id="cd06d-112">A bulk copy operation within a transaction</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cd06d-113">Ao usar o .NET Framework versão 1.1 ou anterior (que não dá suporte à classe <xref:System.Data.SqlClient.SqlBulkCopy>), você pode executar a instrução **BULK INSERT** do Transact-SQL no SQL Server usando o objeto <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="cd06d-113">When using .NET Framework version 1.1 or earlier (which does not support the <xref:System.Data.SqlClient.SqlBulkCopy> class), you can execute the SQL Server Transact-SQL **BULK INSERT** statement using the <xref:System.Data.SqlClient.SqlCommand> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cd06d-114">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="cd06d-114">In This Section</span></span>  
 [<span data-ttu-id="cd06d-115">Configuração de exemplo de cópia em massa</span><span class="sxs-lookup"><span data-stu-id="cd06d-115">Bulk Copy Example Setup</span></span>](bulk-copy-example-setup.md)  
 <span data-ttu-id="cd06d-116">Descreve as tabelas usadas nos exemplos de cópia em massa e fornece scripts SQL para criar as tabelas no banco de dados AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="cd06d-116">Describes the tables used in the bulk copy examples and provides SQL scripts for creating the tables in the AdventureWorks database.</span></span>  
  
 [<span data-ttu-id="cd06d-117">Operações de cópia em massa única</span><span class="sxs-lookup"><span data-stu-id="cd06d-117">Single Bulk Copy Operations</span></span>](single-bulk-copy-operations.md)  
 <span data-ttu-id="cd06d-118">Descreve como fazer uma cópia em massa de dados em uma instância do SQL Server usando a classe <xref:System.Data.SqlClient.SqlBulkCopy> e como executar a operação de cópia em massa usando instruções Transact-SQL e a classe <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="cd06d-118">Describes how to do a single bulk copy of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class, and how to perform the bulk copy operation using Transact-SQL statements and the <xref:System.Data.SqlClient.SqlCommand> class.</span></span>  
  
 [<span data-ttu-id="cd06d-119">Várias operações de cópia em massa</span><span class="sxs-lookup"><span data-stu-id="cd06d-119">Multiple Bulk Copy Operations</span></span>](multiple-bulk-copy-operations.md)  
 <span data-ttu-id="cd06d-120">Descreve como realizar várias operações de cópia em massa de dados em uma instância do SQL Server usando a classe <xref:System.Data.SqlClient.SqlBulkCopy>.</span><span class="sxs-lookup"><span data-stu-id="cd06d-120">Describes how to do multiple bulk copy operations of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span>  
  
 [<span data-ttu-id="cd06d-121">Operações de cópia em massa e transação</span><span class="sxs-lookup"><span data-stu-id="cd06d-121">Transaction and Bulk Copy Operations</span></span>](transaction-and-bulk-copy-operations.md)  
 <span data-ttu-id="cd06d-122">Descreve como executar uma operação de cópia em massa em uma transação, incluindo como fazer commit ou reverter a transação.</span><span class="sxs-lookup"><span data-stu-id="cd06d-122">Describes how to perform a bulk copy operation within a transaction, including how to commit or rollback the transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd06d-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="cd06d-123">See also</span></span>

- [<span data-ttu-id="cd06d-124">SQL Server e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cd06d-124">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="cd06d-125">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cd06d-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
