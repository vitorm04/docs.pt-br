---
title: Personalizar a aparência das células no controle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing cells
- DataGridView control [Windows Forms], customizing cells
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 478b20c9-625c-4116-9c5c-5a16e6f4ec67
ms.openlocfilehash: 754932427a365a7b032c1ac9627d3237d1f7d0c6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744047"
---
# <a name="how-to-customize-the-appearance-of-cells-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="f8388-102">Como personalizar a aparência de células no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f8388-102">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f8388-103">Você pode personalizar a aparência de qualquer célula manipulando o evento <xref:System.Windows.Forms.DataGridView.CellPainting> do controle de <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="f8388-103">You can customize the appearance of any cell by handling the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CellPainting> event.</span></span> <span data-ttu-id="f8388-104">Você pode extrair o <xref:System.Drawing.Graphics> do controle de <xref:System.Windows.Forms.DataGridView> da propriedade <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> do <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="f8388-104">You can extract the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Drawing.Graphics> from the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> property of the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>.</span></span> <span data-ttu-id="f8388-105">Com esse <xref:System.Drawing.Graphics>, você pode afetar a aparência de todo o controle de <xref:System.Windows.Forms.DataGridView>, mas geralmente desejará afetar apenas a aparência da célula que está sendo pintada no momento.</span><span class="sxs-lookup"><span data-stu-id="f8388-105">With this <xref:System.Drawing.Graphics>, you can affect the appearance of the entire <xref:System.Windows.Forms.DataGridView> control, but you will usually want to affect only the appearance of the cell that is currently being painted.</span></span> <span data-ttu-id="f8388-106">A propriedade <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> da <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> permite que você restrinja suas operações de pintura para a célula que está sendo pintada no momento.</span><span class="sxs-lookup"><span data-stu-id="f8388-106">The <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> property of the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> enables you to restrict your painting operations to the cell that is currently being painted.</span></span>  
  
 <span data-ttu-id="f8388-107">No exemplo de código a seguir, você irá pintar todas as células em uma `ContactName` coluna usando o esquema de cores do controle de <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="f8388-107">In the following code example, you will paint all the cells in a `ContactName` column using the <xref:System.Windows.Forms.DataGridView> control's color scheme.</span></span> <span data-ttu-id="f8388-108">O conteúdo de texto de cada célula é pintado em <xref:System.Drawing.Color.Crimson%2A>e um retângulo de inserção é desenhado na mesma cor que a propriedade <xref:System.Windows.Forms.DataGridView.GridColor%2A> do controle de <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="f8388-108">Each cell's text content is painted in <xref:System.Drawing.Color.Crimson%2A>, and an inset rectangle is drawn in the same color as the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.GridColor%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8388-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f8388-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f8388-110">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="f8388-110">Compiling the Code</span></span>  
 <span data-ttu-id="f8388-111">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="f8388-111">This example requires:</span></span>  
  
- <span data-ttu-id="f8388-112">Um controle de <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1` com uma coluna `ContactName` como a da tabela Customers no banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="f8388-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` with a `ContactName` column such as the one in the Customers table in the Northwind sample database.</span></span>  
  
- <span data-ttu-id="f8388-113">Referências aos assemblies System, System.Windows.Forms e System.Drawing.</span><span class="sxs-lookup"><span data-stu-id="f8388-113">References to the System, System.Windows.Forms, and System.Drawing assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8388-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="f8388-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellPainting>
- [<span data-ttu-id="f8388-115">Personalizando o controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f8388-115">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
