---
title: DbConnection, DbCommand e DbException
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 58aab611-7e6f-4749-b983-28ab7ae87dbe
ms.openlocfilehash: 419f152d45ec254efab9270f67ace6e46a6b96a7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757119"
---
# <a name="dbconnection-dbcommand-and-dbexception"></a>DbConnection, DbCommand e DbException
Depois de ter criado um <xref:System.Data.Common.DbProviderFactory> e um <xref:System.Data.Common.DbConnection>, você pode trabalhar com comandos e leitores de dados para recuperar dados da fonte de dados.  
  
## <a name="retrieving-data-example"></a>Recuperando exemplo de dados  
 Este exemplo usa uma `DbConnection` objeto como um argumento. Um <xref:System.Data.Common.DbCommand> é criada para selecionar dados da tabela de categorias, definindo o <xref:System.Data.Common.DbCommand.CommandText%2A> para uma instrução SQL SELECT. O código presume que a tabela de categorias existe na fonte de dados. A conexão é aberta e os dados são recuperados usando uma <xref:System.Data.Common.DbDataReader>.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a>Executar um comando de exemplo  
 Este exemplo usa uma `DbConnection` objeto como um argumento. Se o `DbConnection` for válido, a conexão é aberta e um <xref:System.Data.Common.DbCommand> é criado e executado. O <xref:System.Data.Common.DbCommand.CommandText%2A> é definido como uma instrução SQL INSERT que executa uma inserção na tabela de categorias no banco de dados Northwind. O código presume que o banco de dados Northwind existe na fonte de dados, e que a sintaxe SQL usada na instrução INSERT é válida para o provedor especificado. Erros que ocorrem na fonte de dados são manipulados pelo <xref:System.Data.Common.DbException> bloco de código e todas as exceções são tratados no <xref:System.Exception> bloco.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a>Tratamento de erros de dados com DbException  
 O <xref:System.Data.Common.DbException> classe é a classe base para todas as exceções geradas em nome de uma fonte de dados. Você pode usá-lo no seu código de tratamento de exceções para manipular exceções lançadas por provedores diferentes sem ter que fazer referência a uma classe de exceção específica. O fragmento de código a seguir demonstra como usar <xref:System.Data.Common.DbException> para exibir informações de erro retornadas pela fonte de dados usando <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, e <xref:System.Exception.Message%2A> propriedades. A saída exibirá o tipo de erro, a origem que indica o nome do provedor, um código de erro e a mensagem associada ao erro.  
  
```vb  
Try  
    ' Do work here.  
Catch ex As DbException  
    ' Display information about the exception.  
    Console.WriteLine("GetType: {0}", ex.GetType())  
    Console.WriteLine("Source: {0}", ex.Source)  
    Console.WriteLine("ErrorCode: {0}", ex.ErrorCode)  
    Console.WriteLine("Message: {0}", ex.Message)  
Finally  
    ' Perform cleanup here.  
End Try  
```  
  
```csharp  
try  
{  
    // Do work here.  
}  
catch (DbException ex)  
{  
    // Display information about the exception.  
    Console.WriteLine("GetType: {0}", ex.GetType());  
    Console.WriteLine("Source: {0}", ex.Source);  
    Console.WriteLine("ErrorCode: {0}", ex.ErrorCode);  
    Console.WriteLine("Message: {0}", ex.Message);  
}  
finally  
{  
    // Perform cleanup here.  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [Obtendo um DbProviderFactory](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 [Modificando dados com um DbDataAdapter](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
