---
title: Como ancorar controles nos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Anchor property [Windows Forms], enabling resizable forms
- Windows Forms controls, screen resolutions
- resizing forms [Windows Forms]
- Windows Forms controls, size
- screen resolution and control display
- controls [Windows Forms], anchoring
- forms [Windows Forms], resizing
- Windows Forms, resizing
- controls [Windows Forms], positioning
ms.assetid: 59ea914f-fbd3-427a-80fe-decd02f7ae6d
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 15f12cb0d389344351c4ddf97ee9db37882de460
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459684"
---
# <a name="how-to-anchor-controls-on-windows-forms"></a><span data-ttu-id="5808c-102">Como: ancorar controles em Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5808c-102">How to: Anchor controls on Windows Forms</span></span>

<span data-ttu-id="5808c-103">Se você estiver criando um formulário que o usuário pode redimensionar em tempo de execução, os controles em seu formulário devem ser redimensionados e reposicionados corretamente.</span><span class="sxs-lookup"><span data-stu-id="5808c-103">If you're designing a form that the user can resize at run time, the controls on your form should resize and reposition properly.</span></span> <span data-ttu-id="5808c-104">Para redimensionar controles dinamicamente com o formulário, você pode usar a propriedade <xref:System.Windows.Forms.Control.Anchor%2A> de controles de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5808c-104">To resize controls dynamically with the form, you can use the <xref:System.Windows.Forms.Control.Anchor%2A> property of Windows Forms controls.</span></span> <span data-ttu-id="5808c-105">A propriedade <xref:System.Windows.Forms.Control.Anchor%2A> define uma posição de ancoragem para o controle.</span><span class="sxs-lookup"><span data-stu-id="5808c-105">The <xref:System.Windows.Forms.Control.Anchor%2A> property defines an anchor position for the control.</span></span> <span data-ttu-id="5808c-106">Quando um controle é ancorado a um formulário e esse formulário é redimensionado, o controle mantém a distância entre o controle e as posições de âncora.</span><span class="sxs-lookup"><span data-stu-id="5808c-106">When a control is anchored to a form and the form is resized, the control maintains the distance between the control and the anchor positions.</span></span> <span data-ttu-id="5808c-107">Por exemplo, se você tiver um controle de <xref:System.Windows.Forms.TextBox> que está ancorado nas bordas esquerda, direita e inferior do formulário, à medida que o formulário for redimensionado, o controle de <xref:System.Windows.Forms.TextBox> redimensiona horizontalmente para que ele mantenha a mesma distância dos lados direito e esquerdo do formulário.</span><span class="sxs-lookup"><span data-stu-id="5808c-107">For example, if you have a <xref:System.Windows.Forms.TextBox> control that is anchored to the left, right, and bottom edges of the form, as the form is resized, the <xref:System.Windows.Forms.TextBox> control resizes horizontally so that it maintains the same distance from the right and left sides of the form.</span></span> <span data-ttu-id="5808c-108">Além disso, o controle se posiciona verticalmente para que sua localização seja sempre a mesma distância da borda inferior do formulário.</span><span class="sxs-lookup"><span data-stu-id="5808c-108">In addition, the control positions itself vertically so that its location is always the same distance from the bottom edge of the form.</span></span> <span data-ttu-id="5808c-109">Se um controle não estiver ancorado e o formulário for redimensionado, a posição do controle em relação às bordas do formulário será alterada.</span><span class="sxs-lookup"><span data-stu-id="5808c-109">If a control is not anchored and the form is resized, the position of the control relative to the edges of the form is changed.</span></span>

<span data-ttu-id="5808c-110">A propriedade <xref:System.Windows.Forms.Control.Anchor%2A> interage com a propriedade <xref:System.Windows.Forms.Control.AutoSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="5808c-110">The <xref:System.Windows.Forms.Control.Anchor%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="5808c-111">Para obter mais informações, consulte [Visão Geral da Propriedade AutoSize](autosize-property-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5808c-111">For more information, see [AutoSize Property Overview](autosize-property-overview.md).</span></span>

## <a name="anchor-a-control-on-a-form"></a><span data-ttu-id="5808c-112">Ancorar um controle em um formulário</span><span class="sxs-lookup"><span data-stu-id="5808c-112">Anchor a control on a form</span></span>

1. <span data-ttu-id="5808c-113">No Visual Studio, selecione o controle que você deseja ancorar.</span><span class="sxs-lookup"><span data-stu-id="5808c-113">In Visual Studio, select the control you want to anchor.</span></span>

    > [!NOTE]
    > <span data-ttu-id="5808c-114">É possível ancorar vários controles simultaneamente pressionando a tecla CTRL, clicando em cada controle para selecioná-lo e, em seguida, seguindo o resto desse procedimento.</span><span class="sxs-lookup"><span data-stu-id="5808c-114">You can anchor multiple controls simultaneously by pressing the CTRL key, clicking each control to select it, and then following the rest of this procedure.</span></span>

2. <span data-ttu-id="5808c-115">Na janela **Propriedades** , clique na seta à direita da propriedade <xref:System.Windows.Forms.Control.Anchor%2A>.</span><span class="sxs-lookup"><span data-stu-id="5808c-115">In the **Properties** window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span>

     <span data-ttu-id="5808c-116">Um editor será exibido e mostra uma cruz.</span><span class="sxs-lookup"><span data-stu-id="5808c-116">An editor is displayed that shows a cross.</span></span>

3. <span data-ttu-id="5808c-117">Para definir uma âncora, clique na seção superior, esquerda, direita ou inferior da cruz.</span><span class="sxs-lookup"><span data-stu-id="5808c-117">To set an anchor, click the top, left, right, or bottom section of the cross.</span></span>

     <span data-ttu-id="5808c-118">Os controles estão ancorados na parte superior e esquerda por padrão.</span><span class="sxs-lookup"><span data-stu-id="5808c-118">Controls are anchored to the top and left by default.</span></span>

4. <span data-ttu-id="5808c-119">Para limpar um lado do controle que foi ancorado, clique nessa parte da cruz.</span><span class="sxs-lookup"><span data-stu-id="5808c-119">To clear a side of the control that has been anchored, click that arm of the cross.</span></span>

5. <span data-ttu-id="5808c-120">Para fechar o editor de propriedades <xref:System.Windows.Forms.Control.Anchor%2A>, clique no nome da propriedade <xref:System.Windows.Forms.Control.Anchor%2A> novamente.</span><span class="sxs-lookup"><span data-stu-id="5808c-120">To close the <xref:System.Windows.Forms.Control.Anchor%2A> property editor, click the <xref:System.Windows.Forms.Control.Anchor%2A> property name again.</span></span>

<span data-ttu-id="5808c-121">Quando o formulário é exibido em tempo de execução, o controle é redimensionado para permanecer posicionado na mesma distância da borda do formulário.</span><span class="sxs-lookup"><span data-stu-id="5808c-121">When your form is displayed at run time, the control resizes to remain positioned at the same distance from the edge of the form.</span></span> <span data-ttu-id="5808c-122">A distância da borda ancorada sempre é a mesma distância definida quando o controle é posicionado no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="5808c-122">The distance from the anchored edge always remains the same as the distance defined when the control is positioned in the Windows Forms Designer.</span></span>

> [!NOTE]
> <span data-ttu-id="5808c-123">Determinados controles, como o controle de <xref:System.Windows.Forms.ComboBox>, têm um limite para sua altura.</span><span class="sxs-lookup"><span data-stu-id="5808c-123">Certain controls, such as the <xref:System.Windows.Forms.ComboBox> control, have a limit to their height.</span></span> <span data-ttu-id="5808c-124">Ancorar o controle na parte inferior do formulário ou contêiner não pode forçar o controle a exceder o limite de altura.</span><span class="sxs-lookup"><span data-stu-id="5808c-124">Anchoring the control to the bottom of its form or container cannot force the control to exceed its height limit.</span></span>

<span data-ttu-id="5808c-125">Controles herdados devem ser `Protected` para serem ancorados.</span><span class="sxs-lookup"><span data-stu-id="5808c-125">Inherited controls must be `Protected` to be able to be anchored.</span></span> <span data-ttu-id="5808c-126">Para alterar o nível de acesso de um controle, defina sua propriedade `Modifiers` na janela **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="5808c-126">To change the access level of a control, set its `Modifiers` property in the **Properties** window.</span></span>

## <a name="see-also"></a><span data-ttu-id="5808c-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5808c-127">See also</span></span>

- [<span data-ttu-id="5808c-128">Controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5808c-128">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="5808c-129">Visão geral da propriedade AutoSize</span><span class="sxs-lookup"><span data-stu-id="5808c-129">AutoSize Property Overview</span></span>](autosize-property-overview.md)
- [<span data-ttu-id="5808c-130">Como encaixar controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5808c-130">How to: Dock Controls on Windows Forms</span></span>](how-to-dock-controls-on-windows-forms.md)
- [<span data-ttu-id="5808c-131">Passo a passo: organizando controles nos Windows Forms utilizando um FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="5808c-131">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="5808c-132">Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="5808c-132">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="5808c-133">Passo a passo: definindo o layout de controles dos Windows Forms com preenchimento, margens e a propriedade AutoSize</span><span class="sxs-lookup"><span data-stu-id="5808c-133">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)
