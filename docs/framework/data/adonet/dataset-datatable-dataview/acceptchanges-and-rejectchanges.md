---
title: AcceptChanges e RejectChanges
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
ms.openlocfilehash: c537fa808fc6ba4c740e71bfd70fe9cd1f3bd31a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785565"
---
# <a name="acceptchanges-and-rejectchanges"></a><span data-ttu-id="c72fc-102">AcceptChanges e RejectChanges</span><span class="sxs-lookup"><span data-stu-id="c72fc-102">AcceptChanges and RejectChanges</span></span>
<span data-ttu-id="c72fc-103">Depois de verificar a precisão das alterações feitas nos dados em um <xref:System.Data.DataTable>, você pode aceitar as alterações usando o <xref:System.Data.DataRow.AcceptChanges%2A> método do <xref:System.Data.DataRow>, <xref:System.Data.DataTable>ou <xref:System.Data.DataSet>, que definirá os valores da linha **atual** como oOs valores originais e definirão a propriedade **RowState** como **inalterado**.</span><span class="sxs-lookup"><span data-stu-id="c72fc-103">After verifying the accuracy of changes made to data in a <xref:System.Data.DataTable>, you can accept the changes using the <xref:System.Data.DataRow.AcceptChanges%2A> method of the <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, or <xref:System.Data.DataSet>, which will set the **Current** row values to be the **Original** values and will set the **RowState** property to **Unchanged**.</span></span> <span data-ttu-id="c72fc-104">Aceitar ou rejeitar alterações limpa todas as informações de linhas de **erro** e define a propriedade **HasErrors** como **false**.</span><span class="sxs-lookup"><span data-stu-id="c72fc-104">Accepting or rejecting changes clears out any **RowError** information and sets the **HasErrors** property to **false**.</span></span> <span data-ttu-id="c72fc-105">Aceitar ou rejeitar alterações também pode afetar a atualização de dados na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="c72fc-105">Accepting or rejecting changes can also affect updating data in the data source.</span></span> <span data-ttu-id="c72fc-106">Para obter mais informações, consulte [Atualizando fontes de dados com DataAdapters](../updating-data-sources-with-dataadapters.md).</span><span class="sxs-lookup"><span data-stu-id="c72fc-106">For more information, see [Updating Data Sources with DataAdapters](../updating-data-sources-with-dataadapters.md).</span></span>  
  
 <span data-ttu-id="c72fc-107">Se houver restrições de chave estrangeira na **DataTable**, as alterações aceitas ou rejeitadas usando **AcceptChanges** e **RejectChanges** serão propagadas para as linhas filho da **DataRow** de acordo com o  **ForeignKeyConstraint. AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="c72fc-107">If foreign key constraints exist on the **DataTable**, changes accepted or rejected using **AcceptChanges** and **RejectChanges** are propagated to child rows of the **DataRow** according to the **ForeignKeyConstraint.AcceptRejectRule**.</span></span> <span data-ttu-id="c72fc-108">Para obter mais informações, consulte as [restrições de DataTable](datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="c72fc-108">For more information, see [DataTable Constraints](datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="c72fc-109">O exemplo a seguir verifica as linhas com erros, resolve os erros quando aplicável e rejeita as linhas em que o erro não pode ser resolvido.</span><span class="sxs-lookup"><span data-stu-id="c72fc-109">The following example checks for rows with errors, resolves the errors where applicable, and rejects the rows where the error cannot be resolved.</span></span> <span data-ttu-id="c72fc-110">Observe que, para erros resolvidos, o valor de **Usererror** é redefinido como uma cadeia de caracteres vazia, fazendo com que a propriedade **HasErrors** seja definida como **false**.</span><span class="sxs-lookup"><span data-stu-id="c72fc-110">Note that, for resolved errors, the **RowError** value is reset to an empty string, causing the **HasErrors** property to be set to **false**.</span></span> <span data-ttu-id="c72fc-111">Quando todas as linhas com erros tiverem sido resolvidas ou rejeitadas, **AcceptChanges** será chamado para aceitar todas as alterações de toda a **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="c72fc-111">When all the rows with errors have been resolved or rejected, **AcceptChanges** is called to accept all changes for the entire **DataTable**.</span></span>  
  
```vb  
If workTable.HasErrors Then  
  Dim errRow As DataRow  
  
  For Each errRow in workTable.GetErrors()  
  
    If errRow.RowError = "Total cannot exceed 1000." Then  
      errRow("Total") = 1000  
      errRow.RowError = ""    ' Clear the error.  
    Else  
      errRow.RejectChanges()  
    End If  
  Next  
End If  
  
workTable.AcceptChanges()  
```  
  
```csharp  
if (workTable.HasErrors)  
{  
  
  foreach (DataRow errRow in workTable.GetErrors())  
  {  
    if (errRow.RowError == "Total cannot exceed 1000.")  
    {  
      errRow["Total"] = 1000;  
      errRow.RowError = "";    // Clear the error.  
    }  
    else  
      errRow.RejectChanges();  
  }  
}  
  
workTable.AcceptChanges();  
```  
  
## <a name="see-also"></a><span data-ttu-id="c72fc-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c72fc-112">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="c72fc-113">Manipulação de dados em uma DataTable</span><span class="sxs-lookup"><span data-stu-id="c72fc-113">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- <span data-ttu-id="c72fc-114">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="c72fc-114">[ADO.NET Overview](../ado-net-overview.md)</span></span>
