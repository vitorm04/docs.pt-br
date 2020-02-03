---
title: Tornar as colunas somente leitura no controle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], read-only columns
- DataGridView control [Windows Forms], read-only columns
ms.assetid: 2bb73ebb-1a55-4362-9fda-e50574c087d5
ms.openlocfilehash: 11d008d47ec5edb594d3d862c68ff3b9920e0e25
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736190"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="da648-102">Como deixar colunas somente leitura no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="da648-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="da648-103">Nem todos os dados destinam-se à edição.</span><span class="sxs-lookup"><span data-stu-id="da648-103">Not all data is meant for editing.</span></span> <span data-ttu-id="da648-104">No controle <xref:System.Windows.Forms.DataGridView>, o valor da propriedade <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> da coluna determina se os usuários podem editar células nessa coluna.</span><span class="sxs-lookup"><span data-stu-id="da648-104">In the <xref:System.Windows.Forms.DataGridView> control, the column <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property value determines whether users can edit cells in that column.</span></span> <span data-ttu-id="da648-105">Para obter informações sobre como tornar o controle totalmente somente leitura, consulte [como impedir a adição e exclusão de linhas no controle Windows Forms DataGridView](prevent-row-addition-and-deletion-datagridview.md).</span><span class="sxs-lookup"><span data-stu-id="da648-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](prevent-row-addition-and-deletion-datagridview.md).</span></span>  
  
 <span data-ttu-id="da648-106">Há suporte para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="da648-106">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="da648-107">Consulte também [como: tornar as colunas somente leitura no controle Windows Forms DataGridView usando o designer](make-columns-read-only-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="da648-107">Also see [How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer](make-columns-read-only-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-make-a-column-read-only-programmatically"></a><span data-ttu-id="da648-108">Para tornar uma coluna somente leitura programaticamente</span><span class="sxs-lookup"><span data-stu-id="da648-108">To make a column read-only programmatically</span></span>  
  
- <span data-ttu-id="da648-109">Defina a propriedade <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> como `true`.</span><span class="sxs-lookup"><span data-stu-id="da648-109">Set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#064](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#064)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#064](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#064)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="da648-110">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="da648-110">Compiling the Code</span></span>  
 <span data-ttu-id="da648-111">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="da648-111">This example requires:</span></span>  
  
- <span data-ttu-id="da648-112">Um controle de <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1` com uma coluna denominada `CompanyName`.</span><span class="sxs-lookup"><span data-stu-id="da648-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` with a column named `CompanyName`.</span></span>  
  
- <span data-ttu-id="da648-113">Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="da648-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da648-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da648-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="da648-115">Funcionalidades de coluna, linha e célula básicas no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="da648-115">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="da648-116">Como evitar a adição e a exclusão de linha no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="da648-116">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>](prevent-row-addition-and-deletion-datagridview.md)
