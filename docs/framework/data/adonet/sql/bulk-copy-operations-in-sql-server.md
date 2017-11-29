---
title: "Operações de cópia em massa no SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 31da2fbc7dca4c0c2c077991ddec39e8979b08b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="bulk-copy-operations-in-sql-server"></a>Operações de cópia em massa no SQL Server
Microsoft SQL Server inclui um utilitário de linha de comando popular chamado **bcp** para rapidamente cópia em massa de arquivos grandes em tabelas ou exibições em bancos de dados do SQL Server. O <xref:System.Data.SqlClient.SqlBulkCopy> classe lhe permite escrever soluções de código gerenciado que fornecem funcionalidade semelhante. Existem outras maneiras para carregar dados em uma tabela do SQL Server (instruções INSERT, por exemplo), mas <xref:System.Data.SqlClient.SqlBulkCopy> oferece uma vantagem de desempenho significativa sobre eles.  
  
 O <xref:System.Data.SqlClient.SqlBulkCopy> classe pode ser usada para gravar dados somente em tabelas do SQL Server. Mas a fonte de dados não está limitada ao SQL Server; qualquer fonte de dados pode ser usado, desde que os dados podem ser carregados para um <xref:System.Data.DataTable> instância ou de leitura com um <xref:System.Data.IDataReader> instância.  
  
 Usando o <xref:System.Data.SqlClient.SqlBulkCopy> classe, você pode executar:  
  
-   Uma operação de cópia em massa único  
  
-   Várias operações de cópia em massa  
  
-   Uma operação de cópia em massa em uma transação  
  
> [!NOTE]
>  Ao usar o .NET Framework versão 1.1 ou anterior (que não dá suporte a <xref:System.Data.SqlClient.SqlBulkCopy> classe), você pode executar o SQL Server Transact-SQL **BULK INSERT** instrução usando o <xref:System.Data.SqlClient.SqlCommand> objeto.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Configuração de exemplo de cópia em massa](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 Descreve as tabelas usadas nos exemplos de cópia em massa e fornece scripts SQL para criar as tabelas no banco de dados AdventureWorks.  
  
 [Operações de cópia em massa único](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 Descreve como fazer uma cópia em massa único dos dados em uma instância do SQL Server usando o <xref:System.Data.SqlClient.SqlBulkCopy> classe e como executar a operação de cópia em massa usando instruções Transact-SQL e o <xref:System.Data.SqlClient.SqlCommand> classe.  
  
 [Várias operações de cópia em massa](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 Descreve como realizar várias operações de cópia em massa de dados em uma instância do SQL Server usando o <xref:System.Data.SqlClient.SqlBulkCopy> classe.  
  
 [Transações e operações de cópia em massa](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 Descreve como executar uma operação de cópia em massa em uma transação, incluindo como confirmar ou reverter a transação.  
  
## <a name="see-also"></a>Consulte também  
 [SQL Server and ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md) (SQL Server e ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
