---
title: Informações de erro de linha
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b1f9070-d032-48c7-b030-bd8fbb2ca59a
ms.openlocfilehash: af000d104a3b0821e69f11c1bce1392f04fe8f5e
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203225"
---
# <a name="row-error-information"></a>Informações de erro de linha
Para evitar a resposta a erros de linha durante a edição de valores <xref:System.Data.DataTable>em um, você pode adicionar as informações de erro à linha para uso posterior. O <xref:System.Data.DataRow> objeto fornece uma <xref:System.Data.DataRow.RowError%2A> Propriedade em cada linha para essa finalidade. A adição de dados à propriedade usererror de uma DataRow <xref:System.Data.DataRow.HasErrors%2A> define a propriedade da **DataRow** como **true**. Se a **DataRow** for parte de uma **DataTable**e **DataRow. HasErrors** for **true**, a propriedade **DataTable. HasErrors** também será **verdadeira**. Isso se aplica também ao **conjunto de conjuntos** ao qual a **DataTable** pertence. Ao testar erros, você pode verificar a propriedade **HasErrors** para determinar se as informações de erro foram adicionadas a qualquer linha. Se o **HasErrors** for **true**, você poderá usar <xref:System.Data.DataTable.GetErrors%2A> o método da **DataTable** para retornar e examinar apenas as linhas com erros, conforme mostrado no exemplo a seguir.  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
workTable.Columns.Add("CustID", Type.GetType("System.Int32"))  
workTable.Columns.Add("Total", Type.GetType("System.Double"))  
  
AddHandler workTable.RowChanged, New DataRowChangeEventHandler(AddressOf OnRowChanged)  
  
Dim i  As Int32  
  
For i  = 0 To 10  
  workTable.Rows.Add(New Object() {i , i *100})  
Next  
  
If workTable.HasErrors Then  
  Console.WriteLine("Errors in Table " & workTable.TableName)  
  
  Dim myRow As DataRow  
  
  For Each myRow In workTable.GetErrors()  
    Console.WriteLine("CustID = " & myRow("CustID").ToString())  
    Console.WriteLine(" Error = " & myRow.RowError & vbCrLf)  
  Next  
End If  
  
Private Shared Sub OnRowChanged( _  
    sender As Object, args As DataRowChangeEventArgs)  
  ' Check for zero values.  
  If CDbl(args.Row("Total")) = 0 Then args.Row.RowError = _  
      "Total cannot be 0."  
End Sub  
```  
  
```csharp  
DataTable  workTable = new DataTable("Customers");  
workTable.Columns.Add("CustID", typeof(Int32));  
workTable.Columns.Add("Total", typeof(Double));  
  
workTable.RowChanged += new DataRowChangeEventHandler(OnRowChanged);  
  
for (int i = 0; i < 10; i++)  
  workTable.Rows.Add(new Object[] {i, i*100});  
  
if (workTable.HasErrors)  
{  
  Console.WriteLine("Errors in Table " + workTable.TableName);  
  
  foreach (DataRow myRow in workTable.GetErrors())  
  {  
    Console.WriteLine("CustID = " + myRow["CustID"]);  
    Console.WriteLine(" Error = " + myRow.RowError + "\n");  
  }  
}  
  
protected static void OnRowChanged(  
    Object sender, DataRowChangeEventArgs args)  
{  
  // Check for zero values.  
  if (args.Row["Total"].Equals(0D))  
    args.Row.RowError = "Total cannot be 0.";  
}  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- [Manipulação de dados em uma DataTable](manipulating-data-in-a-datatable.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
