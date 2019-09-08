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
# <a name="acceptchanges-and-rejectchanges"></a>AcceptChanges e RejectChanges
Depois de verificar a precisão das alterações feitas nos dados em um <xref:System.Data.DataTable>, você pode aceitar as alterações usando o <xref:System.Data.DataRow.AcceptChanges%2A> método do <xref:System.Data.DataRow>, <xref:System.Data.DataTable>ou <xref:System.Data.DataSet>, que definirá os valores da linha **atual** como oOs valores originais e definirão a propriedade **RowState** como **inalterado**. Aceitar ou rejeitar alterações limpa todas as informações de linhas de **erro** e define a propriedade **HasErrors** como **false**. Aceitar ou rejeitar alterações também pode afetar a atualização de dados na fonte de dados. Para obter mais informações, consulte [Atualizando fontes de dados com DataAdapters](../updating-data-sources-with-dataadapters.md).  
  
 Se houver restrições de chave estrangeira na **DataTable**, as alterações aceitas ou rejeitadas usando **AcceptChanges** e **RejectChanges** serão propagadas para as linhas filho da **DataRow** de acordo com o  **ForeignKeyConstraint. AcceptRejectRule**. Para obter mais informações, consulte as [restrições de DataTable](datatable-constraints.md).  
  
 O exemplo a seguir verifica as linhas com erros, resolve os erros quando aplicável e rejeita as linhas em que o erro não pode ser resolvido. Observe que, para erros resolvidos, o valor de **Usererror** é redefinido como uma cadeia de caracteres vazia, fazendo com que a propriedade **HasErrors** seja definida como **false**. Quando todas as linhas com erros tiverem sido resolvidas ou rejeitadas, **AcceptChanges** será chamado para aceitar todas as alterações de toda a **DataTable**.  
  
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
  
## <a name="see-also"></a>Consulte também

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [Manipulação de dados em uma DataTable](manipulating-data-in-a-datatable.md)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
