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
# <a name="single-bulk-copy-operations"></a><span data-ttu-id="69455-102">Operações únicas de cópia em massa</span><span class="sxs-lookup"><span data-stu-id="69455-102">Single Bulk Copy Operations</span></span>
<span data-ttu-id="69455-103">A abordagem mais simples para executar uma SQL Server operação de cópia em massa é executar uma única operação em um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="69455-103">The simplest approach to performing a SQL Server bulk copy operation is to perform a single operation against a database.</span></span> <span data-ttu-id="69455-104">Por padrão, uma operação de cópia em massa é executada como uma operação isolada: a operação de cópia ocorre de forma não-transacionada, sem nenhuma oportunidade de redistribuí-la.</span><span class="sxs-lookup"><span data-stu-id="69455-104">By default, a bulk copy operation is performed as an isolated operation: the copy operation occurs in a non-transacted way, with no opportunity for rolling it back.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="69455-105">Se você precisar reverter toda ou parte da cópia em massa quando ocorrer um erro, poderá usar uma <xref:System.Data.SqlClient.SqlBulkCopy>transação gerenciada ou executar a operação de cópia em massa em uma transação existente.</span><span class="sxs-lookup"><span data-stu-id="69455-105">If you need to roll back all or part of the bulk copy when an error occurs, you can either use a <xref:System.Data.SqlClient.SqlBulkCopy>-managed transaction, or perform the bulk copy operation within an existing transaction.</span></span> <span data-ttu-id="69455-106">O **SqlBulkCopy** também funcionará <xref:System.Transactions> se a conexão for listada (implícita ou explicitamente) em uma transação **System.** Transactions.</span><span class="sxs-lookup"><span data-stu-id="69455-106">**SqlBulkCopy** will also work with <xref:System.Transactions> if the connection is enlisted (implicitly or explicitly) into a **System.Transactions** transaction.</span></span>  
>   
>  <span data-ttu-id="69455-107">Para obter mais informações, consulte [operações de cópia em massa e transação](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).</span><span class="sxs-lookup"><span data-stu-id="69455-107">For more information, see [Transaction and Bulk Copy Operations](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).</span></span>  
  
 <span data-ttu-id="69455-108">As etapas gerais para executar uma operação de cópia em massa são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="69455-108">The general steps for performing a bulk copy operation are as follows:</span></span>  
  
1. <span data-ttu-id="69455-109">Conecte-se ao servidor de origem e obtenha os dados a serem copiados.</span><span class="sxs-lookup"><span data-stu-id="69455-109">Connect to the source server and obtain the data to be copied.</span></span> <span data-ttu-id="69455-110">Os dados também podem vir de outras fontes, se puderem ser recuperados <xref:System.Data.IDataReader> de <xref:System.Data.DataTable> um objeto ou.</span><span class="sxs-lookup"><span data-stu-id="69455-110">Data can also come from other sources, if it can be retrieved from an <xref:System.Data.IDataReader> or <xref:System.Data.DataTable> object.</span></span>  
  
2. <span data-ttu-id="69455-111">Conecte-se ao servidor de destino (a menos que você queira que o **SqlBulkCopy** estabeleça uma conexão para você).</span><span class="sxs-lookup"><span data-stu-id="69455-111">Connect to the destination server (unless you want **SqlBulkCopy** to establish a connection for you).</span></span>  
  
3. <span data-ttu-id="69455-112">Crie um <xref:System.Data.SqlClient.SqlBulkCopy> objeto, definindo as propriedades necessárias.</span><span class="sxs-lookup"><span data-stu-id="69455-112">Create a <xref:System.Data.SqlClient.SqlBulkCopy> object, setting any necessary properties.</span></span>  
  
4. <span data-ttu-id="69455-113">Defina a propriedade **DestinationTableName** para indicar a tabela de destino para a operação de inserção em massa.</span><span class="sxs-lookup"><span data-stu-id="69455-113">Set the **DestinationTableName** property to indicate the target table for the bulk insert operation.</span></span>  
  
5. <span data-ttu-id="69455-114">Chame um dos métodos **WriteToServer** .</span><span class="sxs-lookup"><span data-stu-id="69455-114">Call one of the **WriteToServer** methods.</span></span>  
  
6. <span data-ttu-id="69455-115">Opcionalmente, atualize as propriedades e chame **WriteToServer** novamente conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="69455-115">Optionally, update properties and call **WriteToServer** again as necessary.</span></span>  
  
7. <span data-ttu-id="69455-116">Chamar <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>ou encapsular as operações de cópia em massa `Using` em uma instrução.</span><span class="sxs-lookup"><span data-stu-id="69455-116">Call <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>, or wrap the bulk copy operations within a `Using` statement.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="69455-117">É recomendável que os tipos de dados de coluna de origem e destino coincidam.</span><span class="sxs-lookup"><span data-stu-id="69455-117">We recommend that the source and target column data types match.</span></span> <span data-ttu-id="69455-118">Se os tipos de dados não corresponderem, o **SqlBulkCopy** tentará converter cada valor de origem no tipo de dados de destino, <xref:System.Data.SqlClient.SqlParameter.Value%2A>usando as regras empregadas pelo.</span><span class="sxs-lookup"><span data-stu-id="69455-118">If the data types do not match, **SqlBulkCopy** attempts to convert each source value to the target data type, using the rules employed by <xref:System.Data.SqlClient.SqlParameter.Value%2A>.</span></span> <span data-ttu-id="69455-119">As conversões podem afetar o desempenho e também podem resultar em erros inesperados.</span><span class="sxs-lookup"><span data-stu-id="69455-119">Conversions can affect performance, and also can result in unexpected errors.</span></span> <span data-ttu-id="69455-120">Por exemplo, um `Double` tipo de dados pode ser convertido em `Decimal` um tipo de dados na maior parte do tempo, mas nem sempre.</span><span class="sxs-lookup"><span data-stu-id="69455-120">For example, a `Double` data type can be converted to a `Decimal` data type most of the time, but not always.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69455-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69455-121">Example</span></span>  
 <span data-ttu-id="69455-122">O aplicativo de console a seguir demonstra como carregar dados usando <xref:System.Data.SqlClient.SqlBulkCopy> a classe.</span><span class="sxs-lookup"><span data-stu-id="69455-122">The following console application demonstrates how to load data using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="69455-123">Neste exemplo, um <xref:System.Data.SqlClient.SqlDataReader> é usado para copiar dados da tabela de **produção. Product** no banco SQL Server dados **AdventureWorks** para uma tabela semelhante no mesmo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="69455-123">In this example, a <xref:System.Data.SqlClient.SqlDataReader> is used to copy data from the **Production.Product** table in the SQL Server **AdventureWorks** database to a similar table in the same database.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="69455-124">Este exemplo não será executado a menos que você tenha criado as tabelas de trabalho conforme descrito em [configuração de exemplo de cópia em massa](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span><span class="sxs-lookup"><span data-stu-id="69455-124">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span></span> <span data-ttu-id="69455-125">Esse código é fornecido para demonstrar a sintaxe somente para uso de **SqlBulkCopy** .</span><span class="sxs-lookup"><span data-stu-id="69455-125">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="69455-126">Se as tabelas de origem e destino estiverem localizadas na mesma instância de SQL Server, será mais fácil e rápido usar uma instrução Transact `INSERT … SELECT` -SQL para copiar os dados.</span><span class="sxs-lookup"><span data-stu-id="69455-126">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
 [!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
 [!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]  
  
## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a><span data-ttu-id="69455-127">Executando uma operação de cópia em massa usando Transact-SQL e a classe Command</span><span class="sxs-lookup"><span data-stu-id="69455-127">Performing a Bulk Copy Operation Using Transact-SQL and the Command Class</span></span>  
 <span data-ttu-id="69455-128">O exemplo a seguir ilustra como usar o <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> método para executar a instrução BULK INSERT.</span><span class="sxs-lookup"><span data-stu-id="69455-128">The following example illustrates how to use the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method to execute the BULK INSERT statement.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="69455-129">O caminho do arquivo para a fonte de dados é relativo ao servidor.</span><span class="sxs-lookup"><span data-stu-id="69455-129">The file path for the data source is relative to the server.</span></span> <span data-ttu-id="69455-130">O processo do servidor deve ter acesso a esse caminho para que a operação de cópia em massa tenha sucesso.</span><span class="sxs-lookup"><span data-stu-id="69455-130">The server process must have access to that path in order for the bulk copy operation to succeed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="69455-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69455-131">See also</span></span>

- [<span data-ttu-id="69455-132">Operações de cópia em massa no SQL Server</span><span class="sxs-lookup"><span data-stu-id="69455-132">Bulk Copy Operations in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- <span data-ttu-id="69455-133">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="69455-133">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
