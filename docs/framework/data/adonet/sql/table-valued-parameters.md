---
title: Parâmetros de valores de tabela
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 01b19d49ee82a884247e4eb260f659f19f124cee
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="table-valued-parameters"></a><span data-ttu-id="3cdb1-102">Parâmetros de valores de tabela</span><span class="sxs-lookup"><span data-stu-id="3cdb1-102">Table-Valued Parameters</span></span>
<span data-ttu-id="3cdb1-103">Os parâmetros com valor de tabela fornecem uma maneira fácil de marshaling em várias linhas de dados de um aplicativo cliente para o SQL Server sem exigir várias viagens de ida e volta ou uma lógica especial do lado do servidor para processar os dados.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-103">Table-valued parameters provide an easy way to marshal multiple rows of data from a client application to SQL Server without requiring multiple round trips or special server-side logic for processing the data.</span></span> <span data-ttu-id="3cdb1-104">Você pode usar parâmetros de valores de tabela para encapsular linhas de dados em um aplicativo cliente e enviar os dados para o servidor em um único comando parametrizado.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-104">You can use table-valued parameters to encapsulate rows of data in a client application and send the data to the server in a single parameterized command.</span></span> <span data-ttu-id="3cdb1-105">As linhas de dados de entrada são armazenadas em uma variável da tabela que pode, em seguida, ser operada usando o [!INCLUDE[tsql](../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3cdb1-105">The incoming data rows are stored in a table variable that can then be operated on by using [!INCLUDE[tsql](../../../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="3cdb1-106">Os valores de coluna em parâmetros de valores de tabela podem ser acessados usando instruções SELECT padrão do [!INCLUDE[tsql](../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3cdb1-106">Column values in table-valued parameters can be accessed using standard [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] SELECT statements.</span></span> <span data-ttu-id="3cdb1-107">Os parâmetros de valores de tabela são fortemente tipados e sua estrutura é validada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-107">Table-valued parameters are strongly typed and their structure is automatically validated.</span></span> <span data-ttu-id="3cdb1-108">O tamanho de parâmetros de valores de tabela é delimitado somente pela memória do servidor.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-108">The size of table-valued parameters is limited only by server memory.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3cdb1-109">Você não pode retornar dados em um parâmetro com valor de tabela.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-109">You cannot return data in a table-valued parameter.</span></span> <span data-ttu-id="3cdb1-110">Os parâmetros de valores de tabela são somente entrada; a palavra-chave OUTPUT não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-110">Table-valued parameters are input-only; the OUTPUT keyword is not supported.</span></span>  
  
 <span data-ttu-id="3cdb1-111">Para obter mais informações sobre parâmetros de valores de tabela, consulte os seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-111">For more information about table-valued parameters, see the following resources.</span></span>  
  
|<span data-ttu-id="3cdb1-112">Recurso</span><span class="sxs-lookup"><span data-stu-id="3cdb1-112">Resource</span></span>|<span data-ttu-id="3cdb1-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="3cdb1-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="3cdb1-114">[Parâmetros com valor de tabela (mecanismo de banco de dados)](http://go.microsoft.com/fwlink/?LinkId=98363) nos Manuais Online do SQL Server</span><span class="sxs-lookup"><span data-stu-id="3cdb1-114">[Table-Valued Parameters (Database Engine)](http://go.microsoft.com/fwlink/?LinkId=98363) in SQL Server Books Online</span></span>|<span data-ttu-id="3cdb1-115">Descreve como criar e usar parâmetros de valores de tabela.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-115">Describes how to create and use table-valued parameters.</span></span>|  
|<span data-ttu-id="3cdb1-116">[Tipos de tabela definidos pelo usuário](http://go.microsoft.com/fwlink/?LinkId=98364) nos Manuais Online do SQL Server</span><span class="sxs-lookup"><span data-stu-id="3cdb1-116">[User-Defined Table Types](http://go.microsoft.com/fwlink/?LinkId=98364) in SQL Server Books Online</span></span>|<span data-ttu-id="3cdb1-117">Descreve os tipos de tabela definidos pelo usuário que são usados para declarar parâmetros de valores de tabela.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-117">Describes user-defined table types that are used to declare table-valued parameters.</span></span>|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a><span data-ttu-id="3cdb1-118">Passando várias linhas em versões anteriores do SQL Server</span><span class="sxs-lookup"><span data-stu-id="3cdb1-118">Passing Multiple Rows in Previous Versions of SQL Server</span></span>  
 <span data-ttu-id="3cdb1-119">Antes de parâmetros com valor de tabela foram introduzidos no SQL Server 2008, as opções para passar várias linhas de dados para um procedimento armazenado ou um comando SQL parametrizado eram limitadas.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-119">Before table-valued parameters were introduced to SQL Server 2008, the options for passing multiple rows of data to a stored procedure or a parameterized SQL command were limited.</span></span> <span data-ttu-id="3cdb1-120">Um desenvolvedor poderia escolher as seguintes opções para passar várias linhas para o servidor:</span><span class="sxs-lookup"><span data-stu-id="3cdb1-120">A developer could choose from the following options for passing multiple rows to the server:</span></span>  
  
-   <span data-ttu-id="3cdb1-121">Usar uma série de parâmetros individuais para representar os valores em várias colunas e linhas de dados.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-121">Use a series of individual parameters to represent the values in multiple columns and rows of data.</span></span> <span data-ttu-id="3cdb1-122">A quantidade de dados que podem ser passados usando esse método é limitada pelo número de parâmetros permitidos.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-122">The amount of data that can be passed by using this method is limited by the number of parameters allowed.</span></span> <span data-ttu-id="3cdb1-123">Procedimentos do SQL Server podem ter, no máximo, 2100 parâmetros.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-123">SQL Server procedures can have, at most, 2100 parameters.</span></span> <span data-ttu-id="3cdb1-124">A lógica do lado do servidor é necessária para reunir esses valores individuais em uma variável da tabela ou uma tabela temporária para processamento.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-124">Server-side logic is required to assemble these individual values into a table variable or a temporary table for processing.</span></span>  
  
-   <span data-ttu-id="3cdb1-125">Empacotar vários valores de dados em cadeias de caracteres delimitados ou documentos XML e, em seguida, passar esses valores de texto para um procedimento ou a uma instrução.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-125">Bundle multiple data values into delimited strings or XML documents and then pass those text values to a procedure or statement.</span></span> <span data-ttu-id="3cdb1-126">Isso exige que o procedimento ou a declaração inclua a lógica necessária para validar as estruturas de dados e desempacotar os valores.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-126">This requires the procedure or statement to include the logic necessary for validating the data structures and unbundling the values.</span></span>  
  
-   <span data-ttu-id="3cdb1-127">Criar uma série de instruções SQL individuais para as modificações de dados que afetam várias linhas, como as criadas chamando o método `Update` de um <xref:System.Data.SqlClient.SqlDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-127">Create a series of individual SQL statements for data modifications that affect multiple rows, such as those created by calling the `Update` method of a <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="3cdb1-128">As alterações podem ser enviadas para o servidor individualmente ou serem distribuídas em grupos.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-128">Changes can be submitted to the server individually or batched into groups.</span></span> <span data-ttu-id="3cdb1-129">No entanto, mesmo quando enviadas em lotes que contêm várias instruções, cada declaração é executada separadamente no servidor.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-129">However, even when submitted in batches that contain multiple statements, each statement is executed separately on the server.</span></span>  
  
-   <span data-ttu-id="3cdb1-130">Use o programa de utilitário do `bcp` ou o objeto de <xref:System.Data.SqlClient.SqlBulkCopy> para carregar várias linhas de dados em uma tabela.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-130">Use the `bcp` utility program or the <xref:System.Data.SqlClient.SqlBulkCopy> object to load many rows of data into a table.</span></span> <span data-ttu-id="3cdb1-131">Embora essa técnica seja muito eficiente, ela não dá suporte ao processamento do lado do servidor a menos que os dados sejam carregados em uma tabela temporária ou uma variável da tabela.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-131">Although this technique is very efficient, it does not support server-side processing unless the data is loaded into a temporary table or table variable.</span></span>  
  
## <a name="creating-table-valued-parameter-types"></a><span data-ttu-id="3cdb1-132">Criando tipos de parâmetro com valor de tabela</span><span class="sxs-lookup"><span data-stu-id="3cdb1-132">Creating Table-Valued Parameter Types</span></span>  
 <span data-ttu-id="3cdb1-133">Os parâmetros de valores de tabela são baseados em estruturas de tabela fortemente tipadas que são definidas usando as instruções CREATE TYPE do [!INCLUDE[tsql](../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3cdb1-133">Table-valued parameters are based on strongly-typed table structures that are defined by using [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] CREATE TYPE statements.</span></span> <span data-ttu-id="3cdb1-134">Você precisa criar um tipo de tabela e definir a estrutura no SQL Server antes de usar parâmetros com valor de tabela em seus aplicativos cliente.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-134">You have to create a table type and define the structure in SQL Server before you can use table-valued parameters in your client applications.</span></span> <span data-ttu-id="3cdb1-135">Para obter mais informações sobre como criar tipos de tabela, consulte [tipos de tabela definidos pelo usuário](http://go.microsoft.com/fwlink/?LinkID=98364) nos Manuais Online do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-135">For more information about creating table types, see [User-Defined Table Types](http://go.microsoft.com/fwlink/?LinkID=98364) in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="3cdb1-136">A instrução a seguir cria um tipo de tabela chamado CategoryTableType composto pelas colunas CategoryID e CategoryName:</span><span class="sxs-lookup"><span data-stu-id="3cdb1-136">The following statement creates a table type named CategoryTableType that consists of CategoryID and CategoryName columns:</span></span>  
  
```  
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 <span data-ttu-id="3cdb1-137">Depois de criar um tipo de tabela, você poderá declarar parâmetros de valores de tabela com base nesse tipo.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-137">After you create a table type, you can declare table-valued parameters based on that type.</span></span> <span data-ttu-id="3cdb1-138">O fragmento do [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] a seguir demonstra como declarar um parâmetro com valor de tabela em uma definição de procedimento armazenado.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-138">The following [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] fragment demonstrates how to declare a table-valued parameter in a stored procedure definition.</span></span> <span data-ttu-id="3cdb1-139">Observe que a palavra-chave READONLY é necessária para declarar um parâmetro com valor de tabela.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-139">Note that the READONLY keyword is required for declaring a table-valued parameter.</span></span>  
  
```  
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a><span data-ttu-id="3cdb1-140">Modificando dados com parâmetros de valores de tabela (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3cdb1-140">Modifying Data with Table-Valued Parameters (Transact-SQL)</span></span>  
 <span data-ttu-id="3cdb1-141">Os parâmetros de valores de tabela podem ser usados em modificações de dados baseadas em conjuntos que afetam várias linhas executando uma única instrução.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-141">Table-valued parameters can be used in set-based data modifications that affect multiple rows by executing a single statement.</span></span> <span data-ttu-id="3cdb1-142">Por exemplo, você pode selecionar todas as linhas em um parâmetro com valor de tabela e inseri-las em uma tabela de banco de dados, ou você pode criar uma instrução de atualização unindo um parâmetro com valor de tabela à tabela que você deseja atualizar.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-142">For example, you can select all the rows in a table-valued parameter and insert them into a database table, or you can create an update statement by joining a table-valued parameter to the table you want to update.</span></span>  
  
 <span data-ttu-id="3cdb1-143">A instrução UPDATE do [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] a seguir demonstra como usar um parâmetro com valor de tabela unindo-a à tabela Categories.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-143">The following [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] UPDATE statement demonstrates how to use a table-valued parameter by joining it to the Categories table.</span></span> <span data-ttu-id="3cdb1-144">Quando você usa um parâmetro com valor de tabela com um JOIN em uma cláusula FROM, você deverá também utilizar um alias, como mostrado aqui, onde o alias do parâmetro com valor de tabela é “ec”:</span><span class="sxs-lookup"><span data-stu-id="3cdb1-144">When you use a table-valued parameter with a JOIN in a FROM clause, you must also alias it, as shown here, where the table-valued parameter is aliased as "ec":</span></span>  
  
```  
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 <span data-ttu-id="3cdb1-145">Este exemplo de [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] demonstra como selecionar linhas de um parâmetro com valor de tabela para realizar um INSERT em uma única operação baseada em conjuntos.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-145">This [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] example demonstrates how to select rows from a table-valued parameter to perform an INSERT in a single set-based operation.</span></span>  
  
```  
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a><span data-ttu-id="3cdb1-146">Limitações de parâmetros de valores de tabela</span><span class="sxs-lookup"><span data-stu-id="3cdb1-146">Limitations of Table-Valued Parameters</span></span>  
 <span data-ttu-id="3cdb1-147">Há várias limitações para os parâmetros de valores de tabela:</span><span class="sxs-lookup"><span data-stu-id="3cdb1-147">There are several limitations to table-valued parameters:</span></span>  
  
-   <span data-ttu-id="3cdb1-148">Você não pode passar parâmetros com valor de tabela para [funções CLR definidas pelo usuário](http://msdn.microsoft.com/library/ms131077.aspx).</span><span class="sxs-lookup"><span data-stu-id="3cdb1-148">You cannot pass table-valued parameters to [CLR user-defined functions](http://msdn.microsoft.com/library/ms131077.aspx).</span></span>  
  
-   <span data-ttu-id="3cdb1-149">Os parâmetros de valores de tabela somente podem ser indexados para oferecer suporte às restrições UNIQUE ou PRIMARY KEY.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-149">Table-valued parameters can only be indexed to support UNIQUE or PRIMARY KEY constraints.</span></span> <span data-ttu-id="3cdb1-150">SQL Server não mantém estatísticas sobre os parâmetros com valor de tabela.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-150">SQL Server does not maintain statistics on table-valued parameters.</span></span>  
  
-   <span data-ttu-id="3cdb1-151">Os parâmetros com valor de tabela são somente leitura no código do [!INCLUDE[tsql](../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3cdb1-151">Table-valued parameters are read-only in [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] code.</span></span> <span data-ttu-id="3cdb1-152">Você não pode atualizar os valores da coluna nas linhas de um parâmetro com valor de tabela e você não pode inserir ou excluir linhas.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-152">You cannot update the column values in the rows of a table-valued parameter and you cannot insert or delete rows.</span></span> <span data-ttu-id="3cdb1-153">Para modificar os dados que são passados para um procedimento armazenado ou instrução parametrizada no parâmetro com valor de tabela, você deverá inserir os dados em uma tabela temporária ou variável da tabela.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-153">To modify the data that is passed to a stored procedure or parameterized statement in table-valued parameter, you must insert the data into a temporary table or into a table variable.</span></span>  
  
-   <span data-ttu-id="3cdb1-154">Você não pode usar instruções ALTER TABLE para modificar o design de parâmetros de valores de tabela.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-154">You cannot use ALTER TABLE statements to modify the design of table-valued parameters.</span></span>  
  
## <a name="configuring-a-sqlparameter-example"></a><span data-ttu-id="3cdb1-155">Configurando um exemplo de SqlParameter</span><span class="sxs-lookup"><span data-stu-id="3cdb1-155">Configuring a SqlParameter Example</span></span>  
 <span data-ttu-id="3cdb1-156"><xref:System.Data.SqlClient> dá suporte a popular parâmetros com valor de tabela do <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> ou <xref:System.Collections.Generic.IEnumerable%601>  \  <xref:Microsoft.SqlServer.Server.SqlDataRecord> objetos.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-156"><xref:System.Data.SqlClient> supports populating table-valued parameters from <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> or <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.SqlServer.Server.SqlDataRecord> objects.</span></span> <span data-ttu-id="3cdb1-157">Você deve especificar um nome de tipo para o parâmetro com valor de tabela usando a propriedade <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> de um <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-157">You must specify a type name for the table-valued parameter by using the <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="3cdb1-158">O `TypeName` deve corresponder ao nome de um tipo compatível criado anteriormente no servidor.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-158">The `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="3cdb1-159">O fragmento de código a seguir demonstra como configurar o <xref:System.Data.SqlClient.SqlParameter> para inserir dados.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-159">The following code fragment demonstrates how to configure <xref:System.Data.SqlClient.SqlParameter> to insert data.</span></span>  
  
```csharp  
// Configure the command and parameter.  
SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
tvpParam.SqlDbType = SqlDbType.Structured;  
tvpParam.TypeName = "dbo.CategoryTableType";  
```  
  
```vb  
' Configure the command and parameter.  
Dim insertCommand As New SqlCommand(sqlInsert, connection)  
Dim tvpParam As SqlParameter = _  
   insertCommand.Parameters.AddWithValue( _  
  "@tvpNewCategories", addedCategories)  
tvpParam.SqlDbType = SqlDbType.Structured  
tvpParam.TypeName = "dbo.CategoryTableType"  
```  
  
 <span data-ttu-id="3cdb1-160">Você também pode usar qualquer objeto derivado do <xref:System.Data.Common.DbDataReader> para transmitir as linhas de dados para um parâmetro com valor de tabela, conforme mostrado neste fragmento:</span><span class="sxs-lookup"><span data-stu-id="3cdb1-160">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter, as shown in this fragment:</span></span>  
  
```csharp  
// Configure the SqlCommand and table-valued parameter.  
SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
insertCommand.CommandType = CommandType.StoredProcedure;  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", dataReader);  
tvpParam.SqlDbType = SqlDbType.Structured;  
```  
  
```vb  
' Configure the SqlCommand and table-valued parameter.  
Dim insertCommand As New SqlCommand("usp_InsertCategories", connection)  
insertCommand.CommandType = CommandType.StoredProcedure  
Dim tvpParam As SqlParameter = _  
  insertCommand.Parameters.AddWithValue("@tvpNewCategories", _  
  dataReader)  
tvpParam.SqlDbType = SqlDbType.Structured  
```  
  
## <a name="passing-a-table-valued-parameter-to-a-stored-procedure"></a><span data-ttu-id="3cdb1-161">Passando um parâmetro com valor de tabela para um procedimento armazenado</span><span class="sxs-lookup"><span data-stu-id="3cdb1-161">Passing a Table-Valued Parameter to a Stored Procedure</span></span>  
 <span data-ttu-id="3cdb1-162">Este exemplo demonstra como passar dados de parâmetro com valor de tabela para um procedimento armazenado.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-162">This example demonstrates how to pass table-valued parameter data to a stored procedure.</span></span> <span data-ttu-id="3cdb1-163">O código extrai linhas adicionadas em um novo <xref:System.Data.DataTable> usando o método <xref:System.Data.DataTable.GetChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-163">The code extracts added rows into a new <xref:System.Data.DataTable> by using the <xref:System.Data.DataTable.GetChanges%2A> method.</span></span> <span data-ttu-id="3cdb1-164">O código em seguida define um <xref:System.Data.SqlClient.SqlCommand>, definindo a propriedade <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> como <xref:System.Data.CommandType.StoredProcedure>.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-164">The code then defines a <xref:System.Data.SqlClient.SqlCommand>, setting the <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> property to <xref:System.Data.CommandType.StoredProcedure>.</span></span> <span data-ttu-id="3cdb1-165">O <xref:System.Data.SqlClient.SqlParameter> é preenchido usando o método <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> e o <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> é definido como `Structured`.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-165">The <xref:System.Data.SqlClient.SqlParameter> is populated by using the <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> method and the <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> is set to `Structured`.</span></span> <span data-ttu-id="3cdb1-166">O <xref:System.Data.SqlClient.SqlCommand> é, em seguida, executado usando o método <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-166">The <xref:System.Data.SqlClient.SqlCommand> is then executed by using the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method.</span></span>  
  
```csharp  
// Assumes connection is an open SqlConnection object.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Configure the SqlCommand and SqlParameter.  
  SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
  insertCommand.CommandType = CommandType.StoredProcedure;  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
```vb  
' Assumes connection is an open SqlConnection object.  
Using connection  
   '  Create a DataTable with the modified rows.  
   Dim addedCategories As DataTable = _  
     CategoriesDataTable.GetChanges(DataRowState.Added)  
  
  ' Configure the SqlCommand and SqlParameter.  
   Dim insertCommand As New SqlCommand( _  
     "usp_InsertCategories", connection)  
   insertCommand.CommandType = CommandType.StoredProcedure  
   Dim tvpParam As SqlParameter = _  
     insertCommand.Parameters.AddWithValue( _  
     "@tvpNewCategories", addedCategories)  
   tvpParam.SqlDbType = SqlDbType.Structured  
  
   '  Execute the command.  
   insertCommand.ExecuteNonQuery()  
End Using  
```  
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a><span data-ttu-id="3cdb1-167">Passando um parâmetro com valor de tabela para uma instrução SQL parametrizada</span><span class="sxs-lookup"><span data-stu-id="3cdb1-167">Passing a Table-Valued Parameter to a Parameterized SQL Statement</span></span>  
 <span data-ttu-id="3cdb1-168">O exemplo a seguir demonstra como inserir dados na tabela dbo.Categories usando uma instrução INSERT com uma subconsulta SELECT que tem um parâmetro com valor de tabela como a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-168">The following example demonstrates how to insert data into the dbo.Categories table by using an INSERT statement with a SELECT subquery that has a table-valued parameter as the data source.</span></span> <span data-ttu-id="3cdb1-169">Ao passar um parâmetro com valor de tabela para uma instrução SQL parametrizada, você deve especificar um nome de tipo para o parâmetro com valor de tabela usando a nova propriedade <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> de um <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-169">When passing a table-valued parameter to a parameterized SQL statement, you must specify a type name for the table-valued parameter by using the new <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="3cdb1-170">Esse `TypeName` deve corresponder ao nome de um tipo compatível criado anteriormente no servidor.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-170">This `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="3cdb1-171">O código nesse exemplo usa a propriedade `TypeName` para fazer referência à estrutura do tipo definida em dbo.CategoryTableType.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-171">The code in this example uses the `TypeName` property to reference the type structure defined in dbo.CategoryTableType.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3cdb1-172">Se você fornecer um valor para uma coluna de identidade em um parâmetro com valor de tabela, deverá emitir a instrução SET IDENTITY_INSERT para a sessão.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-172">If you supply a value for an identity column in a table-valued parameter, you must issue the SET IDENTITY_INSERT statement for the session.</span></span>  
  
```csharp  
// Assumes connection is an open SqlConnection.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Define the INSERT-SELECT statement.  
  string sqlInsert =   
      "INSERT INTO dbo.Categories (CategoryID, CategoryName)"  
      + " SELECT nc.CategoryID, nc.CategoryName"  
      + " FROM @tvpNewCategories AS nc;"  

  // Configure the command and parameter.  
  SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  
  tvpParam.TypeName = "dbo.CategoryTableType";  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
```vb  
' Assumes connection is an open SqlConnection.  
Using connection  
  ' Create a DataTable with the modified rows.  
  Dim addedCategories As DataTable = _  
    CategoriesDataTable.GetChanges(DataRowState.Added)  
  
  ' Define the INSERT-SELECT statement.  
  Dim sqlInsert As String = _  
  "INSERT INTO dbo.Categories (CategoryID, CategoryName)" _  
  & " SELECT nc.CategoryID, nc.CategoryName" _  
  & " FROM @tvpNewCategories AS nc;"  
  
  ' Configure the command and parameter.  
  Dim insertCommand As New SqlCommand(sqlInsert, connection)  
  Dim tvpParam As SqlParameter = _  
     insertCommand.Parameters.AddWithValue( _  
    "@tvpNewCategories", addedCategories)  
  tvpParam.SqlDbType = SqlDbType.Structured  
  tvpParam.TypeName = "dbo.CategoryTableType"  
  
  ' Execute the query  
  insertCommand.ExecuteNonQuery()  
End Using  
```  
  
## <a name="streaming-rows-with-a-datareader"></a><span data-ttu-id="3cdb1-173">Transmitindo linhas com um DataReader</span><span class="sxs-lookup"><span data-stu-id="3cdb1-173">Streaming Rows with a DataReader</span></span>  
 <span data-ttu-id="3cdb1-174">Você também pode usar qualquer objeto derivado do <xref:System.Data.Common.DbDataReader> para transmitir as linhas de dados para um parâmetro com valor de tabela.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-174">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter.</span></span> <span data-ttu-id="3cdb1-175">O fragmento de código a seguir demonstra a recuperação de dados de um banco de dados Oracle usando <xref:System.Data.OracleClient.OracleCommand> e um <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-175">The following code fragment demonstrates retrieving data from an Oracle database by using an <xref:System.Data.OracleClient.OracleCommand> and an <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="3cdb1-176">O código em seguida configura um <xref:System.Data.SqlClient.SqlCommand> para chamar um procedimento armazenado com um único parâmetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-176">The code then configures a <xref:System.Data.SqlClient.SqlCommand> to invoke a stored procedure with a single input parameter.</span></span> <span data-ttu-id="3cdb1-177">A propriedade <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> do <xref:System.Data.SqlClient.SqlParameter> é definida como `Structured`.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-177">The <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> property of the <xref:System.Data.SqlClient.SqlParameter> is set to `Structured`.</span></span> <span data-ttu-id="3cdb1-178">O <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> passa o conjunto de resultados de `OracleDataReader` para o procedimento armazenado como um parâmetro com valor de tabela.</span><span class="sxs-lookup"><span data-stu-id="3cdb1-178">The <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> passes the `OracleDataReader` result set to the stored procedure as a table-valued parameter.</span></span>  
  
```csharp  
// Assumes connection is an open SqlConnection.  
// Retrieve data from Oracle.  
OracleCommand selectCommand = new OracleCommand(  
   "Select CategoryID, CategoryName FROM Categories;",  
   oracleConnection);  
OracleDataReader oracleReader = selectCommand.ExecuteReader(  
   CommandBehavior.CloseConnection);  
  
 // Configure the SqlCommand and table-valued parameter.  
 SqlCommand insertCommand = new SqlCommand(  
   "usp_InsertCategories", connection);  
 insertCommand.CommandType = CommandType.StoredProcedure;  
 SqlParameter tvpParam =  
    insertCommand.Parameters.AddWithValue(  
    "@tvpNewCategories", oracleReader);  
 tvpParam.SqlDbType = SqlDbType.Structured;  
  
 // Execute the command.  
 insertCommand.ExecuteNonQuery();  
```  
  
```vb  
' Assumes connection is an open SqlConnection.  
' Retrieve data from Oracle.  
Dim selectCommand As New OracleCommand( _  
  "Select CategoryID, CategoryName FROM Categories;", _  
  oracleConnection)  
Dim oracleReader As OracleDataReader = _  
  selectCommand.ExecuteReader(CommandBehavior.CloseConnection)  
  
' Configure SqlCommand and table-valued parameter.  
Dim insertCommand As New SqlCommand("usp_InsertCategories", connection)  
insertCommand.CommandType = CommandType.StoredProcedure  
Dim tvpParam As SqlParameter = _  
  insertCommand.Parameters.AddWithValue("@tvpNewCategories", _  
  oracleReader)  
tvpParam.SqlDbType = SqlDbType.Structured  
  
' Execute the command.  
insertCommand.ExecuteNonQuery()  
```  
  
## <a name="see-also"></a><span data-ttu-id="3cdb1-179">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3cdb1-179">See Also</span></span>  
 [<span data-ttu-id="3cdb1-180">Configurando parâmetros e tipos de dados de parâmetro</span><span class="sxs-lookup"><span data-stu-id="3cdb1-180">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="3cdb1-181">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="3cdb1-181">Commands and Parameters</span></span>](../../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="3cdb1-182">Parâmetros DataAdapter</span><span class="sxs-lookup"><span data-stu-id="3cdb1-182">DataAdapter Parameters</span></span>](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 <span data-ttu-id="3cdb1-183">[SQL Server Data Operations in ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md) (Operações de dados do SQL Server no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="3cdb1-183">[SQL Server Data Operations in ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)</span></span>  
 <span data-ttu-id="3cdb1-184">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="3cdb1-184">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
