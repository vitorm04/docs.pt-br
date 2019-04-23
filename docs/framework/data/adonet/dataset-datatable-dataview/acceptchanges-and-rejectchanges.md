---
title: AcceptChanges e RejectChanges
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
ms.openlocfilehash: bbcc666b99c2bade479e5ee51750b043c820845d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172894"
---
# <a name="acceptchanges-and-rejectchanges"></a><span data-ttu-id="22ba4-102">AcceptChanges e RejectChanges</span><span class="sxs-lookup"><span data-stu-id="22ba4-102">AcceptChanges and RejectChanges</span></span>
<span data-ttu-id="22ba4-103">Depois de verificar a precisão das alterações feitas nos dados em um <xref:System.Data.DataTable>, você pode aceitar as alterações usando o <xref:System.Data.DataRow.AcceptChanges%2A> método da <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, ou <xref:System.Data.DataSet>, que definirá o **atual** linha valores a serem os **Original** valores e definirá o **RowState** propriedade a ser **inalterado**.</span><span class="sxs-lookup"><span data-stu-id="22ba4-103">After verifying the accuracy of changes made to data in a <xref:System.Data.DataTable>, you can accept the changes using the <xref:System.Data.DataRow.AcceptChanges%2A> method of the <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, or <xref:System.Data.DataSet>, which will set the **Current** row values to be the **Original** values and will set the **RowState** property to **Unchanged**.</span></span> <span data-ttu-id="22ba4-104">Aceitar ou rejeitar alterações limpa qualquer **RowError** informações e define o **HasErrors** propriedade a ser **false**.</span><span class="sxs-lookup"><span data-stu-id="22ba4-104">Accepting or rejecting changes clears out any **RowError** information and sets the **HasErrors** property to **false**.</span></span> <span data-ttu-id="22ba4-105">Aceitar ou rejeitar alterações também pode afetar a atualização de dados na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="22ba4-105">Accepting or rejecting changes can also affect updating data in the data source.</span></span> <span data-ttu-id="22ba4-106">Para obter mais informações, consulte [Updating Data Sources with DataAdapters](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).</span><span class="sxs-lookup"><span data-stu-id="22ba4-106">For more information, see [Updating Data Sources with DataAdapters](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).</span></span>  
  
 <span data-ttu-id="22ba4-107">Se as restrições de chave estrangeira existem na **DataTable**, as alterações aceitas ou rejeitadas através de **AcceptChanges** e **RejectChanges** são propagadas para as linhas filho do  **DataRow** acordo com o **ForeignKeyConstraint.AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="22ba4-107">If foreign key constraints exist on the **DataTable**, changes accepted or rejected using **AcceptChanges** and **RejectChanges** are propagated to child rows of the **DataRow** according to the **ForeignKeyConstraint.AcceptRejectRule**.</span></span> <span data-ttu-id="22ba4-108">Para obter mais informações, consulte [restrições de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="22ba4-108">For more information, see [DataTable Constraints](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="22ba4-109">O exemplo a seguir verificará se há linhas com erros, resolve os erros quando aplicável e rejeita as linhas em que o erro não pode ser resolvido.</span><span class="sxs-lookup"><span data-stu-id="22ba4-109">The following example checks for rows with errors, resolves the errors where applicable, and rejects the rows where the error cannot be resolved.</span></span> <span data-ttu-id="22ba4-110">Observe que, para resolver erros, o **RowError** valor será redefinido como uma cadeia de caracteres vazia, fazendo com que o **HasErrors** propriedade ser definida como **false**.</span><span class="sxs-lookup"><span data-stu-id="22ba4-110">Note that, for resolved errors, the **RowError** value is reset to an empty string, causing the **HasErrors** property to be set to **false**.</span></span> <span data-ttu-id="22ba4-111">Quando todas as linhas com erros foram resolvidas ou rejeitadas, **AcceptChanges** é chamado para aceitar todas as alterações para toda a **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="22ba4-111">When all the rows with errors have been resolved or rejected, **AcceptChanges** is called to accept all changes for the entire **DataTable**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="22ba4-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22ba4-112">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="22ba4-113">Manipulação de dados em uma DataTable</span><span class="sxs-lookup"><span data-stu-id="22ba4-113">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- <span data-ttu-id="22ba4-114">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="22ba4-114">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
