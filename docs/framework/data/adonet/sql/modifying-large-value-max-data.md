---
title: Modificando dados de valores grandes (max) no ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: 34f0a61329667a42aa42693e93169a5b6fb0aa5e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792044"
---
# <a name="modifying-large-value-max-data-in-adonet"></a><span data-ttu-id="8b747-102">Modificando dados de valores grandes (max) no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8b747-102">Modifying Large-Value (max) Data in ADO.NET</span></span>
<span data-ttu-id="8b747-103">Os tipos de dados de objetos grandes (LOB) são os que excedem o tamanho de linha máximo de 8 quilobytes (KB).</span><span class="sxs-lookup"><span data-stu-id="8b747-103">Large object (LOB) data types are those that exceed the maximum row size of 8 kilobytes (KB).</span></span> <span data-ttu-id="8b747-104">O SQL Server fornece um especificador `max` para os tipos de dados `varchar`, `nvarchar` e `varbinary` para permitir o armazenamento de valores grandes como 2^32 bytes.</span><span class="sxs-lookup"><span data-stu-id="8b747-104">SQL Server provides a `max` specifier for `varchar`, `nvarchar`, and `varbinary` data types to allow storage of values as large as 2^32 bytes.</span></span> <span data-ttu-id="8b747-105">As colunas da tabela e variáveis Transact-SQL podem especificar os tipos de dados `varchar(max)`, `nvarchar(max)` ou `varbinary(max)`.</span><span class="sxs-lookup"><span data-stu-id="8b747-105">Table columns and Transact-SQL variables may specify `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` data types.</span></span> <span data-ttu-id="8b747-106">No ADO.NET, os tipos de dados `max` podem ser encontrados por `DataReader` e também podem ser especificados como valores de parâmetro de entrada e saída sem nenhuma manipulação especial.</span><span class="sxs-lookup"><span data-stu-id="8b747-106">In ADO.NET, the `max` data types can be fetched by a `DataReader`, and can also be specified as both input and output parameter values without any special handling.</span></span> <span data-ttu-id="8b747-107">Para tipos de dados `varchar`, os dados podem ser recuperados e atualizados incrementalmente.</span><span class="sxs-lookup"><span data-stu-id="8b747-107">For large `varchar` data types, data can be retrieved and updated incrementally.</span></span>  
  
 <span data-ttu-id="8b747-108">Os tipos de dados `max` podem ser usados para comparações, como variáveis Transact-SQL, e para concatenação.</span><span class="sxs-lookup"><span data-stu-id="8b747-108">The `max` data types can be used for comparisons, as Transact-SQL variables, and for concatenation.</span></span> <span data-ttu-id="8b747-109">Eles também podem ser usados em cláusulas DISTINCT, ORDER BY e GROUP BY de uma instrução SELECT bem como em agregações, junções e subconsultas.</span><span class="sxs-lookup"><span data-stu-id="8b747-109">They can also be used in the DISTINCT, ORDER BY, GROUP BY clauses of a SELECT statement as well as in aggregates, joins, and subqueries.</span></span>  
  
 <span data-ttu-id="8b747-110">A tabela a seguir fornece links para a documentação nos Manuais Online do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8b747-110">The following table provides links to the documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="8b747-111">**SQL Server Books Online** (Guias online do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8b747-111">**SQL Server Books Online**</span></span>  
  
1. [<span data-ttu-id="8b747-112">Usando tipos de dados de valor grande</span><span class="sxs-lookup"><span data-stu-id="8b747-112">Using Large-Value Data Types</span></span>](https://go.microsoft.com/fwlink/?LinkId=120498)  
  
## <a name="large-value-type-restrictions"></a><span data-ttu-id="8b747-113">Restrições de tipo de valores grandes</span><span class="sxs-lookup"><span data-stu-id="8b747-113">Large-Value Type Restrictions</span></span>  
 <span data-ttu-id="8b747-114">As seguintes restrições aplicam-se a tipos de dados `max`, que não existem para tipos de dados menores:</span><span class="sxs-lookup"><span data-stu-id="8b747-114">The following restrictions apply to the `max` data types, which do not exist for smaller data types:</span></span>  
  
- <span data-ttu-id="8b747-115">Um `sql_variant` não pode conter um tipo de dados `varchar`.</span><span class="sxs-lookup"><span data-stu-id="8b747-115">A `sql_variant` cannot contain a large `varchar` data type.</span></span>  
  
- <span data-ttu-id="8b747-116">As colunas `varchar` grandes não podem ser especificadas como uma coluna de chave em um índice.</span><span class="sxs-lookup"><span data-stu-id="8b747-116">Large `varchar` columns cannot be specified as a key column in an index.</span></span> <span data-ttu-id="8b747-117">Elas são permitidas em uma coluna incluída em um índice não clusterizado.</span><span class="sxs-lookup"><span data-stu-id="8b747-117">They are allowed in an included column in a non-clustered index.</span></span>  
  
- <span data-ttu-id="8b747-118">As colunas `varchar` não podem ser usadas como colunas-chave de particionamento.</span><span class="sxs-lookup"><span data-stu-id="8b747-118">Large `varchar` columns cannot be used as partitioning key columns.</span></span>  
  
## <a name="working-with-large-value-types-in-transact-sql"></a><span data-ttu-id="8b747-119">Trabalhando com tipos de valores grandes no Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8b747-119">Working with Large-Value Types in Transact-SQL</span></span>  
 <span data-ttu-id="8b747-120">A função Transact-SQL `OPENROWSET` é um método único de conexão e acesso a dados remotos.</span><span class="sxs-lookup"><span data-stu-id="8b747-120">The Transact-SQL `OPENROWSET` function is a one-time method of connecting and accessing remote data.</span></span> <span data-ttu-id="8b747-121">Ela inclui todas as informações de conexão necessárias para acessar dados remotos de uma fonte de dados OLE DB.</span><span class="sxs-lookup"><span data-stu-id="8b747-121">It includes all of the connection information necessary to access remote data from an OLE DB data source.</span></span> <span data-ttu-id="8b747-122">`OPENROWSET` pode ser referenciada na cláusula FROM de uma consulta como se fosse um nome de tabela.</span><span class="sxs-lookup"><span data-stu-id="8b747-122">`OPENROWSET` can be referenced in the FROM clause of a query as though it were a table name.</span></span> <span data-ttu-id="8b747-123">Ela também pode ser referenciada como a tabela de destino de uma instrução INSERT, UPDATE ou DELETE, sujeita aos recursos do provedor OLE DB.</span><span class="sxs-lookup"><span data-stu-id="8b747-123">It can also be referenced as the target table of an INSERT, UPDATE, or DELETE statement, subject to the capabilities of the OLE DB provider.</span></span>  
  
 <span data-ttu-id="8b747-124">A função `OPENROWSET` inclui o provedor de conjunto de linhas `BULK`, que permite que você leia dados diretamente de um arquivo sem carregar os dados em uma tabela de destino.</span><span class="sxs-lookup"><span data-stu-id="8b747-124">The `OPENROWSET` function includes the `BULK` rowset provider, which allows you to read data directly from a file without loading the data into a target table.</span></span> <span data-ttu-id="8b747-125">Isso permite usar `OPENROWSET` em uma instrução INSERT SELECT simples.</span><span class="sxs-lookup"><span data-stu-id="8b747-125">This enables you to use `OPENROWSET` in a simple INSERT SELECT statement.</span></span>  
  
 <span data-ttu-id="8b747-126">Os `OPENROWSET BULK` argumentos de opção fornecem um controle significativo sobre onde começar e terminar a leitura de dados, como lidar com erros e como os dados são interpretados.</span><span class="sxs-lookup"><span data-stu-id="8b747-126">The `OPENROWSET BULK` option arguments provide significant control over where to begin and end reading data, how to deal with errors, and how data is interpreted.</span></span> <span data-ttu-id="8b747-127">Por exemplo, você pode especificar que o arquivo de dados seja lido como uma única linha, um conjunto de linhas de coluna única do tipo `varbinary`, `varchar` ou `nvarchar`.</span><span class="sxs-lookup"><span data-stu-id="8b747-127">For example, you can specify that the data file be read as a single-row, single-column rowset of type `varbinary`, `varchar`, or `nvarchar`.</span></span> <span data-ttu-id="8b747-128">Para a sintaxe e as opções completas, consulte os Manuais Online do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8b747-128">For the complete syntax and options, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="8b747-129">O exemplo a seguir insere uma foto na tabela ProductPhoto no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="8b747-129">The following example inserts a photo into the ProductPhoto table in the AdventureWorks sample database.</span></span> <span data-ttu-id="8b747-130">Ao usar o `BULK OPENROWSET` provedor, você deve fornecer a lista nomeada de colunas mesmo se não estiver inserindo valores em todas as colunas.</span><span class="sxs-lookup"><span data-stu-id="8b747-130">When using the `BULK OPENROWSET` provider, you must supply the named list of columns even if you aren't inserting values into every column.</span></span> <span data-ttu-id="8b747-131">A chave primária nesse caso é definida como uma coluna de identidade e pode ser omitida da lista de colunas.</span><span class="sxs-lookup"><span data-stu-id="8b747-131">The primary key in this case is defined as an identity column, and may be omitted from the column list.</span></span> <span data-ttu-id="8b747-132">Observe que você também deve fornecer um nome de correlação no final da instrução `OPENROWSET`, que, nesse caso, é ThumbnailPhoto.</span><span class="sxs-lookup"><span data-stu-id="8b747-132">Note that you must also supply a correlation name at the end of the `OPENROWSET` statement, which in this case is ThumbnailPhoto.</span></span> <span data-ttu-id="8b747-133">Isso correlaciona-se com a coluna na tabela `ProductPhoto` em que o arquivo está sendo carregado.</span><span class="sxs-lookup"><span data-stu-id="8b747-133">This correlates with the column in the `ProductPhoto` table into which the file is being loaded.</span></span>  
  
```  
INSERT Production.ProductPhoto (  
    ThumbnailPhoto,   
    ThumbnailPhotoFilePath,   
    LargePhoto,   
    LargePhotoFilePath)  
SELECT ThumbnailPhoto.*, null, null, N'tricycle_pink.gif'  
FROM OPENROWSET   
    (BULK 'c:\images\tricycle.jpg', SINGLE_BLOB) ThumbnailPhoto  
```  
  
## <a name="updating-data-using-update-write"></a><span data-ttu-id="8b747-134">Atualizando dados usando UPDATE .WRITE</span><span class="sxs-lookup"><span data-stu-id="8b747-134">Updating Data Using UPDATE .WRITE</span></span>  
 <span data-ttu-id="8b747-135">A instrução UPDATE do Transact-SQL tem a nova sintaxe WRITE para modificar o conteúdo das colunas `varchar(max)`, `nvarchar(max)` ou `varbinary(max)`.</span><span class="sxs-lookup"><span data-stu-id="8b747-135">The Transact-SQL UPDATE statement has new WRITE syntax for modifying the contents of `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` columns.</span></span> <span data-ttu-id="8b747-136">Isso permite que você execute atualizações parciais dos dados.</span><span class="sxs-lookup"><span data-stu-id="8b747-136">This allows you to perform partial updates of the data.</span></span> <span data-ttu-id="8b747-137">A sintaxe da instrução UPDATE .WRITE é mostrada aqui na forma abreviada:</span><span class="sxs-lookup"><span data-stu-id="8b747-137">The UPDATE .WRITE syntax is shown here in abbreviated form:</span></span>  
  
 <span data-ttu-id="8b747-138">UPDATE</span><span class="sxs-lookup"><span data-stu-id="8b747-138">UPDATE</span></span>  
  
 <span data-ttu-id="8b747-139">*{\<objeto >* }</span><span class="sxs-lookup"><span data-stu-id="8b747-139">{ *\<object>* }</span></span>  
  
 <span data-ttu-id="8b747-140">SET</span><span class="sxs-lookup"><span data-stu-id="8b747-140">SET</span></span>  
  
 <span data-ttu-id="8b747-141">{ *column_name* = { .WRITE ( *expression* , @Offset , @Length ) }</span><span class="sxs-lookup"><span data-stu-id="8b747-141">{ *column_name* = { .WRITE ( *expression* , @Offset , @Length ) }</span></span>  
  
 <span data-ttu-id="8b747-142">O método WRITE especifica que uma seção do valor de *column_name* será modificada.</span><span class="sxs-lookup"><span data-stu-id="8b747-142">The WRITE method specifies that a section of the value of the *column_name* will be modified.</span></span> <span data-ttu-id="8b747-143">A expressão é o valor que será copiado para o *column_name*, o `@Offset` é o ponto inicial no qual a expressão será gravada e o `@Length` argumento é o comprimento da seção na coluna.</span><span class="sxs-lookup"><span data-stu-id="8b747-143">The expression is the value that will be copied to the *column_name*, the `@Offset` is the beginning point at which the expression will be written, and the `@Length` argument is the length of the section in the column.</span></span>  
  
|<span data-ttu-id="8b747-144">If</span><span class="sxs-lookup"><span data-stu-id="8b747-144">If</span></span>|<span data-ttu-id="8b747-145">Then</span><span class="sxs-lookup"><span data-stu-id="8b747-145">Then</span></span>|  
|--------|----------|  
|<span data-ttu-id="8b747-146">A expressão é definida como NULL</span><span class="sxs-lookup"><span data-stu-id="8b747-146">The expression is set to NULL</span></span>|<span data-ttu-id="8b747-147">`@Length`é ignorado e o valor em *column_name* é truncado no especificado `@Offset`.</span><span class="sxs-lookup"><span data-stu-id="8b747-147">`@Length` is ignored and the value in *column_name* is truncated at the specified `@Offset`.</span></span>|  
|<span data-ttu-id="8b747-148">`@Offset`é nulo</span><span class="sxs-lookup"><span data-stu-id="8b747-148">`@Offset` is NULL</span></span>|<span data-ttu-id="8b747-149">A operação de atualização acrescenta a expressão no final do valor de *column_name* existente e `@Length` é ignorada.</span><span class="sxs-lookup"><span data-stu-id="8b747-149">The update operation appends the expression at the end of the existing *column_name* value and `@Length` is ignored.</span></span>|  
|<span data-ttu-id="8b747-150">`@Offset` é maior do que o comprimento do valor column_name</span><span class="sxs-lookup"><span data-stu-id="8b747-150">`@Offset` is greater than the length of the column_name value</span></span>|<span data-ttu-id="8b747-151">O SQL Server retornará um erro.</span><span class="sxs-lookup"><span data-stu-id="8b747-151">SQL Server returns an error.</span></span>|  
|<span data-ttu-id="8b747-152">`@Length`é nulo</span><span class="sxs-lookup"><span data-stu-id="8b747-152">`@Length` is NULL</span></span>|<span data-ttu-id="8b747-153">A operação de atualização remove todos os dados de `@Offset` para o final do valor `column_name`.</span><span class="sxs-lookup"><span data-stu-id="8b747-153">The update operation removes all data from `@Offset` to the end of the `column_name` value.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="8b747-154">Nem `@Offset` ou `@Length` pode ser um número negativo.</span><span class="sxs-lookup"><span data-stu-id="8b747-154">Neither `@Offset` nor `@Length` can be a negative number.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b747-155">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8b747-155">Example</span></span>  
 <span data-ttu-id="8b747-156">Este exemplo de Transact-SQL atualiza um valor parcial em DocumentSummary, uma coluna `nvarchar(max)` na tabela Document no banco de dados AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="8b747-156">This Transact-SQL example updates a partial value in DocumentSummary, an `nvarchar(max)` column in the Document table in the AdventureWorks database.</span></span> <span data-ttu-id="8b747-157">A palavra 'components' é substituída pela palavra 'features' especificando a palavra de substituição, o local de início (deslocamento) da palavra a ser substituída nos dados existentes e o número de caracteres a serem substituídos (comprimento).</span><span class="sxs-lookup"><span data-stu-id="8b747-157">The word 'components' is replaced by the word 'features' by specifying the replacement word, the beginning location (offset) of the word to be replaced in the existing data, and the number of characters to be replaced (length).</span></span> <span data-ttu-id="8b747-158">O exemplo inclui instruções SELECT antes e depois da instrução UPDATE para comparar resultados.</span><span class="sxs-lookup"><span data-stu-id="8b747-158">The example includes SELECT statements before and after the UPDATE statement to compare results.</span></span>  
  
```  
USE AdventureWorks;  
GO  
--View the existing value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety components of your bicycle.  
  
--Modify a single word in the DocumentSummary column  
UPDATE Production.Document  
SET DocumentSummary .WRITE (N'features',28,10)  
WHERE DocumentID = 3 ;  
GO   
--View the modified value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety features of your bicycle.  
```  
  
## <a name="working-with-large-value-types-in-adonet"></a><span data-ttu-id="8b747-159">Trabalhando com tipos de valores grandes no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8b747-159">Working with Large-Value Types in ADO.NET</span></span>  
 <span data-ttu-id="8b747-160">Você pode trabalhar com tipos de valor grande no ADO.net especificando tipos de valor grande <xref:System.Data.SqlClient.SqlParameter> como objetos em <xref:System.Data.SqlClient.SqlDataReader> um para retornar um conjunto de resultados ou usando um <xref:System.Data.SqlClient.SqlDataAdapter> para preencher um `DataSet` / `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="8b747-160">You can work with large value types in ADO.NET by specifying large value types as <xref:System.Data.SqlClient.SqlParameter> objects in a <xref:System.Data.SqlClient.SqlDataReader> to return a result set, or by using a <xref:System.Data.SqlClient.SqlDataAdapter> to fill a `DataSet`/`DataTable`.</span></span> <span data-ttu-id="8b747-161">Não há nenhuma diferença entre o modo como você trabalha com um tipo de valor grande e o tipo de dados relacionado de menor valor.</span><span class="sxs-lookup"><span data-stu-id="8b747-161">There is no difference between the way you work with a large value type and its related, smaller value data type.</span></span>  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a><span data-ttu-id="8b747-162">Usando GetSqlBytes para recuperar dados</span><span class="sxs-lookup"><span data-stu-id="8b747-162">Using GetSqlBytes to Retrieve Data</span></span>  
 <span data-ttu-id="8b747-163">O método `GetSqlBytes` do <xref:System.Data.SqlClient.SqlDataReader> pode ser usado para recuperar o conteúdo de uma coluna `varbinary(max)`.</span><span class="sxs-lookup"><span data-stu-id="8b747-163">The `GetSqlBytes` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="8b747-164">O fragmento de código a seguir supõe um objeto <xref:System.Data.SqlClient.SqlCommand> chamado `cmd` que seleciona dados `varbinary(max)` de uma tabela e um objeto <xref:System.Data.SqlClient.SqlDataReader> nomeados `reader` que recuperam os dados como <xref:System.Data.SqlTypes.SqlBytes>.</span><span class="sxs-lookup"><span data-stu-id="8b747-164">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as <xref:System.Data.SqlTypes.SqlBytes>.</span></span>  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim bytes As SqlBytes = reader.GetSqlBytes(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBytes bytes = reader.GetSqlBytes(0);  
    }  
```  
  
### <a name="using-getsqlchars-to-retrieve-data"></a><span data-ttu-id="8b747-165">Usando GetSqlChars para recuperar dados</span><span class="sxs-lookup"><span data-stu-id="8b747-165">Using GetSqlChars to Retrieve Data</span></span>  
 <span data-ttu-id="8b747-166">O método `GetSqlChars` do <xref:System.Data.SqlClient.SqlDataReader> pode ser usado para recuperar o conteúdo de uma coluna `varchar(max)` ou `nvarchar(max)`.</span><span class="sxs-lookup"><span data-stu-id="8b747-166">The `GetSqlChars` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varchar(max)` or `nvarchar(max)` column.</span></span> <span data-ttu-id="8b747-167">O fragmento de código a seguir supõe um objeto <xref:System.Data.SqlClient.SqlCommand> chamado `cmd` que seleciona dados `nvarchar(max)` de uma tabela e um objeto <xref:System.Data.SqlClient.SqlDataReader> nomeados `reader` que recuperam os dados.</span><span class="sxs-lookup"><span data-stu-id="8b747-167">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `nvarchar(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim buffer As SqlChars = reader.GetSqlChars(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
{  
    SqlChars buffer = reader.GetSqlChars(0);  
}  
```  
  
### <a name="using-getsqlbinary-to-retrieve-data"></a><span data-ttu-id="8b747-168">Usando GetSqlBinary para recuperar dados</span><span class="sxs-lookup"><span data-stu-id="8b747-168">Using GetSqlBinary to Retrieve Data</span></span>  
 <span data-ttu-id="8b747-169">O método `GetSqlBinary` de um <xref:System.Data.SqlClient.SqlDataReader> pode ser usado para recuperar o conteúdo de uma coluna `varbinary(max)`.</span><span class="sxs-lookup"><span data-stu-id="8b747-169">The `GetSqlBinary` method of a <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="8b747-170">O fragmento de código a seguir supõe um objeto <xref:System.Data.SqlClient.SqlCommand> chamado `cmd` que seleciona dados `varbinary(max)` de uma tabela e um objeto <xref:System.Data.SqlClient.SqlDataReader> nomeados `reader` que recuperam os dados como um fluxo <xref:System.Data.SqlTypes.SqlBinary>.</span><span class="sxs-lookup"><span data-stu-id="8b747-170">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as a <xref:System.Data.SqlTypes.SqlBinary> stream.</span></span>  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim binaryStream As SqlBinary = reader.GetSqlBinary(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBinary binaryStream = reader.GetSqlBinary(0);  
    }  
```  
  
### <a name="using-getbytes-to-retrieve-data"></a><span data-ttu-id="8b747-171">Usando GetBytes para recuperar dados</span><span class="sxs-lookup"><span data-stu-id="8b747-171">Using GetBytes to Retrieve Data</span></span>  
 <span data-ttu-id="8b747-172">O método `GetBytes` de um <xref:System.Data.SqlClient.SqlDataReader> lê um fluxo de bytes do deslocamento da coluna especificada em uma matriz de bytes que inicia no deslocamento da matriz especificada.</span><span class="sxs-lookup"><span data-stu-id="8b747-172">The `GetBytes` method of a <xref:System.Data.SqlClient.SqlDataReader> reads a stream of bytes from the specified column offset into a byte array starting at the specified array offset.</span></span> <span data-ttu-id="8b747-173">O fragmento de código a seguir supõe um objeto <xref:System.Data.SqlClient.SqlDataReader> chamado `reader` que recupera bytes em uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="8b747-173">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves bytes into a byte array.</span></span> <span data-ttu-id="8b747-174">Observe que, ao contrário de `GetSqlBytes`, `GetBytes` exige um tamanho para o buffer da matriz.</span><span class="sxs-lookup"><span data-stu-id="8b747-174">Note that, unlike `GetSqlBytes`, `GetBytes` requires a size for the array buffer.</span></span>  
  
```vb  
While reader.Read()  
    Dim buffer(4000) As Byte  
    Dim byteCount As Integer = _  
    CInt(reader.GetBytes(1, 0, buffer, 0, 4000))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    byte[] buffer = new byte[4000];  
    long byteCount = reader.GetBytes(1, 0, buffer, 0, 4000);  
}  
```  
  
### <a name="using-getvalue-to-retrieve-data"></a><span data-ttu-id="8b747-175">Usando GetValue para recuperar dados</span><span class="sxs-lookup"><span data-stu-id="8b747-175">Using GetValue to Retrieve Data</span></span>  
 <span data-ttu-id="8b747-176">O método `GetValue` de um <xref:System.Data.SqlClient.SqlDataReader> lê o valor de deslocamento da coluna especificada em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="8b747-176">The `GetValue` method of a <xref:System.Data.SqlClient.SqlDataReader> reads the value from the specified column offset into an array.</span></span> <span data-ttu-id="8b747-177">O seguinte fragmento de código supõe um objeto <xref:System.Data.SqlClient.SqlDataReader> chamado `reader` que recupera os dados binários do deslocamento da primeira coluna e, em seguida, os dados de cadeia de caracteres do deslocamento da segunda coluna.</span><span class="sxs-lookup"><span data-stu-id="8b747-177">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves binary data from the first column offset, and then string data from the second column offset.</span></span>  
  
```vb  
While reader.Read()  
    ' Read the data from varbinary(max) column  
    Dim binaryData() As Byte = CByte(reader.GetValue(0))  
  
    ' Read the data from varchar(max) or nvarchar(max) column  
    Dim stringData() As String = Cstr((reader.GetValue(1))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    // Read the data from varbinary(max) column  
    byte[] binaryData = (byte[])reader.GetValue(0);  
  
    // Read the data from varchar(max) or nvarchar(max) column  
    String stringData = (String)reader.GetValue(1);  
}  
```  
  
## <a name="converting-from-large-value-types-to-clr-types"></a><span data-ttu-id="8b747-178">Convertendo de tipos de valores grandes para tipos CLR</span><span class="sxs-lookup"><span data-stu-id="8b747-178">Converting from Large Value Types to CLR Types</span></span>  
 <span data-ttu-id="8b747-179">Você pode converter o conteúdo de uma coluna `varchar(max)` ou `nvarchar(max)` usando qualquer um dos métodos de conversão de cadeia de caracteres, como `ToString`.</span><span class="sxs-lookup"><span data-stu-id="8b747-179">You can convert the contents of a `varchar(max)` or `nvarchar(max)` column using any of the string conversion methods, such as `ToString`.</span></span> <span data-ttu-id="8b747-180">O fragmento de código a seguir supõe um objeto <xref:System.Data.SqlClient.SqlDataReader> chamado `reader` que recupera os dados.</span><span class="sxs-lookup"><span data-stu-id="8b747-180">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
```vb  
While reader.Read()  
    Dim str as String = reader(0).ToString()  
    Console.WriteLine(str)  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
     string str = reader[0].ToString();  
     Console.WriteLine(str);  
}  
```  
  
### <a name="example"></a><span data-ttu-id="8b747-181">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8b747-181">Example</span></span>  
 <span data-ttu-id="8b747-182">O código a seguir recupera o nome e o objeto `LargePhoto` da tabela `ProductPhoto` no banco de dados `AdventureWorks` e o salva em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="8b747-182">The following code retrieves the name and the `LargePhoto` object from the `ProductPhoto` table in the `AdventureWorks` database and saves it to a file.</span></span> <span data-ttu-id="8b747-183">O assembly precisa ser compilado com uma referência ao namespace <xref:System.Drawing>.</span><span class="sxs-lookup"><span data-stu-id="8b747-183">The assembly needs to be compiled with a reference to the <xref:System.Drawing> namespace.</span></span>  <span data-ttu-id="8b747-184">O método <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> do <xref:System.Data.SqlClient.SqlDataReader> retorna um objeto <xref:System.Data.SqlTypes.SqlBytes> que expõe uma propriedade `Stream`.</span><span class="sxs-lookup"><span data-stu-id="8b747-184">The <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> method of the <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.SqlTypes.SqlBytes> object that exposes a `Stream` property.</span></span> <span data-ttu-id="8b747-185">O código usa isso para criar um novo `Bitmap` objeto e, em seguida, salva-o `ImageFormat`no GIF.</span><span class="sxs-lookup"><span data-stu-id="8b747-185">The code uses this to create a new `Bitmap` object, and then saves it in the Gif `ImageFormat`.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a><span data-ttu-id="8b747-186">Usando parâmetros de tipo de valores grandes</span><span class="sxs-lookup"><span data-stu-id="8b747-186">Using Large Value Type Parameters</span></span>  
 <span data-ttu-id="8b747-187">Os tipos de valores grandes podem ser usados em objetos <xref:System.Data.SqlClient.SqlParameter> da mesma maneira que você usa tipos de valores menores em objetos <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="8b747-187">Large value types can be used in <xref:System.Data.SqlClient.SqlParameter> objects the same way you use smaller value types in <xref:System.Data.SqlClient.SqlParameter> objects.</span></span> <span data-ttu-id="8b747-188">Você pode recuperar tipos de valor grande <xref:System.Data.SqlClient.SqlParameter> como valores, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8b747-188">You can retrieve large value types as <xref:System.Data.SqlClient.SqlParameter> values, as shown in the following example.</span></span> <span data-ttu-id="8b747-189">O código presume que o seguinte procedimento armazenado GetDocumentSummary exista no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="8b747-189">The code assumes that the following GetDocumentSummary stored procedure exists in the AdventureWorks sample database.</span></span> <span data-ttu-id="8b747-190">O procedimento armazenado usa um parâmetro de entrada @DocumentID chamado e retorna o conteúdo da coluna DocumentSummary no parâmetro @DocumentSummary de saída.</span><span class="sxs-lookup"><span data-stu-id="8b747-190">The stored procedure takes an input parameter named @DocumentID and returns the contents of the DocumentSummary column in the @DocumentSummary output parameter.</span></span>  
  
```  
CREATE PROCEDURE GetDocumentSummary   
(  
    @DocumentID int,  
    @DocumentSummary nvarchar(MAX) OUTPUT  
)  
AS  
SET NOCOUNT ON  
SELECT  @DocumentSummary=Convert(nvarchar(MAX), DocumentSummary)  
FROM    Production.Document  
WHERE   DocumentID=@DocumentID  
```  
  
### <a name="example"></a><span data-ttu-id="8b747-191">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8b747-191">Example</span></span>  
 <span data-ttu-id="8b747-192">O código do ADO.NET cria objetos <xref:System.Data.SqlClient.SqlConnection> e <xref:System.Data.SqlClient.SqlCommand> para executar o procedimento armazenado GetDocumentSummary e recuperar o resumo do documento, que está armazenado como um tipo de valor grande.</span><span class="sxs-lookup"><span data-stu-id="8b747-192">The ADO.NET code creates <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to execute the GetDocumentSummary stored procedure and retrieve the document summary, which is stored as a large value type.</span></span> <span data-ttu-id="8b747-193">O código passa um valor para o @DocumentID parâmetro de entrada e exibe os resultados passados @DocumentSummary no parâmetro output na janela do console.</span><span class="sxs-lookup"><span data-stu-id="8b747-193">The code passes a value for the @DocumentID input parameter, and displays the results passed back in the @DocumentSummary output parameter in the Console window.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8b747-194">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b747-194">See also</span></span>

- <span data-ttu-id="8b747-195">[SQL Server Binary and Large-Value Data](sql-server-binary-and-large-value-data.md) (Dados binários e de valor grande do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8b747-195">[SQL Server Binary and Large-Value Data](sql-server-binary-and-large-value-data.md)</span></span>
- [<span data-ttu-id="8b747-196">Mapeamentos de tipo de dados do SQL Server</span><span class="sxs-lookup"><span data-stu-id="8b747-196">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- <span data-ttu-id="8b747-197">[SQL Server Data Operations in ADO.NET](sql-server-data-operations.md) (Operações de dados do SQL Server no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="8b747-197">[SQL Server Data Operations in ADO.NET](sql-server-data-operations.md)</span></span>
- <span data-ttu-id="8b747-198">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="8b747-198">[ADO.NET Overview](../ado-net-overview.md)</span></span>
