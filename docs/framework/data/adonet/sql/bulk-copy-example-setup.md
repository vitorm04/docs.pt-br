---
title: Configuração de exemplo de cópia em massa
ms.date: 03/30/2017
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
ms.openlocfilehash: 6244afff348edbde46fdfda7481910aca2b25939
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59117268"
---
# <a name="bulk-copy-example-setup"></a><span data-ttu-id="9987c-102">Configuração de exemplo de cópia em massa</span><span class="sxs-lookup"><span data-stu-id="9987c-102">Bulk Copy Example Setup</span></span>
<span data-ttu-id="9987c-103">O <xref:System.Data.SqlClient.SqlBulkCopy> classe pode ser usado para gravar dados somente em tabelas do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9987c-103">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="9987c-104">Os exemplos de código mostrados neste tópico usam o banco de dados de exemplo do SQL Server, **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="9987c-104">The code samples shown in this topic use the SQL Server sample database, **AdventureWorks**.</span></span> <span data-ttu-id="9987c-105">Para evitar a alteração das tabelas existentes a exemplos de código gravam dados em tabelas que você deve criar primeiro.</span><span class="sxs-lookup"><span data-stu-id="9987c-105">To avoid altering the existing tables code samples write data to tables that you must create first.</span></span>  
  
 <span data-ttu-id="9987c-106">O **BulkCopyDemoMatchingColumns** e **BulkCopyDemoDifferentColumns** tabelas são baseadas no **AdventureWorks** **Production**  tabela.</span><span class="sxs-lookup"><span data-stu-id="9987c-106">The **BulkCopyDemoMatchingColumns** and **BulkCopyDemoDifferentColumns** tables are both based on the **AdventureWorks** **Production.Products** table.</span></span> <span data-ttu-id="9987c-107">Nos exemplos de código que usam essas tabelas, os dados são adicionados dos **Production** tabela para uma dessas tabelas de exemplo.</span><span class="sxs-lookup"><span data-stu-id="9987c-107">In code samples that use these tables, data is added from the **Production.Products** table to one of these sample tables.</span></span> <span data-ttu-id="9987c-108">O **BulkCopyDemoDifferentColumns** tabela é usada quando o exemplo ilustra como mapear colunas de dados de origem para a tabela de destino; **BulkCopyDemoMatchingColumns** é usado para a maioria dos outros exemplos.</span><span class="sxs-lookup"><span data-stu-id="9987c-108">The **BulkCopyDemoDifferentColumns** table is used when the sample illustrates how to map columns from the source data to the destination table; **BulkCopyDemoMatchingColumns** is used for most other samples.</span></span>  
  
 <span data-ttu-id="9987c-109">Alguns dos exemplos de código demonstram como usar um <xref:System.Data.SqlClient.SqlBulkCopy> classe para gravar em várias tabelas.</span><span class="sxs-lookup"><span data-stu-id="9987c-109">A few of the code samples demonstrate how to use one <xref:System.Data.SqlClient.SqlBulkCopy> class to write to multiple tables.</span></span> <span data-ttu-id="9987c-110">Para esses exemplos, o **BulkCopyDemoOrderHeader** e **BulkCopyDemoOrderDetail** tabelas são usadas como tabelas de destino.</span><span class="sxs-lookup"><span data-stu-id="9987c-110">For these samples, the **BulkCopyDemoOrderHeader** and **BulkCopyDemoOrderDetail** tables are used as the destination tables.</span></span> <span data-ttu-id="9987c-111">Essas tabelas são baseadas na **Sales. SalesOrderHeader** e **Sales. SalesOrderDetail** tabelas na **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="9987c-111">These tables are based on the **Sales.SalesOrderHeader** and **Sales.SalesOrderDetail** tables in **AdventureWorks**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9987c-112">O **SqlBulkCopy** exemplos de código são fornecidos para demonstrar a sintaxe para usar **SqlBulkCopy** somente.</span><span class="sxs-lookup"><span data-stu-id="9987c-112">The **SqlBulkCopy** code samples are provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="9987c-113">Se as tabelas de origem e destino estiverem localizadas na mesma instância do SQL Server, é mais fácil e rápido para usar um Transact-SQL `INSERT … SELECT` instrução para copiar os dados.</span><span class="sxs-lookup"><span data-stu-id="9987c-113">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
## <a name="table-setup"></a><span data-ttu-id="9987c-114">Configuração da tabela</span><span class="sxs-lookup"><span data-stu-id="9987c-114">Table Setup</span></span>  
 <span data-ttu-id="9987c-115">Para criar as tabelas necessárias para os exemplos de código seja executado corretamente, você deve executar as seguintes instruções Transact-SQL em um banco de dados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9987c-115">To create the tables necessary for the code samples to run correctly, you must run the following Transact-SQL statements in a SQL Server database.</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="9987c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9987c-116">See also</span></span>

- [<span data-ttu-id="9987c-117">Operações de cópia em massa no SQL Server</span><span class="sxs-lookup"><span data-stu-id="9987c-117">Bulk Copy Operations in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- <span data-ttu-id="9987c-118">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="9987c-118">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
