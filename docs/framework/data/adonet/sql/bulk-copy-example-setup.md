---
title: Configuração de exemplo de cópia em massa
ms.date: 03/30/2017
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
ms.openlocfilehash: 562d36e0aee72fcc0619ec4ed7362622ba652337
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197476"
---
# <a name="bulk-copy-example-setup"></a><span data-ttu-id="9ce02-102">Configuração de exemplo de cópia em massa</span><span class="sxs-lookup"><span data-stu-id="9ce02-102">Bulk Copy Example Setup</span></span>

<span data-ttu-id="9ce02-103">A classe <xref:System.Data.SqlClient.SqlBulkCopy> pode ser usada para gravar dados somente em tabelas do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9ce02-103">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="9ce02-104">Os exemplos de código mostrados neste tópico usam o banco de dados de exemplo do SQL Server, **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="9ce02-104">The code samples shown in this topic use the SQL Server sample database, **AdventureWorks**.</span></span> <span data-ttu-id="9ce02-105">Para evitar a alteração das tabelas existentes, os exemplos de código gravam dados em tabelas que você deve criar primeiro.</span><span class="sxs-lookup"><span data-stu-id="9ce02-105">To avoid altering the existing tables code samples write data to tables that you must create first.</span></span>  
  
 <span data-ttu-id="9ce02-106">As tabelas **BulkCopyDemoMatchingColumns** e **BulkCopyDemoDifferentColumns** são baseadas na tabela **AdventureWorks** **Production.Products**.</span><span class="sxs-lookup"><span data-stu-id="9ce02-106">The **BulkCopyDemoMatchingColumns** and **BulkCopyDemoDifferentColumns** tables are both based on the **AdventureWorks** **Production.Products** table.</span></span> <span data-ttu-id="9ce02-107">Nos exemplos de código que usam essas tabelas, os dados são adicionados da tabela **Production. Products** a uma dessas tabelas de exemplo.</span><span class="sxs-lookup"><span data-stu-id="9ce02-107">In code samples that use these tables, data is added from the **Production.Products** table to one of these sample tables.</span></span> <span data-ttu-id="9ce02-108">A tabela **BulkCopyDemoDifferentColumns** é usada quando o exemplo ilustra como mapear colunas dos dados de origem para a tabela de destino; **BulkCopyDemoMatchingColumns** é usado para a maioria dos outros exemplos.</span><span class="sxs-lookup"><span data-stu-id="9ce02-108">The **BulkCopyDemoDifferentColumns** table is used when the sample illustrates how to map columns from the source data to the destination table; **BulkCopyDemoMatchingColumns** is used for most other samples.</span></span>  
  
 <span data-ttu-id="9ce02-109">Alguns dos exemplos de código demonstram como usar uma classe <xref:System.Data.SqlClient.SqlBulkCopy> para gravar em várias tabelas.</span><span class="sxs-lookup"><span data-stu-id="9ce02-109">A few of the code samples demonstrate how to use one <xref:System.Data.SqlClient.SqlBulkCopy> class to write to multiple tables.</span></span> <span data-ttu-id="9ce02-110">Para esses exemplos, as tabelas **BulkCopyDemoOrderHeader** e **BulkCopyDemoOrderDetail** são usadas como tabelas de destino.</span><span class="sxs-lookup"><span data-stu-id="9ce02-110">For these samples, the **BulkCopyDemoOrderHeader** and **BulkCopyDemoOrderDetail** tables are used as the destination tables.</span></span> <span data-ttu-id="9ce02-111">Essas tabelas são baseadas nas tabelas **Sales. SalesOrderHeader** e **Sales. SalesOrderDetail** no **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="9ce02-111">These tables are based on the **Sales.SalesOrderHeader** and **Sales.SalesOrderDetail** tables in **AdventureWorks**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ce02-112">Os exemplos de código **SqlBulkCopy** são fornecidos para demonstrar a sintaxe para usar o **SqlBulkCopy** apenas.</span><span class="sxs-lookup"><span data-stu-id="9ce02-112">The **SqlBulkCopy** code samples are provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="9ce02-113">Se as tabelas de origem e destino estiverem localizadas na mesma instância do SQL Server, será mais fácil e mais rápido usar uma instrução `INSERT … SELECT` do Transact-SQL para copiar os dados.</span><span class="sxs-lookup"><span data-stu-id="9ce02-113">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
## <a name="table-setup"></a><span data-ttu-id="9ce02-114">Configuração de tabela</span><span class="sxs-lookup"><span data-stu-id="9ce02-114">Table Setup</span></span>  

 <span data-ttu-id="9ce02-115">Para criar as tabelas necessárias para que os exemplos de código sejam executado corretamente, você deve executar as seguintes instruções Transact-SQL em um banco de dados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9ce02-115">To create the tables necessary for the code samples to run correctly, you must run the following Transact-SQL statements in a SQL Server database.</span></span>  
  
```sql
USE AdventureWorks  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoMatchingColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoMatchingColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoMatchingColumns]([ProductID] [int] IDENTITY(1,1) NOT NULL,  
    [Name] [nvarchar](50) NOT NULL,  
    [ProductNumber] [nvarchar](25) NOT NULL,  
 CONSTRAINT [PK_ProductID] PRIMARY KEY CLUSTERED  
(  
    [ProductID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoDifferentColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoDifferentColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoDifferentColumns]([ProdID] [int] IDENTITY(1,1) NOT NULL,  
    [ProdNum] [nvarchar](25) NOT NULL,  
    [ProdName] [nvarchar](50) NOT NULL,  
 CONSTRAINT [PK_ProdID] PRIMARY KEY CLUSTERED  
(  
    [ProdID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderHeader]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderHeader]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderHeader]([SalesOrderID] [int] IDENTITY(1,1) NOT NULL,  
    [OrderDate] [datetime] NOT NULL,  
    [AccountNumber] [nvarchar](15) NULL,  
 CONSTRAINT [PK_SalesOrderID] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderDetail]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderDetail]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderDetail]([SalesOrderID] [int] NOT NULL,  
    [SalesOrderDetailID] [int] NOT NULL,  
    [OrderQty] [smallint] NOT NULL,  
    [ProductID] [int] NOT NULL,  
    [UnitPrice] [money] NOT NULL,  
 CONSTRAINT [PK_LineNumber] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC,  
    [SalesOrderDetailID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
```  
  
## <a name="see-also"></a><span data-ttu-id="9ce02-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="9ce02-116">See also</span></span>

- [<span data-ttu-id="9ce02-117">Operações de cópia em massa no SQL Server</span><span class="sxs-lookup"><span data-stu-id="9ce02-117">Bulk Copy Operations in SQL Server</span></span>](bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="9ce02-118">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9ce02-118">ADO.NET Overview</span></span>](../ado-net-overview.md)
