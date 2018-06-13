---
title: Como encaixar controles nos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
ms.openlocfilehash: 6cb4c982cb4c9e2df8d0335738ca087733209bdc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532308"
---
# <a name="how-to-dock-controls-on-windows-forms"></a><span data-ttu-id="11822-102">Como encaixar controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11822-102">How to: Dock Controls on Windows Forms</span></span>
<span data-ttu-id="11822-103">Você pode encaixar controles nas bordas do formulário ou fazer com que eles preencham o contêiner do controle (um controle de contêiner ou formulário).</span><span class="sxs-lookup"><span data-stu-id="11822-103">You can dock controls to the edges of your form or have them fill the control's container (either a form or a container control).</span></span> <span data-ttu-id="11822-104">Por exemplo, o Windows Explorer encaixa seu <xref:System.Windows.Forms.TreeView> controle para o lado esquerdo da janela e sua <xref:System.Windows.Forms.ListView> controle para o lado direito da janela.</span><span class="sxs-lookup"><span data-stu-id="11822-104">For example, Windows Explorer docks its <xref:System.Windows.Forms.TreeView> control to the left side of the window and its <xref:System.Windows.Forms.ListView> control to the right side of the window.</span></span> <span data-ttu-id="11822-105">Use o <xref:System.Windows.Forms.Control.Dock%2A> propriedade para todos os controles de Windows Forms visíveis definir o modo de encaixe.</span><span class="sxs-lookup"><span data-stu-id="11822-105">Use the <xref:System.Windows.Forms.Control.Dock%2A> property for all visible Windows Forms controls to define the docking mode.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11822-106">Controles são encaixados na ordem z inversa.</span><span class="sxs-lookup"><span data-stu-id="11822-106">Controls are docked in reverse z-order.</span></span>  
  
 <span data-ttu-id="11822-107">O <xref:System.Windows.Forms.Control.Dock%2A> propriedade interage com o <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="11822-107">The <xref:System.Windows.Forms.Control.Dock%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="11822-108">Para obter mais informações, consulte [Visão Geral da Propriedade AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md).</span><span class="sxs-lookup"><span data-stu-id="11822-108">For more information, see [AutoSize Property Overview](../../../../docs/framework/winforms/controls/autosize-property-overview.md).</span></span>  
  
### <a name="to-dock-a-control"></a><span data-ttu-id="11822-109">Para encaixar um controle</span><span class="sxs-lookup"><span data-stu-id="11822-109">To dock a control</span></span>  
  
1.  <span data-ttu-id="11822-110">Selecione o controle que deseja encaixar.</span><span class="sxs-lookup"><span data-stu-id="11822-110">Select the control that you want to dock.</span></span>  
  
2.  <span data-ttu-id="11822-111">Na janela Propriedades, clique na seta à direita do <xref:System.Windows.Forms.Control.Dock%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="11822-111">In the Properties window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>  
  
     <span data-ttu-id="11822-112">Um editor será exibido que mostra uma série de caixas que representam as bordas e o centro do formulário.</span><span class="sxs-lookup"><span data-stu-id="11822-112">An editor is displayed that shows a series of boxes representing the edges and the center of the form.</span></span>  
  
3.  <span data-ttu-id="11822-113">Clique no botão que representa a borda do formulário no qual você deseja encaixar o controle.</span><span class="sxs-lookup"><span data-stu-id="11822-113">Click the button that represents the edge of the form where you want to dock the control.</span></span> <span data-ttu-id="11822-114">Para preencher o conteúdo do controle de contêiner ou formulário do controle, clique na caixa do centro.</span><span class="sxs-lookup"><span data-stu-id="11822-114">To fill the contents of the control's form or container control, click the center box.</span></span> <span data-ttu-id="11822-115">Clique em **(nenhum)** para desabilitar o encaixe.</span><span class="sxs-lookup"><span data-stu-id="11822-115">Click **(none)** to disable docking.</span></span>  
  
     <span data-ttu-id="11822-116">O controle é redimensionado automaticamente para ajustar os limites da borda encaixada.</span><span class="sxs-lookup"><span data-stu-id="11822-116">The control is automatically resized to fit the boundaries of the docked edge.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="11822-117">Controles herdados devem ser `Protected` para poderem ser encaixados.</span><span class="sxs-lookup"><span data-stu-id="11822-117">Inherited controls must be `Protected` to be able to be docked.</span></span> <span data-ttu-id="11822-118">Para alterar o nível de acesso de um controle, defina sua propriedade **Modifier** na janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="11822-118">To change the access level of a control, set its **Modifier** property in the Properties window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11822-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11822-119">See Also</span></span>  
 [<span data-ttu-id="11822-120">Controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11822-120">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="11822-121">Organizando Controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11822-121">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="11822-122">Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles</span><span class="sxs-lookup"><span data-stu-id="11822-122">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="11822-123">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11822-123">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="11822-124">Controles dos Windows Forms por função</span><span class="sxs-lookup"><span data-stu-id="11822-124">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)  
 [<span data-ttu-id="11822-125">Como ancorar e encaixar controles filho em um controle FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="11822-125">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [<span data-ttu-id="11822-126">Como ancorar e encaixar controles filho em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="11822-126">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="11822-127">Visão geral da propriedade AutoSize</span><span class="sxs-lookup"><span data-stu-id="11822-127">AutoSize Property Overview</span></span>](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [<span data-ttu-id="11822-128">Como ancorar controles no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11822-128">How to: Anchor Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)
