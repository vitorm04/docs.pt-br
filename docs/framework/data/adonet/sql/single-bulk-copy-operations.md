---
title: Operações de cópia em massa único
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.openlocfilehash: 274a6e87b272002a567fd92605c4e690c03b6e26
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "44778559"
---
# <a name="single-bulk-copy-operations"></a>Operações de cópia em massa único
A abordagem mais simples para executar uma operação de cópia em massa do SQL Server é executar uma única operação em um banco de dados. Por padrão, uma operação de cópia em massa é executada como uma operação isolada: a operação de cópia ocorre de forma não transacionada, sem a oportunidade de revertê-la de volta.  
  
> [!NOTE]
>  Se você precisar reverter toda ou parte da cópia em massa quando ocorrer um erro, você pode usar um <xref:System.Data.SqlClient.SqlBulkCopy>-transação gerenciada ou executar a operação de cópia em massa dentro de uma transação existente. **SqlBulkCopy** também trabalhará <xref:System.Transactions> se a conexão será inscrita (implícita ou explicitamente) em um **System. Transactions** transação.  
>   
>  Para obter mais informações, consulte [transações e operações de cópia em massa](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).  
  
 As etapas gerais para executar uma operação de cópia em massa são da seguinte maneira:  
  
1.  Conectar-se ao servidor de origem e obter os dados a serem copiados. Dados também podem vir de outras fontes, se ele pode ser recuperado de um <xref:System.Data.IDataReader> ou <xref:System.Data.DataTable> objeto.  
  
2.  Conectar-se ao servidor de destino (a menos que você deseje **SqlBulkCopy** para estabelecer uma conexão para você).  
  
3.  Criar um <xref:System.Data.SqlClient.SqlBulkCopy> objeto, definindo as propriedades necessárias.  
  
4.  Defina as **DestinationTableName** propriedade para indicar a tabela de destino para a maior parte de operação de inserção.  
  
5.  Chame um dos **WriteToServer** métodos.  
  
6.  Opcionalmente, atualize as propriedades e chamar **WriteToServer** novamente, conforme necessário.  
  
7.  Chame <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>, ou encapsular as operações de cópia em massa dentro de um `Using` instrução.  
  
> [!CAUTION]
>  É recomendável que os tipos de dados de coluna de origem e destino correspondam. Se os tipos de dados não corresponderem, **SqlBulkCopy** tenta converter cada valor de origem para o tipo de dados de destino, usando as regras de empregado pelo <xref:System.Data.SqlClient.SqlParameter.Value%2A>. As conversões podem afetar o desempenho e também podem resultar em erros inesperados. Por exemplo, uma `Double` tipo de dados pode ser convertido em um `Decimal` a maioria do tipo de dados do tempo, mas não sempre.  
  
## <a name="example"></a>Exemplo  
 O aplicativo de console a seguir demonstra como carregar dados usando o <xref:System.Data.SqlClient.SqlBulkCopy> classe. Neste exemplo, uma <xref:System.Data.SqlClient.SqlDataReader> é usado para copiar dados do **Production. Product** tabela no SQL Server**AdventureWorks** banco de dados em uma tabela semelhante no mesmo banco de dados.  
  
> [!IMPORTANT]
>  Este exemplo não será executado, a menos que você criou as tabelas de trabalho conforme descrito em [configuração de exemplo de cópia em massa](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Esse código é fornecido para demonstrar a sintaxe para usar **SqlBulkCopy** somente. Se as tabelas de origem e destino estiverem localizadas na mesma instância do SQL Server, é mais fácil e rápido para usar um Transact-SQL `INSERT … SELECT` instrução para copiar os dados.  
  
 [!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
 [!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]  
  
## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a>Executando uma operação de cópia em massa usando Transact-SQL e a classe de comando  
 O exemplo a seguir ilustra como usar o <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> método para executar a instrução BULK INSERT.  
  
> [!NOTE]
>  O caminho do arquivo da fonte de dados é relativo ao servidor. O processo do servidor deve ter acesso a esse caminho para que a operação de cópia em massa seja bem-sucedida.  
  
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
 [Operações de cópia em massa no SQL Server](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
