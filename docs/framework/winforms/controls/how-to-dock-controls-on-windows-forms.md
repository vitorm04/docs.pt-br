---
title: encaixar controles
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 02f1c26dcb322a39c41781c83d8c820bd2fd27e0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745515"
---
# <a name="how-to-dock-controls-on-windows-forms"></a><span data-ttu-id="c7e78-102">Como encaixar controles em Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7e78-102">How to: Dock controls on Windows Forms</span></span>

<span data-ttu-id="c7e78-103">Você pode encaixar controles nas bordas do formulário ou fazer com que eles preencham o contêiner do controle (um controle de contêiner ou formulário).</span><span class="sxs-lookup"><span data-stu-id="c7e78-103">You can dock controls to the edges of your form or have them fill the control's container (either a form or a container control).</span></span> <span data-ttu-id="c7e78-104">Por exemplo, o Windows Explorer encaixa seu controle de <xref:System.Windows.Forms.TreeView> no lado esquerdo da janela e seu controle de <xref:System.Windows.Forms.ListView> no lado direito da janela.</span><span class="sxs-lookup"><span data-stu-id="c7e78-104">For example, Windows Explorer docks its <xref:System.Windows.Forms.TreeView> control to the left side of the window and its <xref:System.Windows.Forms.ListView> control to the right side of the window.</span></span> <span data-ttu-id="c7e78-105">Use a propriedade <xref:System.Windows.Forms.Control.Dock%2A> para todos os controles de Windows Forms visíveis para definir o modo de encaixe.</span><span class="sxs-lookup"><span data-stu-id="c7e78-105">Use the <xref:System.Windows.Forms.Control.Dock%2A> property for all visible Windows Forms controls to define the docking mode.</span></span>

> [!NOTE]
> <span data-ttu-id="c7e78-106">Controles são encaixados na ordem z inversa.</span><span class="sxs-lookup"><span data-stu-id="c7e78-106">Controls are docked in reverse z-order.</span></span>

<span data-ttu-id="c7e78-107">A propriedade <xref:System.Windows.Forms.Control.Dock%2A> interage com a propriedade <xref:System.Windows.Forms.Control.AutoSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="c7e78-107">The <xref:System.Windows.Forms.Control.Dock%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="c7e78-108">Para obter mais informações, consulte [Visão Geral da Propriedade AutoSize](autosize-property-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c7e78-108">For more information, see [AutoSize Property Overview](autosize-property-overview.md).</span></span>

## <a name="to-dock-a-control"></a><span data-ttu-id="c7e78-109">Para encaixar um controle</span><span class="sxs-lookup"><span data-stu-id="c7e78-109">To dock a control</span></span>

1. <span data-ttu-id="c7e78-110">No Visual Studio, selecione o controle que você deseja encaixar.</span><span class="sxs-lookup"><span data-stu-id="c7e78-110">In Visual Studio, select the control that you want to dock.</span></span>

2. <span data-ttu-id="c7e78-111">Na janela **Propriedades** , clique na seta à direita da propriedade <xref:System.Windows.Forms.Control.Dock%2A>.</span><span class="sxs-lookup"><span data-stu-id="c7e78-111">In the **Properties** window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>

   <span data-ttu-id="c7e78-112">Um editor será exibido que mostra uma série de caixas que representam as bordas e o centro do formulário.</span><span class="sxs-lookup"><span data-stu-id="c7e78-112">An editor is displayed that shows a series of boxes representing the edges and the center of the form.</span></span>

3. <span data-ttu-id="c7e78-113">Clique no botão que representa a borda do formulário no qual você deseja encaixar o controle.</span><span class="sxs-lookup"><span data-stu-id="c7e78-113">Click the button that represents the edge of the form where you want to dock the control.</span></span> <span data-ttu-id="c7e78-114">Para preencher o conteúdo do controle de contêiner ou formulário do controle, clique na caixa do centro.</span><span class="sxs-lookup"><span data-stu-id="c7e78-114">To fill the contents of the control's form or container control, click the center box.</span></span> <span data-ttu-id="c7e78-115">Clique em **(nenhum)** para desabilitar o encaixe.</span><span class="sxs-lookup"><span data-stu-id="c7e78-115">Click **(none)** to disable docking.</span></span>

   <span data-ttu-id="c7e78-116">O controle é redimensionado automaticamente para ajustar os limites da borda encaixada.</span><span class="sxs-lookup"><span data-stu-id="c7e78-116">The control is automatically resized to fit the boundaries of the docked edge.</span></span>

   > [!NOTE]
   > <span data-ttu-id="c7e78-117">Controles herdados devem ser `Protected` para poderem ser encaixados.</span><span class="sxs-lookup"><span data-stu-id="c7e78-117">Inherited controls must be `Protected` to be able to be docked.</span></span> <span data-ttu-id="c7e78-118">Para alterar o nível de acesso de um controle, defina sua propriedade **modificador** na janela **Propriedades** .</span><span class="sxs-lookup"><span data-stu-id="c7e78-118">To change the access level of a control, set its **Modifier** property in the **Properties** window.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7e78-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7e78-119">See also</span></span>

- [<span data-ttu-id="c7e78-120">Controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7e78-120">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="c7e78-121">Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles</span><span class="sxs-lookup"><span data-stu-id="c7e78-121">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="c7e78-122">Controles a serem usados no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7e78-122">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="c7e78-123">Controles dos Windows Forms por função</span><span class="sxs-lookup"><span data-stu-id="c7e78-123">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- [<span data-ttu-id="c7e78-124">Como ancorar e encaixar controles filho em um controle FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="c7e78-124">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="c7e78-125">Como ancorar e encaixar controles filho em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="c7e78-125">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="c7e78-126">Visão geral da propriedade AutoSize</span><span class="sxs-lookup"><span data-stu-id="c7e78-126">AutoSize Property Overview</span></span>](autosize-property-overview.md)
- [<span data-ttu-id="c7e78-127">Como ancorar controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7e78-127">How to: Anchor Controls on Windows Forms</span></span>](how-to-anchor-controls-on-windows-forms.md)
