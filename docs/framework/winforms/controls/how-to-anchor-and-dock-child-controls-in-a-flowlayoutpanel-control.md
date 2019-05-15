---
title: 'Como: Ancorar e encaixar controles filho em um controle FlowLayoutPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
ms.openlocfilehash: f67733b89d2bde652449e2338362868fdb84bcf3
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592944"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="6e366-102">Como: Ancorar e encaixar controles filho em um controle FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="6e366-102">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>
<span data-ttu-id="6e366-103">O <xref:System.Windows.Forms.FlowLayoutPanel> controlar dá suporte a <xref:System.Windows.Forms.Control.Anchor%2A> e <xref:System.Windows.Forms.Control.Dock%2A> propriedades em seus controles filho.</span><span class="sxs-lookup"><span data-stu-id="6e366-103">The <xref:System.Windows.Forms.FlowLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>  
  
### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="6e366-104">Ancorar e encaixar controles filho em um controle FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="6e366-104">To anchor and dock child controls in a FlowLayoutPanel control</span></span>  
  
1. <span data-ttu-id="6e366-105">Criar um <xref:System.Windows.Forms.FlowLayoutPanel> controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="6e366-105">Create a <xref:System.Windows.Forms.FlowLayoutPanel> control on your form.</span></span>  
  
2. <span data-ttu-id="6e366-106">Defina a <xref:System.Windows.Forms.Control.Width%2A> do <xref:System.Windows.Forms.FlowLayoutPanel> o controle para **300**e defina seu <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> para <xref:System.Windows.Forms.FlowDirection.TopDown>.</span><span class="sxs-lookup"><span data-stu-id="6e366-106">Set the <xref:System.Windows.Forms.Control.Width%2A> of the <xref:System.Windows.Forms.FlowLayoutPanel> control to **300**, and set its <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> to <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>  
  
3. <span data-ttu-id="6e366-107">Criar duas <xref:System.Windows.Forms.Button> controles e colocá-los no <xref:System.Windows.Forms.FlowLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="6e366-107">Create two <xref:System.Windows.Forms.Button> controls, and place them in the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
4. <span data-ttu-id="6e366-108">Defina as <xref:System.Windows.Forms.Control.Width%2A> do primeiro botão para **200**.</span><span class="sxs-lookup"><span data-stu-id="6e366-108">Set the <xref:System.Windows.Forms.Control.Width%2A> of the first button to **200**.</span></span>  
  
5. <span data-ttu-id="6e366-109">Defina as <xref:System.Windows.Forms.Control.Dock%2A> propriedade do segundo botão para <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="6e366-109">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6e366-110">O segundo botão assume a mesma largura que o primeiro.</span><span class="sxs-lookup"><span data-stu-id="6e366-110">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="6e366-111">Ele não se alonga pela largura do <xref:System.Windows.Forms.FlowLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="6e366-111">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
6. <span data-ttu-id="6e366-112">Defina as <xref:System.Windows.Forms.Control.Dock%2A> propriedade do segundo botão para `None`.</span><span class="sxs-lookup"><span data-stu-id="6e366-112">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to `None`.</span></span> <span data-ttu-id="6e366-113">Isso faz com que o botão assuma a largura original.</span><span class="sxs-lookup"><span data-stu-id="6e366-113">This causes the button to assume its original width.</span></span>  
  
7. <span data-ttu-id="6e366-114">Defina as <xref:System.Windows.Forms.Control.Anchor%2A> propriedade do segundo botão para `Left, Right`.</span><span class="sxs-lookup"><span data-stu-id="6e366-114">Set the <xref:System.Windows.Forms.Control.Anchor%2A> property of the second button to `Left, Right`.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="6e366-115">O segundo botão assume a mesma largura que o primeiro.</span><span class="sxs-lookup"><span data-stu-id="6e366-115">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="6e366-116">Ele não se alonga pela largura do <xref:System.Windows.Forms.FlowLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="6e366-116">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span> <span data-ttu-id="6e366-117">Esta é a regra geral de ancoragem e encaixe no controle de <xref:System.Windows.Forms.FlowLayoutPanel> controle: para direções de fluxo vertical, o <xref:System.Windows.Forms.FlowLayoutPanel> controle calcula a largura de uma coluna implícita do controle filho mais largo na coluna.</span><span class="sxs-lookup"><span data-stu-id="6e366-117">This is the general rule for anchoring and docking in the <xref:System.Windows.Forms.FlowLayoutPanel> control: for vertical flow directions, the <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the width of an implied column from the widest child control in the column.</span></span> <span data-ttu-id="6e366-118">Todos os outros controles nesta coluna com <xref:System.Windows.Forms.Control.Anchor%2A> ou <xref:System.Windows.Forms.Control.Dock%2A> propriedades são alinhadas ou alongadas para caber nesta coluna implícita.</span><span class="sxs-lookup"><span data-stu-id="6e366-118">All other controls in this column with <xref:System.Windows.Forms.Control.Anchor%2A> or <xref:System.Windows.Forms.Control.Dock%2A> properties are aligned or stretched to fit this implied column.</span></span> <span data-ttu-id="6e366-119">O comportamento funciona de maneira similar a direções de fluxo horizontal.</span><span class="sxs-lookup"><span data-stu-id="6e366-119">The behavior works in a similar way for horizontal flow directions.</span></span> <span data-ttu-id="6e366-120">O <xref:System.Windows.Forms.FlowLayoutPanel> controle calcula a altura de uma linha implícita do controle filho mais alto na linha, e todos os controles filho encaixados ou ancorados nesta linha são alinhados ou dimensionados para se ajustar à linha implícita.</span><span class="sxs-lookup"><span data-stu-id="6e366-120">The <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the height of an implied row from the tallest child control in the row, and all docked or anchored child controls in this row are aligned or sized to fit the implied row.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e366-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6e366-121">Example</span></span>  
 <span data-ttu-id="6e366-122">A ilustração a seguir mostra quatro botões que são ancorados e encaixados em relação ao botão azul em um <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="6e366-122">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="6e366-123">O <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> é <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span><span class="sxs-lookup"><span data-stu-id="6e366-123">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span></span>  
  
 <span data-ttu-id="6e366-124">![Ancoragem FlowLayoutPanel](./media/net-flpanchorexp.gif "NET_FLPanchorExp")</span><span class="sxs-lookup"><span data-stu-id="6e366-124">![FlowLayoutPanel anchoring](./media/net-flpanchorexp.gif "NET_FLPanchorExp")</span></span>  
  
 <span data-ttu-id="6e366-125">A ilustração a seguir mostra quatro botões que são ancorados e encaixados em relação ao botão azul em um <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="6e366-125">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="6e366-126">O <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> é <xref:System.Windows.Forms.FlowDirection.TopDown>.</span><span class="sxs-lookup"><span data-stu-id="6e366-126">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>  
  
 <span data-ttu-id="6e366-127">![Ancoragem FlowLayoutPanel](./media/vs-flpanchor2.gif "VS_FLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="6e366-127">![FlowLayoutPanel anchoring](./media/vs-flpanchor2.gif "VS_FLPanchor2")</span></span>  
  
 <span data-ttu-id="6e366-128">O exemplo de código a seguir demonstra vários <xref:System.Windows.Forms.Control.Anchor%2A> valores de propriedades de um <xref:System.Windows.Forms.Button> de controle em um <xref:System.Windows.Forms.FlowLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="6e366-128">The following code example demonstrates various <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6e366-129">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="6e366-129">Compiling the Code</span></span>  
 <span data-ttu-id="6e366-130">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="6e366-130">This example requires:</span></span>  
  
- <span data-ttu-id="6e366-131">Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="6e366-131">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e366-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e366-132">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="6e366-133">Visão geral do controle FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="6e366-133">FlowLayoutPanel Control Overview</span></span>](flowlayoutpanel-control-overview.md)
