---
title: Criando colunas de expressão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: 11bacf436daf2a77a9cf46b4883d282143572e27
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="creating-expression-columns"></a><span data-ttu-id="96b08-102">Criando colunas de expressão</span><span class="sxs-lookup"><span data-stu-id="96b08-102">Creating Expression Columns</span></span>
<span data-ttu-id="96b08-103">Você pode definir uma expressão para uma coluna, permitindo que ela contenha um valor calculado dos valores de outras colunas na mesma linha ou dos valores de coluna de várias linhas na tabela.</span><span class="sxs-lookup"><span data-stu-id="96b08-103">You can define an expression for a column, enabling it to contain a value calculated from other column values in the same row or from the column values of multiple rows in the table.</span></span> <span data-ttu-id="96b08-104">Para definir a expressão a ser avaliada, use a propriedade <xref:System.Data.DataColumn.Expression%2A> de coluna de destino e use a propriedade <xref:System.Data.DataColumn.ColumnName%2A> para se referir a outras colunas na expressão.</span><span class="sxs-lookup"><span data-stu-id="96b08-104">To define the expression to be evaluated, use the <xref:System.Data.DataColumn.Expression%2A> property of the target column, and use the <xref:System.Data.DataColumn.ColumnName%2A> property to refer to other columns in the expression.</span></span> <span data-ttu-id="96b08-105">O <xref:System.Data.DataColumn.DataType%2A> para a coluna de expressão deve ser apropriado para o valor que a expressão retorna.</span><span class="sxs-lookup"><span data-stu-id="96b08-105">The <xref:System.Data.DataColumn.DataType%2A> for the expression column must be appropriate for the value that the expression returns.</span></span>  
  
 <span data-ttu-id="96b08-106">A tabela a seguir lista vários usos possíveis para colunas de expressão em uma tabela.</span><span class="sxs-lookup"><span data-stu-id="96b08-106">The following table lists several possible uses for expression columns in a table.</span></span>  
  
|<span data-ttu-id="96b08-107">Tipo de expressão</span><span class="sxs-lookup"><span data-stu-id="96b08-107">Expression type</span></span>|<span data-ttu-id="96b08-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="96b08-108">Example</span></span>|  
|---------------------|-------------|  
|<span data-ttu-id="96b08-109">Comparação</span><span class="sxs-lookup"><span data-stu-id="96b08-109">Comparison</span></span>|<span data-ttu-id="96b08-110">"Total >= 500"</span><span class="sxs-lookup"><span data-stu-id="96b08-110">"Total >= 500"</span></span>|  
|<span data-ttu-id="96b08-111">Computação</span><span class="sxs-lookup"><span data-stu-id="96b08-111">Computation</span></span>|<span data-ttu-id="96b08-112">"UnitPrice \* Quantity"</span><span class="sxs-lookup"><span data-stu-id="96b08-112">"UnitPrice \* Quantity"</span></span>|  
|<span data-ttu-id="96b08-113">Agregação</span><span class="sxs-lookup"><span data-stu-id="96b08-113">Aggregation</span></span>|<span data-ttu-id="96b08-114">Sum(Price)</span><span class="sxs-lookup"><span data-stu-id="96b08-114">Sum(Price)</span></span>|  
  
 <span data-ttu-id="96b08-115">Você pode definir o **expressão** propriedade em uma **DataColumn** objeto, ou você pode incluir a propriedade como o terceiro argumento passado para o <xref:System.Data.DataColumn> construtor, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="96b08-115">You can set the **Expression** property on an existing **DataColumn** object, or you can include the property as the third argument passed to the <xref:System.Data.DataColumn> constructor, as shown in the following example.</span></span>  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 <span data-ttu-id="96b08-116">As expressões podem referenciar outras colunas de expressão; no entanto, uma referência circular, na qual duas expressões referenciam-se entre si, gerará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="96b08-116">Expressions can reference other expression columns; however, a circular reference, in which two expressions reference each other, will generate an exception.</span></span> <span data-ttu-id="96b08-117">Para obter regras sobre como escrever expressões, consulte o <xref:System.Data.DataColumn.Expression%2A> propriedade o **DataColumn** classe.</span><span class="sxs-lookup"><span data-stu-id="96b08-117">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96b08-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96b08-118">See Also</span></span>  
 <xref:System.Data.DataColumn>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="96b08-119">Definição de esquema de DataTable</span><span class="sxs-lookup"><span data-stu-id="96b08-119">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="96b08-120">DataTables</span><span class="sxs-lookup"><span data-stu-id="96b08-120">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 <span data-ttu-id="96b08-121">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="96b08-121">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
