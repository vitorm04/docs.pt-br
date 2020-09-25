---
title: Manipulação de eventos DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
ms.openlocfilehash: a2c2dc71cc9e5c445fd05534dad5ad47fd66f436
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194720"
---
# <a name="handling-dataadapter-events"></a>Manipulação de eventos DataAdapter

O ADO.NET <xref:System.Data.Common.DataAdapter> expõe três eventos que você pode usar para responder a alterações feitas nos dados na fonte de dados. A tabela a seguir mostra os `DataAdapter` eventos.  
  
|Evento|Descrição|  
|-----------|-----------------|  
|`RowUpdating`|Uma operação de atualização, inserção ou exclusão em uma linha (por uma chamada para um dos `Update` métodos) está prestes a começar.|  
|`RowUpdated`|Uma operação de atualização, inserção ou exclusão em uma linha (por uma chamada para um dos `Update` métodos) é concluída.|  
|`FillError`|Ocorreu um erro durante uma `Fill` operação.|  
  
## <a name="rowupdating-and-rowupdated"></a>Auto-atualização e atualizado  

 `RowUpdating` é gerado antes que qualquer atualização em uma linha do <xref:System.Data.DataSet> tenha sido processada na fonte de dados. `RowUpdated` é gerado depois que qualquer atualização em uma linha do `DataSet` tiver sido processada na fonte de dados. Como resultado, você pode usar `RowUpdating` para modificar o comportamento da atualização antes que ela ocorra, para fornecer tratamento adicional quando ocorre uma atualização, para manter uma referência a uma linha atualizada, para cancelar a atualização atual e agendá-la para que um processo em lote seja processado posteriormente e assim por diante. `RowUpdated` é útil para responder a erros e exceções que ocorrem durante a atualização. Você pode adicionar informações de erro ao `DataSet` , bem como à lógica de repetição, e assim por diante.  
  
 Os <xref:System.Data.Common.RowUpdatingEventArgs> <xref:System.Data.Common.RowUpdatedEventArgs> argumentos e passados para os `RowUpdating` `RowUpdated` eventos e incluem o seguinte: uma `Command` propriedade que faz referência ao `Command` objeto que está sendo usado para executar a atualização; uma `Row` propriedade que faz referência ao `DataRow` objeto que contém as informações atualizadas; uma `StatementType` propriedade para qual tipo de atualização está sendo executada; o `TableMapping` , se aplicável; e o `Status` da operação.  
  
 Você pode usar a `Status` propriedade para determinar se ocorreu um erro durante a operação e, se desejar, para controlar as ações em relação às linhas atuais e resultantes. Quando o evento ocorre, a `Status` propriedade é igual a `Continue` ou `ErrorsOccurred` . A tabela a seguir mostra os valores para os quais você pode definir a `Status` Propriedade a fim de controlar as ações posteriores durante a atualização.  
  
|Status|Descrição|  
|------------|-----------------|  
|`Continue`|Continue a operação de atualização.|  
|`ErrorsOccurred`|Anule a operação de atualização e acione uma exceção.|  
|`SkipCurrentRow`|Ignore a linha atual e continue a operação de atualização.|  
|`SkipAllRemainingRows`|Anule a operação de atualização, mas não lance uma exceção.|  
  
 Definir a `Status` propriedade como `ErrorsOccurred` faz com que uma exceção seja gerada. Você pode controlar qual exceção é lançada definindo a `Errors` propriedade para a exceção desejada. O uso de um dos outros valores para `Status` impede que uma exceção seja gerada.  
  
 Você também pode usar a `ContinueUpdateOnError` propriedade para tratar erros de linhas atualizadas. Se `DataAdapter.ContinueUpdateOnError` for `true` , quando uma atualização para uma linha resultar em uma exceção sendo gerada, o texto da exceção será colocado nas `RowError` informações da linha específica e o processamento continuará sem gerar uma exceção. Isso permite que você responda a erros quando o `Update` estiver concluído, ao contrário do `RowUpdated` evento, que permite que você responda a erros quando o erro for encontrado.  
  
 O exemplo de código a seguir mostra como adicionar e remover manipuladores de eventos. O `RowUpdating` manipulador de eventos grava um log de todos os registros excluídos com um carimbo de data/hora. O `RowUpdated` manipulador de eventos adiciona informações de erro à `RowError` propriedade da linha no `DataSet` , suprime a exceção e continua o processamento (espelhando o comportamento de `ContinueUpdateOnError`  =  `true` ).  
  
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
  
## <a name="fillerror"></a>FillError  

 O `DataAdapter` emite o `FillError` evento quando ocorre um erro durante uma `Fill` operação. Esse tipo de erro geralmente ocorre quando os dados na linha que está sendo adicionada não podem ser convertidos em um tipo de .NET Framework sem perda de precisão.  
  
 Se ocorrer um erro durante uma `Fill` operação, a linha atual não será adicionada ao `DataTable` . O `FillError` evento permite que você resolva o erro e adicione a linha, ou ignore a linha excluída e continue a `Fill` operação.  
  
 O `FillErrorEventArgs` passado para o `FillError` evento pode conter várias propriedades que permitem que você responda e resolva erros. A tabela a seguir mostra as propriedades do `FillErrorEventArgs` objeto.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|`Errors`|O `Exception` que ocorreu.|  
|`DataTable`|O `DataTable` objeto que está sendo preenchido quando ocorreu o erro.|  
|`Values`|Uma matriz de objetos que contém os valores da linha que está sendo adicionada quando o erro ocorreu. As referências ordinais da `Values` matriz correspondem às referências ordinais das colunas da linha que está sendo adicionada. Por exemplo, `Values[0]` é o valor que estava sendo adicionado como a primeira coluna da linha.|  
|`Continue`|Permite que você escolha se deseja ou não lançar uma exceção. Definir a `Continue` propriedade como `false` interromperá a `Fill` operação atual e uma exceção será gerada. A configuração `Continue` para `true` continuar a `Fill` operação apesar do erro.|  
  
 O exemplo de código a seguir adiciona um manipulador de eventos para o `FillError` evento do `DataAdapter` . No `FillError` código do evento, o exemplo determina se há o potencial para perda de precisão, fornecendo a oportunidade de responder à exceção.  
  
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
  
## <a name="see-also"></a>Veja também

- [DataAdapters e DataReaders](dataadapters-and-datareaders.md)
- [Manipular eventos do DataSet](./dataset-datatable-dataview/handling-dataset-events.md)
- [Manipulação de eventos de DataTable](./dataset-datatable-dataview/handling-datatable-events.md)
- [Eventos](../../../standard/events/index.md)
- [Visão geral do ADO.NET](ado-net-overview.md)
