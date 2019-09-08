---
title: Operações de cópia em massa no SQL Server
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: ae97bcdd6776d573cf9e523133c2c00a42c273bb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782532"
---
# <a name="bulk-copy-operations-in-sql-server"></a><span data-ttu-id="a56ad-102">Operações de cópia em massa no SQL Server</span><span class="sxs-lookup"><span data-stu-id="a56ad-102">Bulk Copy Operations in SQL Server</span></span>
<span data-ttu-id="a56ad-103">O Microsoft SQL Server inclui um utilitário de linha de comando popular chamado **bcp** para copiar arquivos grandes em massa rapidamente em tabelas ou exibições em bancos de dados SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a56ad-103">Microsoft SQL Server includes a popular command-line utility named **bcp** for quickly bulk copying large files into tables or views in SQL Server databases.</span></span> <span data-ttu-id="a56ad-104">A <xref:System.Data.SqlClient.SqlBulkCopy> classe permite que você escreva soluções de código gerenciado que fornecem funcionalidade semelhante.</span><span class="sxs-lookup"><span data-stu-id="a56ad-104">The <xref:System.Data.SqlClient.SqlBulkCopy> class allows you to write managed code solutions that provide similar functionality.</span></span> <span data-ttu-id="a56ad-105">Há outras maneiras de carregar dados em uma tabela SQL Server (instruções INSERT, por exemplo), mas <xref:System.Data.SqlClient.SqlBulkCopy> oferece uma vantagem de desempenho significativa sobre eles.</span><span class="sxs-lookup"><span data-stu-id="a56ad-105">There are other ways to load data into a SQL Server table (INSERT statements, for example) but <xref:System.Data.SqlClient.SqlBulkCopy> offers a significant performance advantage over them.</span></span>  
  
 <span data-ttu-id="a56ad-106">A <xref:System.Data.SqlClient.SqlBulkCopy> classe pode ser usada para gravar dados somente em tabelas SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a56ad-106">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="a56ad-107">Mas a fonte de dados não está limitada a SQL Server; qualquer fonte de dados pode ser usada, desde que os dados possam ser carregados em uma <xref:System.Data.DataTable> instância ou lidos com <xref:System.Data.IDataReader> uma instância do.</span><span class="sxs-lookup"><span data-stu-id="a56ad-107">But the data source is not limited to SQL Server; any data source can be used, as long as the data can be loaded to a <xref:System.Data.DataTable> instance or read with a <xref:System.Data.IDataReader> instance.</span></span>  
  
 <span data-ttu-id="a56ad-108">Usando a <xref:System.Data.SqlClient.SqlBulkCopy> classe, você pode executar:</span><span class="sxs-lookup"><span data-stu-id="a56ad-108">Using the <xref:System.Data.SqlClient.SqlBulkCopy> class, you can perform:</span></span>  
  
- <span data-ttu-id="a56ad-109">Uma única operação de cópia em massa</span><span class="sxs-lookup"><span data-stu-id="a56ad-109">A single bulk copy operation</span></span>  
  
- <span data-ttu-id="a56ad-110">Várias operações de cópia em massa</span><span class="sxs-lookup"><span data-stu-id="a56ad-110">Multiple bulk copy operations</span></span>  
  
- <span data-ttu-id="a56ad-111">Uma operação de cópia em massa em uma transação</span><span class="sxs-lookup"><span data-stu-id="a56ad-111">A bulk copy operation within a transaction</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a56ad-112">Ao usar .NET Framework versão 1,1 ou anterior (que não oferece suporte à <xref:System.Data.SqlClient.SqlBulkCopy> classe), você pode executar a instrução SQL Server Transact-SQL **BULK INSERT** usando o <xref:System.Data.SqlClient.SqlCommand> objeto.</span><span class="sxs-lookup"><span data-stu-id="a56ad-112">When using .NET Framework version 1.1 or earlier (which does not support the <xref:System.Data.SqlClient.SqlBulkCopy> class), you can execute the SQL Server Transact-SQL **BULK INSERT** statement using the <xref:System.Data.SqlClient.SqlCommand> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a56ad-113">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="a56ad-113">In This Section</span></span>  
 [<span data-ttu-id="a56ad-114">Configuração de exemplo de cópia em massa</span><span class="sxs-lookup"><span data-stu-id="a56ad-114">Bulk Copy Example Setup</span></span>](bulk-copy-example-setup.md)  
 <span data-ttu-id="a56ad-115">Descreve as tabelas usadas nos exemplos de cópia em massa e fornece scripts SQL para criar as tabelas no banco de dados AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a56ad-115">Describes the tables used in the bulk copy examples and provides SQL scripts for creating the tables in the AdventureWorks database.</span></span>  
  
 [<span data-ttu-id="a56ad-116">Operações únicas de cópia em massa</span><span class="sxs-lookup"><span data-stu-id="a56ad-116">Single Bulk Copy Operations</span></span>](single-bulk-copy-operations.md)  
 <span data-ttu-id="a56ad-117">Descreve como fazer uma única cópia em massa de dados em uma instância do SQL Server usando a <xref:System.Data.SqlClient.SqlBulkCopy> classe e como executar a operação de cópia em massa usando instruções Transact-SQL e a <xref:System.Data.SqlClient.SqlCommand> classe.</span><span class="sxs-lookup"><span data-stu-id="a56ad-117">Describes how to do a single bulk copy of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class, and how to perform the bulk copy operation using Transact-SQL statements and the <xref:System.Data.SqlClient.SqlCommand> class.</span></span>  
  
 [<span data-ttu-id="a56ad-118">Várias operações de cópia em massa</span><span class="sxs-lookup"><span data-stu-id="a56ad-118">Multiple Bulk Copy Operations</span></span>](multiple-bulk-copy-operations.md)  
 <span data-ttu-id="a56ad-119">Descreve como realizar várias operações de cópia em massa de dados em uma instância do SQL Server usando <xref:System.Data.SqlClient.SqlBulkCopy> a classe.</span><span class="sxs-lookup"><span data-stu-id="a56ad-119">Describes how to do multiple bulk copy operations of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span>  
  
 [<span data-ttu-id="a56ad-120">Transações e operações de cópia em massa</span><span class="sxs-lookup"><span data-stu-id="a56ad-120">Transaction and Bulk Copy Operations</span></span>](transaction-and-bulk-copy-operations.md)  
 <span data-ttu-id="a56ad-121">Descreve como executar uma operação de cópia em massa em uma transação, incluindo como confirmar ou reverter a transação.</span><span class="sxs-lookup"><span data-stu-id="a56ad-121">Describes how to perform a bulk copy operation within a transaction, including how to commit or rollback the transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a56ad-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a56ad-122">See also</span></span>

- <span data-ttu-id="a56ad-123">[SQL Server and ADO.NET](index.md) (SQL Server e ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="a56ad-123">[SQL Server and ADO.NET](index.md)</span></span>
- <span data-ttu-id="a56ad-124">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="a56ad-124">[ADO.NET Overview](../ado-net-overview.md)</span></span>
