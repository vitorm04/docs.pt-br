---
title: Manipulação de eventos DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
ms.openlocfilehash: d01198d158c4e1c64f12e8a0756c3d4e599fce74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149538"
---
# <a name="handling-dataadapter-events"></a><span data-ttu-id="5f6f5-102">Manipulação de eventos DataAdapter</span><span class="sxs-lookup"><span data-stu-id="5f6f5-102">Handling DataAdapter Events</span></span>
<span data-ttu-id="5f6f5-103">O <xref:System.Data.Common.DataAdapter> ADO.NET expõe três eventos que você pode usar para responder a alterações feitas na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-103">The ADO.NET <xref:System.Data.Common.DataAdapter> exposes three events that you can use to respond to changes made to data at the data source.</span></span> <span data-ttu-id="5f6f5-104">A tabela a `DataAdapter` seguir mostra os eventos.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-104">The following table shows the `DataAdapter` events.</span></span>  
  
|<span data-ttu-id="5f6f5-105">Evento</span><span class="sxs-lookup"><span data-stu-id="5f6f5-105">Event</span></span>|<span data-ttu-id="5f6f5-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="5f6f5-106">Description</span></span>|  
|-----------|-----------------|  
|`RowUpdating`|<span data-ttu-id="5f6f5-107">Uma operação UPDATE, INSERT ou DELETE em uma linha `Update` (por uma chamada para um dos métodos) está prestes a começar.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-107">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is about to begin.</span></span>|  
|`RowUpdated`|<span data-ttu-id="5f6f5-108">Uma operação UPDATE, INSERT ou DELETE em uma linha `Update` (por uma chamada para um dos métodos) está concluída.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-108">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is complete.</span></span>|  
|`FillError`|<span data-ttu-id="5f6f5-109">Um erro ocorreu durante `Fill` uma operação.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-109">An error has occurred during a `Fill` operation.</span></span>|  
  
## <a name="rowupdating-and-rowupdated"></a><span data-ttu-id="5f6f5-110">Atualização de linhas e linhaatualizada</span><span class="sxs-lookup"><span data-stu-id="5f6f5-110">RowUpdating and RowUpdated</span></span>  
 <span data-ttu-id="5f6f5-111">`RowUpdating`é levantada antes que qualquer atualização <xref:System.Data.DataSet> para uma linha da tenha sido processada na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-111">`RowUpdating` is raised before any update to a row from the <xref:System.Data.DataSet> has been processed at the data source.</span></span> <span data-ttu-id="5f6f5-112">`RowUpdated`é levantada após qualquer atualização de `DataSet` uma linha da que foi processada na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-112">`RowUpdated` is raised after any update to a row from the `DataSet` has been processed at the data source.</span></span> <span data-ttu-id="5f6f5-113">Como resultado, você `RowUpdating` pode usar para modificar o comportamento de atualização antes que ele aconteça, para fornecer tratamento adicional quando uma atualização ocorrerá, para reter uma referência a uma linha atualizada, para cancelar a atualização atual e agendar para um processo de lote a ser processado mais tarde, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-113">As a result, you can use `RowUpdating` to modify update behavior before it happens, to provide additional handling when an update will occur, to retain a reference to an updated row, to cancel the current update and schedule it for a batch process to be processed later, and so on.</span></span> <span data-ttu-id="5f6f5-114">`RowUpdated`é útil para responder a erros e exceções que ocorrem durante a atualização.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-114">`RowUpdated` is useful for responding to errors and exceptions that occur during the update.</span></span> <span data-ttu-id="5f6f5-115">Você pode adicionar informações `DataSet`de erro à lógica, bem como à lógica de repetição, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-115">You can add error information to the `DataSet`, as well as retry logic, and so on.</span></span>  
  
 <span data-ttu-id="5f6f5-116">Os <xref:System.Data.Common.RowUpdatingEventArgs> <xref:System.Data.Common.RowUpdatedEventArgs> argumentos passados `RowUpdating` `RowUpdated` para os eventos `Command` incluem: uma `Command` propriedade que faz referência ao objeto que está sendo usado para realizar a atualização; uma `Row` propriedade que `DataRow` faz referência ao objeto que contém as informações atualizadas; uma `StatementType` propriedade para que tipo de atualização está sendo realizada; o `TableMapping`, se aplicável; e `Status` a operação.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-116">The <xref:System.Data.Common.RowUpdatingEventArgs> and <xref:System.Data.Common.RowUpdatedEventArgs> arguments passed to the `RowUpdating` and `RowUpdated` events include the following: a `Command` property that references the `Command` object being used to perform the update; a `Row` property that references the `DataRow` object containing the updated information; a `StatementType` property for what type of update is being performed; the `TableMapping`, if applicable; and the `Status` of the operation.</span></span>  
  
 <span data-ttu-id="5f6f5-117">Você pode `Status` usar a propriedade para determinar se ocorreu um erro durante a operação e, se desejar, controlar as ações contra as linhas atuais e resultantes.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-117">You can use the `Status` property to determine if an error has occurred during the operation and, if desired, to control the actions against the current and resulting rows.</span></span> <span data-ttu-id="5f6f5-118">Quando o evento `Status` ocorre, a `Continue` `ErrorsOccurred`propriedade é igual a um ou .</span><span class="sxs-lookup"><span data-stu-id="5f6f5-118">When the event occurs, the `Status` property equals either `Continue` or `ErrorsOccurred`.</span></span> <span data-ttu-id="5f6f5-119">A tabela a seguir mostra os `Status` valores aos quais você pode definir a propriedade para controlar ações posteriores durante a atualização.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-119">The following table shows the values to which you can set the `Status` property in order to control later actions during the update.</span></span>  
  
|<span data-ttu-id="5f6f5-120">Status</span><span class="sxs-lookup"><span data-stu-id="5f6f5-120">Status</span></span>|<span data-ttu-id="5f6f5-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="5f6f5-121">Description</span></span>|  
|------------|-----------------|  
|`Continue`|<span data-ttu-id="5f6f5-122">Continue a operação de atualização.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-122">Continue the update operation.</span></span>|  
|`ErrorsOccurred`|<span data-ttu-id="5f6f5-123">Abortar a operação de atualização e abrir uma exceção.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-123">Abort the update operation and throw an exception.</span></span>|  
|`SkipCurrentRow`|<span data-ttu-id="5f6f5-124">Ignore a linha atual e continue a operação de atualização.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-124">Ignore the current row and continue the update operation.</span></span>|  
|`SkipAllRemainingRows`|<span data-ttu-id="5f6f5-125">Aborte a operação de atualização, mas não lance uma exceção.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-125">Abort the update operation but do not throw an exception.</span></span>|  
  
 <span data-ttu-id="5f6f5-126">Definir `Status` a `ErrorsOccurred` propriedade para fazer com que uma exceção seja lançada.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-126">Setting the `Status` property to `ErrorsOccurred` causes an exception to be thrown.</span></span> <span data-ttu-id="5f6f5-127">Você pode controlar qual exceção `Errors` é lançada definindo a propriedade para a exceção desejada.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-127">You can control which exception is thrown by setting the `Errors` property to the desired exception.</span></span> <span data-ttu-id="5f6f5-128">Usar um dos outros `Status` valores para evitar que uma exceção seja lançada.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-128">Using one of the other values for `Status` prevents an exception from being thrown.</span></span>  
  
 <span data-ttu-id="5f6f5-129">Você também pode `ContinueUpdateOnError` usar a propriedade para lidar com erros para linhas atualizadas.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-129">You can also use the `ContinueUpdateOnError` property to handle errors for updated rows.</span></span> <span data-ttu-id="5f6f5-130">Se `DataAdapter.ContinueUpdateOnError` `true`for , quando uma atualização para uma linha resulta em uma `RowError` exceção sendo lançada, o texto da exceção é colocado nas informações da linha específica, e o processamento continua sem lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-130">If `DataAdapter.ContinueUpdateOnError` is `true`, when an update to a row results in an exception being thrown, the text of the exception is placed into the `RowError` information of the particular row, and processing continues without throwing an exception.</span></span> <span data-ttu-id="5f6f5-131">Isso permite que você responda a erros quando o `Update` evento estiver concluído, em contraste com o evento, o `RowUpdated` que permite que você responda a erros quando o erro é encontrado.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-131">This enables you to respond to errors when the `Update` is complete, in contrast to the `RowUpdated` event, which enables you to respond to errors when the error is encountered.</span></span>  
  
 <span data-ttu-id="5f6f5-132">A amostra de código a seguir mostra como adicionar e remover manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-132">The following code sample shows how to both add and remove event handlers.</span></span> <span data-ttu-id="5f6f5-133">O `RowUpdating` manipulador de eventos grava um registro de todos os registros excluídos com um carimbo de hora.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-133">The `RowUpdating` event handler writes a log of all deleted records with a time stamp.</span></span> <span data-ttu-id="5f6f5-134">O `RowUpdated` manipulador de eventos `RowError` adiciona informações de `DataSet`erro à propriedade da linha no , suprime `ContinueUpdateOnError`  =  `true`a exceção e continua processando (espelhando o comportamento de ).</span><span class="sxs-lookup"><span data-stu-id="5f6f5-134">The `RowUpdated` event handler adds error information to the `RowError` property of the row in the `DataSet`, suppresses the exception, and continues processing (mirroring the behavior of `ContinueUpdateOnError` = `true`).</span></span>  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim custAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
  
' Add handlers.  
AddHandler custAdapter.RowUpdating, New SqlRowUpdatingEventHandler( _  
  AddressOf OnRowUpdating)  
AddHandler custAdapter.RowUpdated, New SqlRowUpdatedEventHandler(  
  AddressOf OnRowUpdated)  
  
' Set DataAdapter command properties, fill DataSet, and modify DataSet.  
  
custAdapter.Update(custDS, "Customers")  
  
' Remove handlers.  
RemoveHandler custAdapter.RowUpdating, _  
  New SqlRowUpdatingEventHandler(AddressOf OnRowUpdating)  
RemoveHandler custAdapter.RowUpdated, _  
  New SqlRowUpdatedEventHandler(AddressOf OnRowUpdated)  
  
Private Shared Sub OnRowUpdating(sender As Object, _  
  args As SqlRowUpdatingEventArgs)  
  If args.StatementType = StatementType.Delete Then  
    Dim tw As System.IO.TextWriter = _  
  System.IO.File.AppendText("Deletes.log")  
    tw.WriteLine( _  
      "{0}: Customer {1} Deleted.", DateTime.Now, args.Row(_  
      "CustomerID", DataRowVersion.Original))  
    tw.Close()  
  End If  
End Sub  
  
Private Shared Sub OnRowUpdated( _  
  sender As Object, args As SqlRowUpdatedEventArgs)  
  If args.Status = UpdateStatus.ErrorsOccurred  
    args.Status = UpdateStatus.SkipCurrentRow  
    args.Row.RowError = args.Errors.Message  
  End If  
End Sub  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
SqlDataAdapter custAdapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
  
// Add handlers.  
custAdapter.RowUpdating += new SqlRowUpdatingEventHandler(OnRowUpdating);  
custAdapter.RowUpdated += new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
// Set DataAdapter command properties, fill DataSet, modify DataSet.  
  
custAdapter.Update(custDS, "Customers");  
  
// Remove handlers.  
custAdapter.RowUpdating -= new SqlRowUpdatingEventHandler(OnRowUpdating);  
custAdapter.RowUpdated -= new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
protected static void OnRowUpdating(  
  object sender, SqlRowUpdatingEventArgs args)  
{  
  if (args.StatementType == StatementType.Delete)  
  {  
    System.IO.TextWriter tw = System.IO.File.AppendText("Deletes.log");  
    tw.WriteLine(  
      "{0}: Customer {1} Deleted.", DateTime.Now,
       args.Row["CustomerID", DataRowVersion.Original]);  
    tw.Close();  
  }  
}  
  
protected static void OnRowUpdated(  
  object sender, SqlRowUpdatedEventArgs args)  
{  
  if (args.Status == UpdateStatus.ErrorsOccurred)  
  {  
    args.Row.RowError = args.Errors.Message;  
    args.Status = UpdateStatus.SkipCurrentRow;  
  }  
}  
```  
  
## <a name="fillerror"></a><span data-ttu-id="5f6f5-135">Fillerror</span><span class="sxs-lookup"><span data-stu-id="5f6f5-135">FillError</span></span>  
 <span data-ttu-id="5f6f5-136">Os `DataAdapter` problemas `FillError` são os eventos `Fill` quando ocorre um erro durante uma operação.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-136">The `DataAdapter` issues the `FillError` event when an error occurs during a `Fill` operation.</span></span> <span data-ttu-id="5f6f5-137">Esse tipo de erro geralmente ocorre quando os dados da linha que estão sendo adicionados não podem ser convertidos em um tipo de Framework .NET sem alguma perda de precisão.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-137">This type of error commonly occurs when the data in the row being added could not be converted to a .NET Framework type without some loss of precision.</span></span>  
  
 <span data-ttu-id="5f6f5-138">Se ocorrer um `Fill` erro durante uma operação, a `DataTable`linha atual não será adicionada à .</span><span class="sxs-lookup"><span data-stu-id="5f6f5-138">If an error occurs during a `Fill` operation, the current row is not added to the `DataTable`.</span></span> <span data-ttu-id="5f6f5-139">O `FillError` evento permite que você resolva o erro e adicione a `Fill` linha, ou ignorar a linha excluída e continuar a operação.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-139">The `FillError` event enables you to resolve the error and add the row, or to ignore the excluded row and continue the `Fill` operation.</span></span>  
  
 <span data-ttu-id="5f6f5-140">O `FillErrorEventArgs` passado `FillError` para o evento pode conter várias propriedades que permitem que você responda e resolva erros.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-140">The `FillErrorEventArgs` passed to the `FillError` event can contain several properties that enable you to respond to and resolve errors.</span></span> <span data-ttu-id="5f6f5-141">A tabela a seguir `FillErrorEventArgs` mostra as propriedades do objeto.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-141">The following table shows the properties of the `FillErrorEventArgs` object.</span></span>  
  
|<span data-ttu-id="5f6f5-142">Propriedade</span><span class="sxs-lookup"><span data-stu-id="5f6f5-142">Property</span></span>|<span data-ttu-id="5f6f5-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="5f6f5-143">Description</span></span>|  
|--------------|-----------------|  
|`Errors`|<span data-ttu-id="5f6f5-144">O `Exception` que ocorreu.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-144">The `Exception` that occurred.</span></span>|  
|`DataTable`|<span data-ttu-id="5f6f5-145">O `DataTable` objeto que está sendo preenchido quando ocorreu o erro.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-145">The `DataTable` object being filled when the error occurred.</span></span>|  
|`Values`|<span data-ttu-id="5f6f5-146">Uma matriz de objetos que contém os valores da linha que estão sendo adicionados quando o erro ocorreu.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-146">An array of objects that contains the values of the row being added when the error occurred.</span></span> <span data-ttu-id="5f6f5-147">As referências ordinais da `Values` matriz correspondem às referências ordinais das colunas da linha que estão sendo adicionadas.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-147">The ordinal references of the `Values` array correspond to the ordinal references of the columns of the row being added.</span></span> <span data-ttu-id="5f6f5-148">Por exemplo, `Values[0]` é o valor que estava sendo adicionado como a primeira coluna da linha.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-148">For example, `Values[0]` is the value that was being added as the first column of the row.</span></span>|  
|`Continue`|<span data-ttu-id="5f6f5-149">Permite que você escolha se deve ou não abrir uma exceção.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-149">Allows you to choose whether or not to throw an exception.</span></span> <span data-ttu-id="5f6f5-150">A `Continue` definição `false` da propriedade `Fill` interromperá a operação atual, e uma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-150">Setting the `Continue` property to `false` will halt the current `Fill` operation, and an exception will be thrown.</span></span> <span data-ttu-id="5f6f5-151">`Continue` Configuração `true` para `Fill` continuar a operação apesar do erro.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-151">Setting `Continue` to `true` continues the `Fill` operation despite the error.</span></span>|  
  
 <span data-ttu-id="5f6f5-152">O exemplo de código a `FillError` seguir adiciona `DataAdapter`um manipulador de eventos para o evento do .</span><span class="sxs-lookup"><span data-stu-id="5f6f5-152">The following code example adds an event handler for the `FillError` event of the `DataAdapter`.</span></span> <span data-ttu-id="5f6f5-153">No `FillError` código do evento, o exemplo determina se há potencial para perda de precisão, proporcionando a oportunidade de responder à exceção.</span><span class="sxs-lookup"><span data-stu-id="5f6f5-153">In the `FillError` event code, the example determines if there is the potential for precision loss, providing the opportunity to respond to the exception.</span></span>  
  
```vb  
AddHandler adapter.FillError, New FillErrorEventHandler( _  
  AddressOf FillError)  
  
Dim dataSet As DataSet = New DataSet  
adapter.Fill(dataSet, "ThisTable")  
  
Private Shared Sub FillError(sender As Object, _  
  args As FillErrorEventArgs)  
  If args.Errors.GetType() Is Type.GetType("System.OverflowException") Then  
    ' Code to handle precision loss.  
    ' Add a row to table using the values from the first two columns.  
    DataRow myRow = args.DataTable.Rows.Add(New Object() _  
      {args.Values(0), args.Values(1), DBNull.Value})  
    ' Set the RowError containing the value for the third column.  
    myRow.RowError = _  
      "OverflowException encountered. Value from data source: " & _  
      args.Values(2)  
    args.Continue = True  
  End If  
End Sub  
```  
  
```csharp  
adapter.FillError += new FillErrorEventHandler(FillError);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "ThisTable");  
  
protected static void FillError(object sender, FillErrorEventArgs args)  
{  
  if (args.Errors.GetType() == typeof(System.OverflowException))  
  {  
    // Code to handle precision loss.  
    //Add a row to table using the values from the first two columns.  
    DataRow myRow = args.DataTable.Rows.Add(new object[]  
       {args.Values[0], args.Values[1], DBNull.Value});  
    //Set the RowError containing the value for the third column.  
    myRow.RowError =
       "OverflowException Encountered. Value from data source: " +  
       args.Values[2];  
    args.Continue = true;  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="5f6f5-154">Confira também</span><span class="sxs-lookup"><span data-stu-id="5f6f5-154">See also</span></span>

- [<span data-ttu-id="5f6f5-155">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="5f6f5-155">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="5f6f5-156">Manipular eventos do DataSet</span><span class="sxs-lookup"><span data-stu-id="5f6f5-156">Handling DataSet Events</span></span>](./dataset-datatable-dataview/handling-dataset-events.md)
- [<span data-ttu-id="5f6f5-157">Manipulação de eventos de DataTable</span><span class="sxs-lookup"><span data-stu-id="5f6f5-157">Handling DataTable Events</span></span>](./dataset-datatable-dataview/handling-datatable-events.md)
- [<span data-ttu-id="5f6f5-158">Eventos</span><span class="sxs-lookup"><span data-stu-id="5f6f5-158">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="5f6f5-159">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5f6f5-159">ADO.NET Overview</span></span>](ado-net-overview.md)
