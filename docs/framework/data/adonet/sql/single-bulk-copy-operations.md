---
title: Operações únicas de cópia em massa
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.openlocfilehash: 8cba2201bf8087633103efe45c5236cab3af0a0e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964749"
---
# <a name="single-bulk-copy-operations"></a>Operações únicas de cópia em massa
A abordagem mais simples para executar uma SQL Server operação de cópia em massa é executar uma única operação em um banco de dados. Por padrão, uma operação de cópia em massa é executada como uma operação isolada: a operação de cópia ocorre de forma não-transacionada, sem nenhuma oportunidade de redistribuí-la.  
  
> [!NOTE]
> Se você precisar reverter toda ou parte da cópia em massa quando ocorrer um erro, poderá usar uma <xref:System.Data.SqlClient.SqlBulkCopy>transação gerenciada ou executar a operação de cópia em massa em uma transação existente. O **SqlBulkCopy** também funcionará <xref:System.Transactions> se a conexão for listada (implícita ou explicitamente) em uma transação **System.** Transactions.  
>   
>  Para obter mais informações, consulte [operações de cópia em massa e transação](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).  
  
 As etapas gerais para executar uma operação de cópia em massa são as seguintes:  
  
1. Conecte-se ao servidor de origem e obtenha os dados a serem copiados. Os dados também podem vir de outras fontes, se puderem ser recuperados <xref:System.Data.IDataReader> de <xref:System.Data.DataTable> um objeto ou.  
  
2. Conecte-se ao servidor de destino (a menos que você queira que o **SqlBulkCopy** estabeleça uma conexão para você).  
  
3. Crie um <xref:System.Data.SqlClient.SqlBulkCopy> objeto, definindo as propriedades necessárias.  
  
4. Defina a propriedade **DestinationTableName** para indicar a tabela de destino para a operação de inserção em massa.  
  
5. Chame um dos métodos **WriteToServer** .  
  
6. Opcionalmente, atualize as propriedades e chame **WriteToServer** novamente conforme necessário.  
  
7. Chamar <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>ou encapsular as operações de cópia em massa `Using` em uma instrução.  
  
> [!CAUTION]
>  É recomendável que os tipos de dados de coluna de origem e destino coincidam. Se os tipos de dados não corresponderem, o **SqlBulkCopy** tentará converter cada valor de origem no tipo de dados de destino, <xref:System.Data.SqlClient.SqlParameter.Value%2A>usando as regras empregadas pelo. As conversões podem afetar o desempenho e também podem resultar em erros inesperados. Por exemplo, um `Double` tipo de dados pode ser convertido em `Decimal` um tipo de dados na maior parte do tempo, mas nem sempre.  
  
## <a name="example"></a>Exemplo  
 O aplicativo de console a seguir demonstra como carregar dados usando <xref:System.Data.SqlClient.SqlBulkCopy> a classe. Neste exemplo, um <xref:System.Data.SqlClient.SqlDataReader> é usado para copiar dados da tabela de **produção. Product** no banco SQL Server dados **AdventureWorks** para uma tabela semelhante no mesmo banco de dados.  
  
> [!IMPORTANT]
> Este exemplo não será executado a menos que você tenha criado as tabelas de trabalho conforme descrito em [configuração de exemplo de cópia em massa](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Esse código é fornecido para demonstrar a sintaxe somente para uso de **SqlBulkCopy** . Se as tabelas de origem e destino estiverem localizadas na mesma instância de SQL Server, será mais fácil e rápido usar uma instrução Transact `INSERT … SELECT` -SQL para copiar os dados.  
  
 [!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
 [!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]  
  
## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a>Executando uma operação de cópia em massa usando Transact-SQL e a classe Command  
 O exemplo a seguir ilustra como usar o <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> método para executar a instrução BULK INSERT.  
  
> [!NOTE]
> O caminho do arquivo para a fonte de dados é relativo ao servidor. O processo do servidor deve ter acesso a esse caminho para que a operação de cópia em massa tenha sucesso.  
  
```vb  
Using connection As SqlConnection = New SqlConnection(connectionString)  
Dim queryString As String = _  
    "BULK INSERT Northwind.dbo.[Order Details] FROM " & _  
    "'f:\mydata\data.tbl' WITH (FORMATFILE='f:\mydata\data.fmt' )"  
connection.Open()  
SqlCommand command = New SqlCommand(queryString, connection);  
  
command.ExecuteNonQuery()  
End Using  
```  
  
```csharp  
using (SqlConnection connection = New SqlConnection(connectionString))  
{  
string queryString =  "BULK INSERT Northwind.dbo.[Order Details] " +  
    "FROM 'f:\mydata\data.tbl' " +  
    "WITH ( FORMATFILE='f:\mydata\data.fmt' )";  
connection.Open();  
SqlCommand command = new SqlCommand(queryString, connection);  
  
command.ExecuteNonQuery();  
}  
```  
  
## <a name="see-also"></a>Consulte também

- [Operações de cópia em massa no SQL Server](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
