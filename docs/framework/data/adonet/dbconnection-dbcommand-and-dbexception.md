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
# <a name="dbconnection-dbcommand-and-dbexception"></a><span data-ttu-id="909b3-102">DbConnection, DbCommand e DbException</span><span class="sxs-lookup"><span data-stu-id="909b3-102">DbConnection, DbCommand and DbException</span></span>
<span data-ttu-id="909b3-103">Depois de ter criado um <xref:System.Data.Common.DbProviderFactory> e um <xref:System.Data.Common.DbConnection>, você pode trabalhar com comandos e leitores de dados para recuperar dados da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="909b3-103">Once you have created a <xref:System.Data.Common.DbProviderFactory> and a <xref:System.Data.Common.DbConnection>, you can then work with commands and data readers to retrieve data from the data source.</span></span>  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="909b3-104">Recuperando exemplo de dados</span><span class="sxs-lookup"><span data-stu-id="909b3-104">Retrieving Data Example</span></span>  
 <span data-ttu-id="909b3-105">Este exemplo usa uma `DbConnection` objeto como um argumento.</span><span class="sxs-lookup"><span data-stu-id="909b3-105">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="909b3-106">Um <xref:System.Data.Common.DbCommand> é criada para selecionar dados da tabela de categorias, definindo o <xref:System.Data.Common.DbCommand.CommandText%2A> para uma instrução SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="909b3-106">A <xref:System.Data.Common.DbCommand> is created to select data from the Categories table by setting the <xref:System.Data.Common.DbCommand.CommandText%2A> to a SQL SELECT statement.</span></span> <span data-ttu-id="909b3-107">O código presume que a tabela de categorias existe na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="909b3-107">The code assumes that the Categories table exists at the data source.</span></span> <span data-ttu-id="909b3-108">A conexão é aberta e os dados são recuperados usando uma <xref:System.Data.Common.DbDataReader>.</span><span class="sxs-lookup"><span data-stu-id="909b3-108">The connection is opened and the data is retrieved using a <xref:System.Data.Common.DbDataReader>.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a><span data-ttu-id="909b3-109">Executar um comando de exemplo</span><span class="sxs-lookup"><span data-stu-id="909b3-109">Executing a Command Example</span></span>  
 <span data-ttu-id="909b3-110">Este exemplo usa uma `DbConnection` objeto como um argumento.</span><span class="sxs-lookup"><span data-stu-id="909b3-110">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="909b3-111">Se o `DbConnection` for válido, a conexão é aberta e um <xref:System.Data.Common.DbCommand> é criado e executado.</span><span class="sxs-lookup"><span data-stu-id="909b3-111">If the `DbConnection` is valid, the connection is opened and a <xref:System.Data.Common.DbCommand> is created and executed.</span></span> <span data-ttu-id="909b3-112">O <xref:System.Data.Common.DbCommand.CommandText%2A> é definido como uma instrução SQL INSERT que executa uma inserção na tabela de categorias no banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="909b3-112">The <xref:System.Data.Common.DbCommand.CommandText%2A> is set to a SQL INSERT statement that performs an insert to the Categories table in the Northwind database.</span></span> <span data-ttu-id="909b3-113">O código presume que o banco de dados Northwind existe na fonte de dados, e que a sintaxe SQL usada na instrução INSERT é válida para o provedor especificado.</span><span class="sxs-lookup"><span data-stu-id="909b3-113">The code assumes that the Northwind database exists at the data source, and that the SQL syntax used in the INSERT statement is valid for the specified provider.</span></span> <span data-ttu-id="909b3-114">Erros que ocorrem na fonte de dados são manipulados pelo <xref:System.Data.Common.DbException> bloco de código e todas as exceções são tratados no <xref:System.Exception> bloco.</span><span class="sxs-lookup"><span data-stu-id="909b3-114">Errors occurring at the data source are handled by the <xref:System.Data.Common.DbException> code block, and all other exceptions are handled in the <xref:System.Exception> block.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a><span data-ttu-id="909b3-115">Tratamento de erros de dados com DbException</span><span class="sxs-lookup"><span data-stu-id="909b3-115">Handling Data Errors with DbException</span></span>  
 <span data-ttu-id="909b3-116">O <xref:System.Data.Common.DbException> classe é a classe base para todas as exceções geradas em nome de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="909b3-116">The <xref:System.Data.Common.DbException> class is the base class for all exceptions thrown on behalf of a data source.</span></span> <span data-ttu-id="909b3-117">Você pode usá-lo no seu código de tratamento de exceções para manipular exceções lançadas por provedores diferentes sem ter que fazer referência a uma classe de exceção específica.</span><span class="sxs-lookup"><span data-stu-id="909b3-117">You can use it in your exception handling code to handle exceptions thrown by different providers without having to reference a specific exception class.</span></span> <span data-ttu-id="909b3-118">O fragmento de código a seguir demonstra como usar <xref:System.Data.Common.DbException> para exibir informações de erro retornadas pela fonte de dados usando <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, e <xref:System.Exception.Message%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="909b3-118">The following code fragment demonstrates how to use <xref:System.Data.Common.DbException> to display error information returned by the data source using <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, and <xref:System.Exception.Message%2A> properties.</span></span> <span data-ttu-id="909b3-119">A saída exibirá o tipo de erro, a origem que indica o nome do provedor, um código de erro e a mensagem associada ao erro.</span><span class="sxs-lookup"><span data-stu-id="909b3-119">The output will display the type of error, the source indicating the provider name, an error code, and the message associated with the error.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="909b3-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="909b3-120">See Also</span></span>  
 [<span data-ttu-id="909b3-121">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="909b3-121">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [<span data-ttu-id="909b3-122">Obtendo um DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="909b3-122">Obtaining a DbProviderFactory</span></span>](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 [<span data-ttu-id="909b3-123">Modificando dados com um DbDataAdapter</span><span class="sxs-lookup"><span data-stu-id="909b3-123">Modifying Data with a DbDataAdapter</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 <span data-ttu-id="909b3-124">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="909b3-124">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
