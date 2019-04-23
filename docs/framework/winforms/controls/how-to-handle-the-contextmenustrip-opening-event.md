---
title: 'Como: Identificar o evento de abertura ContextMenuStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrip control [Windows Forms]
- context menus [Windows Forms], event handling
- ToolStrip control [Windows Forms]
- event handling [Windows Forms], context menus
- shortcut menus [Windows Forms], event handling
ms.assetid: b661b3dd-7815-4cc2-a1aa-a9a391ab3427
ms.openlocfilehash: 3001480959ef90cb31048cbcf70aeff1632979fb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59170703"
---
# <a name="how-to-handle-the-contextmenustrip-opening-event"></a><span data-ttu-id="47ac2-102">Como: Identificar o evento de abertura ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="47ac2-102">How to: Handle the ContextMenuStrip Opening Event</span></span>
<span data-ttu-id="47ac2-103">Você pode personalizar o comportamento do seu <xref:System.Windows.Forms.ContextMenuStrip> controle manipulando o <xref:System.Windows.Forms.ToolStripDropDown.Opening> eventos.</span><span class="sxs-lookup"><span data-stu-id="47ac2-103">You can customize the behavior of your <xref:System.Windows.Forms.ContextMenuStrip> control by handling the <xref:System.Windows.Forms.ToolStripDropDown.Opening> event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47ac2-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="47ac2-104">Example</span></span>  
 <span data-ttu-id="47ac2-105">O exemplo de código a seguir demonstra como manipular o <xref:System.Windows.Forms.ToolStripDropDown.Opening> eventos.</span><span class="sxs-lookup"><span data-stu-id="47ac2-105">The following code example demonstrates how to handle the <xref:System.Windows.Forms.ToolStripDropDown.Opening> event.</span></span> <span data-ttu-id="47ac2-106">O manipulador de eventos adiciona itens dinamicamente para um <xref:System.Windows.Forms.ContextMenuStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="47ac2-106">The event handler adds items dynamically to a <xref:System.Windows.Forms.ContextMenuStrip> control.</span></span> <span data-ttu-id="47ac2-107">No exemplo de código completo, consulte [como: Adicionar itens ToolStrip dinamicamente](how-to-add-toolstrip-items-dynamically.md).</span><span class="sxs-lookup"><span data-stu-id="47ac2-107">For the complete code example, see [How to: Add ToolStrip Items Dynamically](how-to-add-toolstrip-items-dynamically.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#42)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#42)]  
  
 <span data-ttu-id="47ac2-108">Defina as <xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=nameWithType> propriedade para `true` para impedir a abertura de menu.</span><span class="sxs-lookup"><span data-stu-id="47ac2-108">Set the <xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=nameWithType> property to `true` to prevent the menu from opening.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47ac2-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47ac2-109">See also</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>
- <xref:System.Windows.Forms.ToolStripDropDown>
- [<span data-ttu-id="47ac2-110">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="47ac2-110">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
