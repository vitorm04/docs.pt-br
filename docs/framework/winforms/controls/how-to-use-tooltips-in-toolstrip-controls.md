---
title: 'Como: Usar ToolTips em controles ToolStrip'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
ms.openlocfilehash: 3f383b6cccba7825637ea65a0e13280b91b406c9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939726"
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a>Como: Usar ToolTips em controles ToolStrip
Você pode exibir um <xref:System.Windows.Forms.ToolTip> para o <xref:System.Windows.Forms.ToolStrip> controle desejado definindo a propriedade do <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> controle como `true`.  
  
### <a name="to-display-a-tooltip"></a>Para exibir uma dica de ferramenta  
  
- Defina a <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> Propriedade do controle como `true`.  
  
     O valor padrão de <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> é `true`, e o valor padrão de <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> e <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> é `false`.  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a>Para usar a propriedade ToolTipText para o texto de dica de ferramenta de um ToolStripButton  
  
1. Defina a <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> Propriedade do botão como `true`.  
  
2. Defina a <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> Propriedade do botão como `false`.  
  
     A `AutoToolTip` propriedade é `true` por padrão para <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>e. <xref:System.Windows.Forms.ToolStripSplitButton>  
  
     Um <xref:System.Windows.Forms.ToolStripButton> usa sua `Text` propriedade para o <xref:System.Windows.Forms.ToolTip> texto por padrão. Use este procedimento para exibir texto personalizado em um <xref:System.Windows.Forms.ToolStripButton>. <xref:System.Windows.Forms.ToolTip>  
  
> [!NOTE]
> Se você definir <xref:System.Windows.Forms.ToolStripItemDisplayStyle> como <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> ou <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, nenhum texto será exibido no botão, mas a dica de ferramenta ainda aparecerá.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>
- <xref:System.Windows.Forms.ToolStripButton>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- <xref:System.Windows.Forms.ToolStripSplitButton>
- [Visão geral do controle ToolStrip](toolstrip-control-overview-windows-forms.md)
