---
title: AcceptChanges e RejectChanges
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
ms.openlocfilehash: 65e47bafda3e3e47241405c9c8b8e3b4b0055601
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="acceptchanges-and-rejectchanges"></a>AcceptChanges e RejectChanges
Depois de verificar a exatidão das alterações feitas nos dados em um <xref:System.Data.DataTable>, você pode aceitar as alterações usando o <xref:System.Data.DataRow.AcceptChanges%2A> método do <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, ou <xref:System.Data.DataSet>, que definirá o **atual** linha valores para ser o **Original** valores e definirá o **RowState** propriedade **inalterado**. Aceitar ou rejeitar alterações limpa qualquer **RowError** informações e define o **HasErrors** propriedade **false**. Aceitar ou rejeitar as alterações também pode afetar a atualização de dados na fonte de dados. Para obter mais informações, consulte [Atualizar fontes de dados com DataAdapters](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).  
  
 Se existirem restrições de chave estrangeira no **DataTable**, alterações aceitas ou rejeitadas usando **AcceptChanges** e **RejectChanges** são propagadas para as linhas filho do  **DataRow** acordo com o **ForeignKeyConstraint.AcceptRejectRule**. Para obter mais informações, consulte [restrições de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).  
  
 O exemplo a seguir verifica para linhas com erros, resolve os erros quando aplicável e rejeita as linhas em que o erro não pode ser resolvido. Observe que, para resolver erros, o **RowError** valor será redefinido como uma cadeia de caracteres vazia, fazendo com que o **HasErrors** propriedade a ser definida **false**. Quando todas as linhas com erros foram resolvidas ou rejeitadas, **AcceptChanges** é chamado para aceitar todas as alterações para todo o **DataTable**.  
  
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
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [Manipulação de dados em uma DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
