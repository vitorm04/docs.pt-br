---
title: Layout em controles dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms]
- sizing [Windows Forms], automatic [Windows Forms]
- Margin property [Windows Forms]
- Padding property [Windows Forms]
ms.assetid: 99400e3a-720e-4f56-b68f-89df911a251c
ms.openlocfilehash: a184eea8fd6804848cf7dfa324ef1430746ff7e9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57503288"
---
# <a name="layout-in-windows-forms-controls"></a><span data-ttu-id="825b8-102">Layout em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="825b8-102">Layout in Windows Forms Controls</span></span>

<span data-ttu-id="825b8-103">O posicionamento exato dos controles no formulário é uma prioridade alta para muitos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="825b8-103">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="825b8-104">O <xref:System.Windows.Forms?displayProperty=nameWithType> namespace fornece várias ferramentas de layout para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="825b8-104">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace gives you many layout tools to accomplish this.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="825b8-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="825b8-105">In This Section</span></span>

<span data-ttu-id="825b8-106">[Visão geral da propriedade AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md)\\</span><span class="sxs-lookup"><span data-stu-id="825b8-106">[AutoSize Property Overview](../../../../docs/framework/winforms/controls/autosize-property-overview.md)\\</span></span>
<span data-ttu-id="825b8-107">Descreve o <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade e sua função no layout.</span><span class="sxs-lookup"><span data-stu-id="825b8-107">Describes the <xref:System.Windows.Forms.Control.AutoSize%2A> property and its role in layout.</span></span>

<span data-ttu-id="825b8-108">[Margem e preenchimento nos Windows Forms a controles](../../../../docs/framework/winforms/controls/margin-and-padding-in-windows-forms-controls.md)\\</span><span class="sxs-lookup"><span data-stu-id="825b8-108">[Margin and Padding in Windows Forms Controls](../../../../docs/framework/winforms/controls/margin-and-padding-in-windows-forms-controls.md)\\</span></span>
<span data-ttu-id="825b8-109">Descreve o <xref:System.Windows.Forms.Control.Margin%2A> e <xref:System.Windows.Forms.Control.Padding%2A> propriedades e suas funções no layout.</span><span class="sxs-lookup"><span data-stu-id="825b8-109">Describes the <xref:System.Windows.Forms.Control.Margin%2A> and <xref:System.Windows.Forms.Control.Padding%2A> properties and their roles in layout.</span></span>

<span data-ttu-id="825b8-110">[Como: Alinhar um controle às bordas de formulários](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="825b8-110">[How to: Align a Control to the Edges of Forms](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md)\\</span></span>
<span data-ttu-id="825b8-111">Demonstra como usar o <xref:System.Windows.Forms.Control.Dock%2A> propriedade para alinhar o controle na borda da forma que ele ocupa.</span><span class="sxs-lookup"><span data-stu-id="825b8-111">Demonstrates how to use the <xref:System.Windows.Forms.Control.Dock%2A> property to align your control to the edge of the form it occupies.</span></span>

<span data-ttu-id="825b8-112">[Como: Criar uma borda em torno de um Windows Forms usando preenchimento de controle](../../../../docs/framework/winforms/controls/how-to-create-a-border-around-a-windows-forms-control-using-padding.md)\\</span><span class="sxs-lookup"><span data-stu-id="825b8-112">[How to: Create a Border Around a Windows Forms Control Using Padding](../../../../docs/framework/winforms/controls/how-to-create-a-border-around-a-windows-forms-control-using-padding.md)\\</span></span>
<span data-ttu-id="825b8-113">Demonstra como usar o <xref:System.Windows.Forms.Control.Padding%2A> propriedade descrever um controle.</span><span class="sxs-lookup"><span data-stu-id="825b8-113">Demonstrates how to use the <xref:System.Windows.Forms.Control.Padding%2A> property to outline a control.</span></span>

<span data-ttu-id="825b8-114">[Como: Implementar um mecanismo de Layout personalizado](../../../../docs/framework/winforms/controls/how-to-implement-a-custom-layout-engine.md)\\</span><span class="sxs-lookup"><span data-stu-id="825b8-114">[How to: Implement a Custom Layout Engine](../../../../docs/framework/winforms/controls/how-to-implement-a-custom-layout-engine.md)\\</span></span>
<span data-ttu-id="825b8-115">Demonstra como implementar um <xref:System.Windows.Forms.Layout.LayoutEngine> para organizar os controles de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="825b8-115">Demonstrates how to implement a <xref:System.Windows.Forms.Layout.LayoutEngine> for arranging Windows Forms controls.</span></span>

## <a name="reference"></a><span data-ttu-id="825b8-116">Referência</span><span class="sxs-lookup"><span data-stu-id="825b8-116">Reference</span></span>

<xref:System.Windows.Forms.TableLayoutPanel>\
<span data-ttu-id="825b8-117">Fornece documentação de referência para o <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="825b8-117">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

<xref:System.Windows.Forms.FlowLayoutPanel>\
<span data-ttu-id="825b8-118">Fornece documentação de referência para o <xref:System.Windows.Forms.FlowLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="825b8-118">Provides reference documentation for the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

## <a name="see-also"></a><span data-ttu-id="825b8-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="825b8-119">See also</span></span>

- [<span data-ttu-id="825b8-120">Como: Ancorar e encaixar controles filho em um controle FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="825b8-120">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="825b8-121">Como: Ancorar e encaixar controles filho em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="825b8-121">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="825b8-122">Como: Projetar um Layout de formulários do Windows que responde bem à localização</span><span class="sxs-lookup"><span data-stu-id="825b8-122">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
- [<span data-ttu-id="825b8-123">Comportamento de AutoSize no controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="825b8-123">AutoSize Behavior in the TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/autosize-behavior-in-the-tablelayoutpanel-control.md)
