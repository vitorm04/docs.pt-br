---
title: 'Como: Ancorar e encaixar controles filho em um controle FlowLayoutPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
ms.openlocfilehash: 3e9a5be944e199254ddb9cee0772c4d55be8fb77
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046062"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="8ec42-102">Como: Ancorar e encaixar controles filho em um controle FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8ec42-102">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>

<span data-ttu-id="8ec42-103">O <xref:System.Windows.Forms.FlowLayoutPanel> <xref:System.Windows.Forms.Control.Dock%2A> controle<xref:System.Windows.Forms.Control.Anchor%2A> oferece suporte às propriedades e em seus controles filho.</span><span class="sxs-lookup"><span data-stu-id="8ec42-103">The <xref:System.Windows.Forms.FlowLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>

### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="8ec42-104">Ancorar e encaixar controles filho em um controle FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8ec42-104">To anchor and dock child controls in a FlowLayoutPanel control</span></span>

1. <span data-ttu-id="8ec42-105">Crie um <xref:System.Windows.Forms.FlowLayoutPanel> controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="8ec42-105">Create a <xref:System.Windows.Forms.FlowLayoutPanel> control on your form.</span></span>

2. <span data-ttu-id="8ec42-106">Defina o <xref:System.Windows.Forms.Control.Width%2A> <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> <xref:System.Windows.Forms.FlowDirection.TopDown>do controle como 300 e defina seu como. <xref:System.Windows.Forms.FlowLayoutPanel></span><span class="sxs-lookup"><span data-stu-id="8ec42-106">Set the <xref:System.Windows.Forms.Control.Width%2A> of the <xref:System.Windows.Forms.FlowLayoutPanel> control to **300**, and set its <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> to <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>

3. <span data-ttu-id="8ec42-107">Crie dois <xref:System.Windows.Forms.Button> controles e coloque-os <xref:System.Windows.Forms.FlowLayoutPanel> no controle.</span><span class="sxs-lookup"><span data-stu-id="8ec42-107">Create two <xref:System.Windows.Forms.Button> controls, and place them in the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

4. <span data-ttu-id="8ec42-108">Defina o <xref:System.Windows.Forms.Control.Width%2A> do primeiro botão como **200**.</span><span class="sxs-lookup"><span data-stu-id="8ec42-108">Set the <xref:System.Windows.Forms.Control.Width%2A> of the first button to **200**.</span></span>

5. <span data-ttu-id="8ec42-109">Defina a <xref:System.Windows.Forms.Control.Dock%2A> Propriedade do segundo botão como <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="8ec42-109">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8ec42-110">O segundo botão assume a mesma largura que o primeiro.</span><span class="sxs-lookup"><span data-stu-id="8ec42-110">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="8ec42-111">Ele não se estende pela largura do <xref:System.Windows.Forms.FlowLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="8ec42-111">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

6. <span data-ttu-id="8ec42-112">Defina a <xref:System.Windows.Forms.Control.Dock%2A> Propriedade do segundo botão como `None`.</span><span class="sxs-lookup"><span data-stu-id="8ec42-112">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to `None`.</span></span> <span data-ttu-id="8ec42-113">Isso faz com que o botão assuma a largura original.</span><span class="sxs-lookup"><span data-stu-id="8ec42-113">This causes the button to assume its original width.</span></span>

7. <span data-ttu-id="8ec42-114">Defina a <xref:System.Windows.Forms.Control.Anchor%2A> Propriedade do segundo botão como `Left, Right`.</span><span class="sxs-lookup"><span data-stu-id="8ec42-114">Set the <xref:System.Windows.Forms.Control.Anchor%2A> property of the second button to `Left, Right`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="8ec42-115">O segundo botão assume a mesma largura que o primeiro.</span><span class="sxs-lookup"><span data-stu-id="8ec42-115">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="8ec42-116">Ele não se estende pela largura do <xref:System.Windows.Forms.FlowLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="8ec42-116">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span> <span data-ttu-id="8ec42-117">Essa é a regra geral para ancorar e encaixar <xref:System.Windows.Forms.FlowLayoutPanel> no controle: para direções de fluxo vertical <xref:System.Windows.Forms.FlowLayoutPanel> , o controle calcula a largura de uma coluna implícita do controle filho mais largo na coluna.</span><span class="sxs-lookup"><span data-stu-id="8ec42-117">This is the general rule for anchoring and docking in the <xref:System.Windows.Forms.FlowLayoutPanel> control: for vertical flow directions, the <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the width of an implied column from the widest child control in the column.</span></span> <span data-ttu-id="8ec42-118">Todos os outros controles nesta coluna com <xref:System.Windows.Forms.Control.Anchor%2A> propriedades <xref:System.Windows.Forms.Control.Dock%2A> or são alinhados ou ampliados para se ajustarem a essa coluna implícita.</span><span class="sxs-lookup"><span data-stu-id="8ec42-118">All other controls in this column with <xref:System.Windows.Forms.Control.Anchor%2A> or <xref:System.Windows.Forms.Control.Dock%2A> properties are aligned or stretched to fit this implied column.</span></span> <span data-ttu-id="8ec42-119">O comportamento funciona de maneira similar a direções de fluxo horizontal.</span><span class="sxs-lookup"><span data-stu-id="8ec42-119">The behavior works in a similar way for horizontal flow directions.</span></span> <span data-ttu-id="8ec42-120">O <xref:System.Windows.Forms.FlowLayoutPanel> controle calcula a altura de uma linha implícita do controle filho mais alto na linha e todos os controles filho ancorados ou ancorados nessa linha são alinhados ou dimensionados para se ajustarem à linha implícita.</span><span class="sxs-lookup"><span data-stu-id="8ec42-120">The <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the height of an implied row from the tallest child control in the row, and all docked or anchored child controls in this row are aligned or sized to fit the implied row.</span></span>

## <a name="example"></a><span data-ttu-id="8ec42-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8ec42-121">Example</span></span>

<span data-ttu-id="8ec42-122">A ilustração a seguir mostra quatro botões que são ancorados e encaixados em relação ao botão <xref:System.Windows.Forms.FlowLayoutPanel>azul em um.</span><span class="sxs-lookup"><span data-stu-id="8ec42-122">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="8ec42-123">O <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> é <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span><span class="sxs-lookup"><span data-stu-id="8ec42-123">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span></span>

<span data-ttu-id="8ec42-124">![Ancoragem FlowLayoutPanel](./media/net-flpanchorexp.gif "NET_FLPanchorExp")</span><span class="sxs-lookup"><span data-stu-id="8ec42-124">![FlowLayoutPanel anchoring](./media/net-flpanchorexp.gif "NET_FLPanchorExp")</span></span>

<span data-ttu-id="8ec42-125">A ilustração a seguir mostra quatro botões que são ancorados e encaixados em relação ao botão <xref:System.Windows.Forms.FlowLayoutPanel>azul em um.</span><span class="sxs-lookup"><span data-stu-id="8ec42-125">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="8ec42-126">O <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> é <xref:System.Windows.Forms.FlowDirection.TopDown>.</span><span class="sxs-lookup"><span data-stu-id="8ec42-126">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>

<span data-ttu-id="8ec42-127">![Ancoragem FlowLayoutPanel](./media/vs-flpanchor2.gif "VS_FLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="8ec42-127">![FlowLayoutPanel anchoring](./media/vs-flpanchor2.gif "VS_FLPanchor2")</span></span>

<span data-ttu-id="8ec42-128">O exemplo de código a seguir <xref:System.Windows.Forms.Control.Anchor%2A> demonstra vários valores de <xref:System.Windows.Forms.Button> propriedade para um <xref:System.Windows.Forms.FlowLayoutPanel> controle em um controle.</span><span class="sxs-lookup"><span data-stu-id="8ec42-128">The following code example demonstrates various <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

[!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
[!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]

## <a name="compiling-the-code"></a><span data-ttu-id="8ec42-129">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="8ec42-129">Compiling the Code</span></span>

<span data-ttu-id="8ec42-130">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="8ec42-130">This example requires:</span></span>

- <span data-ttu-id="8ec42-131">Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="8ec42-131">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ec42-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ec42-132">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="8ec42-133">Visão geral do controle FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8ec42-133">FlowLayoutPanel Control Overview</span></span>](flowlayoutpanel-control-overview.md)
