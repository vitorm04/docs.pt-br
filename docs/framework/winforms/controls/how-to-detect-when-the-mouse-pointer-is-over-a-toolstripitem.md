---
title: 'Como: Detectar quando o ponteiro do Mouse sobre um ToolStripItem'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], detecting mouse movement
- ToolStrip control [Windows Forms], detecting mouse movement
- ToolStripItem class [Windows Forms], detecting mouse movement
- mouse [Windows Forms], detecting movement on toolbars
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
ms.openlocfilehash: 20fbc91773f431fc68f606f8aa9f24f4c0cc06bf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539591"
---
# <a name="how-to-detect-when-the-mouse-pointer-is-over-a-toolstripitem"></a>Como: Detectar quando o ponteiro do Mouse sobre um ToolStripItem
Use o procedimento a seguir para detectar quando o ponteiro do mouse sobre um <xref:System.Windows.Forms.ToolStripItem>.  
  
### <a name="to-detect-when-the-pointer-is-over-a-toolstripitem"></a>Para detectar quando o ponteiro está sobre um ToolStripItem  
  
-   Use o <xref:System.Windows.Forms.ToolStripItem.Selected%2A> propriedade para itens em que <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> é `true`.  
  
     Isso impedirá que você precise sincronizar o <xref:System.Windows.Forms.ToolStripItem.MouseEnter> e <xref:System.Windows.Forms.ToolStripItem.MouseLeave> eventos.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripItem.Selected%2A>
- [Visão geral do controle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
