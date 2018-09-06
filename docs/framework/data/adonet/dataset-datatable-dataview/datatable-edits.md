---
title: Edições de DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: 1d9321a1db4f68195fb914f271fb98f904d2f963
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43733346"
---
# <a name="datatable-edits"></a>Edições de DataTable
Quando você altera os valores de coluna em uma <xref:System.Data.DataRow>, as alterações são colocadas imediatamente no estado atual da linha. O <xref:System.Data.DataRowState> é definido como **modificado**, e as alterações são aceitas ou rejeitadas usando o <xref:System.Data.DataRow.AcceptChanges%2A> ou <xref:System.Data.DataRow.RejectChanges%2A> métodos do **DataRow**. O **DataRow** também fornece três métodos que você pode usar para suspender o estado da linha enquanto você estiver editando-lo. Esses métodos são <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A> e <xref:System.Data.DataRow.CancelEdit%2A>.  
  
 Quando você modifica os valores de coluna em uma **DataRow** diretamente, o **DataRow** gerencia os valores de coluna usando o **atual**, **padrão**, e **Original** versões de linha. Além dessas versões de linha, o **BeginEdit**, **EndEdit**, e **CancelEdit** métodos usam uma quarta versão de linha: **proposto**. Para obter mais informações sobre as versões de linha, consulte [estados de linha e versões de linha](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
 O **proposto** versão de linha existe durante uma operação de edição que começa chamando **BeginEdit** e termina usando **EndEdit** ou **CancelEdit,**  ou chamando **AcceptChanges** ou **RejectChanges**.  
  
 Durante a operação de edição, você pode aplicar lógica de validação às colunas individuais avaliando os **ProposedValue** na **ColumnChanged** evento do **DataTable**. O **ColumnChanged** evento mantém **DataColumnChangeEventArgs** que mantém uma referência para a coluna que está sendo alterada e o **ProposedValue**. Depois que você avaliar o valor proposto, poderá modificá-lo ou cancelar a edição. Quando a edição é encerrada, a linha se move do **proposto** estado.  
  
 Você pode confirmar as edições chamando **EndEdit**, ou você pode cancelá-las chamando **CancelEdit**. Observe que, embora **EndEdit** confirme suas edições, o **DataSet** só aceitará realmente as alterações até **AcceptChanges** é chamado. Observe também que, se você chamar **AcceptChanges** antes de encerrar a edição com **EndEdit** ou **CancelEdit**, a edição é encerrada e o **proposto** valores de linha são aceitas para ambos os **atual** e **Original** versões de linha. Da mesma maneira, chamando **RejectChanges** finaliza a edição e descarta o **atual** e **proposto** versões de linha. Chamando **EndEdit** ou **CancelEdit** depois de chamar **AcceptChanges** ou **RejectChanges** não tem nenhum efeito porque a edição já tem foi encerrada.  
  
 O exemplo a seguir demonstra como usar **BeginEdit** com **EndEdit** e **CancelEdit**. O exemplo também verifica se o **ProposedValue** na **ColumnChanged** eventos e decide se cancelar a edição.  
  
```vb  
Dim workTable As DataTable = New DataTable  
workTable.Columns.Add("LastName", Type.GetType("System.String"))  
  
AddHandler workTable.ColumnChanged, _  
  New DataColumnChangeEventHandler(AddressOf OnColumnChanged)  
  
Dim workRow As DataRow = workTable.NewRow()  
workRow(0) = "Smith"  
workTable.Rows.Add(workRow)  
  
workRow.BeginEdit()  
' Causes the ColumnChanged event to write a message and cancel the edit.  
workRow(0) = ""       
workRow.EndEdit()  
  
' Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow(0), workRow.RowState)  
  
Private Shared Sub OnColumnChanged( _  
  sender As Object, args As DataColumnChangeEventArgs)  
  If args.Column.ColumnName = "LastName" Then  
    If args.ProposedValue.ToString() = "" Then  
      Console.WriteLine("Last Name cannot be blank.  Edit canceled.")  
      args.Row.CancelEdit()  
    End If  
  End If  
End Sub  
```  
  
```csharp  
DataTable workTable  = new DataTable();  
workTable.Columns.Add("LastName", typeof(String));  
  
workTable.ColumnChanged +=   
  new DataColumnChangeEventHandler(OnColumnChanged);  
  
DataRow workRow = workTable.NewRow();  
workRow[0] = "Smith";  
workTable.Rows.Add(workRow);  
  
workRow.BeginEdit();  
// Causes the ColumnChanged event to write a message and cancel the edit.  
workRow[0] = "";       
workRow.EndEdit();  
  
// Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow[0], workRow.RowState);    
  
protected static void OnColumnChanged(  
  Object sender, DataColumnChangeEventArgs args)  
{  
  if (args.Column.ColumnName == "LastName")  
    if (args.ProposedValue.ToString() == "")  
    {  
      Console.WriteLine("Last Name cannot be blank. Edit canceled.");  
      args.Row.CancelEdit();  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataRowVersion>  
 [Manipulação de dados em uma DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [Manipulação de eventos de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
