---
title: Como detectar quando o ponteiro do mouse passa sobre um ToolStripItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Windows Forms], detecting mouse movement
- ToolStrip control [Windows Forms], detecting mouse movement
- ToolStripItem class [Windows Forms], detecting mouse movement
- mouse [Windows Forms], detecting movement on toolbars
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 633b92bf6da837b3727001c621548fa58b230102
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
