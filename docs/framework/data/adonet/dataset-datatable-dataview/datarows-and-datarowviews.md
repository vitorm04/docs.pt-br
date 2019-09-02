---
title: DataRows e DataRowViews
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f5eec26-b809-4aca-8778-7e202356d856
ms.openlocfilehash: 8a98dc44eda9ebda09235193c58bd831fc52d04d
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205097"
---
# <a name="datarows-and-datarowviews"></a><span data-ttu-id="ac1b6-102">DataRows e DataRowViews</span><span class="sxs-lookup"><span data-stu-id="ac1b6-102">DataRows and DataRowViews</span></span>
<span data-ttu-id="ac1b6-103">Um <xref:System.Data.DataView> expõe uma coleção enumerável <xref:System.Data.DataRowView> de objetos.</span><span class="sxs-lookup"><span data-stu-id="ac1b6-103">A <xref:System.Data.DataView> exposes an enumerable collection of <xref:System.Data.DataRowView> objects.</span></span> <span data-ttu-id="ac1b6-104">Os objetos **DataRowView** expõem valores como matrizes de objetos que são indexados pelo nome ou pela referência ordinal da coluna na tabela subjacente.</span><span class="sxs-lookup"><span data-stu-id="ac1b6-104">The **DataRowView** objects expose values as object arrays that are indexed by either the name or the ordinal reference of the column in the underlying table.</span></span> <span data-ttu-id="ac1b6-105">Você pode acessar o <xref:System.Data.DataRow> que é exposto pelo **DataRowView** usando a <xref:System.Data.DataRowView.Row%2A> propriedade de **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="ac1b6-105">You can access the <xref:System.Data.DataRow> that is exposed by the **DataRowView** by using the <xref:System.Data.DataRowView.Row%2A> property of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="ac1b6-106">Quando você exibe valores usando um **DataRowView**, a <xref:System.Data.DataView.RowStateFilter%2A> propriedade de **DataView** determina qual versão de linha da **DataRow** subjacente é exposta.</span><span class="sxs-lookup"><span data-stu-id="ac1b6-106">When you view values by using a **DataRowView**, the <xref:System.Data.DataView.RowStateFilter%2A> property of the **DataView** determines which row version of the underlying **DataRow** is exposed.</span></span> <span data-ttu-id="ac1b6-107">Para obter informações sobre como acessar versões de linha diferentes usando uma **DataRow**, consulte [Estados de linha e versões de linha](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="ac1b6-107">For information about accessing different row versions using a **DataRow**, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="ac1b6-108">O exemplo de código a seguir exibe todos os valores atuais e originais em uma tabela.</span><span class="sxs-lookup"><span data-stu-id="ac1b6-108">The following code example displays all the current and original values in a table.</span></span>  
  
```vb  
Dim catView As DataView = New DataView(catDS.Tables("Categories"))  
Console.WriteLine("Current Values:")  
WriteView(catView)  
Console.WriteLine("Original Values:")  
catView.RowStateFilter = DataViewRowState.ModifiedOriginal  
WriteView(catView)      
  
Public Shared Sub WriteView(thisDataView As DataView)  
  Dim rowView As DataRowView  
  Dim i As Integer  
  
  For Each rowView In thisDataView  
    For i = 0 To thisDataView.Table.Columns.Count - 1  
      Console.Write(rowView(i) & vbTab)  
    Next  
    Console.WriteLine()  
  Next  
End Sub  
```  
  
```csharp  
DataView catView = new DataView(catDS.Tables["Categories"]);  
Console.WriteLine("Current Values:");  
WriteView(catView);  
Console.WriteLine("Original Values:");  
catView.RowStateFilter = DataViewRowState.ModifiedOriginal;  
WriteView(catView);  
  
public static void WriteView(DataView thisDataView)  
{  
  foreach (DataRowView rowView in thisDataView)  
  {  
    for (int i = 0; i < thisDataView.Table.Columns.Count; i++)  
      Console.Write(rowView[i] + "\t");  
    Console.WriteLine();  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac1b6-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac1b6-109">See also</span></span>

- <xref:System.Data.DataRowVersion>
- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [<span data-ttu-id="ac1b6-110">DataViews</span><span class="sxs-lookup"><span data-stu-id="ac1b6-110">DataViews</span></span>](dataviews.md)
- <span data-ttu-id="ac1b6-111">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="ac1b6-111">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
