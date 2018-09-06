---
title: Manipulação de eventos DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
ms.openlocfilehash: 7013f855fb54f6c67c569ccabda91727359d22b2
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858620"
---
# <a name="handling-dataadapter-events"></a><span data-ttu-id="8e9ae-102">Manipulação de eventos DataAdapter</span><span class="sxs-lookup"><span data-stu-id="8e9ae-102">Handling DataAdapter Events</span></span>
<span data-ttu-id="8e9ae-103">O ADO.NET <xref:System.Data.Common.DataAdapter> expõe três eventos que você pode usar para responder a alterações feitas nos dados na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-103">The ADO.NET <xref:System.Data.Common.DataAdapter> exposes three events that you can use to respond to changes made to data at the data source.</span></span> <span data-ttu-id="8e9ae-104">A tabela a seguir mostra o `DataAdapter` eventos.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-104">The following table shows the `DataAdapter` events.</span></span>  
  
|<span data-ttu-id="8e9ae-105">evento</span><span class="sxs-lookup"><span data-stu-id="8e9ae-105">Event</span></span>|<span data-ttu-id="8e9ae-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e9ae-106">Description</span></span>|  
|-----------|-----------------|  
|`RowUpdating`|<span data-ttu-id="8e9ae-107">Uma operação UPDATE, INSERT ou DELETE em uma linha (por uma chamada para uma da `Update` métodos) está prestes a começar.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-107">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is about to begin.</span></span>|  
|`RowUpdated`|<span data-ttu-id="8e9ae-108">Uma operação UPDATE, INSERT ou DELETE em uma linha (por uma chamada para uma da `Update` métodos) é concluída.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-108">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is complete.</span></span>|  
|`FillError`|<span data-ttu-id="8e9ae-109">Ocorreu um erro durante uma `Fill` operação.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-109">An error has occurred during a `Fill` operation.</span></span>|  
  
## <a name="rowupdating-and-rowupdated"></a><span data-ttu-id="8e9ae-110">RowUpdating e RowUpdated</span><span class="sxs-lookup"><span data-stu-id="8e9ae-110">RowUpdating and RowUpdated</span></span>  
 <span data-ttu-id="8e9ae-111">`RowUpdating` é gerado antes de qualquer atualização para uma linha de <xref:System.Data.DataSet> foi processada na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-111">`RowUpdating` is raised before any update to a row from the <xref:System.Data.DataSet> has been processed at the data source.</span></span> <span data-ttu-id="8e9ae-112">`RowUpdated` é gerado depois que qualquer atualização para uma linha de `DataSet` foi processada na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-112">`RowUpdated` is raised after any update to a row from the `DataSet` has been processed at the data source.</span></span> <span data-ttu-id="8e9ae-113">Como resultado, você pode usar `RowUpdating` para modificar o comportamento de atualização antes que elas ocorram, para fornecer tratamento adicional quando ocorre uma atualização, para manter uma referência a uma linha atualizada, para cancelar a atualização atual e a agenda para um lote processar para serem processadas posteriormente , e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-113">As a result, you can use `RowUpdating` to modify update behavior before it happens, to provide additional handling when an update will occur, to retain a reference to an updated row, to cancel the current update and schedule it for a batch process to be processed later, and so on.</span></span> <span data-ttu-id="8e9ae-114">`RowUpdated` é útil para responder a erros e exceções que ocorrem durante a atualização.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-114">`RowUpdated` is useful for responding to errors and exceptions that occur during the update.</span></span> <span data-ttu-id="8e9ae-115">Você pode adicionar informações de erro para o `DataSet`, bem como a lógica de repetição e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-115">You can add error information to the `DataSet`, as well as retry logic, and so on.</span></span>  
  
 <span data-ttu-id="8e9ae-116">O <xref:System.Data.Common.RowUpdatingEventArgs> e <xref:System.Data.Common.RowUpdatedEventArgs> argumentos passados para o `RowUpdating` e `RowUpdated` eventos incluem o seguinte: uma `Command` propriedade que faz referência a `Command` do objeto que está sendo usado para executar a atualização; um `Row` propriedade que faz referência a `DataRow` objeto que contém as informações atualizadas; uma `StatementType` propriedade para o tipo de atualização está sendo executada; o `TableMapping`, se aplicável; e o `Status` da operação.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-116">The <xref:System.Data.Common.RowUpdatingEventArgs> and <xref:System.Data.Common.RowUpdatedEventArgs> arguments passed to the `RowUpdating` and `RowUpdated` events include the following: a `Command` property that references the `Command` object being used to perform the update; a `Row` property that references the `DataRow` object containing the updated information; a `StatementType` property for what type of update is being performed; the `TableMapping`, if applicable; and the `Status` of the operation.</span></span>  
  
 <span data-ttu-id="8e9ae-117">Você pode usar o `Status` propriedade para determinar se ocorreu um erro durante a operação e, se desejado, para controlar as ações em linhas atuais e resultantes.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-117">You can use the `Status` property to determine if an error has occurred during the operation and, if desired, to control the actions against the current and resulting rows.</span></span> <span data-ttu-id="8e9ae-118">Quando o evento ocorre, o `Status` propriedade for igual a `Continue` ou `ErrorsOccurred`.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-118">When the event occurs, the `Status` property equals either `Continue` or `ErrorsOccurred`.</span></span> <span data-ttu-id="8e9ae-119">A tabela a seguir mostra os valores para o qual você pode definir o `Status` propriedade a fim de controlar ações posteriores durante a atualização.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-119">The following table shows the values to which you can set the `Status` property in order to control later actions during the update.</span></span>  
  
|<span data-ttu-id="8e9ae-120">Status</span><span class="sxs-lookup"><span data-stu-id="8e9ae-120">Status</span></span>|<span data-ttu-id="8e9ae-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e9ae-121">Description</span></span>|  
|------------|-----------------|  
|`Continue`|<span data-ttu-id="8e9ae-122">Continue a operação de atualização.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-122">Continue the update operation.</span></span>|  
|`ErrorsOccurred`|<span data-ttu-id="8e9ae-123">Anule a operação de atualização e lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-123">Abort the update operation and throw an exception.</span></span>|  
|`SkipCurrentRow`|<span data-ttu-id="8e9ae-124">Ignorar a linha atual e continuar a operação de atualização.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-124">Ignore the current row and continue the update operation.</span></span>|  
|`SkipAllRemainingRows`|<span data-ttu-id="8e9ae-125">Anular a operação de atualização, mas não lance uma exceção.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-125">Abort the update operation but do not throw an exception.</span></span>|  
  
 <span data-ttu-id="8e9ae-126">Definindo o `Status` propriedade para `ErrorsOccurred` faz com que uma exceção seja lançada.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-126">Setting the `Status` property to `ErrorsOccurred` causes an exception to be thrown.</span></span> <span data-ttu-id="8e9ae-127">Você pode controlar qual exceção é gerada, definindo o `Errors` propriedade à exceção desejada.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-127">You can control which exception is thrown by setting the `Errors` property to the desired exception.</span></span> <span data-ttu-id="8e9ae-128">Usando um dos outros valores para `Status` impede uma exceção de que está sendo gerada.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-128">Using one of the other values for `Status` prevents an exception from being thrown.</span></span>  
  
 <span data-ttu-id="8e9ae-129">Você também pode usar o `ContinueUpdateOnError` atualizado de propriedade para lidar com erros para linhas.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-129">You can also use the `ContinueUpdateOnError` property to handle errors for updated rows.</span></span> <span data-ttu-id="8e9ae-130">Se `DataAdapter.ContinueUpdateOnError` está `true`, quando uma atualização para resultados de uma linha em uma exceção é lançada, o texto da exceção é colocado no `RowError` informações de linha específica e o processamento continuará sem gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-130">If `DataAdapter.ContinueUpdateOnError` is `true`, when an update to a row results in an exception being thrown, the text of the exception is placed into the `RowError` information of the particular row, and processing continues without throwing an exception.</span></span> <span data-ttu-id="8e9ae-131">Isso permite responder a erros quando o `Update` for concluída, em contraste com o `RowUpdated` evento, que lhe permite responder a erros quando o erro for encontrado.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-131">This enables you to respond to errors when the `Update` is complete, in contrast to the `RowUpdated` event, which enables you to respond to errors when the error is encountered.</span></span>  
  
 <span data-ttu-id="8e9ae-132">O exemplo de código a seguir mostra como adicionar e remover manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-132">The following code sample shows how to both add and remove event handlers.</span></span> <span data-ttu-id="8e9ae-133">O `RowUpdating` manipulador de eventos grava um log de todos os registros excluídos com um carimbo de data / hora.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-133">The `RowUpdating` event handler writes a log of all deleted records with a time stamp.</span></span> <span data-ttu-id="8e9ae-134">O `RowUpdated` manipulador de eventos adiciona informações de erro para o `RowError` propriedade da linha na `DataSet`suprime a exceção e continua o processamento (espelhamento o comportamento de `ContinueUpdateOnError`  =  `true`).</span><span class="sxs-lookup"><span data-stu-id="8e9ae-134">The `RowUpdated` event handler adds error information to the `RowError` property of the row in the `DataSet`, suppresses the exception, and continues processing (mirroring the behavior of `ContinueUpdateOnError` = `true`).</span></span>  
  
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
  
## <a name="fillerror"></a><span data-ttu-id="8e9ae-135">FillError</span><span class="sxs-lookup"><span data-stu-id="8e9ae-135">FillError</span></span>  
 <span data-ttu-id="8e9ae-136">O `DataAdapter` problemas de `FillError` evento quando ocorre um erro durante uma `Fill` operação.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-136">The `DataAdapter` issues the `FillError` event when an error occurs during a `Fill` operation.</span></span> <span data-ttu-id="8e9ae-137">Esse tipo de erro normalmente ocorre quando os dados na linha que está sendo adicionado não pôde ser convertidos em um tipo .NET Framework sem perda de precisão.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-137">This type of error commonly occurs when the data in the row being added could not be converted to a .NET Framework type without some loss of precision.</span></span>  
  
 <span data-ttu-id="8e9ae-138">Se ocorrer um erro durante uma `Fill` operação, a linha atual não é adicionada para o `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-138">If an error occurs during a `Fill` operation, the current row is not added to the `DataTable`.</span></span> <span data-ttu-id="8e9ae-139">O `FillError` evento permite que você para resolver o erro e adicione a linha, ou ignorar a linha excluída e continuar o `Fill` operação.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-139">The `FillError` event enables you to resolve the error and add the row, or to ignore the excluded row and continue the `Fill` operation.</span></span>  
  
 <span data-ttu-id="8e9ae-140">O `FillErrorEventArgs` passado para o `FillError` evento pode conter várias propriedades que permitem que você deve responder e resolver erros.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-140">The `FillErrorEventArgs` passed to the `FillError` event can contain several properties that enable you to respond to and resolve errors.</span></span> <span data-ttu-id="8e9ae-141">A tabela a seguir mostra as propriedades do `FillErrorEventArgs` objeto.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-141">The following table shows the properties of the `FillErrorEventArgs` object.</span></span>  
  
|<span data-ttu-id="8e9ae-142">Propriedade</span><span class="sxs-lookup"><span data-stu-id="8e9ae-142">Property</span></span>|<span data-ttu-id="8e9ae-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e9ae-143">Description</span></span>|  
|--------------|-----------------|  
|`Errors`|<span data-ttu-id="8e9ae-144">O `Exception` que ocorreu.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-144">The `Exception` that occurred.</span></span>|  
|`DataTable`|<span data-ttu-id="8e9ae-145">O `DataTable` do objeto que está sendo preenchido quando o erro ocorreu.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-145">The `DataTable` object being filled when the error occurred.</span></span>|  
|`Values`|<span data-ttu-id="8e9ae-146">Uma matriz de objetos que contém os valores da linha que está sendo adicionado quando o erro ocorreu.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-146">An array of objects that contains the values of the row being added when the error occurred.</span></span> <span data-ttu-id="8e9ae-147">O ordinal de referências a `Values` matriz correspondem às referências ordinais das colunas da linha que está sendo adicionado.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-147">The ordinal references of the `Values` array correspond to the ordinal references of the columns of the row being added.</span></span> <span data-ttu-id="8e9ae-148">Por exemplo, `Values[0]` é o valor que estava sendo adicionado como a primeira coluna da linha.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-148">For example, `Values[0]` is the value that was being added as the first column of the row.</span></span>|  
|`Continue`|<span data-ttu-id="8e9ae-149">Permite que você escolha se deseja ou não lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-149">Allows you to choose whether or not to throw an exception.</span></span> <span data-ttu-id="8e9ae-150">Definindo o `Continue` propriedade para `false` interromperá atual `Fill` operação e uma exceção serão lançada.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-150">Setting the `Continue` property to `false` will halt the current `Fill` operation, and an exception will be thrown.</span></span> <span data-ttu-id="8e9ae-151">Definindo `Continue` à `true` continua a `Fill` operação, apesar do erro.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-151">Setting `Continue` to `true` continues the `Fill` operation despite the error.</span></span>|  
  
 <span data-ttu-id="8e9ae-152">O exemplo de código a seguir adiciona um manipulador de eventos para o `FillError` eventos do `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-152">The following code example adds an event handler for the `FillError` event of the `DataAdapter`.</span></span> <span data-ttu-id="8e9ae-153">No `FillError` código de evento, o exemplo determina se há o potencial de perda de precisão, fornecendo a oportunidade de responder à exceção.</span><span class="sxs-lookup"><span data-stu-id="8e9ae-153">In the `FillError` event code, the example determines if there is the potential for precision loss, providing the opportunity to respond to the exception.</span></span>  
  
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
    args.RowError = _  
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
    args.RowError =   
       "OverflowException Encountered. Value from data source: " +  
       args.Values[2];  
    args.Continue = true;  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="8e9ae-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e9ae-154">See Also</span></span>  
 [<span data-ttu-id="8e9ae-155">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="8e9ae-155">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 <span data-ttu-id="8e9ae-156">[Handling DataSet Events](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md) (Manipulando eventos do DataSet)</span><span class="sxs-lookup"><span data-stu-id="8e9ae-156">[Handling DataSet Events](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)</span></span>  
 [<span data-ttu-id="8e9ae-157">Manipulação de eventos de DataTable</span><span class="sxs-lookup"><span data-stu-id="8e9ae-157">Handling DataTable Events</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [<span data-ttu-id="8e9ae-158">Eventos</span><span class="sxs-lookup"><span data-stu-id="8e9ae-158">Events</span></span>](../../../../docs/standard/events/index.md)  
 <span data-ttu-id="8e9ae-159">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="8e9ae-159">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
