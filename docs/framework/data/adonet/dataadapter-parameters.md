---
title: Parâmetros DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
ms.openlocfilehash: e633c7cdd105125fc5fb595566d15cf5f5fe4e6f
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48266813"
---
# <a name="dataadapter-parameters"></a><span data-ttu-id="3149c-102">Parâmetros DataAdapter</span><span class="sxs-lookup"><span data-stu-id="3149c-102">DataAdapter Parameters</span></span>
<span data-ttu-id="3149c-103">O <xref:System.Data.Common.DbDataAdapter> tem quatro propriedades que são usadas para recuperar dados da fonte de dados e atualizá-los nela: a propriedade <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> retorna dados da fonte de dados; e as propriedades <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> e <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> são usadas para gerenciar alterações na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="3149c-103">The <xref:System.Data.Common.DbDataAdapter> has four properties that are used to retrieve data from and update data to the data source: the <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> property returns data from the data source; and the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, and <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> properties are used to manage changes at the data source.</span></span> <span data-ttu-id="3149c-104">A propriedade `SelectCommand` deve ser definida antes que você chame o método `Fill` do `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="3149c-104">The `SelectCommand` property must be set before you call the `Fill` method of the `DataAdapter`.</span></span> <span data-ttu-id="3149c-105">A propriedade `InsertCommand`, `UpdateCommand` ou `DeleteCommand` deve ser definida antes que o método `Update` do `DataAdapter` seja chamado, dependendo de quais alterações foram feitas nos dados da <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="3149c-105">The `InsertCommand`, `UpdateCommand`, or `DeleteCommand` properties must be set before the `Update` method of the `DataAdapter` is called, depending on what changes were made to the data in the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="3149c-106">Por exemplo, se as linhas tiverem sido adicionadas, o `InsertCommand` deve ser definido antes de chamar `Update`.</span><span class="sxs-lookup"><span data-stu-id="3149c-106">For example, if rows have been added, the `InsertCommand` must be set before you call `Update`.</span></span> <span data-ttu-id="3149c-107">Quando `Update` estiver processando uma linha inserida, atualizada ou excluída, o `DataAdapter` usará a respectiva propriedade `Command` para processar a ação.</span><span class="sxs-lookup"><span data-stu-id="3149c-107">When `Update` is processing an inserted, updated, or deleted row, the `DataAdapter` uses the respective `Command` property to process the action.</span></span> <span data-ttu-id="3149c-108">As informações atuais sobre a linha modificada são passadas para o objeto `Command` através da coleção `Parameters`.</span><span class="sxs-lookup"><span data-stu-id="3149c-108">Current information about the modified row is passed to the `Command` object through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="3149c-109">Ao atualizar uma linha na fonte de dados, você chama a instrução UPDATE, que usa um identificador exclusivo para identificar a linha na tabela a ser atualizada.</span><span class="sxs-lookup"><span data-stu-id="3149c-109">When you update a row at the data source, you call the UPDATE statement, which uses a unique identifier to identify the row in the table be updated.</span></span> <span data-ttu-id="3149c-110">O identificador exclusivo é geralmente o valor de um campo de chave primária.</span><span class="sxs-lookup"><span data-stu-id="3149c-110">The unique identifier is typically the value of a primary key field.</span></span> <span data-ttu-id="3149c-111">A instrução UPDATE usa os parâmetros que contêm o identificador exclusivo e as colunas e os valores a serem atualizados, conforme mostrado na declaração Transact-SQL a seguir.</span><span class="sxs-lookup"><span data-stu-id="3149c-111">The UPDATE statement uses parameters that contain both the unique identifier and the columns and values to be updated, as shown in the following Transact-SQL statement.</span></span>  
  
```  
UPDATE Customers SET CompanyName = @CompanyName   
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
>  <span data-ttu-id="3149c-112">A sintaxe para espaços reservados de parâmetro depende da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="3149c-112">The syntax for parameter placeholders depends on the data source.</span></span> <span data-ttu-id="3149c-113">Este exemplo mostra os espaços reservados de uma fonte de dados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3149c-113">This example shows placeholders for a SQL Server data source.</span></span> <span data-ttu-id="3149c-114">Use espaços reservados de ponto de interrogação (?) para os parâmetros <xref:System.Data.OleDb> e <xref:System.Data.Odbc>.</span><span class="sxs-lookup"><span data-stu-id="3149c-114">Use question mark (?) placeholders for <xref:System.Data.OleDb> and <xref:System.Data.Odbc> parameters.</span></span>  
  
 <span data-ttu-id="3149c-115">Neste exemplo do Visual Basic, o `CompanyName` campo é atualizado com o valor da `@CompanyName` parâmetro para a linha em que `CustomerID` é igual ao valor da `@CustomerID` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="3149c-115">In this Visual Basic example, the `CompanyName` field is updated with the value of the `@CompanyName` parameter for the row where `CustomerID` equals the value of the `@CustomerID` parameter.</span></span> <span data-ttu-id="3149c-116">Os parâmetros recuperam informações da linha modificada usando o <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> propriedade do <xref:System.Data.SqlClient.SqlParameter> objeto.</span><span class="sxs-lookup"><span data-stu-id="3149c-116">The parameters retrieve information from the modified row using the <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> property of the <xref:System.Data.SqlClient.SqlParameter> object.</span></span> <span data-ttu-id="3149c-117">Estes são os parâmetros da instrução UPDATE de exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="3149c-117">The following are the parameters for the previous sample UPDATE statement.</span></span> <span data-ttu-id="3149c-118">O código assume que a variável `adapter` representa um objeto <xref:System.Data.SqlClient.SqlDataAdapter> válido.</span><span class="sxs-lookup"><span data-stu-id="3149c-118">The code assumes that the variable `adapter` represents a valid <xref:System.Data.SqlClient.SqlDataAdapter> object.</span></span>  
  
```  
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 <span data-ttu-id="3149c-119">O método `Add` da coleção `Parameters` adota o nome do parâmetro, o tipo de dados, o tamanho (se aplicável ao tipo) e o nome da <xref:System.Data.Common.DbParameter.SourceColumn%2A> da `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="3149c-119">The `Add` method of the `Parameters` collection takes the name of the parameter, the data type, the size (if applicable to the type), and the name of the <xref:System.Data.Common.DbParameter.SourceColumn%2A> from the `DataTable`.</span></span> <span data-ttu-id="3149c-120">Observe que <xref:System.Data.Common.DbParameter.SourceVersion%2A> do parâmetro `@CustomerID` é definido como `Original`.</span><span class="sxs-lookup"><span data-stu-id="3149c-120">Notice that the <xref:System.Data.Common.DbParameter.SourceVersion%2A> of the `@CustomerID` parameter is set to `Original`.</span></span> <span data-ttu-id="3149c-121">Isso garante que a linha existente na fonte de dados será atualizada se o valor da(s) coluna(s) de identificação tiverem sido alteradas na <xref:System.Data.DataRow> modificada.</span><span class="sxs-lookup"><span data-stu-id="3149c-121">This guarantees that the existing row in the data source is updated if the value of the identifying column or columns has been changed in the modified <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="3149c-122">Nesse caso, o valor de linha `Original` corresponderia ao valor atual na fonte de dados, e o valor de linha `Current` conteria o valor atualizado.</span><span class="sxs-lookup"><span data-stu-id="3149c-122">In that case, the `Original` row value would match the current value at the data source, and the `Current` row value would contain the updated value.</span></span> <span data-ttu-id="3149c-123">A `SourceVersion` do parâmetro `@CompanyName` não está definida e usa o padrão, o valor de linha `Current`.</span><span class="sxs-lookup"><span data-stu-id="3149c-123">The `SourceVersion` for the `@CompanyName` parameter is not set and uses the default, `Current` row value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3149c-124">Para as operações `Fill` dos métodos `DataAdapter` e `Get` do `DataReader`, o tipo do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] é inferido do tipo retornado pelo provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3149c-124">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] type is inferred from the type returned from the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data provider.</span></span> <span data-ttu-id="3149c-125">Inferido [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipos e métodos de acessador para tipos de dados do Microsoft SQL Server, OLE DB e ODBC são descritos na [mapeamentos de tipo de dados no ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md).</span><span class="sxs-lookup"><span data-stu-id="3149c-125">The inferred [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types and accessor methods for Microsoft SQL Server, OLE DB, and ODBC data types are described in [Data Type Mappings in ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md).</span></span>  
  
## <a name="parametersourcecolumn-parametersourceversion"></a><span data-ttu-id="3149c-126">Parameter.SourceColumn, Parameter.SourceVersion</span><span class="sxs-lookup"><span data-stu-id="3149c-126">Parameter.SourceColumn, Parameter.SourceVersion</span></span>  
 <span data-ttu-id="3149c-127">A `SourceColumn` e a `SourceVersion` podem ser passadas como argumentos para o construtor `Parameter` ou definidas como propriedades de um `Parameter` existente.</span><span class="sxs-lookup"><span data-stu-id="3149c-127">The `SourceColumn` and `SourceVersion` may be passed as arguments to the `Parameter` constructor, or set as properties of an existing `Parameter`.</span></span> <span data-ttu-id="3149c-128">A `SourceColumn` é o nome da <xref:System.Data.DataColumn> da <xref:System.Data.DataRow>, em que o valor do `Parameter` será recuperado.</span><span class="sxs-lookup"><span data-stu-id="3149c-128">The `SourceColumn` is the name of the <xref:System.Data.DataColumn> from the <xref:System.Data.DataRow> where the value of the `Parameter` will be retrieved.</span></span> <span data-ttu-id="3149c-129">A `SourceVersion` especifica a versão da `DataRow` que o `DataAdapter` usa para recuperar o valor.</span><span class="sxs-lookup"><span data-stu-id="3149c-129">The `SourceVersion` specifies the `DataRow` version that the `DataAdapter` uses to retrieve the value.</span></span>  
  
 <span data-ttu-id="3149c-130">A tabela a seguir mostra os valores de enumeração <xref:System.Data.DataRowVersion> disponíveis para uso com a `SourceVersion`.</span><span class="sxs-lookup"><span data-stu-id="3149c-130">The following table shows the <xref:System.Data.DataRowVersion> enumeration values available for use with `SourceVersion`.</span></span>  
  
|<span data-ttu-id="3149c-131">Enumeração DataRowVersion</span><span class="sxs-lookup"><span data-stu-id="3149c-131">DataRowVersion Enumeration</span></span>|<span data-ttu-id="3149c-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="3149c-132">Description</span></span>|  
|--------------------------------|-----------------|  
|`Current`|<span data-ttu-id="3149c-133">O parâmetro usa o valor atual da coluna.</span><span class="sxs-lookup"><span data-stu-id="3149c-133">The parameter uses the current value of the column.</span></span> <span data-ttu-id="3149c-134">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="3149c-134">This is the default.</span></span>|  
|`Default`|<span data-ttu-id="3149c-135">O parâmetro usa o `DefaultValue` da coluna.</span><span class="sxs-lookup"><span data-stu-id="3149c-135">The parameter uses the `DefaultValue` of the column.</span></span>|  
|`Original`|<span data-ttu-id="3149c-136">O parâmetro usa o valor original da coluna.</span><span class="sxs-lookup"><span data-stu-id="3149c-136">The parameter uses the original value of the column.</span></span>|  
|`Proposed`|<span data-ttu-id="3149c-137">O parâmetro usa um valor proposto.</span><span class="sxs-lookup"><span data-stu-id="3149c-137">The parameter uses a proposed value.</span></span>|  
  
 <span data-ttu-id="3149c-138">O exemplo de código `SqlClient` na seção a seguir define um parâmetro para um <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> em que a coluna `CustomerID` é usada como `SourceColumn` de dois parâmetros: `@CustomerID` (`SET CustomerID = @CustomerID`) e `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`).</span><span class="sxs-lookup"><span data-stu-id="3149c-138">The `SqlClient` code example in the next section defines a parameter for an <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> in which the `CustomerID` column is used as a `SourceColumn` for two parameters: `@CustomerID` (`SET CustomerID = @CustomerID`), and `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`).</span></span> <span data-ttu-id="3149c-139">O `@CustomerID` parâmetro é usado para atualizar o **CustomerID** coluna para o valor atual no `DataRow`.</span><span class="sxs-lookup"><span data-stu-id="3149c-139">The `@CustomerID` parameter is used to update the **CustomerID** column to the current value in the `DataRow`.</span></span> <span data-ttu-id="3149c-140">Como resultado, o `CustomerID` `SourceColumn` com um `SourceVersion` de `Current` é usado.</span><span class="sxs-lookup"><span data-stu-id="3149c-140">As a result, the `CustomerID` `SourceColumn` with a `SourceVersion` of `Current` is used.</span></span> <span data-ttu-id="3149c-141">O `@OldCustomerID` parâmetro é usado para identificar a linha atual na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="3149c-141">The `@OldCustomerID` parameter is used to identify the current row in the data source.</span></span> <span data-ttu-id="3149c-142">Como o valor de coluna correspondente é encontrado na versão `Original` da linha, a mesma `SourceColumn` (`CustomerID`) com uma `SourceVersion` de `Original` é usada.</span><span class="sxs-lookup"><span data-stu-id="3149c-142">Because the matching column value is found in the `Original` version of the row, the same `SourceColumn` (`CustomerID`) with a `SourceVersion` of `Original` is used.</span></span>  
  
## <a name="working-with-sqlclient-parameters"></a><span data-ttu-id="3149c-143">Trabalhando com parâmetros SqlClient</span><span class="sxs-lookup"><span data-stu-id="3149c-143">Working with SqlClient Parameters</span></span>  
 <span data-ttu-id="3149c-144">O exemplo a seguir demonstra como criar um <xref:System.Data.SqlClient.SqlDataAdapter> e definir <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> para <xref:System.Data.MissingSchemaAction.AddWithKey> a fim de recuperar informações adicionais do esquema no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="3149c-144">The following example demonstrates how to create a <xref:System.Data.SqlClient.SqlDataAdapter> and set the <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> to <xref:System.Data.MissingSchemaAction.AddWithKey> in order to retrieve additional schema information from the database.</span></span> <span data-ttu-id="3149c-145">O conjunto de propriedades <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A> e <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> e os objetos <xref:System.Data.SqlClient.SqlParameter> correspondentes adicionados à coleção <xref:System.Data.SqlClient.SqlCommand.Parameters%2A>.</span><span class="sxs-lookup"><span data-stu-id="3149c-145">The <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties set and their corresponding <xref:System.Data.SqlClient.SqlParameter> objects added to the <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection.</span></span> <span data-ttu-id="3149c-146">O método retorna um objeto `SqlDataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="3149c-146">The method returns a `SqlDataAdapter` object.</span></span>  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a><span data-ttu-id="3149c-147">Espaços reservados do parâmetro OleDb</span><span class="sxs-lookup"><span data-stu-id="3149c-147">OleDb Parameter Placeholders</span></span>  
 <span data-ttu-id="3149c-148">Para os objetos <xref:System.Data.OleDb.OleDbDataAdapter> e <xref:System.Data.Odbc.OdbcDataAdapter>, você deve usar os espaços reservados de ponto de interrogação (?) para identificar os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="3149c-148">For the <xref:System.Data.OleDb.OleDbDataAdapter> and <xref:System.Data.Odbc.OdbcDataAdapter> objects, you must use question mark (?) placeholders to identify the parameters.</span></span>  
  
```vb  
Dim selectSQL As String = _  
  "SELECT CustomerID, CompanyName FROM Customers " & _  
  "WHERE CountryRegion = ? AND City = ?"  
Dim insertSQL AS String = _  
  "INSERT INTO Customers (CustomerID, CompanyName) VALUES (?, ?)"  
Dim updateSQL AS String = _  
  "UPDATE Customers SET CustomerID = ?, CompanyName = ? " & _  
  WHERE CustomerID = ?"  
Dim deleteSQL As String = "DELETE FROM Customers WHERE CustomerID = ?"  
```  
  
```csharp  
string selectSQL =   
  "SELECT CustomerID, CompanyName FROM Customers " +  
  "WHERE CountryRegion = ? AND City = ?";  
string insertSQL =   
  "INSERT INTO Customers (CustomerID, CompanyName) " +  
  "VALUES (?, ?)";  
string updateSQL =   
  "UPDATE Customers SET CustomerID = ?, CompanyName = ? " +  
  "WHERE CustomerID = ? ";  
string deleteSQL = "DELETE FROM Customers WHERE CustomerID = ?";  
```  
  
 <span data-ttu-id="3149c-149">As instruções de consulta parametrizadas definem quais parâmetros de entrada e de saída devem ser criados.</span><span class="sxs-lookup"><span data-stu-id="3149c-149">The parameterized query statements define which input and output parameters must be created.</span></span> <span data-ttu-id="3149c-150">Para criar um parâmetro, use o método `Parameters.Add` ou o construtor `Parameter` para especificar o nome da coluna, o tipo de dados e o tamanho.</span><span class="sxs-lookup"><span data-stu-id="3149c-150">To create a parameter, use the `Parameters.Add` method or the `Parameter` constructor to specify the column name, data type, and size.</span></span> <span data-ttu-id="3149c-151">Para tipos de dados intrínsecos, como `Integer`, você não precisa incluir o tamanho ou pode especificar o tamanho padrão.</span><span class="sxs-lookup"><span data-stu-id="3149c-151">For intrinsic data types, such as `Integer`, you do not have to include the size, or you can specify the default size.</span></span>  
  
 <span data-ttu-id="3149c-152">O exemplo de código a seguir cria os parâmetros para uma instrução SQL e preenche um `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="3149c-152">The following code example creates the parameters for a SQL statement and then fills a `DataSet`.</span></span>  
  
## <a name="oledb-example"></a><span data-ttu-id="3149c-153">Exemplo de OleDb</span><span class="sxs-lookup"><span data-stu-id="3149c-153">OleDb Example</span></span>  
  
```vb  
' Assumes that connection is a valid OleDbConnection object.  
Dim adapter As OleDbDataAdapter = New OleDbDataAdapter   
  
Dim selectCMD AS OleDbCommand = New OleDbCommand(selectSQL, connection)  
adapter.SelectCommand = selectCMD  
  
' Add parameters and set values.  
selectCMD.Parameters.Add( _  
  "@CountryRegion", OleDbType.VarChar, 15).Value = "UK"  
selectCMD.Parameters.Add( _  
  "@City", OleDbType.VarChar, 15).Value = "London"  
  
Dim customers As DataSet = New DataSet  
adapter.Fill(customers, "Customers")  
```  
  
```csharp  
// Assumes that connection is a valid OleDbConnection object.  
OleDbDataAdapter adapter = new OleDbDataAdapter();  
  
OleDbCommand selectCMD = new OleDbCommand(selectSQL, connection);  
adapter.SelectCommand = selectCMD;  
  
// Add parameters and set values.  
selectCMD.Parameters.Add(  
  "@CountryRegion", OleDbType.VarChar, 15).Value = "UK";  
selectCMD.Parameters.Add(  
  "@City", OleDbType.VarChar, 15).Value = "London";  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
```  
  
## <a name="odbc-parameters"></a><span data-ttu-id="3149c-154">Parâmetros Odbc</span><span class="sxs-lookup"><span data-stu-id="3149c-154">Odbc Parameters</span></span>  
  
```vb  
' Assumes that connection is a valid OdbcConnection object.  
Dim adapter As OdbcDataAdapter = New OdbcDataAdapter  
  
Dim selectCMD AS OdbcCommand = New OdbcCommand(selectSQL, connection)  
adapter.SelectCommand = selectCMD  
  
' Add Parameters and set values.  
selectCMD.Parameters.Add("@CountryRegion", OdbcType.VarChar, 15).Value = "UK"  
selectCMD.Parameters.Add("@City", OdbcType.VarChar, 15).Value = "London"  
  
Dim customers As DataSet = New DataSet  
adapter.Fill(customers, "Customers")  
```  
  
```csharp  
// Assumes that connection is a valid OdbcConnection object.  
OdbcDataAdapter adapter = new OdbcDataAdapter();  
  
OdbcCommand selectCMD = new OdbcCommand(selectSQL, connection);  
adapter.SelectCommand = selectCMD;  
  
//Add Parameters and set values.  
selectCMD.Parameters.Add("@CountryRegion", OdbcType.VarChar, 15).Value = "UK";  
selectCMD.Parameters.Add("@City", OdbcType.VarChar, 15).Value = "London";  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
```  
  
> [!NOTE]
>  <span data-ttu-id="3149c-155">Se um nome de parâmetro não for fornecido para um parâmetro, o parâmetro é fornecido um nome padrão incremental de parâmetro*N* *,* começando com "Parameter1".</span><span class="sxs-lookup"><span data-stu-id="3149c-155">If a parameter name is not supplied for a parameter, the parameter is given an incremental default name of Parameter*N* *,* starting with "Parameter1".</span></span> <span data-ttu-id="3149c-156">É recomendável que você evite o parâmetro*N* convenção de nomenclatura ao fornecer um nome de parâmetro, porque o nome que você fornece pode entrar em conflito com um nome de parâmetro padrão existente no `ParameterCollection`.</span><span class="sxs-lookup"><span data-stu-id="3149c-156">We recommend that you avoid the Parameter*N* naming convention when you supply a parameter name, because the name that you supply might conflict with an existing default parameter name in the `ParameterCollection`.</span></span> <span data-ttu-id="3149c-157">Se o nome fornecido já existir, será gerada uma exceção.</span><span class="sxs-lookup"><span data-stu-id="3149c-157">If the supplied name already exists, an exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3149c-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3149c-158">See Also</span></span>  
 [<span data-ttu-id="3149c-159">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="3149c-159">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="3149c-160">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="3149c-160">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 <span data-ttu-id="3149c-161">[Updating Data Sources with DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md) (Atualizando fontes de dados com DataAdapters)</span><span class="sxs-lookup"><span data-stu-id="3149c-161">[Updating Data Sources with DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)</span></span>  
 [<span data-ttu-id="3149c-162">Modificando dados com procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="3149c-162">Modifying Data with Stored Procedures</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 <span data-ttu-id="3149c-163">[Data Type Mappings in ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md) (Mapeamentos de tipo de dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="3149c-163">[Data Type Mappings in ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)</span></span>  
 <span data-ttu-id="3149c-164">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="3149c-164">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
