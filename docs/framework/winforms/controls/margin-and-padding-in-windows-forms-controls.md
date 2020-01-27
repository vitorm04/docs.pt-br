---
title: Margem e preenchimento em controles
ms.date: 03/30/2017
helpviewer_keywords:
- Padding property [Windows Forms]
- layout [Windows Forms], margins and padding
- Windows Forms, layout
- Margin property [Windows Forms]
ms.assetid: 3781b5a1-3085-4072-bed0-44670c23ffdc
ms.openlocfilehash: 02cabccd0d51a3501a8aafb8733a5273deef6c49
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728563"
---
# <a name="margin-and-padding-in-windows-forms-controls"></a><span data-ttu-id="30b06-102">Margem e preenchimento em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="30b06-102">Margin and Padding in Windows Forms Controls</span></span>
<span data-ttu-id="30b06-103">O posicionamento exato dos controles no formulário é uma prioridade alta para muitos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="30b06-103">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="30b06-104">O namespace <xref:System.Windows.Forms?displayProperty=nameWithType> oferece muitos recursos de layout para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="30b06-104">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace gives you many layout features to accomplish this.</span></span> <span data-ttu-id="30b06-105">Duas das mais importantes são as propriedades <xref:System.Windows.Forms.Control.Margin%2A> e <xref:System.Windows.Forms.Control.Padding%2A>.</span><span class="sxs-lookup"><span data-stu-id="30b06-105">Two of the most important are the <xref:System.Windows.Forms.Control.Margin%2A> and <xref:System.Windows.Forms.Control.Padding%2A> properties.</span></span>  
  
 <span data-ttu-id="30b06-106">A propriedade <xref:System.Windows.Forms.Control.Margin%2A> define o espaço em torno do controle que mantém outros controles uma distância especificada das bordas do controle.</span><span class="sxs-lookup"><span data-stu-id="30b06-106">The <xref:System.Windows.Forms.Control.Margin%2A> property defines the space around the control that keeps other controls a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="30b06-107">A propriedade <xref:System.Windows.Forms.Control.Padding%2A> define o espaço no interior de um controle que mantém o conteúdo do controle (por exemplo, o valor de sua propriedade <xref:System.Windows.Forms.Control.Text%2A>) uma distância especificada das bordas do controle.</span><span class="sxs-lookup"><span data-stu-id="30b06-107">The <xref:System.Windows.Forms.Control.Padding%2A> property defines the space in the interior of a control that keeps the control's content (for example, the value of its <xref:System.Windows.Forms.Control.Text%2A> property) a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="30b06-108">A ilustração a seguir mostra as propriedades <xref:System.Windows.Forms.Control.Padding%2A> e <xref:System.Windows.Forms.Control.Margin%2A> em um controle.</span><span class="sxs-lookup"><span data-stu-id="30b06-108">The following illustration shows the <xref:System.Windows.Forms.Control.Padding%2A> and <xref:System.Windows.Forms.Control.Margin%2A> properties on a control.</span></span>  
  
 <span data-ttu-id="30b06-109">![Preenchimento e margem para controles de Windows Forms](./media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span><span class="sxs-lookup"><span data-stu-id="30b06-109">![Padding And Margin for Windows Forms Controls](./media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span></span>  
  
 <span data-ttu-id="30b06-110">Há suporte para o tempo de design para esse recurso no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="30b06-110">There is design-time support for this feature in Visual Studio.</span></span> <span data-ttu-id="30b06-111">Além disso, veja [o passo a passos: dispor Windows Forms controles com preenchimento, margens e a propriedade AutoSize](windows-forms-controls-padding-autosize.md).</span><span class="sxs-lookup"><span data-stu-id="30b06-111">Also see [Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property](windows-forms-controls-padding-autosize.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30b06-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="30b06-112">See also</span></span>

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- <xref:System.Windows.Forms.Control.LayoutEngine%2A>
- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
