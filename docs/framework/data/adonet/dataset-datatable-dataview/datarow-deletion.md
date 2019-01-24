---
title: Exclusão de DataRow
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 69bdf4d23463cc07259a2b1de6b9efaa78f0f0de
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54593752"
---
# <a name="datarow-deletion"></a>Exclusão de DataRow
Há dois métodos que você pode usar para excluir uma <xref:System.Data.DataRow> do objeto de um <xref:System.Data.DataTable> objeto: o **remover** método da <xref:System.Data.DataRowCollection> objeto e o <xref:System.Data.DataRow.Delete%2A> o método da **DataRow**objeto. Enquanto o <xref:System.Data.DataRowCollection.Remove%2A> exclusões de método uma **DataRow** da **DataRowCollection**, o <xref:System.Data.DataRow.Delete%2A> método marca apenas a linha para exclusão. A remoção real ocorre quando o aplicativo chama o **AcceptChanges** método. Usando <xref:System.Data.DataRow.Delete%2A>, você pode verificar programaticamente quais linhas estão marcadas para exclusão antes de realmente removê-las. Quando uma linha está marcada para exclusão, sua propriedade <xref:System.Data.DataRow.RowState%2A> é definida como <xref:System.Data.DataRow.Delete%2A>.  
  
 Nem <xref:System.Data.DataRow.Delete%2A> ou <xref:System.Data.DataRowCollection.Remove%2A> deve ser chamado em um loop foreach ao fazer a iteração por meio de um objeto de <xref:System.Data.DataRowCollection>. Nem <xref:System.Data.DataRow.Delete%2A> ou <xref:System.Data.DataRowCollection.Remove%2A> modificam o estado da coleção.  
  
 Ao usar um <xref:System.Data.DataSet> ou **DataTable** junto com um **DataAdapter** e uma fonte de dados relacional, use o **excluir** método do  **DataRow** para remover a linha. O **excluir** método marca a linha como **Deleted** no **conjunto de dados** ou **DataTable** , mas não removê-lo. Em vez disso, quando o **DataAdapter** encontra uma linha marcada como **Deleted**, ele executa seu **DeleteCommand** método para excluir a linha na fonte de dados. A linha pode então ser permanentemente removida usando o **AcceptChanges** método. Se você usar **remova** para excluir a linha, a linha será completamente removida da tabela, mas o **DataAdapter** não excluirá a linha na fonte de dados.  
  
 O **remover** método o **DataRowCollection** leva um **DataRow** como um argumento e a remove da coleção, conforme mostrado no exemplo a seguir.  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 Em contraste, o exemplo a seguir demonstra como chamar o **excluir** método em um **DataRow** para alterar sua **RowState** para **Deleted** .  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 Se uma linha está marcada para exclusão e chamar o **AcceptChanges** método o **DataTable** do objeto, a linha é removida da **DataTable**. Por outro lado, se você chamar **RejectChanges**, o **RowState** da linha será revertido ao que era antes de ser marcado como **Deleted**.  
  
> [!NOTE]
>  Se o **RowState** de uma **DataRow** está **adicionado**, que significa que ele acabou de ser adicionado à tabela e está marcado como **Deleted**, é removido da tabela.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [Manipulação de dados em uma DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
