---
title: Como ancorar e encaixar controles filho em um controle FlowLayoutPanel
description: Saiba como ancorar e encaixar controles filho de forma programática em um controle FlowLayoutPanel Windows Forms.
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
ms.openlocfilehash: b4fb3bf6d148a526a75926bd67c1f967286332bf
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174530"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="7d7ac-103">Como ancorar e encaixar controles filho em um controle FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7d7ac-103">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>

<span data-ttu-id="7d7ac-104">O <xref:System.Windows.Forms.FlowLayoutPanel> controle oferece suporte <xref:System.Windows.Forms.Control.Anchor%2A> às <xref:System.Windows.Forms.Control.Dock%2A> Propriedades e em seus controles filho.</span><span class="sxs-lookup"><span data-stu-id="7d7ac-104">The <xref:System.Windows.Forms.FlowLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>

### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="7d7ac-105">Ancorar e encaixar controles filho em um controle FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7d7ac-105">To anchor and dock child controls in a FlowLayoutPanel control</span></span>

1. <span data-ttu-id="7d7ac-106">Crie um <xref:System.Windows.Forms.FlowLayoutPanel> controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="7d7ac-106">Create a <xref:System.Windows.Forms.FlowLayoutPanel> control on your form.</span></span>

2. <span data-ttu-id="7d7ac-107">Defina o <xref:System.Windows.Forms.Control.Width%2A> do <xref:System.Windows.Forms.FlowLayoutPanel> controle como **300**e defina seu <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> como <xref:System.Windows.Forms.FlowDirection.TopDown> .</span><span class="sxs-lookup"><span data-stu-id="7d7ac-107">Set the <xref:System.Windows.Forms.Control.Width%2A> of the <xref:System.Windows.Forms.FlowLayoutPanel> control to **300**, and set its <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> to <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>

3. <span data-ttu-id="7d7ac-108">Crie dois <xref:System.Windows.Forms.Button> controles e coloque-os no <xref:System.Windows.Forms.FlowLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="7d7ac-108">Create two <xref:System.Windows.Forms.Button> controls, and place them in the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

4. <span data-ttu-id="7d7ac-109">Defina o <xref:System.Windows.Forms.Control.Width%2A> do primeiro botão como **200**.</span><span class="sxs-lookup"><span data-stu-id="7d7ac-109">Set the <xref:System.Windows.Forms.Control.Width%2A> of the first button to **200**.</span></span>

5. <span data-ttu-id="7d7ac-110">Defina a <xref:System.Windows.Forms.Control.Dock%2A> Propriedade do segundo botão como <xref:System.Windows.Forms.DockStyle.Fill> .</span><span class="sxs-lookup"><span data-stu-id="7d7ac-110">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7d7ac-111">O segundo botão assume a mesma largura que o primeiro.</span><span class="sxs-lookup"><span data-stu-id="7d7ac-111">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="7d7ac-112">Ele não se estende pela largura do <xref:System.Windows.Forms.FlowLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="7d7ac-112">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

6. <span data-ttu-id="7d7ac-113">Defina a <xref:System.Windows.Forms.Control.Dock%2A> Propriedade do segundo botão como `None` .</span><span class="sxs-lookup"><span data-stu-id="7d7ac-113">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to `None`.</span></span> <span data-ttu-id="7d7ac-114">Isso faz com que o botão assuma a largura original.</span><span class="sxs-lookup"><span data-stu-id="7d7ac-114">This causes the button to assume its original width.</span></span>

7. <span data-ttu-id="7d7ac-115">Defina a <xref:System.Windows.Forms.Control.Anchor%2A> Propriedade do segundo botão como `Left, Right` .</span><span class="sxs-lookup"><span data-stu-id="7d7ac-115">Set the <xref:System.Windows.Forms.Control.Anchor%2A> property of the second button to `Left, Right`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="7d7ac-116">O segundo botão assume a mesma largura que o primeiro.</span><span class="sxs-lookup"><span data-stu-id="7d7ac-116">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="7d7ac-117">Ele não se estende pela largura do <xref:System.Windows.Forms.FlowLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="7d7ac-117">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span> <span data-ttu-id="7d7ac-118">Essa é a regra geral para ancorar e encaixar no <xref:System.Windows.Forms.FlowLayoutPanel> controle: para direções de fluxo vertical, o <xref:System.Windows.Forms.FlowLayoutPanel> controle calcula a largura de uma coluna implícita do controle filho mais largo na coluna.</span><span class="sxs-lookup"><span data-stu-id="7d7ac-118">This is the general rule for anchoring and docking in the <xref:System.Windows.Forms.FlowLayoutPanel> control: for vertical flow directions, the <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the width of an implied column from the widest child control in the column.</span></span> <span data-ttu-id="7d7ac-119">Todos os outros controles nesta coluna com <xref:System.Windows.Forms.Control.Anchor%2A> <xref:System.Windows.Forms.Control.Dock%2A> Propriedades or são alinhados ou ampliados para se ajustarem a essa coluna implícita.</span><span class="sxs-lookup"><span data-stu-id="7d7ac-119">All other controls in this column with <xref:System.Windows.Forms.Control.Anchor%2A> or <xref:System.Windows.Forms.Control.Dock%2A> properties are aligned or stretched to fit this implied column.</span></span> <span data-ttu-id="7d7ac-120">O comportamento funciona de maneira similar a direções de fluxo horizontal.</span><span class="sxs-lookup"><span data-stu-id="7d7ac-120">The behavior works in a similar way for horizontal flow directions.</span></span> <span data-ttu-id="7d7ac-121">O <xref:System.Windows.Forms.FlowLayoutPanel> controle calcula a altura de uma linha implícita do controle filho mais alto na linha e todos os controles filho ancorados ou ancorados nessa linha são alinhados ou dimensionados para se ajustarem à linha implícita.</span><span class="sxs-lookup"><span data-stu-id="7d7ac-121">The <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the height of an implied row from the tallest child control in the row, and all docked or anchored child controls in this row are aligned or sized to fit the implied row.</span></span>

## <a name="example"></a><span data-ttu-id="7d7ac-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7d7ac-122">Example</span></span>

<span data-ttu-id="7d7ac-123">A ilustração a seguir mostra quatro botões que são ancorados e encaixados em relação ao botão azul em um <xref:System.Windows.Forms.FlowLayoutPanel> .</span><span class="sxs-lookup"><span data-stu-id="7d7ac-123">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="7d7ac-124">O <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> é <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span><span class="sxs-lookup"><span data-stu-id="7d7ac-124">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span></span>

<span data-ttu-id="7d7ac-125">![Ancoragem de FlowLayoutPanel](./media/net-flpanchorexp.gif "NET_FLPanchorExp")</span><span class="sxs-lookup"><span data-stu-id="7d7ac-125">![FlowLayoutPanel anchoring](./media/net-flpanchorexp.gif "NET_FLPanchorExp")</span></span>

<span data-ttu-id="7d7ac-126">A ilustração a seguir mostra quatro botões que são ancorados e encaixados em relação ao botão azul em um <xref:System.Windows.Forms.FlowLayoutPanel> .</span><span class="sxs-lookup"><span data-stu-id="7d7ac-126">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="7d7ac-127">O <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> é <xref:System.Windows.Forms.FlowDirection.TopDown>.</span><span class="sxs-lookup"><span data-stu-id="7d7ac-127">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>

<span data-ttu-id="7d7ac-128">![Ancoragem de FlowLayoutPanel](./media/vs-flpanchor2.gif "VS_FLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="7d7ac-128">![FlowLayoutPanel anchoring](./media/vs-flpanchor2.gif "VS_FLPanchor2")</span></span>

<span data-ttu-id="7d7ac-129">O exemplo de código a seguir demonstra vários <xref:System.Windows.Forms.Control.Anchor%2A> valores de propriedade para um <xref:System.Windows.Forms.Button> controle em um <xref:System.Windows.Forms.FlowLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="7d7ac-129">The following code example demonstrates various <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

[!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
[!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]

## <a name="compiling-the-code"></a><span data-ttu-id="7d7ac-130">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="7d7ac-130">Compiling the Code</span></span>

<span data-ttu-id="7d7ac-131">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="7d7ac-131">This example requires:</span></span>

- <span data-ttu-id="7d7ac-132">Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="7d7ac-132">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d7ac-133">Veja também</span><span class="sxs-lookup"><span data-stu-id="7d7ac-133">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="7d7ac-134">Visão geral do controle FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7d7ac-134">FlowLayoutPanel Control Overview</span></span>](flowlayoutpanel-control-overview.md)
