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
---
# <a name="datarow-deletion"></a><span data-ttu-id="ad480-102">Exclusão de DataRow</span><span class="sxs-lookup"><span data-stu-id="ad480-102">DataRow Deletion</span></span>
<span data-ttu-id="ad480-103">Há dois métodos que você pode usar para excluir um <xref:System.Data.DataRow> do objeto de um <xref:System.Data.DataTable> objeto: o **remover** método o <xref:System.Data.DataRowCollection> objeto e o <xref:System.Data.DataRow.Delete%2A> método do **DataRow**objeto.</span><span class="sxs-lookup"><span data-stu-id="ad480-103">There are two methods you can use to delete a <xref:System.Data.DataRow> object from a <xref:System.Data.DataTable> object: the **Remove** method of the <xref:System.Data.DataRowCollection> object, and the <xref:System.Data.DataRow.Delete%2A> method of the **DataRow** object.</span></span> <span data-ttu-id="ad480-104">Enquanto o <xref:System.Data.DataRowCollection.Remove%2A> método exclui um **DataRow** do **DataRowCollection**, o <xref:System.Data.DataRow.Delete%2A> método somente marca a linha para exclusão.</span><span class="sxs-lookup"><span data-stu-id="ad480-104">Whereas the <xref:System.Data.DataRowCollection.Remove%2A> method deletes a **DataRow** from the **DataRowCollection**, the <xref:System.Data.DataRow.Delete%2A> method only marks the row for deletion.</span></span> <span data-ttu-id="ad480-105">A remoção real ocorre quando o aplicativo chama o **AcceptChanges** método.</span><span class="sxs-lookup"><span data-stu-id="ad480-105">The actual removal occurs when the application calls the **AcceptChanges** method.</span></span> <span data-ttu-id="ad480-106">Usando <xref:System.Data.DataRow.Delete%2A>, você pode verificar programaticamente quais linhas estão marcadas para exclusão antes de realmente removê-las.</span><span class="sxs-lookup"><span data-stu-id="ad480-106">By using <xref:System.Data.DataRow.Delete%2A>, you can programmatically check which rows are marked for deletion before actually removing them.</span></span> <span data-ttu-id="ad480-107">Quando uma linha está marcada para exclusão, sua propriedade <xref:System.Data.DataRow.RowState%2A> é definida como <xref:System.Data.DataRow.Delete%2A>.</span><span class="sxs-lookup"><span data-stu-id="ad480-107">When a row is marked for deletion, its <xref:System.Data.DataRow.RowState%2A> property is set to <xref:System.Data.DataRow.Delete%2A>.</span></span>  
  
 <span data-ttu-id="ad480-108">Nem <xref:System.Data.DataRow.Delete%2A> ou <xref:System.Data.DataRowCollection.Remove%2A> deve ser chamado em um loop foreach ao fazer a iteração por meio de um objeto de <xref:System.Data.DataRowCollection>.</span><span class="sxs-lookup"><span data-stu-id="ad480-108">Neither <xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> should be called in a foreach loop while iterating through a <xref:System.Data.DataRowCollection> object.</span></span> <span data-ttu-id="ad480-109">Nem <xref:System.Data.DataRow.Delete%2A> ou <xref:System.Data.DataRowCollection.Remove%2A> modificam o estado da coleção.</span><span class="sxs-lookup"><span data-stu-id="ad480-109"><xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> modify the state of the collection.</span></span>  
  
 <span data-ttu-id="ad480-110">Ao usar um <xref:System.Data.DataSet> ou **DataTable** em conjunto com um **DataAdapter** e uma fonte de dados relacional, use o **excluir** método o  **DataRow** para remover a linha.</span><span class="sxs-lookup"><span data-stu-id="ad480-110">When using a <xref:System.Data.DataSet> or **DataTable** in conjunction with a **DataAdapter** and a relational data source, use the **Delete** method of the **DataRow** to remove the row.</span></span> <span data-ttu-id="ad480-111">O **excluir** método marca a linha como **excluído** no **DataSet** ou **DataTable** mas não removê-lo.</span><span class="sxs-lookup"><span data-stu-id="ad480-111">The **Delete** method marks the row as **Deleted** in the **DataSet** or **DataTable** but does not remove it.</span></span> <span data-ttu-id="ad480-112">Em vez disso, quando o **DataAdapter** encontra uma linha marcada como **excluído**, ele executa seu **DeleteCommand** método para excluir a linha na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="ad480-112">Instead, when the **DataAdapter** encounters a row marked as **Deleted**, it executes its **DeleteCommand** method to delete the row at the data source.</span></span> <span data-ttu-id="ad480-113">A linha pode então ser permanentemente removida usando o **AcceptChanges** método.</span><span class="sxs-lookup"><span data-stu-id="ad480-113">The row can then be permanently removed using the **AcceptChanges** method.</span></span> <span data-ttu-id="ad480-114">Se você usar **remover** para excluir a linha, a linha é removida completamente da tabela, mas o **DataAdapter** não excluirá a linha na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="ad480-114">If you use **Remove** to delete the row, the row is removed entirely from the table, but the **DataAdapter** will not delete the row at the data source.</span></span>  
  
 <span data-ttu-id="ad480-115">O **remover** método o **DataRowCollection** leva um **DataRow** como um argumento e remove da coleção, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ad480-115">The **Remove** method of the **DataRowCollection** takes a **DataRow** as an argument and removes it from the collection, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 <span data-ttu-id="ad480-116">Por outro lado, o exemplo a seguir demonstra como chamar o **excluir** método em um **DataRow** para alterar sua **RowState** para **excluído** .</span><span class="sxs-lookup"><span data-stu-id="ad480-116">In contrast, the following example demonstrates how to call the **Delete** method on a **DataRow** to change its **RowState** to **Deleted**.</span></span>  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 <span data-ttu-id="ad480-117">Se uma linha está marcada para exclusão e você chamar o **AcceptChanges** método o **DataTable** do objeto, a linha é removida do **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="ad480-117">If a row is marked for deletion and you call the **AcceptChanges** method of the **DataTable** object, the row is removed from the **DataTable**.</span></span> <span data-ttu-id="ad480-118">Por outro lado, se você chamar **RejectChanges**, o **RowState** da linha é revertido ao que era antes de ser marcada como **excluído**.</span><span class="sxs-lookup"><span data-stu-id="ad480-118">In contrast, if you call **RejectChanges**, the **RowState** of the row reverts to what it was before being marked as **Deleted**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad480-119">Se o **RowState** de um **DataRow** é **adicionado**, que significa que acabou de ser adicionada à tabela e, em seguida, está marcado como **excluído**, é removidos da tabela.</span><span class="sxs-lookup"><span data-stu-id="ad480-119">If the **RowState** of a **DataRow** is **Added**, meaning it has just been added to the table, and it is then marked as **Deleted**, it is removed from the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad480-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ad480-120">See Also</span></span>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataRowCollection>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="ad480-121">Manipulação de dados em uma DataTable</span><span class="sxs-lookup"><span data-stu-id="ad480-121">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 <span data-ttu-id="ad480-122">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="ad480-122">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
