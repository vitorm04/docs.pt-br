---
title: Operações de cópia em massa único
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.openlocfilehash: 274a6e87b272002a567fd92605c4e690c03b6e26
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44271004"
---
# <a name="single-bulk-copy-operations"></a><span data-ttu-id="766cf-102">Operações de cópia em massa único</span><span class="sxs-lookup"><span data-stu-id="766cf-102">Single Bulk Copy Operations</span></span>
<span data-ttu-id="766cf-103">A abordagem mais simples para executar uma operação de cópia em massa do SQL Server é executar uma única operação em um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="766cf-103">The simplest approach to performing a SQL Server bulk copy operation is to perform a single operation against a database.</span></span> <span data-ttu-id="766cf-104">Por padrão, uma operação de cópia em massa é executada como uma operação isolada: a operação de cópia ocorre de forma não transacionada, sem a oportunidade de revertê-la de volta.</span><span class="sxs-lookup"><span data-stu-id="766cf-104">By default, a bulk copy operation is performed as an isolated operation: the copy operation occurs in a non-transacted way, with no opportunity for rolling it back.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="766cf-105">Se você precisar reverter toda ou parte da cópia em massa quando ocorrer um erro, você pode usar um <xref:System.Data.SqlClient.SqlBulkCopy>-transação gerenciada ou executar a operação de cópia em massa dentro de uma transação existente.</span><span class="sxs-lookup"><span data-stu-id="766cf-105">If you need to roll back all or part of the bulk copy when an error occurs, you can either use a <xref:System.Data.SqlClient.SqlBulkCopy>-managed transaction, or perform the bulk copy operation within an existing transaction.</span></span> <span data-ttu-id="766cf-106">**SqlBulkCopy** também trabalhará <xref:System.Transactions> se a conexão será inscrita (implícita ou explicitamente) em um **System. Transactions** transação.</span><span class="sxs-lookup"><span data-stu-id="766cf-106">**SqlBulkCopy** will also work with <xref:System.Transactions> if the connection is enlisted (implicitly or explicitly) into a **System.Transactions** transaction.</span></span>  
>   
>  <span data-ttu-id="766cf-107">Para obter mais informações, consulte [transações e operações de cópia em massa](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).</span><span class="sxs-lookup"><span data-stu-id="766cf-107">For more information, see [Transaction and Bulk Copy Operations](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).</span></span>  
  
 <span data-ttu-id="766cf-108">As etapas gerais para executar uma operação de cópia em massa são da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="766cf-108">The general steps for performing a bulk copy operation are as follows:</span></span>  
  
1.  <span data-ttu-id="766cf-109">Conectar-se ao servidor de origem e obter os dados a serem copiados.</span><span class="sxs-lookup"><span data-stu-id="766cf-109">Connect to the source server and obtain the data to be copied.</span></span> <span data-ttu-id="766cf-110">Dados também podem vir de outras fontes, se ele pode ser recuperado de um <xref:System.Data.IDataReader> ou <xref:System.Data.DataTable> objeto.</span><span class="sxs-lookup"><span data-stu-id="766cf-110">Data can also come from other sources, if it can be retrieved from an <xref:System.Data.IDataReader> or <xref:System.Data.DataTable> object.</span></span>  
  
2.  <span data-ttu-id="766cf-111">Conectar-se ao servidor de destino (a menos que você deseje **SqlBulkCopy** para estabelecer uma conexão para você).</span><span class="sxs-lookup"><span data-stu-id="766cf-111">Connect to the destination server (unless you want **SqlBulkCopy** to establish a connection for you).</span></span>  
  
3.  <span data-ttu-id="766cf-112">Criar um <xref:System.Data.SqlClient.SqlBulkCopy> objeto, definindo as propriedades necessárias.</span><span class="sxs-lookup"><span data-stu-id="766cf-112">Create a <xref:System.Data.SqlClient.SqlBulkCopy> object, setting any necessary properties.</span></span>  
  
4.  <span data-ttu-id="766cf-113">Defina as **DestinationTableName** propriedade para indicar a tabela de destino para a maior parte de operação de inserção.</span><span class="sxs-lookup"><span data-stu-id="766cf-113">Set the **DestinationTableName** property to indicate the target table for the bulk insert operation.</span></span>  
  
5.  <span data-ttu-id="766cf-114">Chame um dos **WriteToServer** métodos.</span><span class="sxs-lookup"><span data-stu-id="766cf-114">Call one of the **WriteToServer** methods.</span></span>  
  
6.  <span data-ttu-id="766cf-115">Opcionalmente, atualize as propriedades e chamar **WriteToServer** novamente, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="766cf-115">Optionally, update properties and call **WriteToServer** again as necessary.</span></span>  
  
7.  <span data-ttu-id="766cf-116">Chame <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>, ou encapsular as operações de cópia em massa dentro de um `Using` instrução.</span><span class="sxs-lookup"><span data-stu-id="766cf-116">Call <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>, or wrap the bulk copy operations within a `Using` statement.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="766cf-117">É recomendável que os tipos de dados de coluna de origem e destino correspondam.</span><span class="sxs-lookup"><span data-stu-id="766cf-117">We recommend that the source and target column data types match.</span></span> <span data-ttu-id="766cf-118">Se os tipos de dados não corresponderem, **SqlBulkCopy** tenta converter cada valor de origem para o tipo de dados de destino, usando as regras de empregado pelo <xref:System.Data.SqlClient.SqlParameter.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="766cf-118">If the data types do not match, **SqlBulkCopy** attempts to convert each source value to the target data type, using the rules employed by <xref:System.Data.SqlClient.SqlParameter.Value%2A>.</span></span> <span data-ttu-id="766cf-119">As conversões podem afetar o desempenho e também podem resultar em erros inesperados.</span><span class="sxs-lookup"><span data-stu-id="766cf-119">Conversions can affect performance, and also can result in unexpected errors.</span></span> <span data-ttu-id="766cf-120">Por exemplo, uma `Double` tipo de dados pode ser convertido em um `Decimal` a maioria do tipo de dados do tempo, mas não sempre.</span><span class="sxs-lookup"><span data-stu-id="766cf-120">For example, a `Double` data type can be converted to a `Decimal` data type most of the time, but not always.</span></span>  
  
## <a name="example"></a><span data-ttu-id="766cf-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="766cf-121">Example</span></span>  
 <span data-ttu-id="766cf-122">O aplicativo de console a seguir demonstra como carregar dados usando o <xref:System.Data.SqlClient.SqlBulkCopy> classe.</span><span class="sxs-lookup"><span data-stu-id="766cf-122">The following console application demonstrates how to load data using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="766cf-123">Neste exemplo, uma <xref:System.Data.SqlClient.SqlDataReader> é usado para copiar dados do **Production. Product** tabela no SQL Server**AdventureWorks** banco de dados em uma tabela semelhante no mesmo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="766cf-123">In this example, a <xref:System.Data.SqlClient.SqlDataReader> is used to copy data from the **Production.Product** table in the SQL Server**AdventureWorks** database to a similar table in the same database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="766cf-124">Este exemplo não será executado, a menos que você criou as tabelas de trabalho conforme descrito em [configuração de exemplo de cópia em massa](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span><span class="sxs-lookup"><span data-stu-id="766cf-124">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span></span> <span data-ttu-id="766cf-125">Esse código é fornecido para demonstrar a sintaxe para usar **SqlBulkCopy** somente.</span><span class="sxs-lookup"><span data-stu-id="766cf-125">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="766cf-126">Se as tabelas de origem e destino estiverem localizadas na mesma instância do SQL Server, é mais fácil e rápido para usar um Transact-SQL `INSERT … SELECT` instrução para copiar os dados.</span><span class="sxs-lookup"><span data-stu-id="766cf-126">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
 [!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
 [!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]  
  
## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a><span data-ttu-id="766cf-127">Executando uma operação de cópia em massa usando Transact-SQL e a classe de comando</span><span class="sxs-lookup"><span data-stu-id="766cf-127">Performing a Bulk Copy Operation Using Transact-SQL and the Command Class</span></span>  
 <span data-ttu-id="766cf-128">O exemplo a seguir ilustra como usar o <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> método para executar a instrução BULK INSERT.</span><span class="sxs-lookup"><span data-stu-id="766cf-128">The following example illustrates how to use the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method to execute the BULK INSERT statement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="766cf-129">O caminho do arquivo da fonte de dados é relativo ao servidor.</span><span class="sxs-lookup"><span data-stu-id="766cf-129">The file path for the data source is relative to the server.</span></span> <span data-ttu-id="766cf-130">O processo do servidor deve ter acesso a esse caminho para que a operação de cópia em massa seja bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="766cf-130">The server process must have access to that path in order for the bulk copy operation to succeed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="766cf-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="766cf-131">See Also</span></span>  
 [<span data-ttu-id="766cf-132">Operações de cópia em massa no SQL Server</span><span class="sxs-lookup"><span data-stu-id="766cf-132">Bulk Copy Operations in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 <span data-ttu-id="766cf-133">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="766cf-133">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
