---
title: Executando operações em lote usando DataAdapters
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e72ed5af-b24f-486c-8429-c8fd2208f844
ms.openlocfilehash: bb3f35f17b2dd451b41035c8e34f7b3a886a26e8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178120"
---
# <a name="performing-batch-operations-using-dataadapters"></a><span data-ttu-id="9300f-102">Executando operações em lote usando DataAdapters</span><span class="sxs-lookup"><span data-stu-id="9300f-102">Performing Batch Operations Using DataAdapters</span></span>
<span data-ttu-id="9300f-103">O suporte a lotes no ADO.NET permite que um <xref:System.Data.Common.DataAdapter> agrupe operações INSERT, UPDATE e DELETE de um <xref:System.Data.DataSet> ou <xref:System.Data.DataTable> para o servidor, em vez de enviar uma operação de cada vez.</span><span class="sxs-lookup"><span data-stu-id="9300f-103">Batch support in ADO.NET allows a <xref:System.Data.Common.DataAdapter> to group INSERT, UPDATE, and DELETE operations from a <xref:System.Data.DataSet> or <xref:System.Data.DataTable> to the server, instead of sending one operation at a time.</span></span> <span data-ttu-id="9300f-104">A redução no número de viagens de ida e volta para o servidor costuma resultar em ganhos significativos de desempenho.</span><span class="sxs-lookup"><span data-stu-id="9300f-104">The reduction in the number of round trips to the server typically results in significant performance gains.</span></span> <span data-ttu-id="9300f-105">Atualizações em lotes têm suporte nos provedores de dados .NET para SQL Server (<xref:System.Data.SqlClient>) e Oracle (<xref:System.Data.OracleClient>).</span><span class="sxs-lookup"><span data-stu-id="9300f-105">Batch updates are supported for the .NET data providers for SQL Server (<xref:System.Data.SqlClient>) and Oracle (<xref:System.Data.OracleClient>).</span></span>  
  
 <span data-ttu-id="9300f-106">Ao atualizar um banco de dados com alterações de um <xref:System.Data.DataSet> em versões anteriores do ADO.NET, o método `Update` de um `DataAdapter` executava atualizações no banco de dados em uma linha por vez.</span><span class="sxs-lookup"><span data-stu-id="9300f-106">When updating a database with changes from a <xref:System.Data.DataSet> in previous versions of ADO.NET, the `Update` method of a `DataAdapter` performed updates to the database one row at a time.</span></span> <span data-ttu-id="9300f-107">Ao iterar pelas linhas no <xref:System.Data.DataTable> especificado, ele revisava cada <xref:System.Data.DataRow> para verificar se ocorreram modificações.</span><span class="sxs-lookup"><span data-stu-id="9300f-107">As it iterated through the rows in the specified <xref:System.Data.DataTable>, it examined each <xref:System.Data.DataRow> to see if it had been modified.</span></span> <span data-ttu-id="9300f-108">Se a linha tivesse sido alterada, ele chamava o `UpdateCommand`, `InsertCommand` ou `DeleteCommand` apropriado, dependendo do valor da propriedade <xref:System.Data.DataRow.RowState%2A> para essa linha.</span><span class="sxs-lookup"><span data-stu-id="9300f-108">If the row had been modified, it called the appropriate `UpdateCommand`, `InsertCommand`, or `DeleteCommand`, depending on the value of the <xref:System.Data.DataRow.RowState%2A> property for that row.</span></span> <span data-ttu-id="9300f-109">Cada atualização de linha envolvia uma viagem de ida e volta da rede ao banco de dados.</span><span class="sxs-lookup"><span data-stu-id="9300f-109">Every row update involved a network round-trip to the database.</span></span>  
  
 <span data-ttu-id="9300f-110">A partir do ADO.NET 2.0, o <xref:System.Data.Common.DbDataAdapter> expõe uma propriedade <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="9300f-110">Starting with ADO.NET 2.0, the <xref:System.Data.Common.DbDataAdapter> exposes an <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> property.</span></span> <span data-ttu-id="9300f-111">Definir o `UpdateBatchSize` com um valor inteiro positivo causa o envio de atualizações do banco de dados como lotes de tamanho especificado.</span><span class="sxs-lookup"><span data-stu-id="9300f-111">Setting the `UpdateBatchSize` to a positive integer value causes updates to the database to be sent as batches of the specified size.</span></span> <span data-ttu-id="9300f-112">Por exemplo, a definição do `UpdateBatchSize` como 10 agrupará 10 instruções separadas e as submeterá como um único lote.</span><span class="sxs-lookup"><span data-stu-id="9300f-112">For example, setting the `UpdateBatchSize` to 10 will group 10 separate statements and submit them as single batch.</span></span> <span data-ttu-id="9300f-113">Definir o `UpdateBatchSize` como 0 fará com que o <xref:System.Data.Common.DataAdapter> use o maior tamanho de lotes que o servidor possa manipular.</span><span class="sxs-lookup"><span data-stu-id="9300f-113">Setting the `UpdateBatchSize` to 0 will cause the <xref:System.Data.Common.DataAdapter> to use the largest batch size that the server can handle.</span></span> <span data-ttu-id="9300f-114">Defini-lo como 1 desabilitará atualizações em lotes, pois as linhas são enviadas uma de cada vez.</span><span class="sxs-lookup"><span data-stu-id="9300f-114">Setting it to 1 disables batch updates, as rows are sent one at a time.</span></span>  
  
 <span data-ttu-id="9300f-115">Executar um lote extremamente grande pode diminuir o desempenho.</span><span class="sxs-lookup"><span data-stu-id="9300f-115">Executing an extremely large batch could decrease performance.</span></span> <span data-ttu-id="9300f-116">Portanto, você deve testar para verificar qual é a melhor configuração de tamanho de lote antes de implementar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9300f-116">Therefore, you should test for the optimum batch size setting before implementing your application.</span></span>  
  
## <a name="using-the-updatebatchsize-property"></a><span data-ttu-id="9300f-117">Usando a propriedade UpdateBatchSize</span><span class="sxs-lookup"><span data-stu-id="9300f-117">Using the UpdateBatchSize Property</span></span>  
 <span data-ttu-id="9300f-118">Quando atualizações em lotes são habilitadas, o valor da propriedade <xref:System.Data.IDbCommand.UpdatedRowSource%2A> de `UpdateCommand`, de `InsertCommand` e de `DeleteCommand` do DataAdapter deve ser definido como <xref:System.Data.UpdateRowSource.None> ou <xref:System.Data.UpdateRowSource.OutputParameters>.</span><span class="sxs-lookup"><span data-stu-id="9300f-118">When batch updates are enabled, the <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of the DataAdapter's `UpdateCommand`, `InsertCommand`, and `DeleteCommand` should be set to <xref:System.Data.UpdateRowSource.None> or <xref:System.Data.UpdateRowSource.OutputParameters>.</span></span> <span data-ttu-id="9300f-119">Ao executar uma atualização em lotes, o valor da propriedade <xref:System.Data.IDbCommand.UpdatedRowSource%2A> do comando de <xref:System.Data.UpdateRowSource.FirstReturnedRecord> ou de <xref:System.Data.UpdateRowSource.Both> é inválido.</span><span class="sxs-lookup"><span data-stu-id="9300f-119">When performing a batch update, the command's <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of <xref:System.Data.UpdateRowSource.FirstReturnedRecord> or <xref:System.Data.UpdateRowSource.Both> is invalid.</span></span>  
  
 <span data-ttu-id="9300f-120">O procedimento a seguir demonstra o uso da propriedade `UpdateBatchSize`.</span><span class="sxs-lookup"><span data-stu-id="9300f-120">The following procedure demonstrates the use of the `UpdateBatchSize` property.</span></span> <span data-ttu-id="9300f-121">O procedimento leva dois argumentos, uma <xref:System.Data.DataSet> objeto que tem colunas que representam os **ProductCategoryID** e **nome** campos no **Production**tabela e um inteiro que representa o tamanho do lote (o número de linhas no lote).</span><span class="sxs-lookup"><span data-stu-id="9300f-121">The procedure takes two arguments, a <xref:System.Data.DataSet> object that has columns representing the **ProductCategoryID** and **Name** fields in the **Production.ProductCategory** table, and an integer representing the batch size (the number of rows in the batch).</span></span> <span data-ttu-id="9300f-122">O código cria um novo objeto <xref:System.Data.SqlClient.SqlDataAdapter>, definindo suas propriedades <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> e <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A>.</span><span class="sxs-lookup"><span data-stu-id="9300f-122">The code creates a new <xref:System.Data.SqlClient.SqlDataAdapter> object, setting its <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties.</span></span> <span data-ttu-id="9300f-123">O código pressupõe que o objeto <xref:System.Data.DataSet> alterou linhas.</span><span class="sxs-lookup"><span data-stu-id="9300f-123">The code assumes that the <xref:System.Data.DataSet> object has modified rows.</span></span> <span data-ttu-id="9300f-124">Ele define a propriedade `UpdateBatchSize` e executa a atualização.</span><span class="sxs-lookup"><span data-stu-id="9300f-124">It sets the `UpdateBatchSize` property and executes the update.</span></span>  
  
```vb  
Public Sub BatchUpdate( _  
  ByVal dataTable As DataTable, ByVal batchSize As Int32)  
    ' Assumes GetConnectionString() returns a valid connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    ' Connect to the AdventureWorks database.  
    Using connection As New SqlConnection(connectionString)  
        ' Create a SqlDataAdapter.  
        Dim adapter As New SqlDataAdapter()  
  
        'Set the UPDATE command and parameters.  
        adapter.UpdateCommand = New SqlCommand( _  
          "UPDATE Production.ProductCategory SET " _  
          & "Name=@Name WHERE ProductCategoryID=@ProdCatID;", _  
          connection)  
        adapter.UpdateCommand.Parameters.Add("@Name", _  
          SqlDbType.NVarChar, 50, "Name")  
        adapter.UpdateCommand.Parameters.Add("@ProdCatID",  _  
          SqlDbType.Int, 4, " ProductCategoryID ")  
        adapter.UpdateCommand.UpdatedRowSource = _  
          UpdateRowSource.None  
  
        'Set the INSERT command and parameter.  
        adapter.InsertCommand = New SqlCommand( _  
          "INSERT INTO Production.ProductCategory (Name) VALUES (@Name);", _  
  connection)  
        adapter.InsertCommand.Parameters.Add("@Name", _  
          SqlDbType.NVarChar, 50, "Name")  
        adapter.InsertCommand.UpdatedRowSource = _  
          UpdateRowSource.None  
  
        'Set the DELETE command and parameter.  
        adapter.DeleteCommand = New SqlCommand( _  
          "DELETE FROM Production.ProductCategory " _  
          & "WHERE ProductCategoryID=@ProdCatID;", connection)  
        adapter.DeleteCommand.Parameters.Add("@ProdCatID", _  
           SqlDbType.Int, 4, " ProductCategoryID ")  
        adapter.DeleteCommand.UpdatedRowSource = UpdateRowSource.None  
  
        ' Set the batch size.  
        adapter.UpdateBatchSize = batchSize  
  
        ' Execute the update.  
        adapter.Update(dataTable)  
    End Using  
End Sub  
```  
  
```csharp  
public static void BatchUpdate(DataTable dataTable,Int32 batchSize)  
{  
    // Assumes GetConnectionString() returns a valid connection string.  
    string connectionString = GetConnectionString();  
  
    // Connect to the AdventureWorks database.  
    using (SqlConnection connection = new   
      SqlConnection(connectionString))  
    {  
  
        // Create a SqlDataAdapter.  
        SqlDataAdapter adapter = new SqlDataAdapter();  
  
        // Set the UPDATE command and parameters.  
        adapter.UpdateCommand = new SqlCommand(  
            "UPDATE Production.ProductCategory SET "  
            + "Name=@Name WHERE ProductCategoryID=@ProdCatID;",   
            connection);  
        adapter.UpdateCommand.Parameters.Add("@Name",   
           SqlDbType.NVarChar, 50, "Name");  
        adapter.UpdateCommand.Parameters.Add("@ProdCatID",   
           SqlDbType.Int, 4, "ProductCategoryID");  
         adapter.UpdateCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the INSERT command and parameter.  
        adapter.InsertCommand = new SqlCommand(  
            "INSERT INTO Production.ProductCategory (Name) VALUES (@Name);",   
            connection);  
        adapter.InsertCommand.Parameters.Add("@Name",   
          SqlDbType.NVarChar, 50, "Name");  
        adapter.InsertCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the DELETE command and parameter.  
        adapter.DeleteCommand = new SqlCommand(  
            "DELETE FROM Production.ProductCategory "  
            + "WHERE ProductCategoryID=@ProdCatID;", connection);  
        adapter.DeleteCommand.Parameters.Add("@ProdCatID",   
          SqlDbType.Int, 4, "ProductCategoryID");  
        adapter.DeleteCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the batch size.  
        adapter.UpdateBatchSize = batchSize;  
  
        // Execute the update.  
        adapter.Update(dataTable);  
    }  
}  
```  
  
## <a name="handling-batch-update-related-events-and-errors"></a><span data-ttu-id="9300f-125">Manipulando eventos relativos à atualização em lotes e erros</span><span class="sxs-lookup"><span data-stu-id="9300f-125">Handling Batch Update-Related Events and Errors</span></span>  
 <span data-ttu-id="9300f-126">O **DataAdapter** tem dois eventos relativos à atualização: **RowUpdating** e **RowUpdated**.</span><span class="sxs-lookup"><span data-stu-id="9300f-126">The **DataAdapter** has two update-related events: **RowUpdating** and **RowUpdated**.</span></span> <span data-ttu-id="9300f-127">Em versões anteriores do ADO.NET, quando o processamento em lotes estava desabilitado, cada um desses eventos era gerado uma vez para cada linha processada.</span><span class="sxs-lookup"><span data-stu-id="9300f-127">In previous versions of ADO.NET, when batch processing is disabled, each of these events is generated once for each row processed.</span></span> <span data-ttu-id="9300f-128">**RowUpdating** é gerado antes que a atualização ocorra, e **RowUpdated** é gerado após a atualização do banco de dados foi concluída.</span><span class="sxs-lookup"><span data-stu-id="9300f-128">**RowUpdating** is generated before the update occurs, and **RowUpdated** is generated after the database update has been completed.</span></span>  
  
### <a name="event-behavior-changes-with-batch-updates"></a><span data-ttu-id="9300f-129">Alterações de comportamento dos eventos com atualizações em lotes</span><span class="sxs-lookup"><span data-stu-id="9300f-129">Event Behavior Changes with Batch Updates</span></span>  
 <span data-ttu-id="9300f-130">Quando o processamento em lotes está habilitado, várias linhas são atualizadas em uma única operação de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="9300f-130">When batch processing is enabled, multiple rows are updated in a single database operation.</span></span> <span data-ttu-id="9300f-131">Portanto, somente um evento `RowUpdated` ocorre para cada lote, enquanto o evento `RowUpdating` ocorre para cada linha processada.</span><span class="sxs-lookup"><span data-stu-id="9300f-131">Therefore, only one `RowUpdated` event occurs for each batch, whereas the `RowUpdating` event occurs for each row processed.</span></span> <span data-ttu-id="9300f-132">Quando o processamento em lotes está desabilitado, os dois eventos são disparados com interpolação um a um, onde um evento `RowUpdating` e um evento `RowUpdated` são disparados para uma linha e, depois, um evento `RowUpdating` e um evento `RowUpdated` são disparados para a próxima linha, até que todas as linhas sejam processadas.</span><span class="sxs-lookup"><span data-stu-id="9300f-132">When batch processing is disabled, the two events are fired with one-to-one interleaving, where one `RowUpdating` event and one `RowUpdated` event fire for a row, and then one `RowUpdating` and one `RowUpdated` event fire for the next row, until all of the rows are processed.</span></span>  
  
### <a name="accessing-updated-rows"></a><span data-ttu-id="9300f-133">Acessando linhas atualizadas</span><span class="sxs-lookup"><span data-stu-id="9300f-133">Accessing Updated Rows</span></span>  
 <span data-ttu-id="9300f-134">Quando o processamento em lotes está desabilitado, a linha que está sendo atualizada pode ser acessada usando a propriedade <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> da classe <xref:System.Data.Common.RowUpdatedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="9300f-134">When batch processing is disabled, the row being updated can be accessed using the <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> property of the <xref:System.Data.Common.RowUpdatedEventArgs> class.</span></span>  
  
 <span data-ttu-id="9300f-135">Quando o processamento em lotes está habilitado, um único evento `RowUpdated` é gerado para várias linhas.</span><span class="sxs-lookup"><span data-stu-id="9300f-135">When batch processing is enabled, a single `RowUpdated` event is generated for multiple rows.</span></span> <span data-ttu-id="9300f-136">Portanto, o valor da propriedade `Row` para cada linha é nulo.</span><span class="sxs-lookup"><span data-stu-id="9300f-136">Therefore, the value of the `Row` property for each row is null.</span></span> `RowUpdating` <span data-ttu-id="9300f-137">ainda, os eventos são gerados para cada linha.</span><span class="sxs-lookup"><span data-stu-id="9300f-137">events are still generated for each row.</span></span> <span data-ttu-id="9300f-138">O método <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> da classe <xref:System.Data.Common.RowUpdatedEventArgs> permite que você acesse as linhas processadas copiando referências às linhas em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="9300f-138">The <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method of the <xref:System.Data.Common.RowUpdatedEventArgs> class allows you to access the processed rows by copying references to the rows into an array.</span></span> <span data-ttu-id="9300f-139">Se nenhuma linha está sendo processada, `CopyToRows` gera <xref:System.ArgumentNullException>.</span><span class="sxs-lookup"><span data-stu-id="9300f-139">If no rows are being processed, `CopyToRows` throws an <xref:System.ArgumentNullException>.</span></span> <span data-ttu-id="9300f-140">Use a propriedade <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> para retornar o número de linhas processadas antes de chamar o método <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A>.</span><span class="sxs-lookup"><span data-stu-id="9300f-140">Use the <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> property to return the number of rows processed before calling the <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method.</span></span>  
  
### <a name="handling-data-errors"></a><span data-ttu-id="9300f-141">Manipulando erros de dados</span><span class="sxs-lookup"><span data-stu-id="9300f-141">Handling Data Errors</span></span>  
 <span data-ttu-id="9300f-142">A execução em lotes tem o mesmo efeito que a execução de cada instrução individual.</span><span class="sxs-lookup"><span data-stu-id="9300f-142">Batch execution has the same effect as the execution of each individual statement.</span></span> <span data-ttu-id="9300f-143">As instruções são executadas na ordem em que elas foram adicionados ao lote.</span><span class="sxs-lookup"><span data-stu-id="9300f-143">Statements are executed in the order that the statements were added to the batch.</span></span> <span data-ttu-id="9300f-144">O tratamento de erros no modo em lotes é o mesmo de quando esse modo está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="9300f-144">Errors are handled the same way in batch mode as they are when batch mode is disabled.</span></span> <span data-ttu-id="9300f-145">Cada linha é processada separadamente.</span><span class="sxs-lookup"><span data-stu-id="9300f-145">Each row is processed separately.</span></span> <span data-ttu-id="9300f-146">Somente linhas que foram processadas com êxito no banco de dados serão atualizadas na <xref:System.Data.DataRow> correspondente dentro da <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="9300f-146">Only rows that have been successfully processed in the database will be updated in the corresponding <xref:System.Data.DataRow> within the <xref:System.Data.DataTable>.</span></span>  
  
 <span data-ttu-id="9300f-147">O provedor de dados e o servidor de banco de dados back-end determinam que construções SQL têm suporte para a execução em lotes.</span><span class="sxs-lookup"><span data-stu-id="9300f-147">The data provider and the back-end database server determine which SQL constructs are supported for batch execution.</span></span> <span data-ttu-id="9300f-148">Uma exceção pode ser gerada quando uma instrução sem suporte é enviada para execução.</span><span class="sxs-lookup"><span data-stu-id="9300f-148">An exception may be thrown if a non-supported statement is submitted for execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9300f-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9300f-149">See also</span></span>

- [<span data-ttu-id="9300f-150">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="9300f-150">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="9300f-151">Atualizando fontes de dados com DataAdapters</span><span class="sxs-lookup"><span data-stu-id="9300f-151">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="9300f-152">Manipulação de eventos DataAdapter</span><span class="sxs-lookup"><span data-stu-id="9300f-152">Handling DataAdapter Events</span></span>](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)
- [<span data-ttu-id="9300f-153">Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet</span><span class="sxs-lookup"><span data-stu-id="9300f-153">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
