---
title: Como detectar quando o ponteiro do mouse passa sobre um ToolStripItem
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], detecting mouse movement
- ToolStrip control [Windows Forms], detecting mouse movement
- ToolStripItem class [Windows Forms], detecting mouse movement
- mouse [Windows Forms], detecting movement on toolbars
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
ms.openlocfilehash: 15a7562efd9a86a029754610ffd9e77c372d1ac2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-detect-when-the-mouse-pointer-is-over-a-toolstripitem"></a>Como detectar quando o ponteiro do mouse passa sobre um ToolStripItem
Use o procedimento a seguir para detectar quando o ponteiro do mouse está sobre um <xref:System.Windows.Forms.ToolStripItem>.  
  
### <a name="to-detect-when-the-pointer-is-over-a-toolstripitem"></a>Detectar quando o ponteiro passa sobre um ToolStripItem  
  
-   Use o <xref:System.Windows.Forms.ToolStripItem.Selected%2A> propriedade para itens na qual <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> é `true`.  
  
     Isso impedirá que você precise sincronizar o <xref:System.Windows.Forms.ToolStripItem.MouseEnter> e <xref:System.Windows.Forms.ToolStripItem.MouseLeave> eventos.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripItem.Selected%2A>  
 [Visão geral do controle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
