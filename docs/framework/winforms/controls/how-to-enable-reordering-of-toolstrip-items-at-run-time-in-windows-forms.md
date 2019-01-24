---
title: 'Como: Habilitar a reorganização de itens ToolStrip em tempo de execução no Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], examples
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], rearranging controls
- ToolStrip control [Windows Forms], reordering items
ms.assetid: 8480b69a-379f-4dc2-8dcf-365ed93692b2
ms.openlocfilehash: 0b3662a700d897607780e8d5032c498faff97753
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577013"
---
# <a name="how-to-enable-reordering-of-toolstrip-items-at-run-time-in-windows-forms"></a>Como: Habilitar a reorganização de itens ToolStrip em tempo de execução no Windows Forms
Você pode permitir que o usuário reorganizar <xref:System.Windows.Forms.ToolStripItem> controles no <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="to-enable-toolstripitem-rearrangement-at-run-time"></a>Para habilitar a reorganização de ToolStripItem em tempo de execução  
  
-   Defina a propriedade <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> como `true`. Por padrão, <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> é `false`.  
  
     Em tempo de execução, o usuário mantiver pressionada a tecla ALT e o botão esquerdo do mouse para arrastar um <xref:System.Windows.Forms.ToolStripItem> em um local diferente no <xref:System.Windows.Forms.ToolStrip>.  
  
    ```vb  
    toolStrip1.AllowItemReorder = True  
    ```  
  
    ```csharp  
    toolStrip1.AllowItemReorder = true;  
    ```  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>
- [Visão geral do controle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
- [Arquitetura de controle do ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)
- [Resumo da tecnologia de ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
