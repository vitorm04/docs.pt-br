---
title: Como usar ToolTips em controles ToolStrip
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d81a1936d8a6159c6225a12f712c546fe9beeb7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a><span data-ttu-id="c6686-102">Como usar ToolTips em controles ToolStrip</span><span class="sxs-lookup"><span data-stu-id="c6686-102">How to: Use ToolTips in ToolStrip Controls</span></span>
<span data-ttu-id="c6686-103">Você pode exibir um <xref:System.Windows.Forms.ToolTip> para o <xref:System.Windows.Forms.ToolStrip> controle que você deseja, definindo o controle <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="c6686-103">You can display a <xref:System.Windows.Forms.ToolTip> for the <xref:System.Windows.Forms.ToolStrip> control you want by setting the control's <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property to `true`.</span></span>  
  
### <a name="to-display-a-tooltip"></a><span data-ttu-id="c6686-104">Para exibir uma dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="c6686-104">To display a ToolTip</span></span>  
  
-   <span data-ttu-id="c6686-105">Definir o <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> propriedade do controle para `true`.</span><span class="sxs-lookup"><span data-stu-id="c6686-105">Set the <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property of the control to `true`.</span></span>  
  
     <span data-ttu-id="c6686-106">O valor padrão de <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> é `true`e o valor padrão de <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> e <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="c6686-106">The default value of <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> is `true`, and the default value of <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> is `false`.</span></span>  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a><span data-ttu-id="c6686-107">Para usar a propriedade ToolTipText para o texto de dica de ferramenta de um ToolStripButton</span><span class="sxs-lookup"><span data-stu-id="c6686-107">To use the ToolTipText property for the ToolTip text of a ToolStripButton</span></span>  
  
1.  <span data-ttu-id="c6686-108">Definir o <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> propriedade do botão para `true`.</span><span class="sxs-lookup"><span data-stu-id="c6686-108">Set the <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property of the button to `true`.</span></span>  
  
2.  <span data-ttu-id="c6686-109">Definir o <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> propriedade do botão para `false`.</span><span class="sxs-lookup"><span data-stu-id="c6686-109">Set the <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> property of the button to `false`.</span></span>  
  
     <span data-ttu-id="c6686-110">O `AutoToolTip` é de propriedade `true` por padrão para <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, e <xref:System.Windows.Forms.ToolStripSplitButton>.</span><span class="sxs-lookup"><span data-stu-id="c6686-110">The `AutoToolTip` property is `true` by default for <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, and <xref:System.Windows.Forms.ToolStripSplitButton>.</span></span>  
  
     <span data-ttu-id="c6686-111">Um <xref:System.Windows.Forms.ToolStripButton> usa seu `Text` propriedade para o <xref:System.Windows.Forms.ToolTip> texto por padrão.</span><span class="sxs-lookup"><span data-stu-id="c6686-111">A <xref:System.Windows.Forms.ToolStripButton> uses its `Text` property for the <xref:System.Windows.Forms.ToolTip> text by default.</span></span> <span data-ttu-id="c6686-112">Use este procedimento para exibir texto personalizado em um <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="c6686-112">Use this procedure to display custom text in a <xref:System.Windows.Forms.ToolStripButton><xref:System.Windows.Forms.ToolTip>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6686-113">Se você definir <xref:System.Windows.Forms.ToolStripItemDisplayStyle> para <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> ou <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, nenhum texto será exibido no botão, mas a dica de ferramenta ainda é exibida.</span><span class="sxs-lookup"><span data-stu-id="c6686-113">If you set <xref:System.Windows.Forms.ToolStripItemDisplayStyle> to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, no text will appear on the button, but the tool tip still appears.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6686-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6686-114">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>  
 <xref:System.Windows.Forms.ToolStripButton>  
 <xref:System.Windows.Forms.ToolStripDropDownButton>  
 <xref:System.Windows.Forms.ToolStripSplitButton>  
 [<span data-ttu-id="c6686-115">Visão geral do controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="c6686-115">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
