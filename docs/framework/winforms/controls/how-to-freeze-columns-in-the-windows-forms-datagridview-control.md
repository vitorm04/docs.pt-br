---
title: 'Como: Congelar colunas no controle DataGridView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], freezing columns
- DataGridView control [Windows Forms], columns always in view
ms.assetid: 2ef8b1de-782e-4867-af8d-58171ab5c106
ms.openlocfilehash: a83c5078d67be40fda2ae3382b8124594ee78103
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966654"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="b613a-102">Como: Congelar colunas no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b613a-102">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b613a-103">Quando os usuários exibem dados exibidos em <xref:System.Windows.Forms.DataGridView> um controle de Windows Forms, às vezes eles precisam se referir a uma única coluna ou conjunto de colunas com frequência.</span><span class="sxs-lookup"><span data-stu-id="b613a-103">When users view data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, they sometimes need to refer to a single column or set of columns frequently.</span></span> <span data-ttu-id="b613a-104">Por exemplo, ao exibir uma tabela de informações do cliente que contém muitas colunas, é útil exibir o nome do cliente em todos os momentos enquanto permite que outras colunas rolem para fora da região visível.</span><span class="sxs-lookup"><span data-stu-id="b613a-104">For example, when displaying a table of customer information that contains many columns, it is useful to display the customer name at all times while enabling other columns to scroll outside the visible region.</span></span>  
  
 <span data-ttu-id="b613a-105">Para obter esse comportamento, você pode congelar colunas no controle.</span><span class="sxs-lookup"><span data-stu-id="b613a-105">To achieve this behavior, you can freeze columns in the control.</span></span> <span data-ttu-id="b613a-106">Quando você congela uma coluna, todas as colunas à esquerda (ou à direita em scripts de idioma da direita para esquerda) são congeladas também.</span><span class="sxs-lookup"><span data-stu-id="b613a-106">When you freeze a column, all the columns to its left (or to its right in right-to-left language scripts) are frozen as well.</span></span> <span data-ttu-id="b613a-107">Colunas congeladas permanecerão no local enquanto todas as outras colunas podem rolar.</span><span class="sxs-lookup"><span data-stu-id="b613a-107">Frozen columns remain in place while all other columns can scroll.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b613a-108">Se a reordenação de coluna estiver habilitada, as colunas congeladas serão tratadas como um grupo diferente das colunas não congeladas.</span><span class="sxs-lookup"><span data-stu-id="b613a-108">If column reordering is enabled, the frozen columns are treated as a group distinct from the unfrozen columns.</span></span> <span data-ttu-id="b613a-109">Os usuários podem reposicionar colunas em um dos grupos, mas não poderão mover uma coluna de um grupo para outro.</span><span class="sxs-lookup"><span data-stu-id="b613a-109">Users can reposition columns in either group, but they cannot move a column from one group to the other.</span></span>  
  
 <span data-ttu-id="b613a-110">A <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> propriedade de uma coluna determina se a coluna está sempre visível dentro da grade.</span><span class="sxs-lookup"><span data-stu-id="b613a-110">The <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> property of a column determines whether the column is always visible within the grid.</span></span>  
  
 <span data-ttu-id="b613a-111">Há suporte para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b613a-111">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="b613a-112">Consulte [também como: Congele colunas no controle Windows Forms DataGridView usando o designer](freeze-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="b613a-112">Also see [How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer](freeze-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-freeze-a-column-programmatically"></a><span data-ttu-id="b613a-113">Para congelar uma coluna programaticamente</span><span class="sxs-lookup"><span data-stu-id="b613a-113">To freeze a column programmatically</span></span>  
  
- <span data-ttu-id="b613a-114">Defina a propriedade <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> como `true`.</span><span class="sxs-lookup"><span data-stu-id="b613a-114">Set the <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b613a-115">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="b613a-115">Compiling the Code</span></span>  
 <span data-ttu-id="b613a-116">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="b613a-116">This example requires:</span></span>  
  
- <span data-ttu-id="b613a-117">Um <xref:System.Windows.Forms.DataGridView> controle chamado `dataGridView1` que contém uma coluna chamada `AddToCartButton`.</span><span class="sxs-lookup"><span data-stu-id="b613a-117">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `AddToCartButton`.</span></span>  
  
- <span data-ttu-id="b613a-118">Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b613a-118">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b613a-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b613a-119">See also</span></span>

- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="b613a-120">Funcionalidades de coluna, linha e célula básicas no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b613a-120">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="b613a-121">Como: Habilitar reordenação de coluna no controle Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b613a-121">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>](how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)
