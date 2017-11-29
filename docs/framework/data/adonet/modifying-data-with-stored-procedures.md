---
title: Modificando dados com procedimentos armazenados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1f8f0c37e5ac84d878f1d443d2bcc1e8ded099a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="modifying-data-with-stored-procedures"></a><span data-ttu-id="2dff2-102">Modificando dados com procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="2dff2-102">Modifying Data with Stored Procedures</span></span>
<span data-ttu-id="2dff2-103">Os procedimentos armazenados podem aceitar dados como parâmetros de entrada e podem retornar dados como parâmetros de saída, conjuntos de resultados ou valores de retorno.</span><span class="sxs-lookup"><span data-stu-id="2dff2-103">Stored procedures can accept data as input parameters and can return data as output parameters, result sets, or return values.</span></span> <span data-ttu-id="2dff2-104">O exemplo a seguir ilustra como o ADO.NET envia e recebe parâmetros de entrada, parâmetros de saída e valores de retorno.</span><span class="sxs-lookup"><span data-stu-id="2dff2-104">The sample below illustrates how ADO.NET sends and receives input parameters, output parameters, and return values.</span></span> <span data-ttu-id="2dff2-105">O exemplo insere um novo registro em uma tabela onde a coluna de chave primária é uma coluna de identidade em um banco de dados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2dff2-105">The example inserts a new record into a table where the primary key column is an identity column in a SQL Server database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2dff2-106">Se você estiver usando procedimentos armazenados do SQL Server para editar ou excluir dados usando um <xref:System.Data.SqlClient.SqlDataAdapter>, não use SET NOCOUNT ON na definição do procedimento armazenado.</span><span class="sxs-lookup"><span data-stu-id="2dff2-106">If you are using SQL Server stored procedures to edit or delete data using a <xref:System.Data.SqlClient.SqlDataAdapter>, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="2dff2-107">Isso faz com que a contagem retornada de linhas afetadas seja zero, o que o `DataAdapter` interpreta como um conflito de simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="2dff2-107">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="2dff2-108">Nesse caso, será gerada uma <xref:System.Data.DBConcurrencyException>.</span><span class="sxs-lookup"><span data-stu-id="2dff2-108">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2dff2-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2dff2-109">Example</span></span>  
 <span data-ttu-id="2dff2-110">O exemplo usa o procedimento armazenado a seguir para inserir uma nova categoria para o **Northwind** **categorias** tabela.</span><span class="sxs-lookup"><span data-stu-id="2dff2-110">The sample uses the following stored procedure to insert a new category into the **Northwind** **Categories** table.</span></span> <span data-ttu-id="2dff2-111">O procedimento armazenado assume o valor de **CategoryName** coluna como um parâmetro de entrada e usa o SCOPE_IDENTITY () de função para recuperar o novo valor do campo de identidade, **CategoryID**e retorná-lo um parâmetro de saída.</span><span class="sxs-lookup"><span data-stu-id="2dff2-111">The stored procedure takes the value in the **CategoryName** column as an input parameter and uses the SCOPE_IDENTITY() function to retrieve the new value of the identity field, **CategoryID**, and return it in an output parameter.</span></span> <span data-ttu-id="2dff2-112">A instrução de retorno usa o @@ROWCOUNT função para retornar o número de linhas inseridas.</span><span class="sxs-lookup"><span data-stu-id="2dff2-112">The RETURN statement uses the @@ROWCOUNT function to return the number of rows inserted.</span></span>  
  
```  
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 <span data-ttu-id="2dff2-113">O código de exemplo a seguir usa o procedimento armazenado `InsertCategory` mostrado acima como a origem de <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> de <xref:System.Data.SqlClient.SqlDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="2dff2-113">The following code example uses the `InsertCategory` stored procedure shown above as the source for the <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> of the <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="2dff2-114">O parâmetro de saída `@Identity` será refletido em <xref:System.Data.DataSet> após a inserção do registro no banco de dados quando o método `Update` de <xref:System.Data.SqlClient.SqlDataAdapter> for chamado.</span><span class="sxs-lookup"><span data-stu-id="2dff2-114">The `@Identity` output parameter will be reflected in the <xref:System.Data.DataSet> after the record has been inserted into the database when the `Update` method of the <xref:System.Data.SqlClient.SqlDataAdapter> is called.</span></span> <span data-ttu-id="2dff2-115">O código também recupera o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="2dff2-115">The code also retrieves the return value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2dff2-116">Ao usar o <xref:System.Data.OleDb.OleDbDataAdapter>, você deve especificar parâmetros com um <xref:System.Data.ParameterDirection> de **ReturnValue** antes dos outros parâmetros.</span><span class="sxs-lookup"><span data-stu-id="2dff2-116">When using the <xref:System.Data.OleDb.OleDbDataAdapter>, you must specify parameters with a <xref:System.Data.ParameterDirection> of **ReturnValue** before the other parameters.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2dff2-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2dff2-117">See Also</span></span>  
 <span data-ttu-id="2dff2-118">[Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="2dff2-118">[Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)</span></span>  
 [<span data-ttu-id="2dff2-119">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="2dff2-119">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="2dff2-120">Executar um comando</span><span class="sxs-lookup"><span data-stu-id="2dff2-120">Executing a Command</span></span>](../../../../docs/framework/data/adonet/executing-a-command.md)  
 <span data-ttu-id="2dff2-121">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="2dff2-121">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
