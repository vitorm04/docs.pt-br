---
title: Várias operações de cópia em massa
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.openlocfilehash: e6a9a82a49d2db2f1a49420c296be6dbf6d37d67
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520290"
---
# <a name="multiple-bulk-copy-operations"></a>Várias operações de cópia em massa
Você pode executar várias operações de cópia em massa usando uma única instância de um <xref:System.Data.SqlClient.SqlBulkCopy> classe. Se os parâmetros da operação alterar entre as cópias (por exemplo, o nome da tabela de destino), você deve atualizá-los antes de qualquer chamada subsequente para qualquer um dos **WriteToServer** métodos, conforme demonstrado no exemplo a seguir. A menos que explicitamente alterado, todos os valores de propriedade permanecem como estavam na operação de cópia em massa anterior para uma determinada instância.  
  
> [!NOTE]
>  Executar várias operações de cópia em massa usando a mesma instância de <xref:System.Data.SqlClient.SqlBulkCopy> é geralmente mais eficiente do que usar uma instância separada para cada operação.  
  
 Se você executar várias operações de cópia em massa usando o mesmo <xref:System.Data.SqlClient.SqlBulkCopy> do objeto, não há nenhuma restrição sobre se as informações de origem ou de destino são iguais ou diferentes em cada operação. No entanto, você deve garantir que as informações de associação de coluna estão definidas corretamente sempre que você grava para o servidor.  
  
> [!IMPORTANT]
>  Este exemplo não será executado, a menos que você criou as tabelas de trabalho conforme descrito em [configuração de exemplo de cópia em massa](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Esse código é fornecido para demonstrar a sintaxe para usar **SqlBulkCopy** somente. Se as tabelas de origem e destino estiverem localizadas na mesma instância do SQL Server, é mais fácil e rápido para usar um Transact-SQL `INSERT … SELECT` instrução para copiar os dados.  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Operações de cópia em massa no SQL Server](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
