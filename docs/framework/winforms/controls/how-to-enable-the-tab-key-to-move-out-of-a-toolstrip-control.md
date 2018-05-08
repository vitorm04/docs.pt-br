---
title: Como habilitar a tecla TAB para deixar um controle ToolStrip
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], moving between
- TAB key [Windows Forms], enabling
- ToolStrip control [Windows Forms], moving from
ms.assetid: 40f9e88b-09a3-428e-8da8-c00bb65079c6
ms.openlocfilehash: 0af6c4c308ac1988b5f1babd80897afd5bf6a4d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enable-the-tab-key-to-move-out-of-a-toolstrip-control"></a>Como habilitar a tecla TAB para deixar um controle ToolStrip
Use o procedimento a seguir para permitir que o usuário pressionar a tecla TAB para mover de um <xref:System.Windows.Forms.ToolStrip> para o próximo controle na ordem de tabulação.  
  
 O <xref:System.Windows.Forms.ToolStrip> aceita a primeira pressione a tecla TAB e os chaves de seta para selecionar itens dentro de <xref:System.Windows.Forms.ToolStrip>. Quando o usuário pressiona a tecla TAB uma segunda vez, ele leva o usuário para o próximo controle na ordem de tabulação.  
  
### <a name="to-enable-the-user-to-press-the-tab-key-to-move-out-of-a-toolstrip-to-the-next-control"></a>Para permitir que o usuário pressionar a tecla TAB para mover para fora de um ToolStrip para o próximo controle  
  
-   Definir o <xref:System.Windows.Forms.ToolStrip.TabStop%2A> propriedade o <xref:System.Windows.Forms.ToolStrip> para `true`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStrip.TabStop%2A>  
 [Visão geral do controle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
