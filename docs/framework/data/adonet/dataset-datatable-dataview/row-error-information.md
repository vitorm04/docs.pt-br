---
title: Informações de erro de linha
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b1f9070-d032-48c7-b030-bd8fbb2ca59a
ms.openlocfilehash: 5ede6e2cd52ad55f8c35a42d137044dd1ceea400
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785959"
---
# <a name="row-error-information"></a><span data-ttu-id="f6ee7-102">Informações de erro de linha</span><span class="sxs-lookup"><span data-stu-id="f6ee7-102">Row Error Information</span></span>
<span data-ttu-id="f6ee7-103">Para evitar a resposta a erros de linha durante a edição de valores <xref:System.Data.DataTable>em um, você pode adicionar as informações de erro à linha para uso posterior.</span><span class="sxs-lookup"><span data-stu-id="f6ee7-103">To avoid having to respond to row errors while editing values in a <xref:System.Data.DataTable>, you can add the error information to the row for later use.</span></span> <span data-ttu-id="f6ee7-104">O <xref:System.Data.DataRow> objeto fornece uma <xref:System.Data.DataRow.RowError%2A> Propriedade em cada linha para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="f6ee7-104">The <xref:System.Data.DataRow> object provides a <xref:System.Data.DataRow.RowError%2A> property on each row for this purpose.</span></span> <span data-ttu-id="f6ee7-105">A adição de dados à propriedade **usererror** de uma **DataRow** define a <xref:System.Data.DataRow.HasErrors%2A> propriedade da **DataRow** como **true**.</span><span class="sxs-lookup"><span data-stu-id="f6ee7-105">Adding data to the **RowError** property of a **DataRow** sets the <xref:System.Data.DataRow.HasErrors%2A> property of the **DataRow** to **true**.</span></span> <span data-ttu-id="f6ee7-106">Se a **DataRow** for parte de uma **DataTable**e **DataRow. HasErrors** for **true**, a propriedade **DataTable. HasErrors** também será **verdadeira**.</span><span class="sxs-lookup"><span data-stu-id="f6ee7-106">If the **DataRow** is part of a **DataTable**, and **DataRow.HasErrors** is **true**, the **DataTable.HasErrors** property is also **true**.</span></span> <span data-ttu-id="f6ee7-107">Isso se aplica também ao **conjunto de conjuntos** ao qual a **DataTable** pertence.</span><span class="sxs-lookup"><span data-stu-id="f6ee7-107">This applies as well to the **DataSet** to which the **DataTable** belongs.</span></span> <span data-ttu-id="f6ee7-108">Ao testar erros, você pode verificar a propriedade **HasErrors** para determinar se as informações de erro foram adicionadas a qualquer linha.</span><span class="sxs-lookup"><span data-stu-id="f6ee7-108">When testing for errors, you can check the **HasErrors** property to determine if error information has been added to any rows.</span></span> <span data-ttu-id="f6ee7-109">Se o **HasErrors** for **true**, você poderá usar <xref:System.Data.DataTable.GetErrors%2A> o método da **DataTable** para retornar e examinar apenas as linhas com erros, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f6ee7-109">If **HasErrors** is **true**, you can use the <xref:System.Data.DataTable.GetErrors%2A> method of the **DataTable** to return and examine only the rows with errors, as shown in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f6ee7-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6ee7-110">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="f6ee7-111">Manipulação de dados em uma DataTable</span><span class="sxs-lookup"><span data-stu-id="f6ee7-111">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- <span data-ttu-id="f6ee7-112">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="f6ee7-112">[ADO.NET Overview](../ado-net-overview.md)</span></span>
