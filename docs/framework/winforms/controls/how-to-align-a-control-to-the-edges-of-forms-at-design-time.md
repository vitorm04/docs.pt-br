---
title: 'Como: Alinhar um controle às bordas de formulários no tempo de design'
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], docking using designer
- Dock property [Windows Forms], aligning controls (using designer)
ms.assetid: 51f08998-5e3b-4330-be58-a4edd0eb60f4
ms.openlocfilehash: b08e01eb9adb984a32a8fc435cf1f3b93b159a14
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65210375"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms-at-design-time"></a><span data-ttu-id="8c7ce-102">Como: Alinhar um controle às bordas de formulários no tempo de design</span><span class="sxs-lookup"><span data-stu-id="8c7ce-102">How to: Align a Control to the Edges of Forms at Design Time</span></span>

<span data-ttu-id="8c7ce-103">Você pode fazer com que o seu controle Alinhar à borda de seus formulários, definindo o valor da <xref:System.Windows.Forms.Control.Dock%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="8c7ce-103">You can make your control align to the edge of your forms by setting the value of the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span> <span data-ttu-id="8c7ce-104">Essa propriedade determina onde reside o controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="8c7ce-104">This property designates where your control resides in the form.</span></span> <span data-ttu-id="8c7ce-105">O <xref:System.Windows.Forms.Control.Dock%2A> propriedade pode ser definida com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="8c7ce-105">The <xref:System.Windows.Forms.Control.Dock%2A> property can be set to the following values:</span></span>

|<span data-ttu-id="8c7ce-106">Configuração</span><span class="sxs-lookup"><span data-stu-id="8c7ce-106">Setting</span></span>|<span data-ttu-id="8c7ce-107">Efeito no seu controle</span><span class="sxs-lookup"><span data-stu-id="8c7ce-107">Effect on your control</span></span>|
|-------------|----------------------------|
|<xref:System.Windows.Forms.DockStyle.Bottom>|<span data-ttu-id="8c7ce-108">Encaixa na parte inferior do formulário.</span><span class="sxs-lookup"><span data-stu-id="8c7ce-108">Docks to the bottom of the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Fill>|<span data-ttu-id="8c7ce-109">Preenche todo o espaço restante no formulário.</span><span class="sxs-lookup"><span data-stu-id="8c7ce-109">Fills all remaining space in the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Left>|<span data-ttu-id="8c7ce-110">Encaixa do lado esquerdo do formulário.</span><span class="sxs-lookup"><span data-stu-id="8c7ce-110">Docks to the left side of the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.None>|<span data-ttu-id="8c7ce-111">Não se encaixa em qualquer lugar e aparece no local especificado pelo seu <xref:System.Windows.Forms.Control.Location%2A>.</span><span class="sxs-lookup"><span data-stu-id="8c7ce-111">Does not dock anywhere, and it appears at the location specified by its <xref:System.Windows.Forms.Control.Location%2A>.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Right>|<span data-ttu-id="8c7ce-112">Encaixa do lado direito do formulário.</span><span class="sxs-lookup"><span data-stu-id="8c7ce-112">Docks to the right side of the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Top>|<span data-ttu-id="8c7ce-113">Encaixa na parte superior do formulário.</span><span class="sxs-lookup"><span data-stu-id="8c7ce-113">Docks to the top of the form.</span></span>|

<span data-ttu-id="8c7ce-114">Esses valores também podem ser definidos no código.</span><span class="sxs-lookup"><span data-stu-id="8c7ce-114">These values can also be set in code.</span></span> <span data-ttu-id="8c7ce-115">Para obter mais informações, confira [Como: Alinhar um controle às bordas de formulários](how-to-align-a-control-to-the-edges-of-forms.md).</span><span class="sxs-lookup"><span data-stu-id="8c7ce-115">For more information, see [How to: Align a Control to the Edges of Forms](how-to-align-a-control-to-the-edges-of-forms.md).</span></span>

## <a name="set-the-dock-property-for-your-control-at-design-time"></a><span data-ttu-id="8c7ce-116">Defina a propriedade Dock para o seu controle em tempo de design</span><span class="sxs-lookup"><span data-stu-id="8c7ce-116">Set the Dock property for your control at design time</span></span>

1. <span data-ttu-id="8c7ce-117">No Designer de formulários do Windows no Visual Studio, selecione seu controle.</span><span class="sxs-lookup"><span data-stu-id="8c7ce-117">In the Windows Forms Designer in Visual Studio, select your control.</span></span>

2. <span data-ttu-id="8c7ce-118">No **propriedades** , clique na lista suspensa caixa ao lado de <xref:System.Windows.Forms.Control.Dock%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="8c7ce-118">In the **Properties** window, click the drop-down box next to the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>

     <span data-ttu-id="8c7ce-119">Uma interface gráfica que representa os seis possíveis <xref:System.Windows.Forms.Control.Dock%2A> configurações é exibida.</span><span class="sxs-lookup"><span data-stu-id="8c7ce-119">A graphical interface representing the six possible <xref:System.Windows.Forms.Control.Dock%2A> settings is displayed.</span></span>

3. <span data-ttu-id="8c7ce-120">Escolha a configuração apropriada.</span><span class="sxs-lookup"><span data-stu-id="8c7ce-120">Choose the appropriate setting.</span></span>

4. <span data-ttu-id="8c7ce-121">O controle agora será encaixado da maneira especificada pela configuração.</span><span class="sxs-lookup"><span data-stu-id="8c7ce-121">Your control will now dock in the manner specified by the setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="8c7ce-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c7ce-122">See also</span></span>

- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8c7ce-123">Como: Alinhar um controle às bordas de formulários</span><span class="sxs-lookup"><span data-stu-id="8c7ce-123">How to: Align a Control to the Edges of Forms</span></span>](how-to-align-a-control-to-the-edges-of-forms.md)
- [<span data-ttu-id="8c7ce-124">Passo a passo: Organizando controles nos formulários do Windows usando guias de alinhamento</span><span class="sxs-lookup"><span data-stu-id="8c7ce-124">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="8c7ce-125">Como: Ancoragem de controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8c7ce-125">How to: Anchor Controls on Windows Forms</span></span>](how-to-anchor-controls-on-windows-forms.md)
- [<span data-ttu-id="8c7ce-126">Como: Ancorar e encaixar controles filho em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8c7ce-126">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="8c7ce-127">Como: Ancorar e encaixar controles filho em um controle FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8c7ce-127">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="8c7ce-128">Passo a passo: Organizando controles nos Windows Forms utilizando um TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8c7ce-128">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="8c7ce-129">Passo a passo: Organizando controles nos Windows Forms utilizando um FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8c7ce-129">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="8c7ce-130">Desenvolvendo controles dos Windows Forms em tempo de design</span><span class="sxs-lookup"><span data-stu-id="8c7ce-130">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
