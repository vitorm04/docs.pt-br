---
title: Como identificar o evento de abertura ContextMenuStrip
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 354631e514d9e2ece39d16bf7f259c36e4f90c32
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-handle-the-contextmenustrip-opening-event"></a><span data-ttu-id="be594-102">Como identificar o evento de abertura ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="be594-102">How to: Handle the ContextMenuStrip Opening Event</span></span>
<span data-ttu-id="be594-103">Você pode personalizar o comportamento do seu <xref:System.Windows.Forms.ContextMenuStrip> controle manipulando o <xref:System.Windows.Forms.ToolStripDropDown.Opening> evento.</span><span class="sxs-lookup"><span data-stu-id="be594-103">You can customize the behavior of your <xref:System.Windows.Forms.ContextMenuStrip> control by handling the <xref:System.Windows.Forms.ToolStripDropDown.Opening> event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be594-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="be594-104">Example</span></span>  
 <span data-ttu-id="be594-105">O exemplo de código a seguir demonstra como tratar o <xref:System.Windows.Forms.ToolStripDropDown.Opening> evento.</span><span class="sxs-lookup"><span data-stu-id="be594-105">The following code example demonstrates how to handle the <xref:System.Windows.Forms.ToolStripDropDown.Opening> event.</span></span> <span data-ttu-id="be594-106">O manipulador de eventos adiciona itens dinamicamente a um <xref:System.Windows.Forms.ContextMenuStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="be594-106">The event handler adds items dynamically to a <xref:System.Windows.Forms.ContextMenuStrip> control.</span></span> <span data-ttu-id="be594-107">Para o exemplo de código completo, consulte [como: adicionar itens de ToolStrip dinamicamente](../../../../docs/framework/winforms/controls/how-to-add-toolstrip-items-dynamically.md).</span><span class="sxs-lookup"><span data-stu-id="be594-107">For the complete code example, see [How to: Add ToolStrip Items Dynamically](../../../../docs/framework/winforms/controls/how-to-add-toolstrip-items-dynamically.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#42)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#42)]  
  
 <span data-ttu-id="be594-108">Definir o <xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=nameWithType> propriedade `true` para impedir a abertura de menu.</span><span class="sxs-lookup"><span data-stu-id="be594-108">Set the <xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=nameWithType> property to `true` to prevent the menu from opening.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be594-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be594-109">See Also</span></span>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>  
 <xref:System.Windows.Forms.ToolStripDropDown>  
 [<span data-ttu-id="be594-110">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="be594-110">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
