---
title: "Edições de DataTable"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d33bd8900c48222142a46ed2c5bd64412d2eaab5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="datatable-edits"></a>Edições de DataTable
Quando você altera os valores de coluna em uma <xref:System.Data.DataRow>, as alterações são colocadas imediatamente no estado atual da linha. O <xref:System.Data.DataRowState> é definido como **modificadas**, e as alterações são aceitas ou rejeitadas usando o <xref:System.Data.DataRow.AcceptChanges%2A> ou <xref:System.Data.DataRow.RejectChanges%2A> métodos do **DataRow**. O **DataRow** também fornece três métodos que você pode usar para suspender o estado da linha enquanto você está editando. Esses métodos são <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A> e <xref:System.Data.DataRow.CancelEdit%2A>.  
  
 Quando você modifica os valores de coluna em uma **DataRow** diretamente, o **DataRow** gerencia os valores de coluna usando o **atual**, **padrão**, e **Original** versões de linha. Além dessas versões de linha, o **BeginEdit**, **EndEdit**, e **CancelEdit** métodos usam uma versão de linha quarta: **proposta**. Para obter mais informações sobre as versões de linha, consulte [estados de linha e versões de linha](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
 O **proposta** versão de linha existe durante uma operação de edição que começa com a chamada **BeginEdit** e que termine com **EndEdit** ou **CancelEdit,**  ou chamando **AcceptChanges** ou **RejectChanges**.  
  
 Durante a operação de edição, você pode aplicar lógica de validação para colunas individuais avaliando o **ProposedValue** no **ColumnChanged** eventos do **DataTable**. O **ColumnChanged** evento contém **DataColumnChangeEventArgs** que manter uma referência para a coluna que está sendo alterado e o **ProposedValue**. Depois que você avaliar o valor proposto, poderá modificá-lo ou cancelar a edição. Quando a edição é concluída, a linha Move entre o **proposta** estado.  
  
 Você pode confirmar edições chamando **EndEdit**, ou você poderá cancelá-los chamando **CancelEdit**. Observe que, embora **EndEdit** confirmar suas edições, o **DataSet** não aceita as alterações até que realmente **AcceptChanges** é chamado. Observe também que, se você chamar **AcceptChanges** antes de você ter terminado a edição com **EndEdit** ou **CancelEdit**, a edição é encerrada e o **proposta** valores de linha são aceitos para ambos os **atual** e **Original** versões de linha. Da mesma maneira, chamando **RejectChanges** termina de editar e descarta o **atual** e **proposta** versões de linha. Chamando **EndEdit** ou **CancelEdit** depois de chamar **AcceptChanges** ou **RejectChanges** não tem nenhum efeito porque já a edição terminou.  
  
 O exemplo a seguir demonstra como usar **BeginEdit** com **EndEdit** e **CancelEdit**. O exemplo também verifica a **ProposedValue** no **ColumnChanged** eventos e decide se cancelar a edição.  
  
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
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
