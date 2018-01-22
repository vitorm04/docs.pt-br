---
title: "Como alinhar um controle às bordas de formulários na hora do design"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], docking using designer
- Dock property [Windows Forms], aligning controls (using designer)
ms.assetid: 51f08998-5e3b-4330-be58-a4edd0eb60f4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1232f1f091412017e22f29d529bf7c76b32a4b6d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-align-a-control-to-the-edges-of-forms-at-design-time"></a><span data-ttu-id="91117-102">Como alinhar um controle às bordas de formulários na hora do design</span><span class="sxs-lookup"><span data-stu-id="91117-102">How to: Align a Control to the Edges of Forms at Design Time</span></span>
<span data-ttu-id="91117-103">Você pode fazer com que o seu controle alinhe a borda de formulários, definindo o <xref:System.Windows.Forms.Control.Dock%2A>.</span><span class="sxs-lookup"><span data-stu-id="91117-103">You can make your control align to the edge of your forms by setting the <xref:System.Windows.Forms.Control.Dock%2A>.</span></span> <span data-ttu-id="91117-104">Essa propriedade determina onde reside o controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="91117-104">This property designates where your control resides in the form.</span></span> <span data-ttu-id="91117-105">O <xref:System.Windows.Forms.Control.Dock%2A> propriedade pode ser definida com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="91117-105">The <xref:System.Windows.Forms.Control.Dock%2A> property can be set to the following values:</span></span>  
  
|<span data-ttu-id="91117-106">Configuração</span><span class="sxs-lookup"><span data-stu-id="91117-106">Setting</span></span>|<span data-ttu-id="91117-107">Efeito no seu controle</span><span class="sxs-lookup"><span data-stu-id="91117-107">Effect on your control</span></span>|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|<span data-ttu-id="91117-108">Encaixa na parte inferior do formulário.</span><span class="sxs-lookup"><span data-stu-id="91117-108">Docks to the bottom of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Fill>|<span data-ttu-id="91117-109">Preenche todo o espaço restante no formulário.</span><span class="sxs-lookup"><span data-stu-id="91117-109">Fills all remaining space in the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Left>|<span data-ttu-id="91117-110">Encaixa do lado esquerdo do formulário.</span><span class="sxs-lookup"><span data-stu-id="91117-110">Docks to the left side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.None>|<span data-ttu-id="91117-111">Faz não encaixe em qualquer local e ele aparece no local especificado por seu <xref:System.Windows.Forms.Control.Location%2A>.</span><span class="sxs-lookup"><span data-stu-id="91117-111">Does not dock anywhere, and it appears at the location specified by its <xref:System.Windows.Forms.Control.Location%2A>.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Right>|<span data-ttu-id="91117-112">Encaixa do lado direito do formulário.</span><span class="sxs-lookup"><span data-stu-id="91117-112">Docks to the right side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Top>|<span data-ttu-id="91117-113">Encaixa na parte superior do formulário.</span><span class="sxs-lookup"><span data-stu-id="91117-113">Docks to the top of the form.</span></span>|  
  
 <span data-ttu-id="91117-114">Esses valores também podem ser definidos no código.</span><span class="sxs-lookup"><span data-stu-id="91117-114">These values can also be set in code.</span></span> <span data-ttu-id="91117-115">Para obter mais informações, consulte [Como alinhar um controle às bordas de formulários](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md).</span><span class="sxs-lookup"><span data-stu-id="91117-115">For more information, see [How to: Align a Control to the Edges of Forms](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="91117-116">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="91117-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="91117-117">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="91117-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="91117-118">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="91117-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-the-dock-property-for-your-control-at-design-time"></a><span data-ttu-id="91117-119">Para definir a propriedade Dock para o seu controle no tempo de design</span><span class="sxs-lookup"><span data-stu-id="91117-119">To set the Dock property for your control at design time</span></span>  
  
1.  <span data-ttu-id="91117-120">No Designer de Formulários do Windows, selecione seu controle.</span><span class="sxs-lookup"><span data-stu-id="91117-120">In the Windows Forms Designer, select your control.</span></span>  
  
2.  <span data-ttu-id="91117-121">No **propriedades** janela, clique na lista suspensa ao lado de caixa de <xref:System.Windows.Forms.Control.Dock%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="91117-121">In the **Properties** window, click the drop-down box next to the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>  
  
     <span data-ttu-id="91117-122">Uma interface gráfica que representa os possíveis seis <xref:System.Windows.Forms.Control.Dock%2A> configurações é exibida.</span><span class="sxs-lookup"><span data-stu-id="91117-122">A graphical interface representing the six possible <xref:System.Windows.Forms.Control.Dock%2A> settings is displayed.</span></span>  
  
3.  <span data-ttu-id="91117-123">Escolha a configuração apropriada.</span><span class="sxs-lookup"><span data-stu-id="91117-123">Choose the appropriate setting.</span></span>  
  
4.  <span data-ttu-id="91117-124">O controle agora será encaixado da maneira especificada pela configuração.</span><span class="sxs-lookup"><span data-stu-id="91117-124">Your control will now dock in the manner specified by the setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91117-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91117-125">See Also</span></span>  
 <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="91117-126">Como alinhar um controle às bordas de formulários</span><span class="sxs-lookup"><span data-stu-id="91117-126">How to: Align a Control to the Edges of Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md)  
 [<span data-ttu-id="91117-127">Instruções passo a passo: organizando controles no Windows Forms usando guias de alinhamento</span><span class="sxs-lookup"><span data-stu-id="91117-127">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="91117-128">Como ancorar controles no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="91117-128">How to: Anchor Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)  
 [<span data-ttu-id="91117-129">Como ancorar e encaixar controles filho em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="91117-129">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="91117-130">Como ancorar e encaixar controles filho em um controle FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="91117-130">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [<span data-ttu-id="91117-131">Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="91117-131">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="91117-132">Passo a passo: organizando controles nos Windows Forms utilizando um FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="91117-132">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [<span data-ttu-id="91117-133">Desenvolvendo controles dos Windows Forms em tempo de design</span><span class="sxs-lookup"><span data-stu-id="91117-133">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
