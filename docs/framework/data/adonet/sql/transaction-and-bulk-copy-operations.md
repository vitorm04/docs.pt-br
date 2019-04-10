---
title: Operações de transação e de cópia em massa
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f6f0cbc9-f7bf-4d6e-875f-ad1ba0b4aa62
ms.openlocfilehash: f30974e020545a69ad20c03bc05ac6a28f289b01
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074619"
---
# <a name="transaction-and-bulk-copy-operations"></a>Operações de transação e de cópia em massa
As operações de cópia em massa podem ser executadas como operações isoladas ou como parte de uma transação de várias etapas. Esta última opção permite executar mais de uma operação de cópia em massa dentro da mesma transação, bem como executar outras operações de banco de dados (como inserções, atualizações e exclusões), podendo ainda confirmar ou reverter toda a transação.  
  
 Por padrão, uma operação de cópia em massa é executada como uma operação isolada. A operação de cópia em massa ocorrerá em um modo não transacionado, sem a oportunidade para reversão. Se você precisar reverter toda ou parte da cópia em massa quando ocorrer um erro, você pode usar um <xref:System.Data.SqlClient.SqlBulkCopy>-transação gerenciada, realizar a operação de cópia em massa dentro de uma transação existente ou ser inscrito em uma **System. Transactions** <xref:System.Transactions.Transaction>.  
  
## <a name="performing-a-non-transacted-bulk-copy-operation"></a>Executando uma operação não transacionada de cópia em massa  
 O aplicativo de console a seguir mostra o que ocorre quando uma operação não transacionada de cópia em massa encontra um erro na operação.  
  
 No exemplo, a tabela de origem e a tabela de destino incluem uma `Identity` coluna denominada **ProductID**. O código prepara primeiro a tabela de destino excluindo todas as linhas e, em seguida, inserindo uma única linha cuja **ProductID** é conhecida por existir na tabela de origem. Por padrão, um novo valor para a coluna `Identity` é gerado na tabela de destino para cada linha adicionada. Neste exemplo, uma opção é definida quando a conexão é aberta, o que força o processo de carregamento em massa usar os valores de `Identity` da tabela de origem.  
  
 A operação de cópia em massa é executada com o conjunto de propriedades <xref:System.Data.SqlClient.SqlBulkCopy.BatchSize%2A> definido como 10. Quando a operação encontra a linha inválida, será gerada uma exceção. Neste primeiro exemplo, a operação de cópia em massa é não transacionada. Todos os lotes copiados até o ponto do erro são confirmados; o lote que contém a chave duplicada é revertido e a operação de cópia em massa é interrompida antes de processar todos os outros lotes.  
  
> [!NOTE]
>  Este exemplo não será executado, a menos que você criou as tabelas de trabalho conforme descrito em [configuração de exemplo de cópia em massa](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Esse código é fornecido para demonstrar a sintaxe para usar **SqlBulkCopy** somente. Se as tabelas de origem e destino estiverem localizadas na mesma instância do SQL Server, é mais fácil e mais rápido usar um [!INCLUDE[tsql](../../../../../includes/tsql-md.md)]`INSERT … SELECT` instrução para copiar os dados.  
  
 [!code-csharp[DataWorks SqlBulkCopy.DefaultTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.DefaultTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.DefaultTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.DefaultTransaction/VB/source.vb#1)]  
  
## <a name="performing-a-dedicated-bulk-copy-operation-in-a-transaction"></a>Executando uma operação dedicada de cópia em massa em uma transação  
 Por padrão, uma operação de cópia em massa é sua própria transação. Quando você desejar executar uma operação dedicada de cópia em massa, crie uma nova instância do <xref:System.Data.SqlClient.SqlBulkCopy> com uma cadeia de conexão, ou use um objeto <xref:System.Data.SqlClient.SqlConnection> existente sem uma transação ativa. Em cada cenário, a operação de cópia em massa cria e depois confirma ou reverte a transação.  
  
 Você pode especificar explicitamente a opção <xref:System.Data.SqlClient.SqlBulkCopyOptions.UseInternalTransaction> no construtor de classe <xref:System.Data.SqlClient.SqlBulkCopy> para fazer com explicitamente uma operação de cópia em massa ser executada em sua própria transação, fazendo cada lote da operação de cópia em massa ser executado dentro de uma transação separada.  
  
> [!NOTE]
>  Como os lotes diferentes são executados em transações diferentes, se ocorrer um erro durante a operação de cópia em massa, todas as linhas no lote atual serão revertidas, mas as linhas de lotes anteriores continuarão no banco de dados.  
  
 O aplicativo de console a seguir é semelhante ao exemplo anterior, com uma exceção: Neste exemplo, a operação de cópia em massa gerencia suas próprias transações. Todos os lotes copiados até o ponto do erro são confirmados; o lote que contém a chave duplicada é revertido e a operação de cópia em massa é interrompida antes de processar todos os outros lotes.  
  
> [!IMPORTANT]
>  Este exemplo não será executado, a menos que você criou as tabelas de trabalho conforme descrito em [configuração de exemplo de cópia em massa](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Esse código é fornecido para demonstrar a sintaxe para usar **SqlBulkCopy** somente. Se as tabelas de origem e destino estiverem localizadas na mesma instância do SQL Server, é mais fácil e mais rápido usar um [!INCLUDE[tsql](../../../../../includes/tsql-md.md)]`INSERT … SELECT` instrução para copiar os dados.  
  
 [!code-csharp[DataWorks SqlBulkCopy.InternalTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.InternalTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.InternalTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.InternalTransaction/VB/source.vb#1)]  
  
## <a name="using-existing-transactions"></a>Usando transações existentes  
 Você pode especificar um objeto existente <xref:System.Data.SqlClient.SqlTransaction> como um parâmetro em um construtor <xref:System.Data.SqlClient.SqlBulkCopy>. Nessa situação, a operação de cópia em massa é executada em uma transação existente e nenhuma alteração é feita ao estado da transação (isto é, não é confirmada nem anulada). Isso permite que um aplicativo inclua a operação de cópia em massa em uma transação com outras operações de banco de dados. No entanto, se você não especificar um objeto <xref:System.Data.SqlClient.SqlTransaction> e não passar uma referência nula, e a conexão tiver uma transação ativa, uma exceção será gerada.  
  
 Se você precisar reverter toda a operação de cópia em massa porque um erro ocorreu, ou se a cópia em massa for executada como parte de um processo maior que pode ser revertido, você poderá fornecer um objeto <xref:System.Data.SqlClient.SqlTransaction> para o construtor <xref:System.Data.SqlClient.SqlBulkCopy>.  
  
 O seguinte aplicativo de console é semelhante ao primeiro exemplo (não transacionado), com uma exceção: neste exemplo, a operação de cópia em massa está incluída em uma transação maior, externa. Quando o erro de violação de chave primária ocorrer, a transação inteira será revertida e nenhuma linha será adicionada à tabela de destino.  
  
> [!IMPORTANT]
>  Este exemplo não será executado, a menos que você criou as tabelas de trabalho conforme descrito em [configuração de exemplo de cópia em massa](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Esse código é fornecido para demonstrar a sintaxe para usar **SqlBulkCopy** somente. Se as tabelas de origem e destino estiverem localizadas na mesma instância do SQL Server, é mais fácil e mais rápido usar um [!INCLUDE[tsql](../../../../../includes/tsql-md.md)]`INSERT … SELECT` instrução para copiar os dados.  
  
 [!code-csharp[DataWorks SqlBulkCopy.SqlTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.SqlTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.SqlTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.SqlTransaction/VB/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [Operações de cópia em massa no SQL Server](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- [Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
