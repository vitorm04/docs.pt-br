---
title: Criando colunas de expressão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: 1c4e0b368a8eb154207382ae70b9767f5a5fe64d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785442"
---
# <a name="creating-expression-columns"></a><span data-ttu-id="e23a0-102">Criando colunas de expressão</span><span class="sxs-lookup"><span data-stu-id="e23a0-102">Creating Expression Columns</span></span>
<span data-ttu-id="e23a0-103">Você pode definir uma expressão para uma coluna, permitindo que ela contenha um valor calculado dos valores de outras colunas na mesma linha ou dos valores de coluna de várias linhas na tabela.</span><span class="sxs-lookup"><span data-stu-id="e23a0-103">You can define an expression for a column, enabling it to contain a value calculated from other column values in the same row or from the column values of multiple rows in the table.</span></span> <span data-ttu-id="e23a0-104">Para definir a expressão a ser avaliada, use a propriedade <xref:System.Data.DataColumn.Expression%2A> de coluna de destino e use a propriedade <xref:System.Data.DataColumn.ColumnName%2A> para se referir a outras colunas na expressão.</span><span class="sxs-lookup"><span data-stu-id="e23a0-104">To define the expression to be evaluated, use the <xref:System.Data.DataColumn.Expression%2A> property of the target column, and use the <xref:System.Data.DataColumn.ColumnName%2A> property to refer to other columns in the expression.</span></span> <span data-ttu-id="e23a0-105">O <xref:System.Data.DataColumn.DataType%2A> para a coluna de expressão deve ser apropriado para o valor que a expressão retorna.</span><span class="sxs-lookup"><span data-stu-id="e23a0-105">The <xref:System.Data.DataColumn.DataType%2A> for the expression column must be appropriate for the value that the expression returns.</span></span>  
  
 <span data-ttu-id="e23a0-106">A tabela a seguir lista vários usos possíveis para colunas de expressão em uma tabela.</span><span class="sxs-lookup"><span data-stu-id="e23a0-106">The following table lists several possible uses for expression columns in a table.</span></span>  
  
|<span data-ttu-id="e23a0-107">Tipo de expressão</span><span class="sxs-lookup"><span data-stu-id="e23a0-107">Expression type</span></span>|<span data-ttu-id="e23a0-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e23a0-108">Example</span></span>|  
|---------------------|-------------|  
|<span data-ttu-id="e23a0-109">Comparação</span><span class="sxs-lookup"><span data-stu-id="e23a0-109">Comparison</span></span>|<span data-ttu-id="e23a0-110">"Total de > = 500"</span><span class="sxs-lookup"><span data-stu-id="e23a0-110">"Total >= 500"</span></span>|  
|<span data-ttu-id="e23a0-111">Computação</span><span class="sxs-lookup"><span data-stu-id="e23a0-111">Computation</span></span>|<span data-ttu-id="e23a0-112">"UnitPrice \* Quantity"</span><span class="sxs-lookup"><span data-stu-id="e23a0-112">"UnitPrice \* Quantity"</span></span>|  
|<span data-ttu-id="e23a0-113">Agregação</span><span class="sxs-lookup"><span data-stu-id="e23a0-113">Aggregation</span></span>|<span data-ttu-id="e23a0-114">Sum(Price)</span><span class="sxs-lookup"><span data-stu-id="e23a0-114">Sum(Price)</span></span>|  
  
 <span data-ttu-id="e23a0-115">Você pode definir a propriedade **expressão** em um objeto **DataColumn** existente ou pode incluir a propriedade como o terceiro argumento passado para o <xref:System.Data.DataColumn> Construtor, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e23a0-115">You can set the **Expression** property on an existing **DataColumn** object, or you can include the property as the third argument passed to the <xref:System.Data.DataColumn> constructor, as shown in the following example.</span></span>  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 <span data-ttu-id="e23a0-116">As expressões podem referenciar outras colunas de expressão; no entanto, uma referência circular, na qual duas expressões referenciam-se entre si, gerará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="e23a0-116">Expressions can reference other expression columns; however, a circular reference, in which two expressions reference each other, will generate an exception.</span></span> <span data-ttu-id="e23a0-117">Para regras sobre como escrever expressões, consulte <xref:System.Data.DataColumn.Expression%2A> a propriedade da classe **DataColumn** .</span><span class="sxs-lookup"><span data-stu-id="e23a0-117">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e23a0-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e23a0-118">See also</span></span>

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="e23a0-119">Definição de esquema de DataTable</span><span class="sxs-lookup"><span data-stu-id="e23a0-119">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="e23a0-120">DataTables</span><span class="sxs-lookup"><span data-stu-id="e23a0-120">DataTables</span></span>](datatables.md)
- <span data-ttu-id="e23a0-121">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="e23a0-121">[ADO.NET Overview](../ado-net-overview.md)</span></span>
