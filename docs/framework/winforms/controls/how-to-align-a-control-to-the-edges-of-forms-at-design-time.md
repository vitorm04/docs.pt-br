---
title: 'Como: Alinhar um controle às bordas de formulários no tempo de design'
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], docking using designer
- Dock property [Windows Forms], aligning controls (using designer)
ms.assetid: 51f08998-5e3b-4330-be58-a4edd0eb60f4
ms.openlocfilehash: 8f74a6b56e99e016bfb27bbe1b271f6c71af8f87
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140888"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms-at-design-time"></a><span data-ttu-id="d75a5-102">Como: Alinhar um controle às bordas de formulários no tempo de design</span><span class="sxs-lookup"><span data-stu-id="d75a5-102">How to: Align a Control to the Edges of Forms at Design Time</span></span>
<span data-ttu-id="d75a5-103">Você pode fazer com que o seu controle Alinhar à borda de seus formulários configurando o <xref:System.Windows.Forms.Control.Dock%2A>.</span><span class="sxs-lookup"><span data-stu-id="d75a5-103">You can make your control align to the edge of your forms by setting the <xref:System.Windows.Forms.Control.Dock%2A>.</span></span> <span data-ttu-id="d75a5-104">Essa propriedade determina onde reside o controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="d75a5-104">This property designates where your control resides in the form.</span></span> <span data-ttu-id="d75a5-105">O <xref:System.Windows.Forms.Control.Dock%2A> propriedade pode ser definida com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="d75a5-105">The <xref:System.Windows.Forms.Control.Dock%2A> property can be set to the following values:</span></span>  
  
|<span data-ttu-id="d75a5-106">Configuração</span><span class="sxs-lookup"><span data-stu-id="d75a5-106">Setting</span></span>|<span data-ttu-id="d75a5-107">Efeito no seu controle</span><span class="sxs-lookup"><span data-stu-id="d75a5-107">Effect on your control</span></span>|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|<span data-ttu-id="d75a5-108">Encaixa na parte inferior do formulário.</span><span class="sxs-lookup"><span data-stu-id="d75a5-108">Docks to the bottom of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Fill>|<span data-ttu-id="d75a5-109">Preenche todo o espaço restante no formulário.</span><span class="sxs-lookup"><span data-stu-id="d75a5-109">Fills all remaining space in the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Left>|<span data-ttu-id="d75a5-110">Encaixa do lado esquerdo do formulário.</span><span class="sxs-lookup"><span data-stu-id="d75a5-110">Docks to the left side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.None>|<span data-ttu-id="d75a5-111">Não se encaixa em qualquer lugar e aparece no local especificado pelo seu <xref:System.Windows.Forms.Control.Location%2A>.</span><span class="sxs-lookup"><span data-stu-id="d75a5-111">Does not dock anywhere, and it appears at the location specified by its <xref:System.Windows.Forms.Control.Location%2A>.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Right>|<span data-ttu-id="d75a5-112">Encaixa do lado direito do formulário.</span><span class="sxs-lookup"><span data-stu-id="d75a5-112">Docks to the right side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Top>|<span data-ttu-id="d75a5-113">Encaixa na parte superior do formulário.</span><span class="sxs-lookup"><span data-stu-id="d75a5-113">Docks to the top of the form.</span></span>|  
  
 <span data-ttu-id="d75a5-114">Esses valores também podem ser definidos no código.</span><span class="sxs-lookup"><span data-stu-id="d75a5-114">These values can also be set in code.</span></span> <span data-ttu-id="d75a5-115">Para obter mais informações, confira [Como: Alinhar um controle às bordas de formulários](how-to-align-a-control-to-the-edges-of-forms.md).</span><span class="sxs-lookup"><span data-stu-id="d75a5-115">For more information, see [How to: Align a Control to the Edges of Forms](how-to-align-a-control-to-the-edges-of-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d75a5-116">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="d75a5-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d75a5-117">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="d75a5-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d75a5-118">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="d75a5-118">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-set-the-dock-property-for-your-control-at-design-time"></a><span data-ttu-id="d75a5-119">Para definir a propriedade Dock para o seu controle no tempo de design</span><span class="sxs-lookup"><span data-stu-id="d75a5-119">To set the Dock property for your control at design time</span></span>  
  
1.  <span data-ttu-id="d75a5-120">No Designer de Formulários do Windows, selecione seu controle.</span><span class="sxs-lookup"><span data-stu-id="d75a5-120">In the Windows Forms Designer, select your control.</span></span>  
  
2.  <span data-ttu-id="d75a5-121">No **propriedades** , clique na lista suspensa caixa ao lado de <xref:System.Windows.Forms.Control.Dock%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="d75a5-121">In the **Properties** window, click the drop-down box next to the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>  
  
     <span data-ttu-id="d75a5-122">Uma interface gráfica que representa os seis possíveis <xref:System.Windows.Forms.Control.Dock%2A> configurações é exibida.</span><span class="sxs-lookup"><span data-stu-id="d75a5-122">A graphical interface representing the six possible <xref:System.Windows.Forms.Control.Dock%2A> settings is displayed.</span></span>  
  
3.  <span data-ttu-id="d75a5-123">Escolha a configuração apropriada.</span><span class="sxs-lookup"><span data-stu-id="d75a5-123">Choose the appropriate setting.</span></span>  
  
4.  <span data-ttu-id="d75a5-124">O controle agora será encaixado da maneira especificada pela configuração.</span><span class="sxs-lookup"><span data-stu-id="d75a5-124">Your control will now dock in the manner specified by the setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d75a5-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d75a5-125">See also</span></span>

- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [<span data-ttu-id="d75a5-126">Como: Alinhar um controle às bordas de formulários</span><span class="sxs-lookup"><span data-stu-id="d75a5-126">How to: Align a Control to the Edges of Forms</span></span>](how-to-align-a-control-to-the-edges-of-forms.md)
- [<span data-ttu-id="d75a5-127">Passo a passo: Organizar controles nos Windows Forms usando linhas de alinhamento</span><span class="sxs-lookup"><span data-stu-id="d75a5-127">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="d75a5-128">Como: Ancorar controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d75a5-128">How to: Anchor Controls on Windows Forms</span></span>](how-to-anchor-controls-on-windows-forms.md)
- [<span data-ttu-id="d75a5-129">Como: Ancorar e encaixar controles filho em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="d75a5-129">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="d75a5-130">Como: Ancorar e encaixar controles filho em um controle FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="d75a5-130">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="d75a5-131">Passo a passo: Organizar controles nos Windows Forms usando um TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="d75a5-131">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="d75a5-132">Passo a passo: Organizando controles nos Windows Forms utilizando um FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="d75a5-132">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="d75a5-133">Desenvolvendo controles dos Windows Forms na hora de design</span><span class="sxs-lookup"><span data-stu-id="d75a5-133">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
