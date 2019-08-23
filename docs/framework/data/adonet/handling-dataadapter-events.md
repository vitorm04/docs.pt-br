---
title: Manipulação de eventos DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
ms.openlocfilehash: a63e65289a51a7647270a978cec11ef6bc201e45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962753"
---
# <a name="handling-dataadapter-events"></a><span data-ttu-id="baca4-102">Manipulação de eventos DataAdapter</span><span class="sxs-lookup"><span data-stu-id="baca4-102">Handling DataAdapter Events</span></span>
<span data-ttu-id="baca4-103">O ADO.NET <xref:System.Data.Common.DataAdapter> expõe três eventos que você pode usar para responder a alterações feitas nos dados na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="baca4-103">The ADO.NET <xref:System.Data.Common.DataAdapter> exposes three events that you can use to respond to changes made to data at the data source.</span></span> <span data-ttu-id="baca4-104">A tabela a seguir mostra `DataAdapter` os eventos.</span><span class="sxs-lookup"><span data-stu-id="baca4-104">The following table shows the `DataAdapter` events.</span></span>  
  
|<span data-ttu-id="baca4-105">evento</span><span class="sxs-lookup"><span data-stu-id="baca4-105">Event</span></span>|<span data-ttu-id="baca4-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="baca4-106">Description</span></span>|  
|-----------|-----------------|  
|`RowUpdating`|<span data-ttu-id="baca4-107">Uma operação de atualização, inserção ou exclusão em uma linha (por uma chamada para um dos `Update` métodos) está prestes a começar.</span><span class="sxs-lookup"><span data-stu-id="baca4-107">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is about to begin.</span></span>|  
|`RowUpdated`|<span data-ttu-id="baca4-108">Uma operação de atualização, inserção ou exclusão em uma linha (por uma chamada para um dos `Update` métodos) é concluída.</span><span class="sxs-lookup"><span data-stu-id="baca4-108">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is complete.</span></span>|  
|`FillError`|<span data-ttu-id="baca4-109">Ocorreu um erro durante uma `Fill` operação.</span><span class="sxs-lookup"><span data-stu-id="baca4-109">An error has occurred during a `Fill` operation.</span></span>|  
  
## <a name="rowupdating-and-rowupdated"></a><span data-ttu-id="baca4-110">Auto-atualização e atualizado</span><span class="sxs-lookup"><span data-stu-id="baca4-110">RowUpdating and RowUpdated</span></span>  
 <span data-ttu-id="baca4-111">`RowUpdating`é gerado antes que qualquer atualização em uma linha do <xref:System.Data.DataSet> tenha sido processada na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="baca4-111">`RowUpdating` is raised before any update to a row from the <xref:System.Data.DataSet> has been processed at the data source.</span></span> <span data-ttu-id="baca4-112">`RowUpdated`é gerado depois que qualquer atualização em uma linha do `DataSet` tiver sido processada na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="baca4-112">`RowUpdated` is raised after any update to a row from the `DataSet` has been processed at the data source.</span></span> <span data-ttu-id="baca4-113">Como resultado, você pode usar `RowUpdating` para modificar o comportamento da atualização antes que ela ocorra, para fornecer tratamento adicional quando ocorre uma atualização, para manter uma referência a uma linha atualizada, para cancelar a atualização atual e agendá-la para que um processo em lote seja processado posteriormente e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="baca4-113">As a result, you can use `RowUpdating` to modify update behavior before it happens, to provide additional handling when an update will occur, to retain a reference to an updated row, to cancel the current update and schedule it for a batch process to be processed later, and so on.</span></span> <span data-ttu-id="baca4-114">`RowUpdated`é útil para responder a erros e exceções que ocorrem durante a atualização.</span><span class="sxs-lookup"><span data-stu-id="baca4-114">`RowUpdated` is useful for responding to errors and exceptions that occur during the update.</span></span> <span data-ttu-id="baca4-115">Você pode adicionar informações de erro ao `DataSet`, bem como à lógica de repetição, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="baca4-115">You can add error information to the `DataSet`, as well as retry logic, and so on.</span></span>  
  
 <span data-ttu-id="baca4-116">Os <xref:System.Data.Common.RowUpdatingEventArgs> argumentos <xref:System.Data.Common.RowUpdatedEventArgs> e passados para os `RowUpdating` eventos `RowUpdated` e incluem o seguinte: uma `Command` propriedade que faz referência `Command` ao objeto que está sendo usado para executar a `Row` atualização; a Propriedade que faz referência `DataRow` ao objeto que contém as informações atualizadas; uma `StatementType` propriedade para qual tipo de atualização está sendo `TableMapping`executada; o, se aplicável `Status` , e o da operação.</span><span class="sxs-lookup"><span data-stu-id="baca4-116">The <xref:System.Data.Common.RowUpdatingEventArgs> and <xref:System.Data.Common.RowUpdatedEventArgs> arguments passed to the `RowUpdating` and `RowUpdated` events include the following: a `Command` property that references the `Command` object being used to perform the update; a `Row` property that references the `DataRow` object containing the updated information; a `StatementType` property for what type of update is being performed; the `TableMapping`, if applicable; and the `Status` of the operation.</span></span>  
  
 <span data-ttu-id="baca4-117">Você pode usar a `Status` propriedade para determinar se ocorreu um erro durante a operação e, se desejar, para controlar as ações em relação às linhas atuais e resultantes.</span><span class="sxs-lookup"><span data-stu-id="baca4-117">You can use the `Status` property to determine if an error has occurred during the operation and, if desired, to control the actions against the current and resulting rows.</span></span> <span data-ttu-id="baca4-118">Quando o evento ocorre, a `Status` propriedade `Continue` é igual a `ErrorsOccurred`ou.</span><span class="sxs-lookup"><span data-stu-id="baca4-118">When the event occurs, the `Status` property equals either `Continue` or `ErrorsOccurred`.</span></span> <span data-ttu-id="baca4-119">A tabela a seguir mostra os valores para os quais você pode `Status` definir a propriedade a fim de controlar as ações posteriores durante a atualização.</span><span class="sxs-lookup"><span data-stu-id="baca4-119">The following table shows the values to which you can set the `Status` property in order to control later actions during the update.</span></span>  
  
|<span data-ttu-id="baca4-120">Status</span><span class="sxs-lookup"><span data-stu-id="baca4-120">Status</span></span>|<span data-ttu-id="baca4-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="baca4-121">Description</span></span>|  
|------------|-----------------|  
|`Continue`|<span data-ttu-id="baca4-122">Continue a operação de atualização.</span><span class="sxs-lookup"><span data-stu-id="baca4-122">Continue the update operation.</span></span>|  
|`ErrorsOccurred`|<span data-ttu-id="baca4-123">Anule a operação de atualização e acione uma exceção.</span><span class="sxs-lookup"><span data-stu-id="baca4-123">Abort the update operation and throw an exception.</span></span>|  
|`SkipCurrentRow`|<span data-ttu-id="baca4-124">Ignore a linha atual e continue a operação de atualização.</span><span class="sxs-lookup"><span data-stu-id="baca4-124">Ignore the current row and continue the update operation.</span></span>|  
|`SkipAllRemainingRows`|<span data-ttu-id="baca4-125">Anule a operação de atualização, mas não lance uma exceção.</span><span class="sxs-lookup"><span data-stu-id="baca4-125">Abort the update operation but do not throw an exception.</span></span>|  
  
 <span data-ttu-id="baca4-126">Definir a `Status` Propriedade como `ErrorsOccurred` faz com que uma exceção seja gerada.</span><span class="sxs-lookup"><span data-stu-id="baca4-126">Setting the `Status` property to `ErrorsOccurred` causes an exception to be thrown.</span></span> <span data-ttu-id="baca4-127">Você pode controlar qual exceção é lançada definindo a `Errors` propriedade para a exceção desejada.</span><span class="sxs-lookup"><span data-stu-id="baca4-127">You can control which exception is thrown by setting the `Errors` property to the desired exception.</span></span> <span data-ttu-id="baca4-128">O uso de um dos outros valores `Status` para impede que uma exceção seja gerada.</span><span class="sxs-lookup"><span data-stu-id="baca4-128">Using one of the other values for `Status` prevents an exception from being thrown.</span></span>  
  
 <span data-ttu-id="baca4-129">Você também pode usar a `ContinueUpdateOnError` propriedade para tratar erros de linhas atualizadas.</span><span class="sxs-lookup"><span data-stu-id="baca4-129">You can also use the `ContinueUpdateOnError` property to handle errors for updated rows.</span></span> <span data-ttu-id="baca4-130">Se `DataAdapter.ContinueUpdateOnError` `RowError` for `true`, quando uma atualização para uma linha resultar em uma exceção sendo gerada, o texto da exceção será colocado nas informações da linha específica e o processamento continuará sem gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="baca4-130">If `DataAdapter.ContinueUpdateOnError` is `true`, when an update to a row results in an exception being thrown, the text of the exception is placed into the `RowError` information of the particular row, and processing continues without throwing an exception.</span></span> <span data-ttu-id="baca4-131">Isso permite que você responda a erros quando o `Update` estiver concluído, ao contrário do `RowUpdated` evento, que permite que você responda a erros quando o erro for encontrado.</span><span class="sxs-lookup"><span data-stu-id="baca4-131">This enables you to respond to errors when the `Update` is complete, in contrast to the `RowUpdated` event, which enables you to respond to errors when the error is encountered.</span></span>  
  
 <span data-ttu-id="baca4-132">O exemplo de código a seguir mostra como adicionar e remover manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="baca4-132">The following code sample shows how to both add and remove event handlers.</span></span> <span data-ttu-id="baca4-133">O `RowUpdating` manipulador de eventos grava um log de todos os registros excluídos com um carimbo de data/hora.</span><span class="sxs-lookup"><span data-stu-id="baca4-133">The `RowUpdating` event handler writes a log of all deleted records with a time stamp.</span></span> <span data-ttu-id="baca4-134">O `RowUpdated` manipulador de eventos adiciona informações de erro `RowError` à propriedade `DataSet`da linha no, suprime a exceção e continua o processamento (espelhando o comportamento de `ContinueUpdateOnError`  =  `true`).</span><span class="sxs-lookup"><span data-stu-id="baca4-134">The `RowUpdated` event handler adds error information to the `RowError` property of the row in the `DataSet`, suppresses the exception, and continues processing (mirroring the behavior of `ContinueUpdateOnError` = `true`).</span></span>  
  
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
  
## <a name="fillerror"></a><span data-ttu-id="baca4-135">FillError</span><span class="sxs-lookup"><span data-stu-id="baca4-135">FillError</span></span>  
 <span data-ttu-id="baca4-136">O `DataAdapter` emite o `FillError` evento quando ocorre um erro durante uma `Fill` operação.</span><span class="sxs-lookup"><span data-stu-id="baca4-136">The `DataAdapter` issues the `FillError` event when an error occurs during a `Fill` operation.</span></span> <span data-ttu-id="baca4-137">Esse tipo de erro geralmente ocorre quando os dados na linha que está sendo adicionada não podem ser convertidos em um tipo de .NET Framework sem perda de precisão.</span><span class="sxs-lookup"><span data-stu-id="baca4-137">This type of error commonly occurs when the data in the row being added could not be converted to a .NET Framework type without some loss of precision.</span></span>  
  
 <span data-ttu-id="baca4-138">Se ocorrer um erro durante uma `Fill` operação, a linha atual não será adicionada `DataTable`ao.</span><span class="sxs-lookup"><span data-stu-id="baca4-138">If an error occurs during a `Fill` operation, the current row is not added to the `DataTable`.</span></span> <span data-ttu-id="baca4-139">O `FillError` evento permite que você resolva o erro e adicione a linha, ou ignore a linha excluída e continue a `Fill` operação.</span><span class="sxs-lookup"><span data-stu-id="baca4-139">The `FillError` event enables you to resolve the error and add the row, or to ignore the excluded row and continue the `Fill` operation.</span></span>  
  
 <span data-ttu-id="baca4-140">O `FillErrorEventArgs` passado para o `FillError` evento pode conter várias propriedades que permitem que você responda e resolva erros.</span><span class="sxs-lookup"><span data-stu-id="baca4-140">The `FillErrorEventArgs` passed to the `FillError` event can contain several properties that enable you to respond to and resolve errors.</span></span> <span data-ttu-id="baca4-141">A tabela a seguir mostra as propriedades do `FillErrorEventArgs` objeto.</span><span class="sxs-lookup"><span data-stu-id="baca4-141">The following table shows the properties of the `FillErrorEventArgs` object.</span></span>  
  
|<span data-ttu-id="baca4-142">Propriedade</span><span class="sxs-lookup"><span data-stu-id="baca4-142">Property</span></span>|<span data-ttu-id="baca4-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="baca4-143">Description</span></span>|  
|--------------|-----------------|  
|`Errors`|<span data-ttu-id="baca4-144">O `Exception` que ocorreu.</span><span class="sxs-lookup"><span data-stu-id="baca4-144">The `Exception` that occurred.</span></span>|  
|`DataTable`|<span data-ttu-id="baca4-145">O `DataTable` objeto que está sendo preenchido quando ocorreu o erro.</span><span class="sxs-lookup"><span data-stu-id="baca4-145">The `DataTable` object being filled when the error occurred.</span></span>|  
|`Values`|<span data-ttu-id="baca4-146">Uma matriz de objetos que contém os valores da linha que está sendo adicionada quando o erro ocorreu.</span><span class="sxs-lookup"><span data-stu-id="baca4-146">An array of objects that contains the values of the row being added when the error occurred.</span></span> <span data-ttu-id="baca4-147">As referências ordinais da `Values` matriz correspondem às referências ordinais das colunas da linha que está sendo adicionada.</span><span class="sxs-lookup"><span data-stu-id="baca4-147">The ordinal references of the `Values` array correspond to the ordinal references of the columns of the row being added.</span></span> <span data-ttu-id="baca4-148">Por exemplo, `Values[0]` é o valor que estava sendo adicionado como a primeira coluna da linha.</span><span class="sxs-lookup"><span data-stu-id="baca4-148">For example, `Values[0]` is the value that was being added as the first column of the row.</span></span>|  
|`Continue`|<span data-ttu-id="baca4-149">Permite que você escolha se deseja ou não lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="baca4-149">Allows you to choose whether or not to throw an exception.</span></span> <span data-ttu-id="baca4-150">Definir a `Continue` Propriedade como `false` interromperá a operação `Fill` atual e uma exceção será gerada.</span><span class="sxs-lookup"><span data-stu-id="baca4-150">Setting the `Continue` property to `false` will halt the current `Fill` operation, and an exception will be thrown.</span></span> <span data-ttu-id="baca4-151">A `Continue` configuração `true` para continuar `Fill` a operação apesar do erro.</span><span class="sxs-lookup"><span data-stu-id="baca4-151">Setting `Continue` to `true` continues the `Fill` operation despite the error.</span></span>|  
  
 <span data-ttu-id="baca4-152">O exemplo de código a seguir adiciona um manipulador de `FillError` eventos para o `DataAdapter`evento do.</span><span class="sxs-lookup"><span data-stu-id="baca4-152">The following code example adds an event handler for the `FillError` event of the `DataAdapter`.</span></span> <span data-ttu-id="baca4-153">No código do evento, o exemplo determina se há o potencial para perda de precisão, fornecendo a oportunidade de responder à exceção. `FillError`</span><span class="sxs-lookup"><span data-stu-id="baca4-153">In the `FillError` event code, the example determines if there is the potential for precision loss, providing the opportunity to respond to the exception.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="baca4-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="baca4-154">See also</span></span>

- [<span data-ttu-id="baca4-155">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="baca4-155">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- <span data-ttu-id="baca4-156">[Handling DataSet Events](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md) (Manipulando eventos do DataSet)</span><span class="sxs-lookup"><span data-stu-id="baca4-156">[Handling DataSet Events](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)</span></span>
- [<span data-ttu-id="baca4-157">Manipulação de eventos de DataTable</span><span class="sxs-lookup"><span data-stu-id="baca4-157">Handling DataTable Events</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)
- [<span data-ttu-id="baca4-158">Eventos</span><span class="sxs-lookup"><span data-stu-id="baca4-158">Events</span></span>](../../../standard/events/index.md)
- <span data-ttu-id="baca4-159">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="baca4-159">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
