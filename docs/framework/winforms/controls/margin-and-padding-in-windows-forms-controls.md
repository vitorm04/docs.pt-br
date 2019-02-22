---
title: Margem e preenchimento em controles dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Padding property [Windows Forms]
- layout [Windows Forms], margins and padding
- Windows Forms, layout
- Margin property [Windows Forms]
ms.assetid: 3781b5a1-3085-4072-bed0-44670c23ffdc
ms.openlocfilehash: a3218ad029735f4a5d70b3166951dcd93e061c26
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56665219"
---
# <a name="margin-and-padding-in-windows-forms-controls"></a><span data-ttu-id="248b1-102">Margem e preenchimento em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="248b1-102">Margin and Padding in Windows Forms Controls</span></span>
<span data-ttu-id="248b1-103">O posicionamento exato dos controles no formulário é uma prioridade alta para muitos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="248b1-103">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="248b1-104">O <xref:System.Windows.Forms?displayProperty=nameWithType> namespace fornece muitos recursos de layout para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="248b1-104">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace gives you many layout features to accomplish this.</span></span> <span data-ttu-id="248b1-105">Duas das mais importantes são as <xref:System.Windows.Forms.Control.Margin%2A> e <xref:System.Windows.Forms.Control.Padding%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="248b1-105">Two of the most important are the <xref:System.Windows.Forms.Control.Margin%2A> and <xref:System.Windows.Forms.Control.Padding%2A> properties.</span></span>  
  
 <span data-ttu-id="248b1-106">O <xref:System.Windows.Forms.Control.Margin%2A> propriedade define o espaço em torno do controle que mantém outros controla uma distância especificada da bordas do controle.</span><span class="sxs-lookup"><span data-stu-id="248b1-106">The <xref:System.Windows.Forms.Control.Margin%2A> property defines the space around the control that keeps other controls a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="248b1-107">O <xref:System.Windows.Forms.Control.Padding%2A> propriedade define o espaço no interior de um controle que mantém o conteúdo do controle (por exemplo, o valor de seu <xref:System.Windows.Forms.Control.Text%2A> propriedade) uma distância especificada da bordas do controle.</span><span class="sxs-lookup"><span data-stu-id="248b1-107">The <xref:System.Windows.Forms.Control.Padding%2A> property defines the space in the interior of a control that keeps the control's content (for example, the value of its <xref:System.Windows.Forms.Control.Text%2A> property) a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="248b1-108">A ilustração a seguir mostra a <xref:System.Windows.Forms.Control.Padding%2A> e <xref:System.Windows.Forms.Control.Margin%2A> propriedades em um controle.</span><span class="sxs-lookup"><span data-stu-id="248b1-108">The following illustration shows the <xref:System.Windows.Forms.Control.Padding%2A> and <xref:System.Windows.Forms.Control.Margin%2A> properties on a control.</span></span>  
  
 <span data-ttu-id="248b1-109">![Preenchimento e margem para controles dos Windows Forms](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span><span class="sxs-lookup"><span data-stu-id="248b1-109">![Padding And Margin for Windows Forms Controls](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span></span>  
  
 <span data-ttu-id="248b1-110">Não há suporte de tempo de design para esse recurso no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="248b1-110">There is design-time support for this feature in Visual Studio.</span></span> <span data-ttu-id="248b1-111">Consulte também [passo a passo: Definindo o layout dos Windows Forms a controles com preenchimento, margens e a propriedade AutoSize](windows-forms-controls-padding-autosize.md).</span><span class="sxs-lookup"><span data-stu-id="248b1-111">Also see [Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property](windows-forms-controls-padding-autosize.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="248b1-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="248b1-112">See also</span></span>
- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- <xref:System.Windows.Forms.Control.LayoutEngine%2A>
- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
