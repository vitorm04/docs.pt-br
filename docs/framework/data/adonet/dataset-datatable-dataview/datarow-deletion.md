---
title: Exclusão de DataRow
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 46109ee1781b8b509df87b4203c51a55b9f596ae
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205112"
---
# <a name="datarow-deletion"></a>Exclusão de DataRow
Há dois métodos que você pode usar para excluir um <xref:System.Data.DataRow> objeto de um <xref:System.Data.DataTable> objeto: <xref:System.Data.DataRowCollection> o método **Remove** do objeto e o <xref:System.Data.DataRow.Delete%2A> método do objeto **DataRow** . Enquanto o <xref:System.Data.DataRowCollection.Remove%2A> método exclui uma **DataRow** de **DataRowCollection**, o <xref:System.Data.DataRow.Delete%2A> método marca apenas a linha para exclusão. A remoção real ocorre quando o aplicativo chama o método **AcceptChanges** . Usando <xref:System.Data.DataRow.Delete%2A>, você pode verificar programaticamente quais linhas estão marcadas para exclusão antes de realmente removê-las. Quando uma linha está marcada para exclusão, sua propriedade <xref:System.Data.DataRow.RowState%2A> é definida como <xref:System.Data.DataRow.Delete%2A>.  
  
 Nem <xref:System.Data.DataRow.Delete%2A> ou <xref:System.Data.DataRowCollection.Remove%2A> deve ser chamado em um loop foreach ao fazer a iteração por meio de um objeto de <xref:System.Data.DataRowCollection>. Nem <xref:System.Data.DataRow.Delete%2A> ou <xref:System.Data.DataRowCollection.Remove%2A> modificam o estado da coleção.  
  
 Ao usar uma <xref:System.Data.DataSet> **DataTable** ou em conjunto com um **DataAdapter** e uma fonte de dados relacional, use o método **delete** da **DataRow** para remover a linha. O método **delete** marca a linha como **excluída** no **DataSet** ou **DataTable** , mas não a remove. Em vez disso, quando o **DataAdapter** encontra uma linhamarcada como excluída, ele executa seu método **DeleteCommand** para excluir a linha na fonte de dados. Em seguida, a linha pode ser removida permanentemente usando o método **AcceptChanges** . Se você usar **remover** para excluir a linha, a linha será completamente removida da tabela, mas o **DataAdapter** não excluirá a linha na fonte de dados.  
  
 O método **Remove** da **DataRowCollection** usa uma **DataRow** como um argumento e a remove da coleção, conforme mostrado no exemplo a seguir.  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 Por outro lado, o exemplo a seguir demonstra como chamar o método **delete** em uma **DataRow** para alterar seu **RowState** para **excluído**.  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 Se uma linha for marcada para exclusão e você chamar o método **AcceptChanges** do objeto **DataTable** , a linha será removida da **DataTable**. Por outro lado, se você chamar **RejectChanges**, o **RowState** da linha será revertido para o que estava antes de ser marcado como **excluído**.  
  
> [!NOTE]
> Se o **RowState** de uma **DataRow** for **adicionado**, o que significa que acabou de ser adicionado à tabela e, em seguida, marcado como **excluído**, ele será removido da tabela.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [Manipulação de dados em uma DataTable](manipulating-data-in-a-datatable.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
