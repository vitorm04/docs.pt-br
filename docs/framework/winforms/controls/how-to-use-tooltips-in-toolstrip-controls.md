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
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a><span data-ttu-id="2143e-102">Como: Usar ToolTips em controles ToolStrip</span><span class="sxs-lookup"><span data-stu-id="2143e-102">How to: Use ToolTips in ToolStrip Controls</span></span>
<span data-ttu-id="2143e-103">Você pode exibir um <xref:System.Windows.Forms.ToolTip> para o <xref:System.Windows.Forms.ToolStrip> controle desejado definindo a propriedade do <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> controle como `true`.</span><span class="sxs-lookup"><span data-stu-id="2143e-103">You can display a <xref:System.Windows.Forms.ToolTip> for the <xref:System.Windows.Forms.ToolStrip> control you want by setting the control's <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property to `true`.</span></span>  
  
### <a name="to-display-a-tooltip"></a><span data-ttu-id="2143e-104">Para exibir uma dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="2143e-104">To display a ToolTip</span></span>  
  
- <span data-ttu-id="2143e-105">Defina a <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> Propriedade do controle como `true`.</span><span class="sxs-lookup"><span data-stu-id="2143e-105">Set the <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property of the control to `true`.</span></span>  
  
     <span data-ttu-id="2143e-106">O valor padrão de <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> é `true`, e o valor padrão de <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> e <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="2143e-106">The default value of <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> is `true`, and the default value of <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> is `false`.</span></span>  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a><span data-ttu-id="2143e-107">Para usar a propriedade ToolTipText para o texto de dica de ferramenta de um ToolStripButton</span><span class="sxs-lookup"><span data-stu-id="2143e-107">To use the ToolTipText property for the ToolTip text of a ToolStripButton</span></span>  
  
1. <span data-ttu-id="2143e-108">Defina a <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> Propriedade do botão como `true`.</span><span class="sxs-lookup"><span data-stu-id="2143e-108">Set the <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property of the button to `true`.</span></span>  
  
2. <span data-ttu-id="2143e-109">Defina a <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> Propriedade do botão como `false`.</span><span class="sxs-lookup"><span data-stu-id="2143e-109">Set the <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> property of the button to `false`.</span></span>  
  
     <span data-ttu-id="2143e-110">A `AutoToolTip` propriedade é `true` por padrão para <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>e. <xref:System.Windows.Forms.ToolStripSplitButton></span><span class="sxs-lookup"><span data-stu-id="2143e-110">The `AutoToolTip` property is `true` by default for <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, and <xref:System.Windows.Forms.ToolStripSplitButton>.</span></span>  
  
     <span data-ttu-id="2143e-111">Um <xref:System.Windows.Forms.ToolStripButton> usa sua `Text` propriedade para o <xref:System.Windows.Forms.ToolTip> texto por padrão.</span><span class="sxs-lookup"><span data-stu-id="2143e-111">A <xref:System.Windows.Forms.ToolStripButton> uses its `Text` property for the <xref:System.Windows.Forms.ToolTip> text by default.</span></span> <span data-ttu-id="2143e-112">Use este procedimento para exibir texto personalizado em um <xref:System.Windows.Forms.ToolStripButton>. <xref:System.Windows.Forms.ToolTip></span><span class="sxs-lookup"><span data-stu-id="2143e-112">Use this procedure to display custom text in a <xref:System.Windows.Forms.ToolStripButton><xref:System.Windows.Forms.ToolTip>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2143e-113">Se você definir <xref:System.Windows.Forms.ToolStripItemDisplayStyle> como <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> ou <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, nenhum texto será exibido no botão, mas a dica de ferramenta ainda aparecerá.</span><span class="sxs-lookup"><span data-stu-id="2143e-113">If you set <xref:System.Windows.Forms.ToolStripItemDisplayStyle> to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, no text will appear on the button, but the tool tip still appears.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2143e-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2143e-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>
- <xref:System.Windows.Forms.ToolStripButton>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- <xref:System.Windows.Forms.ToolStripSplitButton>
- [<span data-ttu-id="2143e-115">Visão geral do controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="2143e-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
