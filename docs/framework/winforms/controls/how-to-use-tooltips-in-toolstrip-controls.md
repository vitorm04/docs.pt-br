---
title: Como usar ToolTips em controles ToolStrip
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
ms.openlocfilehash: 2b10b3fcf3930d5848f1d7a9602cfcc945bc8975
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a>Como usar ToolTips em controles ToolStrip
Você pode exibir um <xref:System.Windows.Forms.ToolTip> para o <xref:System.Windows.Forms.ToolStrip> controle que você deseja, definindo o controle <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> propriedade `true`.  
  
### <a name="to-display-a-tooltip"></a>Para exibir uma dica de ferramenta  
  
-   Definir o <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> propriedade do controle para `true`.  
  
     O valor padrão de <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> é `true`e o valor padrão de <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> e <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> é `false`.  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a>Para usar a propriedade ToolTipText para o texto de dica de ferramenta de um ToolStripButton  
  
1.  Definir o <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> propriedade do botão para `true`.  
  
2.  Definir o <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> propriedade do botão para `false`.  
  
     O `AutoToolTip` é de propriedade `true` por padrão para <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, e <xref:System.Windows.Forms.ToolStripSplitButton>.  
  
     Um <xref:System.Windows.Forms.ToolStripButton> usa seu `Text` propriedade para o <xref:System.Windows.Forms.ToolTip> texto por padrão. Use este procedimento para exibir texto personalizado em um <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolTip>.  
  
> [!NOTE]
>  Se você definir <xref:System.Windows.Forms.ToolStripItemDisplayStyle> para <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> ou <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, nenhum texto será exibido no botão, mas a dica de ferramenta ainda é exibida.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>  
 <xref:System.Windows.Forms.ToolStripButton>  
 <xref:System.Windows.Forms.ToolStripDropDownButton>  
 <xref:System.Windows.Forms.ToolStripSplitButton>  
 [Visão geral do controle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
