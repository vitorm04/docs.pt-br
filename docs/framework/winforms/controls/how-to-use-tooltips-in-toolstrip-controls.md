---
title: 'Como: Usar ToolTips em controles ToolStrip'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
ms.openlocfilehash: b009d19ed949edbd52ec02252ba1e2271e4cb738
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64750566"
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a>Como: Usar ToolTips em controles ToolStrip
Você pode exibir uma <xref:System.Windows.Forms.ToolTip> para o <xref:System.Windows.Forms.ToolStrip> controle que você deseja, definindo o controle <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> propriedade `true`.  
  
### <a name="to-display-a-tooltip"></a>Para exibir uma dica de ferramenta  
  
- Defina as <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> propriedade do controle para `true`.  
  
     O valor padrão de <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> está `true`e o valor padrão de <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> e <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> é `false`.  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a>Para usar a propriedade ToolTipText para o texto de dica de ferramenta de um ToolStripButton  
  
1. Defina as <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> propriedade do botão para `true`.  
  
2. Defina as <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> propriedade do botão para `false`.  
  
     O `AutoToolTip` é de propriedade `true` por padrão para <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, e <xref:System.Windows.Forms.ToolStripSplitButton>.  
  
     Um <xref:System.Windows.Forms.ToolStripButton> usa sua `Text` propriedade para o <xref:System.Windows.Forms.ToolTip> texto por padrão. Use este procedimento para exibir o texto personalizado em um <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolTip>.  
  
> [!NOTE]
>  Se você definir <xref:System.Windows.Forms.ToolStripItemDisplayStyle> à <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> ou <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, nenhum texto será exibido no botão, mas ainda aparecerá a dica de ferramenta.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>
- <xref:System.Windows.Forms.ToolStripButton>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- <xref:System.Windows.Forms.ToolStripSplitButton>
- [Visão geral do controle ToolStrip](toolstrip-control-overview-windows-forms.md)
