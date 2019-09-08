---
title: Configuração de exemplo de cópia em massa
ms.date: 03/30/2017
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
ms.openlocfilehash: ac09ed85315aee7c6b29952916088ebe6e301eb9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794423"
---
# <a name="bulk-copy-example-setup"></a>Configuração de exemplo de cópia em massa
A <xref:System.Data.SqlClient.SqlBulkCopy> classe pode ser usada para gravar dados somente em tabelas SQL Server. Os exemplos de código mostrados neste tópico usam o SQL Server banco de dados de exemplo, **AdventureWorks**. Para evitar alterar as tabelas existentes, os exemplos de código gravam dados em tabelas que você deve criar primeiro.  
  
 As tabelas **BulkCopyDemoMatchingColumns** e **BulkCopyDemoDifferentColumns** são baseadas na tabela **AdventureWorks** **Production. Products** . Nos exemplos de código que usam essas tabelas, os dados são adicionados da tabela **Production. Products** a uma dessas tabelas de exemplo. A tabela **BulkCopyDemoDifferentColumns** é usada quando o exemplo ilustra como mapear colunas dos dados de origem para a tabela de destino; **BulkCopyDemoMatchingColumns** é usado para a maioria dos outros exemplos.  
  
 Alguns dos exemplos de código demonstram como usar uma <xref:System.Data.SqlClient.SqlBulkCopy> classe para gravar em várias tabelas. Para esses exemplos, as tabelas **BulkCopyDemoOrderHeader** e **BulkCopyDemoOrderDetail** são usadas como tabelas de destino. Essas tabelas são baseadas nas tabelas **Sales. SalesOrderHeader** e **Sales. SalesOrderDetail** no **AdventureWorks**.  
  
> [!NOTE]
> Os exemplos de código **SqlBulkCopy** são fornecidos para demonstrar a sintaxe somente para uso do **SqlBulkCopy** . Se as tabelas de origem e destino estiverem localizadas na mesma instância de SQL Server, será mais fácil e rápido usar uma instrução Transact `INSERT … SELECT` -SQL para copiar os dados.  
  
## <a name="table-setup"></a>Configuração de tabela  
 Para criar as tabelas necessárias para que os exemplos de código sejam executados corretamente, você deve executar as instruções Transact-SQL a seguir em um banco de dados SQL Server.  
  
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
  
## <a name="see-also"></a>Consulte também

- [Operações de cópia em massa no SQL Server](bulk-copy-operations-in-sql-server.md)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
