---
title: Exclusão de DataRow
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 128c41e1906b17e7f42458e8a5f1b3d3ec9cc449
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757509"
---
# <a name="datarow-deletion"></a>Exclusão de DataRow
Há dois métodos que você pode usar para excluir um <xref:System.Data.DataRow> do objeto de um <xref:System.Data.DataTable> objeto: o **remover** método o <xref:System.Data.DataRowCollection> objeto e o <xref:System.Data.DataRow.Delete%2A> método do **DataRow**objeto. Enquanto o <xref:System.Data.DataRowCollection.Remove%2A> método exclui um **DataRow** do **DataRowCollection**, o <xref:System.Data.DataRow.Delete%2A> método somente marca a linha para exclusão. A remoção real ocorre quando o aplicativo chama o **AcceptChanges** método. Usando <xref:System.Data.DataRow.Delete%2A>, você pode verificar programaticamente quais linhas estão marcadas para exclusão antes de realmente removê-las. Quando uma linha está marcada para exclusão, sua propriedade <xref:System.Data.DataRow.RowState%2A> é definida como <xref:System.Data.DataRow.Delete%2A>.  
  
 Nem <xref:System.Data.DataRow.Delete%2A> ou <xref:System.Data.DataRowCollection.Remove%2A> deve ser chamado em um loop foreach ao fazer a iteração por meio de um objeto de <xref:System.Data.DataRowCollection>. Nem <xref:System.Data.DataRow.Delete%2A> ou <xref:System.Data.DataRowCollection.Remove%2A> modificam o estado da coleção.  
  
 Ao usar um <xref:System.Data.DataSet> ou **DataTable** em conjunto com um **DataAdapter** e uma fonte de dados relacional, use o **excluir** método o  **DataRow** para remover a linha. O **excluir** método marca a linha como **excluído** no **DataSet** ou **DataTable** mas não removê-lo. Em vez disso, quando o **DataAdapter** encontra uma linha marcada como **excluído**, ele executa seu **DeleteCommand** método para excluir a linha na fonte de dados. A linha pode então ser permanentemente removida usando o **AcceptChanges** método. Se você usar **remover** para excluir a linha, a linha é removida completamente da tabela, mas o **DataAdapter** não excluirá a linha na fonte de dados.  
  
 O **remover** método o **DataRowCollection** leva um **DataRow** como um argumento e remove da coleção, conforme mostrado no exemplo a seguir.  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 Por outro lado, o exemplo a seguir demonstra como chamar o **excluir** método em um **DataRow** para alterar sua **RowState** para **excluído** .  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 Se uma linha está marcada para exclusão e você chamar o **AcceptChanges** método o **DataTable** do objeto, a linha é removida do **DataTable**. Por outro lado, se você chamar **RejectChanges**, o **RowState** da linha é revertido ao que era antes de ser marcada como **excluído**.  
  
> [!NOTE]
>  Se o **RowState** de um **DataRow** é **adicionado**, que significa que acabou de ser adicionada à tabela e, em seguida, está marcado como **excluído**, é removidos da tabela.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataRowCollection>  
 <xref:System.Data.DataTable>  
 [Manipulação de dados em uma DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
