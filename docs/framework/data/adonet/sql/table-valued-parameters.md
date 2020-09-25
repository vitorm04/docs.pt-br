---
title: Parâmetros com valor de tabela
description: Saiba como realizar marshaling de várias linhas de dados de um aplicativo cliente para SQL Server usando parâmetros com valor de tabela.
ms.date: 10/12/2018
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.openlocfilehash: ea063b333ea0680071b880f26753bfd74b71d80f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91188870"
---
# <a name="table-valued-parameters"></a><span data-ttu-id="7ce4e-103">Parâmetros com valor de tabela</span><span class="sxs-lookup"><span data-stu-id="7ce4e-103">Table-Valued Parameters</span></span>

<span data-ttu-id="7ce4e-104">Os parâmetros com valor de tabela fornecem uma maneira fácil de realizar marshaling em várias linhas de dados de um aplicativo cliente do SQL Server sem exigir várias viagens de ida e volta ou uma lógica especial do lado do servidor para processar os dados.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-104">Table-valued parameters provide an easy way to marshal multiple rows of data from a client application to SQL Server without requiring multiple round trips or special server-side logic for processing the data.</span></span> <span data-ttu-id="7ce4e-105">Você pode usar parâmetros com valor de tabela para encapsular linhas de dados em um aplicativo cliente e enviar os dados para o servidor em um único comando parametrizado.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-105">You can use table-valued parameters to encapsulate rows of data in a client application and send the data to the server in a single parameterized command.</span></span> <span data-ttu-id="7ce4e-106">As linhas de dados de entrada são armazenadas em uma variável de tabela, as quais você poderá operar usando o Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-106">The incoming data rows are stored in a table variable that can then be operated on by using Transact-SQL.</span></span>  
  
 <span data-ttu-id="7ce4e-107">Os valores de coluna em parâmetros com valor de tabela podem ser acessados usando instruções SELECT padrão do Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-107">Column values in table-valued parameters can be accessed using standard Transact-SQL SELECT statements.</span></span> <span data-ttu-id="7ce4e-108">Os parâmetros com valor de tabela são fortemente tipados e a estrutura deles é validada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-108">Table-valued parameters are strongly typed and their structure is automatically validated.</span></span> <span data-ttu-id="7ce4e-109">O tamanho dos parâmetros com valor de tabela é limitado somente pela memória do servidor.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-109">The size of table-valued parameters is limited only by server memory.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7ce4e-110">Não é possível retornar dados em um parâmetro com valor de tabela.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-110">You cannot return data in a table-valued parameter.</span></span> <span data-ttu-id="7ce4e-111">Os parâmetros com valor de tabela são somente entrada; não há suporte para a palavra-chave OUTPUT.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-111">Table-valued parameters are input-only; the OUTPUT keyword is not supported.</span></span>  
  
 <span data-ttu-id="7ce4e-112">Para obter mais informações sobre os parâmetros com valor de tabela, confira os recursos a seguir.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-112">For more information about table-valued parameters, see the following resources.</span></span>  
  
|<span data-ttu-id="7ce4e-113">Recurso</span><span class="sxs-lookup"><span data-stu-id="7ce4e-113">Resource</span></span>|<span data-ttu-id="7ce4e-114">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="7ce4e-114">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="7ce4e-115">Usar parâmetros com valor de tabela (Mecanismo de Banco de Dados)</span><span class="sxs-lookup"><span data-stu-id="7ce4e-115">Use Table-Valued Parameters (Database Engine)</span></span>](/sql/relational-databases/tables/use-table-valued-parameters-database-engine)|<span data-ttu-id="7ce4e-116">Descreve como criar e usar parâmetros com valor de tabela.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-116">Describes how to create and use table-valued parameters.</span></span>|  
|<span data-ttu-id="7ce4e-117">[Tipos de tabela definidos pelo usuário](/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="7ce4e-117">[User-Defined Table Types](/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))</span></span>|<span data-ttu-id="7ce4e-118">Descreve os tipos de tabela definidos pelo usuário usados para declarar parâmetros com valor de tabela.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-118">Describes user-defined table types that are used to declare table-valued parameters.</span></span>|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a><span data-ttu-id="7ce4e-119">Passando várias linhas em versões anteriores do SQL Server</span><span class="sxs-lookup"><span data-stu-id="7ce4e-119">Passing Multiple Rows in Previous Versions of SQL Server</span></span>  

 <span data-ttu-id="7ce4e-120">Antes de os parâmetros de valores de tabela serem introduzidos no SQL Server 2008, as opções para passar várias linhas de dados para um procedimento armazenado ou um comando SQL parametrizado eram limitadas.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-120">Before table-valued parameters were introduced to SQL Server 2008, the options for passing multiple rows of data to a stored procedure or a parameterized SQL command were limited.</span></span> <span data-ttu-id="7ce4e-121">Um desenvolvedor pode escolher entre as seguintes opções para passar várias linhas para o servidor:</span><span class="sxs-lookup"><span data-stu-id="7ce4e-121">A developer could choose from the following options for passing multiple rows to the server:</span></span>  
  
- <span data-ttu-id="7ce4e-122">Usar uma série de parâmetros individuais para representar os valores em várias colunas e linhas de dados.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-122">Use a series of individual parameters to represent the values in multiple columns and rows of data.</span></span> <span data-ttu-id="7ce4e-123">A quantidade de dados que pode ser passada usando esse método é limitada pelo número de parâmetros permitidos.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-123">The amount of data that can be passed by using this method is limited by the number of parameters allowed.</span></span> <span data-ttu-id="7ce4e-124">Os procedimentos do SQL Server podem ter, no máximo, 2100 parâmetros.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-124">SQL Server procedures can have, at most, 2100 parameters.</span></span> <span data-ttu-id="7ce4e-125">A lógica do lado do servidor é necessária para montar esses valores individuais em uma variável de tabela ou uma tabela temporária para processamento.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-125">Server-side logic is required to assemble these individual values into a table variable or a temporary table for processing.</span></span>  
  
- <span data-ttu-id="7ce4e-126">Agrupe múltiplos valores de dados em cadeias de caracteres delimitadas ou em documentos XML e, em seguida, passe esses valores de texto para um procedimento ou uma instrução.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-126">Bundle multiple data values into delimited strings or XML documents and then pass those text values to a procedure or statement.</span></span> <span data-ttu-id="7ce4e-127">Isso requer que o procedimento ou a instrução inclua a lógica necessária para validar as estruturas de dados e desagrupar os valores.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-127">This requires the procedure or statement to include the logic necessary for validating the data structures and unbundling the values.</span></span>  
  
- <span data-ttu-id="7ce4e-128">Criar uma série de instruções SQL individuais para modificações de dados que afetam várias linhas, como aquelas criadas ao chamar o método `Update` de um <xref:System.Data.SqlClient.SqlDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-128">Create a series of individual SQL statements for data modifications that affect multiple rows, such as those created by calling the `Update` method of a <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="7ce4e-129">As alterações podem ser enviadas ao servidor individualmente ou em lotes em grupos.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-129">Changes can be submitted to the server individually or batched into groups.</span></span> <span data-ttu-id="7ce4e-130">No entanto, mesmo quando enviados em lotes que contêm várias instruções, cada instrução é executada separadamente no servidor.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-130">However, even when submitted in batches that contain multiple statements, each statement is executed separately on the server.</span></span>  
  
- <span data-ttu-id="7ce4e-131">Usar o programa utilitário `bcp` ou o objeto <xref:System.Data.SqlClient.SqlBulkCopy> para carregar várias linhas de dados em uma tabela.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-131">Use the `bcp` utility program or the <xref:System.Data.SqlClient.SqlBulkCopy> object to load many rows of data into a table.</span></span> <span data-ttu-id="7ce4e-132">Embora essa técnica seja muito eficiente, ela não dá suporte ao processamento do lado do servidor, a menos que os dados sejam carregados em uma tabela temporária ou variável de tabela.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-132">Although this technique is very efficient, it does not support server-side processing unless the data is loaded into a temporary table or table variable.</span></span>  
  
## <a name="creating-table-valued-parameter-types"></a><span data-ttu-id="7ce4e-133">Criando tipos de parâmetro com valor de tabela</span><span class="sxs-lookup"><span data-stu-id="7ce4e-133">Creating Table-Valued Parameter Types</span></span>  

 <span data-ttu-id="7ce4e-134">Os parâmetros com valor de tabela se baseiam em estruturas de tabela fortemente tipadas que são definidas usando instruções Transact-SQL CREATE TYPE.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-134">Table-valued parameters are based on strongly typed table structures that are defined by using Transact-SQL CREATE TYPE statements.</span></span> <span data-ttu-id="7ce4e-135">Você precisa criar um tipo de tabela e definir a estrutura no SQL Server antes de poder usar parâmetros de valores de tabela em seus aplicativos cliente.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-135">You have to create a table type and define the structure in SQL Server before you can use table-valued parameters in your client applications.</span></span> <span data-ttu-id="7ce4e-136">Para obter mais informações sobre como criar tipos de tabela, consulte [tipos de tabela definidos pelo usuário](/previous-versions/sql/sql-server-2008/bb522526(v=sql.100)).</span><span class="sxs-lookup"><span data-stu-id="7ce4e-136">For more information about creating table types, see [User-Defined Table Types](/previous-versions/sql/sql-server-2008/bb522526(v=sql.100)).</span></span>  
  
 <span data-ttu-id="7ce4e-137">A seguinte instrução cria um tipo de tabela chamado CategoryTableType que é composto pelas colunas CategoryID e CategoryName:</span><span class="sxs-lookup"><span data-stu-id="7ce4e-137">The following statement creates a table type named CategoryTableType that consists of CategoryID and CategoryName columns:</span></span>  
  
```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 <span data-ttu-id="7ce4e-138">Depois de criar um tipo de tabela é possível declarar os parâmetros com valor de tabela baseados nesse tipo.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-138">After you create a table type, you can declare table-valued parameters based on that type.</span></span> <span data-ttu-id="7ce4e-139">O fragmento do Transact-SQL a seguir demonstra como declarar um parâmetro com valor de tabela em uma definição de procedimento armazenado.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-139">The following Transact-SQL fragment demonstrates how to declare a table-valued parameter in a stored procedure definition.</span></span> <span data-ttu-id="7ce4e-140">Observe que a palavra-chave READONLY é necessária para declarar um parâmetro com valor de tabela.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-140">Note that the READONLY keyword is required for declaring a table-valued parameter.</span></span>  
  
```sql
CREATE PROCEDURE usp_UpdateCategories
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a><span data-ttu-id="7ce4e-141">Modificando dados com parâmetros de valores de tabela (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7ce4e-141">Modifying Data with Table-Valued Parameters (Transact-SQL)</span></span>  

 <span data-ttu-id="7ce4e-142">Os parâmetros com valor de tabela podem ser usados em modificações de dados baseadas em conjunto que afetam várias linhas executando uma instrução.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-142">Table-valued parameters can be used in set-based data modifications that affect multiple rows by executing a single statement.</span></span> <span data-ttu-id="7ce4e-143">Por exemplo, você pode selecionar todas as linhas em um parâmetro com valor de tabela e inseri-las em uma tabela de banco de dados ou pode criar uma declaração de atualização unindo um parâmetro com valor de tabela à tabela que você deseja atualizar.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-143">For example, you can select all the rows in a table-valued parameter and insert them into a database table, or you can create an update statement by joining a table-valued parameter to the table you want to update.</span></span>  
  
 <span data-ttu-id="7ce4e-144">A instrução UPDATE do Transact-SQL a seguir demonstra como usar um parâmetro com valor de tabela unindo-o à tabela Categorias.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-144">The following Transact-SQL UPDATE statement demonstrates how to use a table-valued parameter by joining it to the Categories table.</span></span> <span data-ttu-id="7ce4e-145">Ao usar um parâmetro com valor de tabela com JOIN em uma cláusula FROM, você também deverá usar o alias, conforme mostrado aqui, em que o parâmetro com valor de tabela tem um alias como "ec":</span><span class="sxs-lookup"><span data-stu-id="7ce4e-145">When you use a table-valued parameter with a JOIN in a FROM clause, you must also alias it, as shown here, where the table-valued parameter is aliased as "ec":</span></span>  
  
```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 <span data-ttu-id="7ce4e-146">Este exemplo do Transact-SQL demonstra como selecionar linhas de um parâmetro com valor de tabela para executar um INSERT em uma operação baseada em conjunto.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-146">This Transact-SQL example demonstrates how to select rows from a table-valued parameter to perform an INSERT in a single set-based operation.</span></span>  
  
```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a><span data-ttu-id="7ce4e-147">Limitações de parâmetros de valores de tabela</span><span class="sxs-lookup"><span data-stu-id="7ce4e-147">Limitations of Table-Valued Parameters</span></span>  

 <span data-ttu-id="7ce4e-148">Há várias limitações para parâmetros com valor de tabela:</span><span class="sxs-lookup"><span data-stu-id="7ce4e-148">There are several limitations to table-valued parameters:</span></span>  
  
- <span data-ttu-id="7ce4e-149">Você não pode passar parâmetros de valores de tabela para [Funções CLR definidas pelo usuário](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).</span><span class="sxs-lookup"><span data-stu-id="7ce4e-149">You cannot pass table-valued parameters to [CLR user-defined functions](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).</span></span>  
  
- <span data-ttu-id="7ce4e-150">Os parâmetros com valor de tabela podem ser indexados somente para dar suporte às restrições UNIQUE ou PRIMARY KEY.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-150">Table-valued parameters can only be indexed to support UNIQUE or PRIMARY KEY constraints.</span></span> <span data-ttu-id="7ce4e-151">O SQL Server não mantém estatísticas de parâmetros com valor de tabela.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-151">SQL Server does not maintain statistics on table-valued parameters.</span></span>  
  
- <span data-ttu-id="7ce4e-152">Os parâmetros com valor de tabela são somente leitura no código Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-152">Table-valued parameters are read-only in Transact-SQL code.</span></span> <span data-ttu-id="7ce4e-153">Não é possível atualizar os valores da coluna nas linhas de um parâmetro com valor de tabela nem inserir ou excluir linhas.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-153">You cannot update the column values in the rows of a table-valued parameter and you cannot insert or delete rows.</span></span> <span data-ttu-id="7ce4e-154">Para modificar os dados que são passados para um procedimento armazenado ou para uma instrução parametrizada no parâmetro com valor de tabela, será necessário inserir os dados em uma tabela temporária ou em uma variável de tabela.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-154">To modify the data that is passed to a stored procedure or parameterized statement in table-valued parameter, you must insert the data into a temporary table or into a table variable.</span></span>  
  
- <span data-ttu-id="7ce4e-155">Não é possível usar as instruções ALTER TABLE para modificar o design dos parâmetros com valor de tabela.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-155">You cannot use ALTER TABLE statements to modify the design of table-valued parameters.</span></span>  
  
## <a name="configuring-a-sqlparameter-example"></a><span data-ttu-id="7ce4e-156">Configurando um exemplo de SqlParameter</span><span class="sxs-lookup"><span data-stu-id="7ce4e-156">Configuring a SqlParameter Example</span></span>  

 <span data-ttu-id="7ce4e-157">O <xref:System.Data.SqlClient> é compatível com o preenchimento dos parâmetros com valor de tabela dos objetos <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> ou <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.SqlServer.Server.SqlDataRecord>.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-157"><xref:System.Data.SqlClient> supports populating table-valued parameters from <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> or <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.SqlServer.Server.SqlDataRecord> objects.</span></span> <span data-ttu-id="7ce4e-158">É necessário especificar um nome de tipo para o parâmetro com valor de tabela usando a propriedade <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> de um <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-158">You must specify a type name for the table-valued parameter by using the <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="7ce4e-159">O `TypeName` deve corresponder ao nome de um tipo compatível criado anteriormente no servidor.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-159">The `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="7ce4e-160">O fragmento de código a seguir demonstra como configurar o <xref:System.Data.SqlClient.SqlParameter> para inserir dados.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-160">The following code fragment demonstrates how to configure <xref:System.Data.SqlClient.SqlParameter> to insert data.</span></span>  

<span data-ttu-id="7ce4e-161">No exemplo a seguir, o nome da variável `addedCategories` contém um <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-161">In the following example, the `addedCategories` variable contains a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="7ce4e-162">Para ver como a variável é preenchida, confira os exemplos na próxima seção, [Como passar um parâmetro com valor de tabela para um procedimento armazenado](#passing).</span><span class="sxs-lookup"><span data-stu-id="7ce4e-162">To see how the variable is populated, see the examples in the next section, [Passing a Table-Valued Parameter to a Stored Procedure](#passing).</span></span>

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
  
 <span data-ttu-id="7ce4e-163">Também é possível usar qualquer objeto derivado de <xref:System.Data.Common.DbDataReader> para transmitir linhas de dados a um parâmetro com valor de tabela, conforme mostrado neste fragmento:</span><span class="sxs-lookup"><span data-stu-id="7ce4e-163">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter, as shown in this fragment:</span></span>  
  
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
  
## <a name="passing-a-table-valued-parameter-to-a-stored-procedure"></a><a name="passing"></a> <span data-ttu-id="7ce4e-164">Passando um parâmetro com valor de tabela para um procedimento armazenado</span><span class="sxs-lookup"><span data-stu-id="7ce4e-164">Passing a Table-Valued Parameter to a Stored Procedure</span></span>  

 <span data-ttu-id="7ce4e-165">Este exemplo demonstra como passar dados de parâmetro com valor de tabela para um procedimento armazenado.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-165">This example demonstrates how to pass table-valued parameter data to a stored procedure.</span></span> <span data-ttu-id="7ce4e-166">O código extrai linhas adicionadas em um novo <xref:System.Data.DataTable> usando o método <xref:System.Data.DataTable.GetChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-166">The code extracts added rows into a new <xref:System.Data.DataTable> by using the <xref:System.Data.DataTable.GetChanges%2A> method.</span></span> <span data-ttu-id="7ce4e-167">Em seguida, o código define um <xref:System.Data.SqlClient.SqlCommand>, configurando a propriedade <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> como <xref:System.Data.CommandType.StoredProcedure>.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-167">The code then defines a <xref:System.Data.SqlClient.SqlCommand>, setting the <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> property to <xref:System.Data.CommandType.StoredProcedure>.</span></span> <span data-ttu-id="7ce4e-168">O <xref:System.Data.SqlClient.SqlParameter> é preenchido usando o método <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> e o <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> é definido como `Structured`.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-168">The <xref:System.Data.SqlClient.SqlParameter> is populated by using the <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> method and the <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> is set to `Structured`.</span></span> <span data-ttu-id="7ce4e-169">Em seguida, o <xref:System.Data.SqlClient.SqlCommand> é executado usando o método <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-169">The <xref:System.Data.SqlClient.SqlCommand> is then executed by using the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method.</span></span>  
  
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
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a><span data-ttu-id="7ce4e-170">Passando um parâmetro com valor de tabela para uma instrução SQL parametrizada</span><span class="sxs-lookup"><span data-stu-id="7ce4e-170">Passing a Table-Valued Parameter to a Parameterized SQL Statement</span></span>  

 <span data-ttu-id="7ce4e-171">O exemplo a seguir demonstra como inserir dados na tabela dbo.Categories usando uma instrução INSERT com uma consulta aninhada SELECT que tem um parâmetro com valor de tabela como fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-171">The following example demonstrates how to insert data into the dbo.Categories table by using an INSERT statement with a SELECT subquery that has a table-valued parameter as the data source.</span></span> <span data-ttu-id="7ce4e-172">Ao passar um parâmetro com valor de tabela para uma instrução SQL parametrizada, será necessário especificar um nome de tipo para ele usando a nova propriedade <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> de um <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-172">When passing a table-valued parameter to a parameterized SQL statement, you must specify a type name for the table-valued parameter by using the new <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="7ce4e-173">Esse `TypeName` deve corresponder ao nome de um tipo compatível criado anteriormente no servidor.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-173">This `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="7ce4e-174">O código nesse exemplo usa a propriedade `TypeName` para fazer referência à estrutura de tipo definida em dbo.CategoryTableType.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-174">The code in this example uses the `TypeName` property to reference the type structure defined in dbo.CategoryTableType.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7ce4e-175">Caso forneça um valor para uma coluna de identidade em um parâmetro com valor de tabela, você deverá emitir a instrução SET IDENTITY_INSERT para a sessão.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-175">If you supply a value for an identity column in a table-valued parameter, you must issue the SET IDENTITY_INSERT statement for the session.</span></span>  
  
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
  
## <a name="streaming-rows-with-a-datareader"></a><span data-ttu-id="7ce4e-176">Transmitindo linhas com um DataReader</span><span class="sxs-lookup"><span data-stu-id="7ce4e-176">Streaming Rows with a DataReader</span></span>  

 <span data-ttu-id="7ce4e-177">Também é possível usar qualquer objeto derivado de <xref:System.Data.Common.DbDataReader> para transmitir linhas de dados a um parâmetro com valor de tabela.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-177">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter.</span></span> <span data-ttu-id="7ce4e-178">O fragmento de código a seguir demonstra como recuperar dados de um Oracle Database usando um <xref:System.Data.OracleClient.OracleCommand> e um <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-178">The following code fragment demonstrates retrieving data from an Oracle database by using an <xref:System.Data.OracleClient.OracleCommand> and an <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="7ce4e-179">Em seguida, o código configura um <xref:System.Data.SqlClient.SqlCommand> para invocar um procedimento armazenado com um parâmetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-179">The code then configures a <xref:System.Data.SqlClient.SqlCommand> to invoke a stored procedure with a single input parameter.</span></span> <span data-ttu-id="7ce4e-180">A propriedade <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> do <xref:System.Data.SqlClient.SqlParameter> é definida como `Structured`.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-180">The <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> property of the <xref:System.Data.SqlClient.SqlParameter> is set to `Structured`.</span></span> <span data-ttu-id="7ce4e-181">O <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> passa o conjunto de resultados do `OracleDataReader` para o procedimento armazenado como um parâmetro com valor de tabela.</span><span class="sxs-lookup"><span data-stu-id="7ce4e-181">The <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> passes the `OracleDataReader` result set to the stored procedure as a table-valued parameter.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7ce4e-182">Veja também</span><span class="sxs-lookup"><span data-stu-id="7ce4e-182">See also</span></span>

- [<span data-ttu-id="7ce4e-183">Configurar parâmetros e tipos de dados de parâmetro</span><span class="sxs-lookup"><span data-stu-id="7ce4e-183">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="7ce4e-184">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="7ce4e-184">Commands and Parameters</span></span>](../commands-and-parameters.md)
- [<span data-ttu-id="7ce4e-185">Parâmetros DataAdapter</span><span class="sxs-lookup"><span data-stu-id="7ce4e-185">DataAdapter Parameters</span></span>](../dataadapter-parameters.md)
- [<span data-ttu-id="7ce4e-186">SQL Server operações de dados no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7ce4e-186">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="7ce4e-187">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7ce4e-187">ADO.NET Overview</span></span>](../ado-net-overview.md)
