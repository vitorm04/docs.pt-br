---
title: Como definir o modo de seleção do controle DataGridView dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
- data grids [Windows Forms], selection mode
ms.assetid: 2f241643-7f82-4583-8757-03494f63b465
ms.openlocfilehash: d064dee497f1e5b07e74c5cd4e1d322ac0ff344e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533550"
---
# <a name="how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="b8cea-102">Como definir o modo de seleção do controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b8cea-102">How to: Set the Selection Mode of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b8cea-103">O exemplo de código a seguir demonstra como configurar um <xref:System.Windows.Forms.DataGridView> controle para que clicar em qualquer lugar dentro de uma linha automaticamente seleciona a linha inteira e portanto pode ser selecionada para que somente uma linha por vez.</span><span class="sxs-lookup"><span data-stu-id="b8cea-103">The following code example demonstrates how to configure a <xref:System.Windows.Forms.DataGridView> control so that clicking anywhere within a row automatically selects the entire row, and so that only one row at a time can be selected.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8cea-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b8cea-104">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#065](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#065)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#065](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#065)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b8cea-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="b8cea-105">Compiling the Code</span></span>  
 <span data-ttu-id="b8cea-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="b8cea-106">This example requires:</span></span>  
  
-   <span data-ttu-id="b8cea-107">Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="b8cea-107">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="b8cea-108">Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b8cea-108">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8cea-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8cea-109">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>  
 <xref:System.Windows.Forms.DataGridViewSelectionMode>  
 [<span data-ttu-id="b8cea-110">Seleção e uso da Área de Transferência com o controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b8cea-110">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="b8cea-111">Modos de seleção no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b8cea-111">Selection Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)
