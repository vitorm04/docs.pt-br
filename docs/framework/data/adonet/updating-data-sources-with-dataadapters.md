---
title: Atualizando fontes de dados com DataAdapters
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1bd9a8c-0e29-40e3-bda8-d89176b72fb1
ms.openlocfilehash: 6989204fac64fc18cae547e272f6d52004c3af69
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728824"
---
# <a name="updating-data-sources-with-dataadapters"></a><span data-ttu-id="cc691-102">Atualizando fontes de dados com DataAdapters</span><span class="sxs-lookup"><span data-stu-id="cc691-102">Updating Data Sources with DataAdapters</span></span>
<span data-ttu-id="cc691-103">O método `Update` do <xref:System.Data.Common.DataAdapter> é chamado para resolver alterações de um <xref:System.Data.DataSet> de volta para a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="cc691-103">The `Update` method of the <xref:System.Data.Common.DataAdapter> is called to resolve changes from a <xref:System.Data.DataSet> back to the data source.</span></span> <span data-ttu-id="cc691-104">O método `Update`, como o método de `Fill`, utiliza como argumentos uma instância do `DataSet` e um objeto <xref:System.Data.DataTable> opcional ou um nome de `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="cc691-104">The `Update` method, like the `Fill` method, takes as arguments an instance of a `DataSet`, and an optional <xref:System.Data.DataTable> object or `DataTable` name.</span></span> <span data-ttu-id="cc691-105">A instância do `DataSet` é o `DataSet` que contém as alterações que foram feitas, e o `DataTable` identifica a tabela da qual recuperar as alterações.</span><span class="sxs-lookup"><span data-stu-id="cc691-105">The `DataSet` instance is the `DataSet` that contains the changes that have been made, and the `DataTable` identifies the table from which to retrieve the changes.</span></span> <span data-ttu-id="cc691-106">Se nenhum `DataTable` for especificado, o primeiro `DataTable` no `DataSet` será usado.</span><span class="sxs-lookup"><span data-stu-id="cc691-106">If no `DataTable` is specified, the first `DataTable` in the `DataSet` is used.</span></span>  
  
 <span data-ttu-id="cc691-107">Quando você chama o método `Update`, o `DataAdapter` analisa as alterações que foram feitas e executa o comando apropriado (INSERT, UPDATE ou DELETE).</span><span class="sxs-lookup"><span data-stu-id="cc691-107">When you call the `Update` method, the `DataAdapter` analyzes the changes that have been made and executes the appropriate command (INSERT, UPDATE, or DELETE).</span></span> <span data-ttu-id="cc691-108">Quando o `DataAdapter` encontra uma alteração em um <xref:System.Data.DataRow>, ele usa <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> ou <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> para processar a alteração.</span><span class="sxs-lookup"><span data-stu-id="cc691-108">When the `DataAdapter` encounters a change to a <xref:System.Data.DataRow>, it uses the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, or <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> to process the change.</span></span> <span data-ttu-id="cc691-109">Isso permite que você maximize o desempenho de seu aplicativo ADO.NET especificando a sintaxe de comando em tempo de design e, quando possível, usando procedimentos armazenados.</span><span class="sxs-lookup"><span data-stu-id="cc691-109">This allows you to maximize the performance of your ADO.NET application by specifying command syntax at design time and, where possible, through the use of stored procedures.</span></span> <span data-ttu-id="cc691-110">Você deve definir explicitamente os comandos antes de chamar `Update`.</span><span class="sxs-lookup"><span data-stu-id="cc691-110">You must explicitly set the commands before calling `Update`.</span></span> <span data-ttu-id="cc691-111">Se `Update` for chamado e o comando apropriado não existir para uma atualização específica (por exemplo, nenhum `DeleteCommand` para linhas excluídas), será gerada uma exceção.</span><span class="sxs-lookup"><span data-stu-id="cc691-111">If `Update` is called and the appropriate command does not exist for a particular update (for example, no `DeleteCommand` for deleted rows), an exception is thrown.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc691-112">Se você estiver usando procedimentos armazenados do SQL Server para editar ou excluir dados usando um `DataAdapter`, não use SET NOCOUNT ON na definição do procedimento armazenado.</span><span class="sxs-lookup"><span data-stu-id="cc691-112">If you are using SQL Server stored procedures to edit or delete data using a `DataAdapter`, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="cc691-113">Isso faz com que a contagem retornada de linhas afetadas seja zero, o que o `DataAdapter` interpreta como um conflito de simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="cc691-113">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="cc691-114">Nesse caso, será gerada uma <xref:System.Data.DBConcurrencyException>.</span><span class="sxs-lookup"><span data-stu-id="cc691-114">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>  
  
 <span data-ttu-id="cc691-115">Os parâmetros do comando podem ser usados para especificar valores de entrada e saída para uma instrução SQL ou procedimento armazenado para cada linha modificada em um `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="cc691-115">Command parameters can be used to specify input and output values for an SQL statement or stored procedure for each modified row in a `DataSet`.</span></span> <span data-ttu-id="cc691-116">Para obter mais informações, consulte [parâmetros DataAdapter](../../../../docs/framework/data/adonet/dataadapter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="cc691-116">For more information, see [DataAdapter Parameters](../../../../docs/framework/data/adonet/dataadapter-parameters.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc691-117">É importante compreender a diferença entre excluir uma linha em um <xref:System.Data.DataTable> e remover a linha.</span><span class="sxs-lookup"><span data-stu-id="cc691-117">It is important to understand the difference between deleting a row in a <xref:System.Data.DataTable> and removing the row.</span></span> <span data-ttu-id="cc691-118">Quando você chama o método `Remove` ou `RemoveAt`, a linha é removida imediatamente.</span><span class="sxs-lookup"><span data-stu-id="cc691-118">When you call the `Remove` or `RemoveAt` method, the row is removed immediately.</span></span> <span data-ttu-id="cc691-119">Nenhuma linha correspondente na fonte de dados de back-end será afetada se você passar o `DataTable` ou o `DataSet` para um `DataAdapter` e chamar `Update`.</span><span class="sxs-lookup"><span data-stu-id="cc691-119">Any corresponding rows in the back end data source will not be affected if you then pass the `DataTable` or `DataSet` to a `DataAdapter` and call `Update`.</span></span> <span data-ttu-id="cc691-120">Quando você usa o método `Delete`, a linha permanece no `DataTable` e é marcada para exclusão.</span><span class="sxs-lookup"><span data-stu-id="cc691-120">When you use the `Delete` method, the row remains in the `DataTable` and is marked for deletion.</span></span> <span data-ttu-id="cc691-121">Se, em seguida, você passar o `DataTable` ou o `DataSet` para um `DataAdapter` e chamar `Update`, a linha correspondente na fonte de dados de back-end será excluída.</span><span class="sxs-lookup"><span data-stu-id="cc691-121">If you then pass the `DataTable` or `DataSet` to a `DataAdapter` and call `Update`, the corresponding row in the back end data source is deleted.</span></span>  
  
 <span data-ttu-id="cc691-122">Se seu `DataTable` mapear para ou for gerado a partir de uma única tabela do banco de dados, você poderá aproveitar o objeto <xref:System.Data.Common.DbCommandBuilder> para gerar automaticamente os objetos `DeleteCommand`, `InsertCommand` e `UpdateCommand` para o `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="cc691-122">If your `DataTable` maps to or is generated from a single database table, you can take advantage of the <xref:System.Data.Common.DbCommandBuilder> object to automatically generate the `DeleteCommand`, `InsertCommand`, and `UpdateCommand` objects for the `DataAdapter`.</span></span> <span data-ttu-id="cc691-123">Para obter mais informações, consulte [Gerando comandos com CommandBuilders](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md).</span><span class="sxs-lookup"><span data-stu-id="cc691-123">For more information, see [Generating Commands with CommandBuilders](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md).</span></span>  
  
## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a><span data-ttu-id="cc691-124">Usando UpdatedRowSource para mapear valores para um DataSet</span><span class="sxs-lookup"><span data-stu-id="cc691-124">Using UpdatedRowSource to Map Values to a DataSet</span></span>  
 <span data-ttu-id="cc691-125">Você pode controlar como os valores retornados da fonte de dados são mapeados de volta para o `DataTable` depois de uma chamada para o método Update de um `DataAdapter` usando a propriedade <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> de um objeto <xref:System.Data.Common.DbCommand>.</span><span class="sxs-lookup"><span data-stu-id="cc691-125">You can control how the values returned from the data source are mapped back to the `DataTable` following a call to the Update method of a `DataAdapter`, by using the <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> property of a <xref:System.Data.Common.DbCommand> object.</span></span> <span data-ttu-id="cc691-126">Definindo a propriedade `UpdatedRowSource` para um dos valores de enumeração de <xref:System.Data.UpdateRowSource>, você pode controlar se os parâmetros de saída retornados pelos comandos de `DataAdapter` serão ignorados ou aplicados à linha alterada no `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="cc691-126">By setting the `UpdatedRowSource` property to one of the <xref:System.Data.UpdateRowSource> enumeration values, you can control whether output parameters returned by the `DataAdapter` commands are ignored or applied to the changed row in the `DataSet`.</span></span> <span data-ttu-id="cc691-127">Você também pode especificar se a primeira linha retornada (se existir) é aplicada à linha alterada no `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="cc691-127">You can also specify whether the first returned row (if it exists) is applied to the changed row in the `DataTable`.</span></span>  
  
 <span data-ttu-id="cc691-128">A tabela a seguir descreve os diferentes valores da enumeração de `UpdateRowSource` e como eles afetam o comportamento de um comando usado com o `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="cc691-128">The following table describes the different values of the `UpdateRowSource` enumeration and how they affect the behavior of a command used with a `DataAdapter`.</span></span>  
  
|<span data-ttu-id="cc691-129">Enumeração de UpdatedRowSource</span><span class="sxs-lookup"><span data-stu-id="cc691-129">UpdatedRowSource Enumeration</span></span>|<span data-ttu-id="cc691-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="cc691-130">Description</span></span>|  
|----------------------------------|-----------------|  
|<xref:System.Data.UpdateRowSource.Both>|<span data-ttu-id="cc691-131">Os parâmetros de saída e a primeira linha de um conjunto de resultados retornado podem ser mapeados para a linha alterada no `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="cc691-131">Both the output parameters and the first row of a returned result set may be mapped to the changed row in the `DataSet`.</span></span>|  
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|<span data-ttu-id="cc691-132">Somente os dados da primeira linha de um conjunto de resultados retornado podem ser mapeados para a linha alterada no `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="cc691-132">Only the data in the first row of a returned result set may be mapped to the changed row in the `DataSet`.</span></span>|  
|<xref:System.Data.UpdateRowSource.None>|<span data-ttu-id="cc691-133">Todos os parâmetros de saída ou linhas de um conjunto de resultados retornado são ignorados.</span><span class="sxs-lookup"><span data-stu-id="cc691-133">Any output parameters or rows of a returned result set are ignored.</span></span>|  
|<xref:System.Data.UpdateRowSource.OutputParameters>|<span data-ttu-id="cc691-134">Somente os parâmetros de saída podem ser mapeados para a linha alterada no `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="cc691-134">Only output parameters may be mapped to the changed row in the `DataSet`.</span></span>|  
  
 <span data-ttu-id="cc691-135">O método `Update` resolve as alterações de volta para a fonte de dados. No entanto, outros clientes podem ter modificado dados na fonte de dados desde a última vez que você preencheu o `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="cc691-135">The `Update` method resolves your changes back to the data source; however other clients may have modified data at the data source since the last time you filled the `DataSet`.</span></span> <span data-ttu-id="cc691-136">Para atualizar seu `DataSet` com dados atuais, use o método `DataAdapter` e o método `Fill`.</span><span class="sxs-lookup"><span data-stu-id="cc691-136">To refresh your `DataSet` with current data, use the `DataAdapter` and `Fill` method.</span></span> <span data-ttu-id="cc691-137">As novas linhas serão adicionadas à tabela, e informações atualizadas serão incorporadas às linhas existentes.</span><span class="sxs-lookup"><span data-stu-id="cc691-137">New rows will be added to the table, and updated information will be incorporated into existing rows.</span></span> <span data-ttu-id="cc691-138">O método `Fill` determina se uma nova linha será adicionada ou se uma linha existente será atualizada examinando os valores de chave primária das linhas no `DataSet` e as linhas retornadas pelo `SelectCommand`.</span><span class="sxs-lookup"><span data-stu-id="cc691-138">The `Fill` method determines whether a new row will be added or an existing row will be updated by examining the primary key values of the rows in the `DataSet` and the rows returned by the `SelectCommand`.</span></span> <span data-ttu-id="cc691-139">Se o método `Fill` encontrar um valor de chave primária para uma linha no `DataSet` que corresponda a um valor de chave primária de uma linha nos resultados retornados pelo `SelectCommand`, ele atualizará a linha existente com as informações da linha retornadas pelo `SelectCommand` e definirá o <xref:System.Data.DataRow.RowState%2A> da linha existente como `Unchanged`.</span><span class="sxs-lookup"><span data-stu-id="cc691-139">If the `Fill` method encounters a primary key value for a row in the `DataSet` that matches a primary key value from a row in the results returned by the `SelectCommand`, it updates the existing row with the information from the row returned by the `SelectCommand` and sets the <xref:System.Data.DataRow.RowState%2A> of the existing row to `Unchanged`.</span></span> <span data-ttu-id="cc691-140">Se uma linha retornada pelo `SelectCommand` tiver um valor de chave primária que não corresponda a alguns dos valores de chave primária das linhas do `DataSet`, o método `Fill` adicionará uma nova linha com um `RowState` de `Unchanged`.</span><span class="sxs-lookup"><span data-stu-id="cc691-140">If a row returned by the `SelectCommand` has a primary key value that does not match any of the primary key values of the rows in the `DataSet`, the `Fill` method adds a new row with a `RowState` of `Unchanged`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc691-141">Se o `SelectCommand` retornar os resultados de um OUTER JOIN, o `DataAdapter` não definirá um valor de `PrimaryKey` para o`DataTable` resultante.</span><span class="sxs-lookup"><span data-stu-id="cc691-141">If the `SelectCommand` returns the results of an OUTER JOIN, the `DataAdapter` will not set a `PrimaryKey` value for the resulting `DataTable`.</span></span> <span data-ttu-id="cc691-142">Você deve definir o `PrimaryKey` você mesmo para garantir que as linhas duplicadas sejam resolvidas corretamente.</span><span class="sxs-lookup"><span data-stu-id="cc691-142">You must define the `PrimaryKey` yourself to ensure that duplicate rows are resolved correctly.</span></span> <span data-ttu-id="cc691-143">Para obter mais informações, consulte [definindo chaves primárias](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="cc691-143">For more information, see [Defining Primary Keys](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
 <span data-ttu-id="cc691-144">Para lidar com exceções que podem ocorrer ao chamar o `Update` método, você pode usar o `RowUpdated` eventos para responder a erros de atualização de linha conforme ocorrerem (consulte [manipulação de eventos DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)), ou você pode definir `DataAdapter.ContinueUpdateOnError` para `true` antes de chamar `Update`e responder às informações de erro armazenadas do `RowError` propriedade de uma linha específica quando a atualização for concluída (consulte [informações de erro de linha](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)).</span><span class="sxs-lookup"><span data-stu-id="cc691-144">To handle exceptions that may occur when calling the `Update` method, you can use the `RowUpdated` event to respond to row update errors as they occur (see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)), or you can set `DataAdapter.ContinueUpdateOnError` to `true` before calling `Update`, and respond to the error information stored in the `RowError` property of a particular row when the update is complete (see [Row Error Information](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)).</span></span>  
  
 <span data-ttu-id="cc691-145">**Observação** chamando `AcceptChanges` na `DataSet`, `DataTable`, ou `DataRow` fará com que todos `Original` valores para uma `DataRow` seja substituído pelo `Current` valores para o `DataRow`.</span><span class="sxs-lookup"><span data-stu-id="cc691-145">**Note** Calling `AcceptChanges` on the `DataSet`, `DataTable`, or `DataRow` will cause all `Original` values for a `DataRow` to be overwritten with the `Current` values for the `DataRow`.</span></span> <span data-ttu-id="cc691-146">Se os valores dos campos que identificam a linha como exclusiva foram modificados, depois de chamar `AcceptChanges` os valores `Original` não corresponderão mais aos valores na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="cc691-146">If the field values that identify the row as unique have been modified, after calling `AcceptChanges` the `Original` values will no longer match the values in the data source.</span></span> <span data-ttu-id="cc691-147">`AcceptChanges` é chamado automaticamente para cada linha durante uma chamada para o método Update de um `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="cc691-147">`AcceptChanges` is called automatically for each row during a call to the Update method of a `DataAdapter`.</span></span> <span data-ttu-id="cc691-148">Você pode preservar os valores originais durante uma chamada para o método Update definindo primeiro a propriedade `AcceptChangesDuringUpdate` do `DataAdapter` como false, ou criando um manipulador de eventos para o evento `RowUpdated` e definindo o <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> como <xref:System.Data.UpdateStatus.SkipCurrentRow>.</span><span class="sxs-lookup"><span data-stu-id="cc691-148">You can preserve the original values during a call to the Update method by first setting the `AcceptChangesDuringUpdate` property of the `DataAdapter` to false, or by creating an event handler for the `RowUpdated` event and setting the <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> to <xref:System.Data.UpdateStatus.SkipCurrentRow>.</span></span> <span data-ttu-id="cc691-149">Para obter mais informações, consulte [mesclando conteúdo do DataSet](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md) e [manipulação de eventos DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="cc691-149">For more information, see [Merging DataSet Contents](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md) and [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc691-150">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cc691-150">Example</span></span>  
 <span data-ttu-id="cc691-151">Os exemplos a seguir demonstram como executar atualizações em linhas modificadas definindo explicitamente o `UpdateCommand` de um `DataAdapter` e chamar seu `Update` método.</span><span class="sxs-lookup"><span data-stu-id="cc691-151">The following examples demonstrate how to perform updates to modified rows by explicitly setting the `UpdateCommand` of a `DataAdapter` and calling its `Update` method.</span></span> <span data-ttu-id="cc691-152">Observe que o parâmetro especificado na cláusula WHERE da instrução UPDATE está definido para usar o valor `Original` de `SourceColumn`.</span><span class="sxs-lookup"><span data-stu-id="cc691-152">Notice that the parameter specified in the WHERE clause of the UPDATE statement is set to use the `Original` value of the `SourceColumn`.</span></span> <span data-ttu-id="cc691-153">Isso é importante, porque o valor `Current` pode ter sido modificado e não corresponder ao valor na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="cc691-153">This is important, because the `Current` value may have been modified and may not match the value in the data source.</span></span> <span data-ttu-id="cc691-154">O valor `Original` é o valor que foi usado para popular o `DataTable` da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="cc691-154">The `Original` value is the value that was used to populate the `DataTable` from the data source.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]  
  
## <a name="autoincrement-columns"></a><span data-ttu-id="cc691-155">Colunas AutoIncrement</span><span class="sxs-lookup"><span data-stu-id="cc691-155">AutoIncrement Columns</span></span>  
 <span data-ttu-id="cc691-156">Se as tabelas de sua fonte de dados possuírem colunas de incremento automático, você poderá preencher as colunas em seu `DataSet` retornando o valor de incremento automático como um parâmetro de saída de um procedimento armazenado e mapeando esse valor para uma coluna em uma tabela, retornando o valor de incremento automático na primeira linha de um conjunto de resultados retornado por um procedimento armazenado ou instrução SQL ou usando o evento `RowUpdated` do `DataAdapter` para executar uma instrução SELECT adicional.</span><span class="sxs-lookup"><span data-stu-id="cc691-156">If the tables from your data source have auto-incrementing columns, you can fill the columns in your `DataSet` either by returning the auto-increment value as an output parameter of a stored procedure and mapping that to a column in a table, by returning the auto-increment value in the first row of a result set returned by a stored procedure or SQL statement, or by using the `RowUpdated` event of the `DataAdapter` to execute an additional SELECT statement.</span></span> <span data-ttu-id="cc691-157">Para obter mais informações e um exemplo, consulte [recuperando identidade ou valores de Autonumber](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).</span><span class="sxs-lookup"><span data-stu-id="cc691-157">For more information and an example, see [Retrieving Identity or Autonumber Values](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).</span></span>  
  
## <a name="ordering-of-inserts-updates-and-deletes"></a><span data-ttu-id="cc691-158">Ordenação de atualizações, inserções e exclusões</span><span class="sxs-lookup"><span data-stu-id="cc691-158">Ordering of Inserts, Updates, and Deletes</span></span>  
 <span data-ttu-id="cc691-159">Em muitas circunstâncias, a ordem em que as alterações feitas no `DataSet` são enviadas para a fonte de dados é importante.</span><span class="sxs-lookup"><span data-stu-id="cc691-159">In many circumstances, the order in which changes made through the `DataSet` are sent to the data source is important.</span></span> <span data-ttu-id="cc691-160">Por exemplo, se um valor de chave primária de uma linha existente for atualizado, e uma nova linha for adicionada com o novo valor de chave primária como uma chave estrangeira, é importante processar a atualização antes da inserção.</span><span class="sxs-lookup"><span data-stu-id="cc691-160">For example, if a primary key value for an existing row is updated, and a new row has been added with the new primary key value as a foreign key, it is important to process the update before the insert.</span></span>  
  
 <span data-ttu-id="cc691-161">Você pode usar o método `Select` do `DataTable` para retornar uma matriz de `DataRow` que referencie somente linhas com um `RowState` específico.</span><span class="sxs-lookup"><span data-stu-id="cc691-161">You can use the `Select` method of the `DataTable` to return a `DataRow` array that only references rows with a particular `RowState`.</span></span> <span data-ttu-id="cc691-162">Você pode passar a matriz de `DataRow` retornada para o método `Update` do `DataAdapter` para processar as linhas modificadas.</span><span class="sxs-lookup"><span data-stu-id="cc691-162">You can then pass the returned `DataRow` array to the `Update` method of the `DataAdapter` to process the modified rows.</span></span> <span data-ttu-id="cc691-163">Especificando um subconjunto de linhas a serem atualizadas, você pode controlar a ordem na qual as inserções, atualizações e exclusões são processadas.</span><span class="sxs-lookup"><span data-stu-id="cc691-163">By specifying a subset of rows to be updated, you can control the order in which inserts, updates, and deletes are processed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc691-164">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cc691-164">Example</span></span>  
 <span data-ttu-id="cc691-165">Por exemplo, o código a seguir garante que as linhas excluídas da tabela sejam processadas primeiro, em seguida as linhas atualizadas e depois as linhas inseridas.</span><span class="sxs-lookup"><span data-stu-id="cc691-165">For example, the following code ensures that the deleted rows of the table are processed first, then the updated rows, and then the inserted rows.</span></span>  
  
```vb  
Dim table As DataTable = dataSet.Tables("Customers")  
  
' First process deletes.  
dataSet.Update(table.Select(Nothing, Nothing, _  
  DataViewRowState.Deleted))  
  
' Next process updates.  
adapter.Update(table.Select(Nothing, Nothing, _  
  DataViewRowState.ModifiedCurrent))  
  
' Finally, process inserts.  
dataAdapater.Update(table.Select(Nothing, Nothing, _  
  DataViewRowState.Added))  
```  
  
```csharp  
DataTable table = dataSet.Tables["Customers"];  
  
// First process deletes.  
adapter.Update(table.Select(null, null, DataViewRowState.Deleted));  
  
// Next process updates.  
adapter.Update(table.Select(null, null,   
  DataViewRowState.ModifiedCurrent));  
  
// Finally, process inserts.  
adapter.Update(table.Select(null, null, DataViewRowState.Added));  
```  
  
## <a name="use-a-dataadapter-to-retrieve-and-update-data"></a><span data-ttu-id="cc691-166">Use um DataAdapter para recuperar e atualizar dados</span><span class="sxs-lookup"><span data-stu-id="cc691-166">Use a DataAdapter to Retrieve and Update Data</span></span>  
 <span data-ttu-id="cc691-167">Você pode usar um DataAdapter para recuperar e atualizar os dados.</span><span class="sxs-lookup"><span data-stu-id="cc691-167">You can use a DataAdapter to retrieve and update the data.</span></span>  
  
-   <span data-ttu-id="cc691-168">O exemplo usa DataAdapter.AcceptChangesDuringFill para clonar os dados no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="cc691-168">The sample uses DataAdapter.AcceptChangesDuringFill to clone the data in the database.</span></span> <span data-ttu-id="cc691-169">Se a propriedade é definida como false, AcceptChanges não é chamado ao preencher a tabela e as linhas adicionadas recentemente são tratadas como linhas inseridas.</span><span class="sxs-lookup"><span data-stu-id="cc691-169">If the property is set as false, AcceptChanges is not called when filling the table, and the newly added rows are treated as inserted rows.</span></span> <span data-ttu-id="cc691-170">Portanto, o exemplo usa essas linhas para inserir novas linhas no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="cc691-170">So, the sample uses these rows to insert the new rows into the database.</span></span>  
  
-   <span data-ttu-id="cc691-171">Os exemplos usam DataAdapter.TableMappings para definir o mapeamento entre a tabela de origem e o DataTable.</span><span class="sxs-lookup"><span data-stu-id="cc691-171">The samples uses DataAdapter.TableMappings to define the mapping between the source table and DataTable.</span></span>  
  
-   <span data-ttu-id="cc691-172">O exemplo usa DataAdapter.FillLoadOption para determinar como o adaptador preenche o DataTable do DbDataReader.</span><span class="sxs-lookup"><span data-stu-id="cc691-172">The sample uses DataAdapter.FillLoadOption to determine how the adapter fills the DataTable from the DbDataReader.</span></span> <span data-ttu-id="cc691-173">Quando você cria um DataTable, só pode gravar os dados do banco de dados na versão atual ou na versão original definindo a propriedade como LoadOption.Upsert ou LoadOption.PreserveChanges.</span><span class="sxs-lookup"><span data-stu-id="cc691-173">When you create a DataTable, you can only write the data from database to the current version or the original version by setting the property as the LoadOption.Upsert or the LoadOption.PreserveChanges.</span></span>  
  
-   <span data-ttu-id="cc691-174">O exemplo também atualizará a tabela usando DbDataAdapter.UpdateBatchSize para executar operações em lote.</span><span class="sxs-lookup"><span data-stu-id="cc691-174">The sample will also update the table by using DbDataAdapter.UpdateBatchSize to perform batch operations.</span></span>  
  
 <span data-ttu-id="cc691-175">Antes de compilar e executar o exemplo, você precisará criar o banco de dados de exemplo:</span><span class="sxs-lookup"><span data-stu-id="cc691-175">Before you compile and run the sample, you need to create the sample database:</span></span>  
  
```sql
USE [master]  
GO  
  
CREATE DATABASE [MySchool]   
  
GO  
  
USE [MySchool]  
GO  
  
SET ANSI_NULLS ON  
GO  
SET QUOTED_IDENTIFIER ON  
GO  
CREATE TABLE [dbo].[Course]([CourseID] [nvarchar](10) NOT NULL,  
[Year] [smallint] NOT NULL,  
[Title] [nvarchar](100) NOT NULL,  
[Credits] [int] NOT NULL,  
[DepartmentID] [int] NOT NULL,  
 CONSTRAINT [PK_Course] PRIMARY KEY CLUSTERED  
(  
[CourseID] ASC,  
[Year] ASC  
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]  
  
GO  
  
SET ANSI_NULLS ON  
GO  
SET QUOTED_IDENTIFIER ON  
GO  
CREATE TABLE [dbo].[Department]([DepartmentID] [int] IDENTITY(1,1) NOT NULL,  
[Name] [nvarchar](50) NOT NULL,  
[Budget] [money] NOT NULL,  
[StartDate] [datetime] NOT NULL,  
[Administrator] [int] NULL,  
 CONSTRAINT [PK_Department] PRIMARY KEY CLUSTERED  
(  
[DepartmentID] ASC  
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]  
  
GO  
  
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C1045', 2012, N'Calculus', 4, 7)  
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C1061', 2012, N'Physics', 4, 1)  
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C2021', 2012, N'Composition', 3, 2)  
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C2042', 2012, N'Literature', 4, 2)  
  
SET IDENTITY_INSERT [dbo].[Department] ON   
  
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (1, N'Engineering', 350000.0000, CAST(0x0000999C00000000 AS DateTime), 2)  
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (2, N'English', 120000.0000, CAST(0x0000999C00000000 AS DateTime), 6)  
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (4, N'Economics', 200000.0000, CAST(0x0000999C00000000 AS DateTime), 4)  
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (7, N'Mathematics', 250024.0000, CAST(0x0000999C00000000 AS DateTime), 3)  
SET IDENTITY_INSERT [dbo].[Department] OFF  
  
ALTER TABLE [dbo].[Course]  WITH CHECK ADD  CONSTRAINT [FK_Course_Department] FOREIGN KEY([DepartmentID])  
REFERENCES [dbo].[Department] ([DepartmentID])  
GO  
ALTER TABLE [dbo].[Course] CHECK CONSTRAINT [FK_Course_Department]  
GO  
```  
  
 <span data-ttu-id="cc691-176">Projetos c# e Visual Basic com este exemplo de código podem ser encontrados no [exemplos de código do desenvolvedor](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).</span><span class="sxs-lookup"><span data-stu-id="cc691-176">C# and Visual Basic projects with this code sample can be found on [Developer Code Samples](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).</span></span>  
  
```csharp
using System;  
using System.Data;  
using System.Data.Common;  
using System.Data.SqlClient;  
using System.Linq;  
using CSDataAdapterOperations.Properties;  
  
namespace CSDataAdapterOperations.Properties {  
   internal sealed partial class Settings : global::System.Configuration.ApplicationSettingsBase {  
  
      private static Settings defaultInstance = ((Settings)(global::System.Configuration.ApplicationSettingsBase.Synchronized(new Settings())));  
  
      public static Settings Default {  
         get {  
            return defaultInstance;  
         }  
      }  
  
      [global::System.Configuration.ApplicationScopedSettingAttribute()]  
      [global::System.Configuration.DefaultSettingValueAttribute("Data Source=(local);Initial Catalog=MySchool;Integrated Security=True")]  
      public string MySchoolConnectionString {  
         get {  
            return ((string)(this["MySchoolConnectionString"]));  
         }  
      }  
   }  
}  
  
class Program {  
   static void Main(string[] args) {  
      Settings settings = new Settings();  
  
      // Copy the data from the database.  Get the table Department and Course from the database.  
      String selectString = @"SELECT [DepartmentID],[Name],[Budget],[StartDate],[Administrator]  
                                     FROM [MySchool].[dbo].[Department];  
  
                                   SELECT [CourseID],@Year as [Year],Max([Title]) as [Title],  
                                   Max([Credits]) as [Credits],Max([DepartmentID]) as [DepartmentID]  
                                   FROM [MySchool].[dbo].[Course]  
                                   Group by [CourseID]";  
  
      DataSet mySchool = new DataSet();  
  
      SqlCommand selectCommand = new SqlCommand(selectString);  
      SqlParameter parameter = selectCommand.Parameters.Add("@Year", SqlDbType.SmallInt, 2);  
      parameter.Value = new Random(DateTime.Now.Millisecond).Next(9999);  
  
      // Use DataTableMapping to map the source tables and the destination tables.  
      DataTableMapping[] tableMappings = {new DataTableMapping("Table", "Department"), new DataTableMapping("Table1", "Course")};  
      CopyData(mySchool, settings.MySchoolConnectionString, selectCommand, tableMappings);  
  
      Console.WriteLine("The following tables are from the database.");  
      foreach (DataTable table in mySchool.Tables) {  
         Console.WriteLine(table.TableName);  
         ShowDataTable(table);  
      }  
  
      // Roll back the changes  
      DataTable department = mySchool.Tables["Department"];  
      DataTable course = mySchool.Tables["Course"];  
  
      department.Rows[0]["Name"] = "New" + department.Rows[0][1];  
      course.Rows[0]["Title"] = "New" + course.Rows[0]["Title"];  
      course.Rows[0]["Credits"] = 10;  
  
      Console.WriteLine("After we changed the tables:");  
      foreach (DataTable table in mySchool.Tables) {  
         Console.WriteLine(table.TableName);  
         ShowDataTable(table);  
      }  
  
      department.RejectChanges();  
      Console.WriteLine("After use the RejectChanges method in Department table to roll back the changes:");  
      ShowDataTable(department);  
  
      DataColumn[] primaryColumns = { course.Columns["CourseID"] };  
      DataColumn[] resetColumns = { course.Columns["Title"] };  
      ResetCourse(course, settings.MySchoolConnectionString, primaryColumns, resetColumns);  
      Console.WriteLine("After use the ResetCourse method in Course table to roll back the changes:");  
      ShowDataTable(course);  
  
      // Batch update the table.  
      String insertString = @"Insert into [MySchool].[dbo].[Course]([CourseID],[Year],[Title],   
                                   [Credits],[DepartmentID])   
             values (@CourseID,@Year,@Title,@Credits,@DepartmentID)";  
      SqlCommand insertCommand = new SqlCommand(insertString);  
      insertCommand.Parameters.Add("@CourseID", SqlDbType.NVarChar, 10, "CourseID");  
      insertCommand.Parameters.Add("@Year", SqlDbType.SmallInt, 2, "Year");  
      insertCommand.Parameters.Add("@Title", SqlDbType.NVarChar, 100, "Title");  
      insertCommand.Parameters.Add("@Credits", SqlDbType.Int, 4, "Credits");  
      insertCommand.Parameters.Add("@DepartmentID", SqlDbType.Int, 4, "DepartmentID");  
  
      const Int32 batchSize = 10;  
      BatchInsertUpdate(course, settings.MySchoolConnectionString, insertCommand, batchSize);  
   }  
  
   private static void CopyData(DataSet dataSet, String connectionString, SqlCommand selectCommand, DataTableMapping[] tableMappings) {  
      using (SqlConnection connection = new SqlConnection(connectionString)) {  
         selectCommand.Connection = connection;  
  
         connection.Open();  
  
         using (SqlDataAdapter adapter = new SqlDataAdapter(selectCommand)) {adapter.TableMappings.AddRange(tableMappings);  
            // If set the AcceptChangesDuringFill as the false, AcceptChanges will not be called on a   
            // DataRow after it is added to the DataTable during any of the Fill operations.  
            adapter.AcceptChangesDuringFill = false;  
  
            adapter.Fill(dataSet);  
         }  
      }  
   }  
  
   // Roll back only one column or several columns data of the Course table by call ResetDataTable method.  
   private static void ResetCourse(DataTable table, String connectionString,  
       DataColumn[] primaryColumns, DataColumn[] resetColumns) {  
      table.PrimaryKey = primaryColumns;  
  
      // Build the query string  
      String primaryCols = String.Join(",", primaryColumns.Select(col => col.ColumnName));  
      String resetCols = String.Join(",", resetColumns.Select(col => $"Max({col.ColumnName}) as {col.ColumnName}"));
  
      String selectString = $"Select {primaryCols},{resetCols} from Course Group by {primaryCols}");
  
      SqlCommand selectCommand = new SqlCommand(selectString);  
  
      ResetDataTable(table, connectionString, selectCommand);  
   }  
  
   // RejectChanges will roll back all changes made to the table since it was loaded, or the last time AcceptChanges   
   // was called. When you copy from the database, you can lose all the data after calling RejectChanges  
   // The ResetDataTable method rolls back one or more columns of data.  
   private static void ResetDataTable(DataTable table, String connectionString,  
       SqlCommand selectCommand) {  
      using (SqlConnection connection = new SqlConnection(connectionString)) {  
         selectCommand.Connection = connection;  
  
         connection.Open();  
  
         using (SqlDataAdapter adapter = new SqlDataAdapter(selectCommand)) {  
            // The incoming values for this row will be written to the current version of each   
            // column. The original version of each column's data will not be changed.  
            adapter.FillLoadOption = LoadOption.Upsert;  
  
            adapter.Fill(table);  
         }  
      }  
   }  
  
   private static void BatchInsertUpdate(DataTable table, String connectionString,  
       SqlCommand insertCommand, Int32 batchSize) {  
      using (SqlConnection connection = new SqlConnection(connectionString)) {  
         insertCommand.Connection = connection;  
         // When setting UpdateBatchSize to a value other than 1, all the commands   
         // associated with the SqlDataAdapter have to have their UpdatedRowSource   
         // property set to None or OutputParameters. An exception is thrown otherwise.  
         insertCommand.UpdatedRowSource = UpdateRowSource.None;  
  
         connection.Open();  
  
         using (SqlDataAdapter adapter = new SqlDataAdapter()) {  
            adapter.InsertCommand = insertCommand;  
            // Gets or sets the number of rows that are processed in each round-trip to the server.  
            // Setting it to 1 disables batch updates, as rows are sent one at a time.  
            adapter.UpdateBatchSize = batchSize;  
  
            adapter.Update(table);  
  
            Console.WriteLine("Successfully to update the table.");  
         }  
      }  
   }  
  
   private static void ShowDataTable(DataTable table) {  
      foreach (DataColumn col in table.Columns) {  
         Console.Write("{0,-14}", col.ColumnName);  
      }  
      Console.WriteLine("{0,-14}", "RowState");  
  
      foreach (DataRow row in table.Rows) {  
         foreach (DataColumn col in table.Columns) {  
            if (col.DataType.Equals(typeof(DateTime)))  
               Console.Write("{0,-14:d}", row[col]);  
            else if (col.DataType.Equals(typeof(Decimal)))  
               Console.Write("{0,-14:C}", row[col]);  
            else  
               Console.Write("{0,-14}", row[col]);  
         }  
         Console.WriteLine("{0,-14}", row.RowState);  
      }  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="cc691-177">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc691-177">See also</span></span>
- [<span data-ttu-id="cc691-178">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="cc691-178">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="cc691-179">Estados e versões de linha</span><span class="sxs-lookup"><span data-stu-id="cc691-179">Row States and Row Versions</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)
- [<span data-ttu-id="cc691-180">AcceptChanges e RejectChanges</span><span class="sxs-lookup"><span data-stu-id="cc691-180">AcceptChanges and RejectChanges</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)
- <span data-ttu-id="cc691-181">[Merging DataSet Contents](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md) (Mesclando o conteúdo do DataSet)</span><span class="sxs-lookup"><span data-stu-id="cc691-181">[Merging DataSet Contents](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)</span></span>
- [<span data-ttu-id="cc691-182">Recuperando identidade ou valores de Autonumber</span><span class="sxs-lookup"><span data-stu-id="cc691-182">Retrieving Identity or Autonumber Values</span></span>](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)
- <span data-ttu-id="cc691-183">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="cc691-183">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
