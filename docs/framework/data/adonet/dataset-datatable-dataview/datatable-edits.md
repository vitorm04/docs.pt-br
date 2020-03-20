---
title: Edições de DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: 9e8c4204b51121b147fc7614066d9b849a687574
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151254"
---
# <a name="datatable-edits"></a>Edições de DataTable
Quando você altera os valores de coluna em uma <xref:System.Data.DataRow>, as alterações são colocadas imediatamente no estado atual da linha. Em <xref:System.Data.DataRowState> seguida, é definido como **Modificado,** e as <xref:System.Data.DataRow.AcceptChanges%2A> <xref:System.Data.DataRow.RejectChanges%2A> alterações são aceitas ou rejeitadas usando os ou métodos do **DataRow**. O **DataRow** também fornece três métodos que você pode usar para suspender o estado da linha enquanto você está editando-a. Esses métodos são <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A> e <xref:System.Data.DataRow.CancelEdit%2A>.  
  
 Quando você modifica os valores da coluna diretamente em um **DataRow,** o **DataRow** gerencia os valores da coluna usando as versões de linha **Atual,** **Padrão**e **Original.** Além dessas versões de linha, os métodos **BeginEdit,** **EndEdit**e **CancelEdit** usam uma versão da quarta linha: **Proposta**. Para obter mais informações sobre versões de linha, consulte [Row States e Row Versions](row-states-and-row-versions.md).  
  
 A versão **de** linha proposta existe durante uma operação de edição que começa chamando **BeginEdit** e que termina usando **EndEdit** ou **CancelEdit,** ou chamando **AcceptChanges** ou **RejectChanges**.  
  
 Durante a operação de edição, você pode aplicar a lógica de validação a colunas individuais avaliando o **Evento PropostoValor** no evento **ColunaAlterar** da Tabela de **Dados**. O evento **ColunaAlterar** mantém **DataColumnChangeEventArgs** que mantém uma referência à coluna que está mudando e ao **Valor proposto**. Depois que você avaliar o valor proposto, poderá modificá-lo ou cancelar a edição. Quando a edição é terminada, a linha sai do estado **proposto.**  
  
 Você pode confirmar edições chamando **EndEdit**ou cancelá-las ligando para **CancelEdit**. Observe que, embora **o EndEdit** confirme suas edições, o **DataSet** não aceita as alterações até **que as Alterações sejam** chamadas. Observe também que se você chamar **AcceptChanges** antes de terminar a edição com **EndEdit** ou **CancelEdit,** a edição será encerrada e os valores de linha **propostos** serão aceitos para as versões de linha **Atual** e **Original.** Da mesma forma, chamar **RejectChanges** termina a edição e descarta as versões de linha **Atual** e **Proposta.** Chamar **EndEdit** ou **CancelEdit** depois de chamar **AcceptChanges** ou **RejectChanges** não tem efeito porque a edição já terminou.  
  
 O exemplo a seguir demonstra como usar **BeginEdit** com **EndEdit** e **CancelEdit**. O exemplo também verifica o **Valor proposto** no evento **ColunaAlterou** e decide se cancela a edição.  
  
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
  
## <a name="see-also"></a>Confira também

- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataRowVersion>
- [Manipulando dados em uma DataTable](manipulating-data-in-a-datatable.md)
- [Manipulação de eventos de DataTable](handling-datatable-events.md)
- [Visão geral do ADO.NET](../ado-net-overview.md)
