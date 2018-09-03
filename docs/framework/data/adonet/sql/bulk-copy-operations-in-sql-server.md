---
title: Operações de cópia em massa no SQL Server
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: 16709d1bdc03c767d1e3aed808de220bf91e76ee
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43455660"
---
# <a name="bulk-copy-operations-in-sql-server"></a><span data-ttu-id="8dba2-102">Operações de cópia em massa no SQL Server</span><span class="sxs-lookup"><span data-stu-id="8dba2-102">Bulk Copy Operations in SQL Server</span></span>
<span data-ttu-id="8dba2-103">Microsoft SQL Server inclui um utilitário de linha de comando popular chamado **bcp** para rapidamente em massa copiar arquivos grandes em tabelas ou exibições em bancos de dados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8dba2-103">Microsoft SQL Server includes a popular command-line utility named **bcp** for quickly bulk copying large files into tables or views in SQL Server databases.</span></span> <span data-ttu-id="8dba2-104">O <xref:System.Data.SqlClient.SqlBulkCopy> classe permite que você escrever soluções de código gerenciado que fornecem funcionalidade semelhante.</span><span class="sxs-lookup"><span data-stu-id="8dba2-104">The <xref:System.Data.SqlClient.SqlBulkCopy> class allows you to write managed code solutions that provide similar functionality.</span></span> <span data-ttu-id="8dba2-105">Há outras maneiras de carregar dados em uma tabela do SQL Server (instruções INSERT, por exemplo), mas <xref:System.Data.SqlClient.SqlBulkCopy> oferece uma vantagem de desempenho significativa sobre eles.</span><span class="sxs-lookup"><span data-stu-id="8dba2-105">There are other ways to load data into a SQL Server table (INSERT statements, for example) but <xref:System.Data.SqlClient.SqlBulkCopy> offers a significant performance advantage over them.</span></span>  
  
 <span data-ttu-id="8dba2-106">O <xref:System.Data.SqlClient.SqlBulkCopy> classe pode ser usado para gravar dados somente em tabelas do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8dba2-106">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="8dba2-107">Mas a fonte de dados não está limitada ao SQL Server; qualquer fonte de dados pode ser usada, desde que os dados podem ser carregados para um <xref:System.Data.DataTable> da instância ou de leitura com um <xref:System.Data.IDataReader> instância.</span><span class="sxs-lookup"><span data-stu-id="8dba2-107">But the data source is not limited to SQL Server; any data source can be used, as long as the data can be loaded to a <xref:System.Data.DataTable> instance or read with a <xref:System.Data.IDataReader> instance.</span></span>  
  
 <span data-ttu-id="8dba2-108">Usando o <xref:System.Data.SqlClient.SqlBulkCopy> classe, você pode executar:</span><span class="sxs-lookup"><span data-stu-id="8dba2-108">Using the <xref:System.Data.SqlClient.SqlBulkCopy> class, you can perform:</span></span>  
  
-   <span data-ttu-id="8dba2-109">Uma operação de cópia em massa único</span><span class="sxs-lookup"><span data-stu-id="8dba2-109">A single bulk copy operation</span></span>  
  
-   <span data-ttu-id="8dba2-110">Várias operações de cópia em massa</span><span class="sxs-lookup"><span data-stu-id="8dba2-110">Multiple bulk copy operations</span></span>  
  
-   <span data-ttu-id="8dba2-111">Uma operação de cópia em massa em uma transação</span><span class="sxs-lookup"><span data-stu-id="8dba2-111">A bulk copy operation within a transaction</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8dba2-112">Ao usar o .NET Framework versão 1.1 ou anterior (que não oferece suporte a <xref:System.Data.SqlClient.SqlBulkCopy> classe), você pode executar o SQL Server Transact-SQL **BULK INSERT** instrução usando o <xref:System.Data.SqlClient.SqlCommand> objeto.</span><span class="sxs-lookup"><span data-stu-id="8dba2-112">When using .NET Framework version 1.1 or earlier (which does not support the <xref:System.Data.SqlClient.SqlBulkCopy> class), you can execute the SQL Server Transact-SQL **BULK INSERT** statement using the <xref:System.Data.SqlClient.SqlCommand> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8dba2-113">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="8dba2-113">In This Section</span></span>  
 [<span data-ttu-id="8dba2-114">Configuração de exemplo de cópia em massa</span><span class="sxs-lookup"><span data-stu-id="8dba2-114">Bulk Copy Example Setup</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 <span data-ttu-id="8dba2-115">Descreve as tabelas usadas nos exemplos de cópia em massa e fornece scripts SQL para criar as tabelas no banco de dados AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="8dba2-115">Describes the tables used in the bulk copy examples and provides SQL scripts for creating the tables in the AdventureWorks database.</span></span>  
  
 [<span data-ttu-id="8dba2-116">Operações únicas de cópia em massa</span><span class="sxs-lookup"><span data-stu-id="8dba2-116">Single Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 <span data-ttu-id="8dba2-117">Descreve como fazer uma cópia em massa única dos dados em uma instância do SQL Server usando o <xref:System.Data.SqlClient.SqlBulkCopy> classe e como executar a operação de cópia em massa usando instruções Transact-SQL e o <xref:System.Data.SqlClient.SqlCommand> classe.</span><span class="sxs-lookup"><span data-stu-id="8dba2-117">Describes how to do a single bulk copy of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class, and how to perform the bulk copy operation using Transact-SQL statements and the <xref:System.Data.SqlClient.SqlCommand> class.</span></span>  
  
 [<span data-ttu-id="8dba2-118">Várias operações de cópia em massa</span><span class="sxs-lookup"><span data-stu-id="8dba2-118">Multiple Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 <span data-ttu-id="8dba2-119">Descreve como fazer várias operações de cópia em massa de dados em uma instância do SQL Server usando o <xref:System.Data.SqlClient.SqlBulkCopy> classe.</span><span class="sxs-lookup"><span data-stu-id="8dba2-119">Describes how to do multiple bulk copy operations of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span>  
  
 [<span data-ttu-id="8dba2-120">Transações e operações de cópia em massa</span><span class="sxs-lookup"><span data-stu-id="8dba2-120">Transaction and Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 <span data-ttu-id="8dba2-121">Descreve como executar uma operação de cópia em massa em uma transação, incluindo como confirmar ou reverter a transação.</span><span class="sxs-lookup"><span data-stu-id="8dba2-121">Describes how to perform a bulk copy operation within a transaction, including how to commit or rollback the transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dba2-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8dba2-122">See Also</span></span>  
 <span data-ttu-id="8dba2-123">[SQL Server and ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md) (SQL Server e ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="8dba2-123">[SQL Server and ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)</span></span>  
 <span data-ttu-id="8dba2-124">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="8dba2-124">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
