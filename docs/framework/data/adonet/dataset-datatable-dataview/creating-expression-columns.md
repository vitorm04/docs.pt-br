---
title: Criando colunas de expressão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: db38d42e9c7dc1657e06030599ae2b8ba66ef6b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549870"
---
# <a name="creating-expression-columns"></a><span data-ttu-id="c3730-102">Criando colunas de expressão</span><span class="sxs-lookup"><span data-stu-id="c3730-102">Creating Expression Columns</span></span>
<span data-ttu-id="c3730-103">Você pode definir uma expressão para uma coluna, permitindo que ela contenha um valor calculado dos valores de outras colunas na mesma linha ou dos valores de coluna de várias linhas na tabela.</span><span class="sxs-lookup"><span data-stu-id="c3730-103">You can define an expression for a column, enabling it to contain a value calculated from other column values in the same row or from the column values of multiple rows in the table.</span></span> <span data-ttu-id="c3730-104">Para definir a expressão a ser avaliada, use a propriedade <xref:System.Data.DataColumn.Expression%2A> de coluna de destino e use a propriedade <xref:System.Data.DataColumn.ColumnName%2A> para se referir a outras colunas na expressão.</span><span class="sxs-lookup"><span data-stu-id="c3730-104">To define the expression to be evaluated, use the <xref:System.Data.DataColumn.Expression%2A> property of the target column, and use the <xref:System.Data.DataColumn.ColumnName%2A> property to refer to other columns in the expression.</span></span> <span data-ttu-id="c3730-105">O <xref:System.Data.DataColumn.DataType%2A> para a coluna de expressão deve ser apropriado para o valor que a expressão retorna.</span><span class="sxs-lookup"><span data-stu-id="c3730-105">The <xref:System.Data.DataColumn.DataType%2A> for the expression column must be appropriate for the value that the expression returns.</span></span>  
  
 <span data-ttu-id="c3730-106">A tabela a seguir lista vários usos possíveis para colunas de expressão em uma tabela.</span><span class="sxs-lookup"><span data-stu-id="c3730-106">The following table lists several possible uses for expression columns in a table.</span></span>  
  
|<span data-ttu-id="c3730-107">Tipo de expressão</span><span class="sxs-lookup"><span data-stu-id="c3730-107">Expression type</span></span>|<span data-ttu-id="c3730-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c3730-108">Example</span></span>|  
|---------------------|-------------|  
|<span data-ttu-id="c3730-109">Comparação</span><span class="sxs-lookup"><span data-stu-id="c3730-109">Comparison</span></span>|<span data-ttu-id="c3730-110">"Total >= 500"</span><span class="sxs-lookup"><span data-stu-id="c3730-110">"Total >= 500"</span></span>|  
|<span data-ttu-id="c3730-111">Computação</span><span class="sxs-lookup"><span data-stu-id="c3730-111">Computation</span></span>|<span data-ttu-id="c3730-112">"UnitPrice \* Quantity"</span><span class="sxs-lookup"><span data-stu-id="c3730-112">"UnitPrice \* Quantity"</span></span>|  
|<span data-ttu-id="c3730-113">Agregação</span><span class="sxs-lookup"><span data-stu-id="c3730-113">Aggregation</span></span>|<span data-ttu-id="c3730-114">Sum(Price)</span><span class="sxs-lookup"><span data-stu-id="c3730-114">Sum(Price)</span></span>|  
  
 <span data-ttu-id="c3730-115">Você pode definir as **expressão** propriedade em uma existente **DataColumn** objeto, ou você pode incluir a propriedade como o terceiro argumento passado para o <xref:System.Data.DataColumn> construtor, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c3730-115">You can set the **Expression** property on an existing **DataColumn** object, or you can include the property as the third argument passed to the <xref:System.Data.DataColumn> constructor, as shown in the following example.</span></span>  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 <span data-ttu-id="c3730-116">As expressões podem referenciar outras colunas de expressão; no entanto, uma referência circular, na qual duas expressões referenciam-se entre si, gerará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="c3730-116">Expressions can reference other expression columns; however, a circular reference, in which two expressions reference each other, will generate an exception.</span></span> <span data-ttu-id="c3730-117">Para obter regras sobre como escrever expressões, consulte o <xref:System.Data.DataColumn.Expression%2A> propriedade do **DataColumn** classe.</span><span class="sxs-lookup"><span data-stu-id="c3730-117">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3730-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3730-118">See also</span></span>
- <xref:System.Data.DataColumn>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="c3730-119">Definição de esquema de DataTable</span><span class="sxs-lookup"><span data-stu-id="c3730-119">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [<span data-ttu-id="c3730-120">DataTables</span><span class="sxs-lookup"><span data-stu-id="c3730-120">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- <span data-ttu-id="c3730-121">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="c3730-121">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
