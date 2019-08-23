---
title: Operações de cópia em massa no SQL Server
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: efa13eb1633fce3b59040ef8da79dba0f6ea81d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918059"
---
# <a name="bulk-copy-operations-in-sql-server"></a>Operações de cópia em massa no SQL Server
O Microsoft SQL Server inclui um utilitário de linha de comando popular chamado **bcp** para copiar arquivos grandes em massa rapidamente em tabelas ou exibições em bancos de dados SQL Server. A <xref:System.Data.SqlClient.SqlBulkCopy> classe permite que você escreva soluções de código gerenciado que fornecem funcionalidade semelhante. Há outras maneiras de carregar dados em uma tabela SQL Server (instruções INSERT, por exemplo), mas <xref:System.Data.SqlClient.SqlBulkCopy> oferece uma vantagem de desempenho significativa sobre eles.  
  
 A <xref:System.Data.SqlClient.SqlBulkCopy> classe pode ser usada para gravar dados somente em tabelas SQL Server. Mas a fonte de dados não está limitada a SQL Server; qualquer fonte de dados pode ser usada, desde que os dados possam ser carregados em uma <xref:System.Data.DataTable> instância ou lidos com <xref:System.Data.IDataReader> uma instância do.  
  
 Usando a <xref:System.Data.SqlClient.SqlBulkCopy> classe, você pode executar:  
  
- Uma única operação de cópia em massa  
  
- Várias operações de cópia em massa  
  
- Uma operação de cópia em massa em uma transação  
  
> [!NOTE]
> Ao usar .NET Framework versão 1,1 ou anterior (que não oferece suporte à <xref:System.Data.SqlClient.SqlBulkCopy> classe), você pode executar a instrução SQL Server Transact-SQL **BULK INSERT** usando o <xref:System.Data.SqlClient.SqlCommand> objeto.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Configuração de exemplo de cópia em massa](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 Descreve as tabelas usadas nos exemplos de cópia em massa e fornece scripts SQL para criar as tabelas no banco de dados AdventureWorks.  
  
 [Operações únicas de cópia em massa](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 Descreve como fazer uma única cópia em massa de dados em uma instância do SQL Server usando a <xref:System.Data.SqlClient.SqlBulkCopy> classe e como executar a operação de cópia em massa usando instruções Transact-SQL e a <xref:System.Data.SqlClient.SqlCommand> classe.  
  
 [Várias operações de cópia em massa](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 Descreve como realizar várias operações de cópia em massa de dados em uma instância do SQL Server usando <xref:System.Data.SqlClient.SqlBulkCopy> a classe.  
  
 [Transações e operações de cópia em massa](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 Descreve como executar uma operação de cópia em massa em uma transação, incluindo como confirmar ou reverter a transação.  
  
## <a name="see-also"></a>Consulte também

- [SQL Server and ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md) (SQL Server e ADO.NET)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
