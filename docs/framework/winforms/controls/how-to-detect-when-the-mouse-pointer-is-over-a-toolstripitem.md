---
title: 'Como: Detectar quando o ponteiro do mouse passa sobre um ToolStripItem'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], detecting mouse movement
- ToolStrip control [Windows Forms], detecting mouse movement
- ToolStripItem class [Windows Forms], detecting mouse movement
- mouse [Windows Forms], detecting movement on toolbars
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
ms.openlocfilehash: f01a9acb3a566be40d65fb075c8487d4e9cb6e73
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623636"
---
# <a name="how-to-detect-when-the-mouse-pointer-is-over-a-toolstripitem"></a><span data-ttu-id="0662e-102">Como: Detectar quando o ponteiro do mouse passa sobre um ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="0662e-102">How to: Detect When the Mouse Pointer Is Over a ToolStripItem</span></span>
<span data-ttu-id="0662e-103">Use o procedimento a seguir para detectar quando o ponteiro do mouse sobre um <xref:System.Windows.Forms.ToolStripItem>.</span><span class="sxs-lookup"><span data-stu-id="0662e-103">Use the following procedure to detect when the mouse pointer is over a <xref:System.Windows.Forms.ToolStripItem>.</span></span>  
  
### <a name="to-detect-when-the-pointer-is-over-a-toolstripitem"></a><span data-ttu-id="0662e-104">Para detectar quando o ponteiro está sobre um ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="0662e-104">To detect when the pointer is over a ToolStripItem</span></span>  
  
- <span data-ttu-id="0662e-105">Use o <xref:System.Windows.Forms.ToolStripItem.Selected%2A> propriedade para itens em que <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> é `true`.</span><span class="sxs-lookup"><span data-stu-id="0662e-105">Use the <xref:System.Windows.Forms.ToolStripItem.Selected%2A> property for items in which <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> is `true`.</span></span>  
  
     <span data-ttu-id="0662e-106">Isso impedirá que você precise sincronizar o <xref:System.Windows.Forms.ToolStripItem.MouseEnter> e <xref:System.Windows.Forms.ToolStripItem.MouseLeave> eventos.</span><span class="sxs-lookup"><span data-stu-id="0662e-106">This will prevent you from having to synchronize the <xref:System.Windows.Forms.ToolStripItem.MouseEnter> and <xref:System.Windows.Forms.ToolStripItem.MouseLeave> events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0662e-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0662e-107">See also</span></span>

- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripItem.Selected%2A>
- [<span data-ttu-id="0662e-108">Visão geral do controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="0662e-108">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
