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
# <a name="handling-dataadapter-events"></a>Manipulação de eventos DataAdapter
O <xref:System.Data.Common.DataAdapter> ADO.NET expõe três eventos que você pode usar para responder a alterações feitas na fonte de dados. A tabela a `DataAdapter` seguir mostra os eventos.  
  
|Evento|Descrição|  
|-----------|-----------------|  
|`RowUpdating`|Uma operação UPDATE, INSERT ou DELETE em uma linha `Update` (por uma chamada para um dos métodos) está prestes a começar.|  
|`RowUpdated`|Uma operação UPDATE, INSERT ou DELETE em uma linha `Update` (por uma chamada para um dos métodos) está concluída.|  
|`FillError`|Um erro ocorreu durante `Fill` uma operação.|  
  
## <a name="rowupdating-and-rowupdated"></a>Atualização de linhas e linhaatualizada  
 `RowUpdating`é levantada antes que qualquer atualização <xref:System.Data.DataSet> para uma linha da tenha sido processada na fonte de dados. `RowUpdated`é levantada após qualquer atualização de `DataSet` uma linha da que foi processada na fonte de dados. Como resultado, você `RowUpdating` pode usar para modificar o comportamento de atualização antes que ele aconteça, para fornecer tratamento adicional quando uma atualização ocorrerá, para reter uma referência a uma linha atualizada, para cancelar a atualização atual e agendar para um processo de lote a ser processado mais tarde, e assim por diante. `RowUpdated`é útil para responder a erros e exceções que ocorrem durante a atualização. Você pode adicionar informações `DataSet`de erro à lógica, bem como à lógica de repetição, e assim por diante.  
  
 Os <xref:System.Data.Common.RowUpdatingEventArgs> <xref:System.Data.Common.RowUpdatedEventArgs> argumentos passados `RowUpdating` `RowUpdated` para os eventos `Command` incluem: uma `Command` propriedade que faz referência ao objeto que está sendo usado para realizar a atualização; uma `Row` propriedade que `DataRow` faz referência ao objeto que contém as informações atualizadas; uma `StatementType` propriedade para que tipo de atualização está sendo realizada; o `TableMapping`, se aplicável; e `Status` a operação.  
  
 Você pode `Status` usar a propriedade para determinar se ocorreu um erro durante a operação e, se desejar, controlar as ações contra as linhas atuais e resultantes. Quando o evento `Status` ocorre, a `Continue` `ErrorsOccurred`propriedade é igual a um ou . A tabela a seguir mostra os `Status` valores aos quais você pode definir a propriedade para controlar ações posteriores durante a atualização.  
  
|Status|Descrição|  
|------------|-----------------|  
|`Continue`|Continue a operação de atualização.|  
|`ErrorsOccurred`|Abortar a operação de atualização e abrir uma exceção.|  
|`SkipCurrentRow`|Ignore a linha atual e continue a operação de atualização.|  
|`SkipAllRemainingRows`|Aborte a operação de atualização, mas não lance uma exceção.|  
  
 Definir `Status` a `ErrorsOccurred` propriedade para fazer com que uma exceção seja lançada. Você pode controlar qual exceção `Errors` é lançada definindo a propriedade para a exceção desejada. Usar um dos outros `Status` valores para evitar que uma exceção seja lançada.  
  
 Você também pode `ContinueUpdateOnError` usar a propriedade para lidar com erros para linhas atualizadas. Se `DataAdapter.ContinueUpdateOnError` `true`for , quando uma atualização para uma linha resulta em uma `RowError` exceção sendo lançada, o texto da exceção é colocado nas informações da linha específica, e o processamento continua sem lançar uma exceção. Isso permite que você responda a erros quando o `Update` evento estiver concluído, em contraste com o evento, o `RowUpdated` que permite que você responda a erros quando o erro é encontrado.  
  
 A amostra de código a seguir mostra como adicionar e remover manipuladores de eventos. O `RowUpdating` manipulador de eventos grava um registro de todos os registros excluídos com um carimbo de hora. O `RowUpdated` manipulador de eventos `RowError` adiciona informações de `DataSet`erro à propriedade da linha no , suprime `ContinueUpdateOnError`  =  `true`a exceção e continua processando (espelhando o comportamento de ).  
  
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
  
## <a name="fillerror"></a>Fillerror  
 Os `DataAdapter` problemas `FillError` são os eventos `Fill` quando ocorre um erro durante uma operação. Esse tipo de erro geralmente ocorre quando os dados da linha que estão sendo adicionados não podem ser convertidos em um tipo de Framework .NET sem alguma perda de precisão.  
  
 Se ocorrer um `Fill` erro durante uma operação, a `DataTable`linha atual não será adicionada à . O `FillError` evento permite que você resolva o erro e adicione a `Fill` linha, ou ignorar a linha excluída e continuar a operação.  
  
 O `FillErrorEventArgs` passado `FillError` para o evento pode conter várias propriedades que permitem que você responda e resolva erros. A tabela a seguir `FillErrorEventArgs` mostra as propriedades do objeto.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|`Errors`|O `Exception` que ocorreu.|  
|`DataTable`|O `DataTable` objeto que está sendo preenchido quando ocorreu o erro.|  
|`Values`|Uma matriz de objetos que contém os valores da linha que estão sendo adicionados quando o erro ocorreu. As referências ordinais da `Values` matriz correspondem às referências ordinais das colunas da linha que estão sendo adicionadas. Por exemplo, `Values[0]` é o valor que estava sendo adicionado como a primeira coluna da linha.|  
|`Continue`|Permite que você escolha se deve ou não abrir uma exceção. A `Continue` definição `false` da propriedade `Fill` interromperá a operação atual, e uma exceção será lançada. `Continue` Configuração `true` para `Fill` continuar a operação apesar do erro.|  
  
 O exemplo de código a `FillError` seguir adiciona `DataAdapter`um manipulador de eventos para o evento do . No `FillError` código do evento, o exemplo determina se há potencial para perda de precisão, proporcionando a oportunidade de responder à exceção.  
  
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
  
## <a name="see-also"></a>Confira também

- [DataAdapters e DataReaders](dataadapters-and-datareaders.md)
- [Manipular eventos do DataSet](./dataset-datatable-dataview/handling-dataset-events.md)
- [Manipulação de eventos de DataTable](./dataset-datatable-dataview/handling-datatable-events.md)
- [Eventos](../../../standard/events/index.md)
- [Visão geral do ADO.NET](ado-net-overview.md)
