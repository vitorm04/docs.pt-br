---
title: Operações de cópia em massa único
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.openlocfilehash: 47f89feb90efbafb6c43bbad78f05292213a0c58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="single-bulk-copy-operations"></a>Operações de cópia em massa único
A abordagem mais simples para a execução de uma operação de cópia em massa do SQL Server é executar uma única operação em um banco de dados. Por padrão, uma operação de cópia em massa é executada como uma operação isolada: a operação de cópia ocorre de forma não transacionada, sem a oportunidade de disponibilizá-la de volta.  
  
> [!NOTE]
>  Se você precisar reverter toda ou parte da cópia em massa quando ocorre um erro, você pode usar um <xref:System.Data.SqlClient.SqlBulkCopy>-gerenciado transação ou executar a operação de cópia em massa dentro de uma transação existente. **SqlBulkCopy** também funcionará com <xref:System.Transactions> se a conexão está inscrito (implícita ou explicitamente) em um **System. Transactions** transação.  
>   
>  Para obter mais informações, consulte [transações e operações de cópia em massa](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).  
  
 As etapas gerais para executar uma operação de cópia em massa são da seguinte maneira:  
  
1.  Conecte-se ao servidor de origem e obter os dados a serem copiados. Os dados também podem vir de outras fontes, se ele pode ser recuperado de um <xref:System.Data.IDataReader> ou <xref:System.Data.DataTable> objeto.  
  
2.  Conecte-se ao servidor de destino (a menos que você deseje **SqlBulkCopy** para estabelecer uma conexão para você).  
  
3.  Criar um <xref:System.Data.SqlClient.SqlBulkCopy> objeto, definindo as propriedades necessárias.  
  
4.  Definir o **DestinationTableName** operação de inserção de propriedade para indicar a tabela de destino em massa.  
  
5.  Chame um do **WriteToServer** métodos.  
  
6.  Opcionalmente, atualize propriedades e chamada **WriteToServer** novamente, conforme necessário.  
  
7.  Chamar <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>, ou encapsular as operações de cópia em massa dentro de um `Using` instrução.  
  
> [!CAUTION]
>  É recomendável que correspondem os tipos de dados de coluna de origem e destino. Se os tipos de dados não coincidirem, **SqlBulkCopy** tenta converter cada valor de origem para o tipo de dados de destino, usando as regras empregadas pelo <xref:System.Data.SqlClient.SqlParameter.Value%2A>. Conversões podem afetar o desempenho e também podem resultar em erros inesperados. Por exemplo, um `Double` tipo de dados pode ser convertido em um `Decimal` maioria de tipo de dados de tempo, mas não sempre.  
  
## <a name="example"></a>Exemplo  
 O aplicativo de console a seguir demonstra como carregar dados usando o <xref:System.Data.SqlClient.SqlBulkCopy> classe. Neste exemplo, um <xref:System.Data.SqlClient.SqlDataReader> é usado para copiar dados do **Production. Product** tabela no SQL Server**AdventureWorks** banco de dados para uma tabela semelhante no mesmo banco de dados.  
  
> [!IMPORTANT]
>  Este exemplo não funcionará a menos que você criou as tabelas de trabalho conforme descrito em [configuração de exemplo de cópia em massa](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Esse código é fornecido para demonstrar a sintaxe para usar **SqlBulkCopy** somente. Se as tabelas de origem e destino estão localizadas na mesma instância do SQL Server, é mais fácil e rápido para usar um Transact-SQL `INSERT … SELECT` instrução para copiar os dados.  
  
 [!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
 [!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]  
  
## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a>Executar uma operação de cópia em massa usando Transact-SQL e a classe de comando  
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
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
