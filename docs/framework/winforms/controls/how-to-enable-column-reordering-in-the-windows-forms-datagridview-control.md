---
title: 'Como: Habilitar a reorganização da coluna no controle DataGridView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], reordering columns
- columns [Windows Forms], reordering
ms.assetid: cc20eae3-e4db-493f-95ce-a4215e29472a
ms.openlocfilehash: 625c4987a45ed3749284e7abc7b6cde6d24821ca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59161467"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="8741c-102">Como: Habilitar a reorganização da coluna no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8741c-102">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="8741c-103">Quando você habilitar a reorganização da coluna no <xref:System.Windows.Forms.DataGridView> controle, os usuários podem mover uma coluna para uma nova posição, arrastando o cabeçalho de coluna com o mouse.</span><span class="sxs-lookup"><span data-stu-id="8741c-103">When you enable column reordering in the <xref:System.Windows.Forms.DataGridView> control, users can move a column to a new position by dragging the column header with the mouse.</span></span> <span data-ttu-id="8741c-104">No <xref:System.Windows.Forms.DataGridView> controle, o <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> valor da propriedade determina se os usuários podem mover colunas em diferentes posições.</span><span class="sxs-lookup"><span data-stu-id="8741c-104">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> property value determines whether users can move columns to different positions.</span></span>  
  
 <span data-ttu-id="8741c-105">Há suporte para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8741c-105">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="8741c-106">Consulte também [como: Habilitar a reorganização da coluna em que o Windows Forms usando o Designer de controle de DataGridView](enable-column-reordering-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="8741c-106">Also see [How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer](enable-column-reordering-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-enable-column-reordering-programmatically"></a><span data-ttu-id="8741c-107">Para habilitar a reordenação de forma programática de coluna</span><span class="sxs-lookup"><span data-stu-id="8741c-107">To enable column reordering programmatically</span></span>  
  
-   <span data-ttu-id="8741c-108">Defina a propriedade <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> como `true`.</span><span class="sxs-lookup"><span data-stu-id="8741c-108">Set the <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#060](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#060)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#060](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#060)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8741c-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="8741c-109">Compiling the Code</span></span>  
 <span data-ttu-id="8741c-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="8741c-110">This example requires:</span></span>  
  
-   <span data-ttu-id="8741c-111">Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="8741c-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="8741c-112">Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8741c-112">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8741c-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8741c-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8741c-114">Funcionalidades de coluna, linha e célula básicas no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8741c-114">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="8741c-115">Como: Congelar colunas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8741c-115">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>](how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)
